# Low-Fidelity Mobile Wireframes: Automated Microloan Onboarding
**Project:** Digital Microloan Onboarding Optimization  
**Traceability:** Aligned with `FR-01` to `FR-05` and `US-01` to `US-05`  

---

## 1. UX Design Principles
* **Zero Manual Uploads:** Replaces PDF statements and certified ID scans with real-time DHA and Open Banking API screens.
* **Resilient Mobile UX (`US-05`):** Displays an auto-save status indicator so users can safely resume within 7 days if mobile data drops.
* **Regulatory Transparency (`US-03`, `US-04`):** Embeds explicit POPIA consent and NCA cost-of-credit breakdowns directly into the user journey.

---

## 2. Mobile Screen Flow

### Screen 1: 13-Digit SA ID Validation (`FR-01` | `US-01`)
* **Behavior:** Validates the 13-digit SA ID number in real time using the Luhn checksum and checks that applicant age is ≥ 18 before enabling **Continue**.

```text
+---------------------------------------+

|  < Back     Identity Check    Step 1/4|
|  [✓ Progress auto-saved]              |
|---------------------------------------|
|  Enter your South African ID Number   |
|  We use this for instant FICA checks. |
|                                       |
|  SA ID Number (13 Digits):            |
|  [ 950412 5089 08 2 ]  [✓]            |
|  * Real-time Luhn & Age (18+) check   |
|                                       |
|  Mobile Number (for OTP & Updates):   |
|  [ +27  |  82 555 1234        ]       |
|                                       |
|  [x] Save my progress for 7 days      |
|                                       |
|  [      Continue to Selfie Check    ] |
+---------------------------------------+
```

---

### Screen 2: Live Selfie Biometric Verification (`FR-02` | `US-02`)
* **Behavior:** Captures a live selfie and verifies against Department of Home Affairs (DHA) records within 30 seconds. After **3 failed attempts**, automatically routes to the **Compliance Queue** (`02-Process-Models`).

```text
+---------------------------------------+

|  < Back     Live Biometric    Step 2/4|
|  [✓ Progress auto-saved]              |
|---------------------------------------|
|  Take a quick live selfie             |
|  Ensure you are in a well-lit area.   |
|                                       |
|  +---------------------------------+  |
|  |                                 |  |
|  |           . - ~ - .             |  |
|  |         /   o   o   \           |  |
|  |        |      ^      |          |  |
|  |         \   \___/   /           |  |
|  |           ' - _ - '             |  |
|  |     Position face inside oval   |  |
|  +---------------------------------+  |
|                                       |
|  Attempt 1 of 3 • DHA API Verification|
|                                       |
|  [          Capture Selfie          ] |
+---------------------------------------+
```

---

### Screen 3: POPIA Consent & Open Banking API (`FR-03` | `US-03`)
* **Behavior:** Obtains explicit digital POPIA consent before securely retrieving 90 days of transactional bank history via Open Banking API.

```text
+---------------------------------------+

|  < Back     Bank Verification Step 3/4|
|  [✓ Progress auto-saved]              |
|---------------------------------------|
|  Connect your primary salary account  |
|  No PDF uploads needed (90-day check).|
|                                       |
|  Select Your Bank:                    |
|  [  Capitec  ]       [    FNB    ]    |
|  [  Standard ]       [   Absa    ]    |
|  [  Nedbank  ]       [  TymeBank ]    |
|                                       |
|  POPIA Data-Sharing Disclosure:       |
|  [x] I consent to read-only retrieval |
|      of 90-day bank statements for    |
|      NCA affordability assessment.    |
|                                       |
|  [    I Consent & Connect Bank      ] |
|  [     Decline & Pause Application  ] |
+---------------------------------------+
```

---

### Screen 4A: Auto-Approved Instant Offer (`FR-04` | `US-04`)
* **Behavior:** Triggered on the **Yes** branch of `Auto-Approved?` in the To-Be BPMN diagram, presenting a personalized NCA-compliant offer within 15 seconds.

```text
+---------------------------------------+

|  Instant Loan Offer 🎉        Step 4/4|
|  Decision Time: 11 mins 40 secs       |
|---------------------------------------|
|  You qualify for up to:               |
|  [  R 4,500.00  ]                     |
|  R500 -----------o----------- R4,500  |
|                                       |
|  Repayment Term:  (•) 3 Mo   ( ) 6 Mo |
|                                       |
|  NCA Cost Breakdown:                  |
|  • Monthly Installment:    R 1,715.00 |
|  • Interest Rate (p.a.):        27.5% |
|  • Initiation & Service Fee: Included |
|  • Total Repayable:        R 5,145.00 |
|                                       |
|  [  Accept Offer & Instant EFT Payout ]|
+---------------------------------------+
```

---

### Screen 4B: Exception State — Compliance Queue (`US-02` / `To-Be BPMN`)
* **Behavior:** Triggered on the **No** branch of `Auto-Approved?` or after 3 failed selfie matches.

```text
+---------------------------------------+

|  Application In Review        Step 4/4|
|  Ref: #ML-2026-8841                   |
|---------------------------------------|
|  [ ! ] Additional Verification Needed |
|                                       |
|  Your details have been securely      |
|  routed to our Compliance Queue for   |
|  a quick manual check.                |
|                                       |
|  • No need to re-upload documents.    |
|  • We will notify you via SMS/App     |
|    as soon as review is complete.     |
|                                       |
|  [         Back to Dashboard        ] |
+---------------------------------------+
```
