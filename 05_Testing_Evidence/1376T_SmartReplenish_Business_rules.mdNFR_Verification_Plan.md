# NFR Verification Plan (Performance, Safety, Security)

**Purpose:** This document defines how the project team will verify the Nonfunctional Requirements (NFRs) in Section 6.  
**Scope:** Performance (NFR-PR-xx), Safety (NFR-SAF-xx), Security (NFR-SEC-xx).  
**Method types:** Test (T), Inspection (I), Analysis/Review (A), Log Review (L).

---

## 1. Test Environment

### 1.1 Reference Mobile Device Profile (example)
- **OS:** Android 6.0+ (minimum supported)
- **CPU/RAM:** Mid-tier reference (e.g., 8-core, 3–4GB RAM)
- **Network:** Wi-Fi (stable), 4G/5G (typical), throttled (poor network simulation)

### 1.2 Backend Environment (example)
- **Deployment:** Azure-hosted services (staging environment)
- **Database:** Azure-managed SQL / equivalent
- **Logging:** Centralized logs enabled (request IDs, timestamps, status codes)

> **Note:** Replace device/back-end specifics with your actual project environment if needed.

---

## 2. Test Data Profiles

### 2.1 Dataset A (Typical User Dataset)
- Inventory items: **100**
- Mix: branded + generic items
- Includes: expiry dates, category assignments

### 2.2 Dataset B (Stress List View)
- Inventory items: **300** (used to validate list load constraints)

### 2.3 Dataset C (Barcode Set)
- A set of **30 barcodes**:
  - 20 valid lookups (existing catalogue)
  - 10 lookup failures (to test fallback/manual entry)

---

## 3. Verification Matrix

### 3.1 Performance NFR Verification (NFR-PR)

| NFR ID | Requirement (summary) | Method | Test Procedure (high level) | Pass/Fail Evidence |
|---|---|---|---|---|
| NFR-PR-01 | Cold start ≤ 4s to Home | T | Force-stop app → launch → time until Home displayed (10 trials) | Avg + worst-case times recorded |
| NFR-PR-02 | Warm resume ≤ 2s | T | Send app to background → resume → time to interactive state (10 trials) | Avg + worst-case times recorded |
| NFR-PR-03 | Inventory list load ≤ 2s (≤300 items) | T | Seed Dataset B → open inventory list → measure render time (10 trials) | Timing logs/screenshots |
| NFR-PR-04 | Update reflects on-screen ≤ 1s after save | T | Update qty/expiry → tap save → time until UI reflects change (10 trials) | Screen recording/timing |
| NFR-PR-05 | Scan-to-result ≤ 2s (online) | T | Scan barcodes in Dataset C (valid) → measure time to result (20 trials) | Timing logs |
| NFR-PR-06 | 95% API responses ≤ 1.5s | T/L | Run scripted API calls (n≥200) → compute 95th percentile latency | Log export + percentile calc |
| NFR-PR-07 | Sync completes ≤ 60s after reconnect | T | Disable network → make allowed actions (or view-only) → reconnect → measure sync completion | Sync timestamp evidence |
| NFR-PR-08 | UI remains responsive on poor network | T | Throttle network → repeat key flows → confirm no ANR/freeze; progress shown | Screen recording + notes |
| NFR-PR-09 | Price refresh non-blocking; cached if >3s | T/I | Trigger price refresh under throttling → verify UI usable and cached+freshness shown | Screenshot evidence |
| NFR-PR-10 | No runaway memory growth over 15 min | T/A | Continuous usage scenario (15 min) + profiler sampling | Profiler screenshots/logs |

---

### 3.2 Safety NFR Verification (NFR-SAF)

| NFR ID | Requirement (summary) | Method | Test Procedure (high level) | Pass/Fail Evidence |
|---|---|---|---|---|
| NFR-SAF-01 | Confirm destructive actions | T/I | Attempt delete/clear → confirm prompt appears and blocks unintended delete | Screenshots |
| NFR-SAF-02 | Undo within 10s where feasible | T | Delete item → confirm Undo appears → restore within 10s | Screen recording |
| NFR-SAF-03 | Reject invalid inputs + helpful error | T | Enter negative qty / invalid dates → verify blocked + message | Screenshots |
| NFR-SAF-04 | Show “Last synced at …” when offline/fail | T | Go offline or force sync fail → verify timestamp visible | Screenshot evidence |
| NFR-SAF-05 | Safe degraded mode when backend unreachable | T | Simulate backend outage → attempt restricted actions → verify system prevents inconsistent states + informs user | Screenshots/notes |
| NFR-SAF-06 | Expiry messaging is guidance (no certification claims) | I | Review UI copy for expiry alerts and notices | Review checklist |

---

### 3.3 Security NFR Verification (NFR-SEC)

| NFR ID | Requirement (summary) | Method | Test Procedure (high level) | Pass/Fail Evidence |
|---|---|---|---|---|
| NFR-SEC-01 | HTTPS + TLS 1.2+ | T/I | Inspect network calls using proxy tool; verify HTTPS; confirm TLS version | Capture evidence |
| NFR-SEC-02 | Encryption at rest | I/A | Inspect cloud config (managed encryption settings) | Configuration screenshots |
| NFR-SEC-03 | Token auth + expiry enforced | T | Obtain token → wait/force expiry → verify requests rejected after expiry | API response logs |
| NFR-SEC-04 | Secure token storage; no plaintext in logs | I/T | Inspect storage approach + search logs for token strings | Code/log review notes |
| NFR-SEC-05 | Reset token single-use + 24h expiry | T | Request reset → use token once → ensure reuse fails; test expiry behaviour | Test notes |
| NFR-SEC-06 | RBAC for admin actions | T | Attempt privileged actions under non-privileged role → verify denied | Screenshots/logs |
| NFR-SEC-07 | Audit log security events | L/I | Trigger login/fail login/catalogue edit → confirm log entries present | Log excerpts |
| NFR-SEC-08 | Rate limiting login/reset attempts | T/L | Exceed threshold attempts → verify blocked/cooldown response | Logs/screenshots |
| NFR-SEC-09 | Data minimization (no unnecessary identifiers) | I/A | Review data fields stored vs purposes | Data inventory review |
| NFR-SEC-10 | Admin process for data access/correction/deletion | I | Inspect admin workflow documentation and UI/admin endpoints | Checklist + notes |

---

## 4. Evidence Recording Template

Use this mini-template per NFR when you execute tests:

- **NFR ID:**  
- **Date/Tester:**  
- **Environment:** (device, OS, build, network, backend)  
- **Steps Taken:**  
- **Observed Result:**  
- **Evidence:** (screenshots, logs, recordings, profiler output)  
- **Pass/Fail:**  
- **Notes/Issues:**  

---

## 5. Repository Cross-References

- Quality scenarios are in: `02_Analysis/Quality_Attribute_Scenarios_McCall.md`
- Business rules catalogue is in: `01_Requirements/Business_Rules_Catalog.md`
