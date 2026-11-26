# Business Requirements Document (BRD)
**Project:** Digital Microloan Onboarding Optimization  
**Role:** Business Systems Analyst  
**Version:** 1.0  

---

## 1. Problem Statement & Opportunity
Currently, mobile microloan applicants must manually scan and upload South African ID documents, proof of residence, and 3 months of bank statements. Manual verification by back-office credit agents creates a **48-hour bottleneck**, resulting in a **42% application abandonment rate**. Automating KYC/FICA checks and bank statement retrieval via third-party APIs will reduce decisioning time to under 15 minutes.

## 2. Project Scope
### In-Scope
* Digital selfie biometric verification integrated with Department of Home Affairs (DHA) database.
* Automated 90-day bank statement retrieval via Open Banking / DebiCheck-compliant APIs.
* Automated affordability calculation aligned with the **National Credit Act (NCA)**.
* Real-time SMS/in-app status notifications for applicants.

### Out-of-Scope
* Business or commercial loans exceeding R50,000.
* Manual branch-based walk-in loan processing.
* Core banking ledger replacement.

## 3. Stakeholder Analysis

| Stakeholder | Role / Department | Key Interest / Requirement |
| :--- | :--- | :--- |
| **Loan Applicant** | External Customer | Fast, low-data mobile application with instant payout clarity. |
| **Credit Risk Team** | Internal Risk & Underwriting | Accurate income/expense data to prevent reckless lending (NCA). |
| **Compliance Officer** | Legal & Regulatory | Strict adherence to **FICA** verification and **POPIA** consent rules. |
| **Mobile Dev Squad** | IT Engineering | Clear API specifications, field validations, and error states. |

## 4. Functional Requirements (MoSCoW Prioritized)
* **FR-01 [Must Have]:** The system shall allow applicants to enter their 13-digit South African ID number and validate checksum digits in real time.
* **FR-02 [Must Have]:** The system shall capture a live selfie and match facial biometrics against DHA records within 30 seconds.
* **FR-03 [Must Have]:** The system shall obtain explicit POPIA digital consent before fetching 3 months of bank statements via API.
* **FR-04 [Must Have]:** The system shall automatically calculate disposable income and maximum eligible loan amount per NCA affordability guidelines.
* **FR-05 [Should Have]:** The system shall save application progress automatically so users can resume if mobile data drops.
* **FR-06 [Could Have]:** The system shall offer an instant WhatsApp status tracker for approved payouts.

## 5. Non-Functional Requirements
* **NFR-01 (Security & Privacy):** All PII (Personally Identifiable Information) must be encrypted in transit (TLS 1.3) and at rest (AES-256) in compliance with **POPIA**.
* **NFR-02 (Performance):** Automated KYC and credit scoring API calls must complete within **15 seconds** under normal load.
* **NFR-03 (Availability):** The onboarding service must maintain **99.9% uptime**, particularly during month-end peak borrowing periods (25th–3rd of each month).
