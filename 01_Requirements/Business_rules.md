# Business Rules Catalog

**Purpose:** Central catalogue of Business Rules (BRs) supporting Section 6.5 (Figure C.5).  
**Convention:** Each rule is written as an enforceable constraint starting with **“The system shall …”**.

---

## 1. Business Rules Table

| BR ID | Rule (The system shall…) | Rationale | Related Use Case / Feature | Owner / Source |
|---|---|---|---|---|
| BR-01 | The system shall ensure each inventory item belongs to exactly **one** category. | Enables consistent filtering, analytics, and alerts. | Add/Update Item | Product Owner / BA |
| BR-02 | The system shall prevent item quantity from being negative. | Prevents invalid inventory states. | Update Quantity | BA |
| BR-03 | The system shall prevent an expiry date from being earlier than the item’s creation/add date. | Prevents invalid date records and misleading alerts. | Add/Update Item | BA |
| BR-04 | The system shall allow users to manually add an item and mark it as “unverified” when barcode lookup fails. | Users are not blocked by lookup failures. | Scan/Add Item | BA |
| BR-05 | The system shall allow users to create and update inventory items while offline by storing changes locally and queuing them for synchronization when connectivity is restored. | Enables offline continuity while ensuring updates are eventually synchronized. | Offline Usage | BA / Tech Lead |
| BR-06 | The system shall display a “last updated” timestamp when showing cached price information. | Prevents misleading representation of real-time pricing. | View Item / Price Display | BA |
| BR-07 | The system shall enforce that a loyalty identifier is unique to one user account at a time. | Prevents identity conflicts and duplication. | Registration/Login | BA |
| BR-08 | The system shall restrict administrative catalogue updates to authorized roles (e.g., Marketing). | Governance and change control. | Admin Dashboard | Business Stakeholder |
| BR-09 | The system shall log security-sensitive administrative actions (e.g., role changes, account actions). | Accountability and auditability. | Admin Dashboard | IT/Admin Stakeholder |
| BR-10 | The system shall enforce personal data retention and deletion in accordance with the project’s defined policy. | Privacy/compliance expectation alignment. | Account/Data Management | BA / Compliance |
| BR-11 | The system shall persist queued offline changes across app restarts until synchronization succeeds or the user discards them. | Prevents loss of user updates made offline and ensures eventual consistency. | Offline Usage / Sync | BA / Tech Lead |
| BR-12 | The system shall synchronize queued offline changes in chronological order (first-in, first-out) when connectivity is restored. | Ensures predictable outcomes and avoids out-of-order overwrites. | Offline Usage / Sync | Tech Lead |
| BR-13 | The system shall detect a synchronization conflict when the same inventory record is modified both locally (offline) and on the server after the user’s last successful sync. | Prevents silent overwriting of newer data and enables controlled conflict handling. | Offline Usage / Sync | Tech Lead |
| BR-14 | The system shall resolve synchronization conflicts by preserving the server value and prompting the user to either accept the server value or re-apply their queued offline change. | Prevents accidental overwriting of newer server data while allowing an informed user decision. | Offline Usage / Sync | BA / Tech Lead |
| BR-15 | The system shall display the synchronization status of offline changes (e.g., Pending Sync, Syncing, Synced, Conflict—Action Required, Failed) to the user. | Improves transparency and prevents users from relying on stale or unsynchronized information. | Offline Usage / Sync Status | BA |

---

## 2. Offline Policy Statement

The project adopts **Option B (Queue edits)**: the system supports offline creation and updates by queuing changes locally and synchronizing them when connectivity is restored. Conflict handling is governed by **BR-13** and **BR-14**, and user visibility is governed by **BR-15**.

---

