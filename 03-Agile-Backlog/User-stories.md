# Agile Product Backlog & User Stories
**Project:** Digital Microloan Onboarding Optimization  
**Methodology:** Scrum / Agile  
**Acceptance Criteria Format:** Behavior-Driven Development (*Given - When - Then*)  

---

## Epic 1: Automated FICA & Identity Verification

### US-01: Real-Time South African ID Validation
* **As a** loan applicant,  
* **I want** the app to immediately validate my 13-digit South African ID number as I type it,  
* **So that** I catch typing mistakes immediately instead of waiting days for a manual rejection.

**Acceptance Criteria:**
* **Given** I am on the personal details screen,  
* **When** I enter a 13-digit SA ID number that fails the Luhn checksum or indicates I am under 18,  
* **Then** the system displays an inline error message explaining the issue and disables the "Continue" button.

---

### US-02: Live Biometric Selfie KYC Check
* **As a** loan applicant,  
* **I want** to verify my identity using a live selfie instead of scanning and uploading a certified ID copy,  
* **So that** I can complete FICA verification from my phone in under a minute.

**Acceptance Criteria:**
* **Given** I have entered a valid SA ID number and granted camera permissions,  
* **When** I capture a live selfie in adequate lighting,  
* **Then** the system compares my facial biometrics against Department of Home Affairs (DHA) records within 30 seconds and confirms verification.
* **And** if the biometric match fails 3 consecutive times, the system routes my application to a manual compliance queue with a clear status message.

---

## Epic 2: Automated Affordability & Open Banking

### US-03: POPIA-Compliant Bank Statement Retrieval
* **As a** loan applicant,  
* **I want** to securely link my primary bank account via Open Banking rather than downloading and uploading PDF bank statements,  
* **So that** my income and expenses are assessed automatically without manual paperwork.

**Acceptance Criteria:**
* **Given** I have passed biometric KYC verification,  
* **When** I review the POPIA data-sharing disclosure and tap "I Consent & Connect Bank",  
* **Then** the system securely retrieves my last 90 days of transactional data via API and confirms receipt.
* **And** if I decline consent, the application pauses cleanly without storing any financial data.

---

### US-04: Instant NCA Affordability & Loan Offer Calculation
* **As a** credit risk system,  
* **I want** to automatically calculate an applicant's net disposable income from retrieved bank transactions,  
* **So that** the loan offer complies with the National Credit Act (NCA) and prevents reckless lending.

**Acceptance Criteria:**
* **Given** 90 days of bank statements have been retrieved,  
* **When** the affordability engine deducts verified living expenses and existing debt obligations from net salary inflows,  
* **Then** the system presents a personalized maximum loan offer, interest rate, and repayment schedule within 15 seconds.

---

## Epic 3: Customer Experience & Drop-Off Recovery

### US-05: Auto-Save & Resume Application Progress
* **As a** mobile user with intermittent data connectivity,  
* **I want** my application progress to save automatically after each completed step,  
* **So that** I don't have to restart from scratch if my connection drops.

**Acceptance Criteria:**
* **Given** I have completed at least Step 1 (ID Verification) and exit the app,  
* **When** I log back into the app within 7 days,  
* **Then** the system restores my saved progress and resumes directly on my next incomplete step.
