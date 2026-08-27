# INNFLOW — Enterprise Hotel Operations & Management Ecosystem
**AICA Level-2 Capstone Project**  
**Author:** CA Ankit Tandon  
**Target Industry:** Hospitality, Hotel Property Management & Internal Financial Controls

---

## 📌 Project Overview

**INNFLOW** is a full-stack, enterprise-grade Hotel Operations and Property Management platform designed to solve operational bottlenecks, prevent financial leakages, enforce multi-tier approval hierarchies, and provide real-time statutory audit transparency across luxury hotel properties.

The system features a **Dual-Access Ecosystem**:
1. **📱 Mobile Application (React Native / Expo / Android APK & AAB)**: Used by floor staff (Housekeeping, Engineering technicians, Duty managers, Security) for real-time room readiness inspections, work order execution, lost & found safekeeping, and instant voice/chat task dispatch.
2. **💻 Web-Based Administration Portal (React / TypeScript / Tailwind)**: Used by General Managers, Financial Controllers, and Department Heads on desktop browsers for capital expenditure approvals, CMMS plant maintenance scheduling, compliance tracking, and revenue reconciliation.
3. **🗄️ Centralized Server & Relational Database (Express / tRPC / Drizzle ORM / MySQL)**: Single source of truth with immutable append-only audit event logging.
4. **☁️ Secure Cloudflare Tunnel Integration (`cloudflared`)**: Encrypted zero-trust connection bridging on-premise PMS/POS feeds and mobile clients with zero open public ports.

---

## 🚀 Key Functional Modules

### 1. Housekeeping & Room Matrix
- Real-time room status board across floors (*Inspected, Clean, Dirty, Out of Order, Do Not Disturb*).
- **Mandatory 5-Star Digital Inspection Checklist Gate**: Programmatic block preventing room release to the PMS until all safety, hygiene, and amenity verification points are checked.

### 2. Purchase Requisitions & Financial Approvals Hierarchy
- Threshold-based authorization workflow for CAPEX and OPEX expenses (e.g. Linen restocking, Spa vouchers, F&B replenishment).
- Complete variance tracking between Point-of-Sale (POS) night audit settlements and PMS front-desk folios.

### 3. Engineering CMMS & Preventative Maintenance (PPM)
- Registry of heavy hotel plant equipment (HVAC Chillers, Steam Boilers, Elevator Banks, Cold Storage).
- Automated preventative maintenance service scheduling with SLA response target tracking.

### 4. Lost & Found Safekeeping Registry
- Digital chain-of-custody tracking with designated locker/vault IDs, item categorization, and verified guest claim handover workflow.

### 5. Hotel ERP Operations & 3-Way Procurement Cockpit
- Integrated inventory management distinguishing usable stock from physical, reserved, and damaged stock.
- 3-Way matching control (*Purchase Order ➔ Goods Receipt ➔ Invoice*) with automated payment holds on discrepancies.
- Perishable goods tracking with First-Expired, First-Out (FEFO) watchlists and booking-driven demand shortage signals.

### 6. Statutory Compliance & License Register
- Tracking statutory operating permits (Fire Safety Certificates, FSSAI/Food Handling Licenses, Lift Inspection Registers, Public Liability Insurance) with automated renewal lead-time alerts.

### 7. Team Shift Roster & Instant Dispatcher
- Real-time staff accountability map tracking active duty statuses (*On Floor, On Task, On Break, Off Duty*) with direct task dispatching.

### 8. Immutable Audit Trail
- Non-repudiable audit logging recording every document creation, approval, status transition, and guest compensation event.

---

## 📂 Codebase Organization

The software is structured into clean architectural layers:
- **🌐 Frontend (`app/`, `components/`, `lib/`, `constants/`)**: Expo Router mobile screens, widescreen desktop web management portal, and offline-first state stores.
- **🖥️ Backend (`server/`)**: Express API server, type-safe tRPC procedure routers, authentication, and CORS security.
- **🗄️ Database (`drizzle/`, `server/db.ts`)**: Normalized relational schema, foreign key relations, and dual MySQL/in-memory store.
- **🧪 Tests (`tests/`)**: 20 automated Vitest unit and integration test suites.
- **⚙️ DevOps & Scripts (`scripts/`, `eas.json`, `app.config.ts`)**: Cloudflare Tunnel runner, EAS production Android builds (`.aab` and `.apk`).
- **📚 Documentation (`docs/`)**: Detailed architecture, tunnel guides, and Google Play Store deployment guides.

*For full details, see [`docs/PROJECT_STRUCTURE.md`](./docs/PROJECT_STRUCTURE.md).*

---

## 🛠️ Technology Stack & Architecture

| Layer | Technologies Used |
| :--- | :--- |
| **Mobile Frontend** | React Native (v0.76+), Expo (v54), Expo Router, TypeScript, NativeWind |
| **Desktop Web Portal** | React 19, HTML5, CSS Grid, tRPC React Query Client |
| **Backend & API** | Node.js, Express, tRPC (Type-safe RPC v11), SuperJSON, Zod Validation |
| **Database & ORM** | MySQL, Drizzle ORM (Relational schema with foreign keys and migrations) |
| **Tunneling & Security**| Cloudflare Tunnel (`cloudflared`), CORS Origin Sanitization, Strict CSP |
| **Testing & CI** | Vitest (Unit & Integration tests), TypeScript Compiler (`tsc --noEmit`) |
| **Build & Distribution**| EAS Build (Android `.aab` for Google Play Store & standalone `.apk`) |

---

## 💻 Local Quickstart & Running Instructions

### 1. Start the Backend API & Database Server (Port 11000)
```bash
pnpm dev:server
```

### 2. Start the Web Portal & Mobile Bundler (Port 8081)
```bash
pnpm dev:metro
```
*(Or launch both simultaneously with `pnpm dev` or double-click `start-pc-server-and-web.bat`)*

### 3. Access URLs
- **Web Management Portal**: `http://localhost:8081/admin`
- **Mobile Web View**: `http://localhost:8081`
- **Backend API Health**: `http://localhost:11000/api/health`

### 4. Start Cloudflare Tunnel
```bash
pnpm tunnel
```

---

## 🧪 Verification & Automated Tests
# TAX COMMAND CENTRE
## AI-Powered Corporate Direct Tax Compliance, Assessment & Litigation Management

**TAX COMMAND CENTRE** is an enterprise-grade direct tax system of record, automated workflow orchestration engine, AI intelligence layer, and executive management control tower designed for Corporate Heads of Tax, Tax Directors, Litigation Specialists, and CFOs.

The system manages the end-to-end direct tax lifecycle under the **Income-tax Act, 1961** — from initial notice ingestion and OCR metadata extraction to evidence collation, AI-assisted legal drafting, maker-checker approvals, e-filing submissions, assessment monitoring, litigation defense, and Ind AS 37 contingent liability reporting.

---

## 🚀 Standalone Windows Executable & Setup Installer

### 1. One-Click Setup & Desktop Shortcut Installer:
- Double-click **`TaxCommandCentre_Setup.bat`** (or run `Install_TaxCommandCentre.ps1` in PowerShell).
- This creates a **Tax Command Centre** shortcut on your Windows Desktop, validates dependencies, and immediately opens the application in your browser.

### 2. Direct Standalone Launch:
- Double-click **`TaxCommandCentre.exe`** (or `TaxCommandCentre_Start.bat`).
- The application starts automatically at **`http://localhost:3000`** with zero external dependencies required.

### 3. Rebuilding the Standalone Executable:
```bash
npm run package:exe
```
This builds the production frontend, compiles the Express backend server with built-in PDF OCR text extraction and direct tax parser, and generates `TaxCommandCentre.exe`.

### 4. Clean Slate vs Demo Dataset:
- To start with an empty database for your own live tax notices, click **"Start Clean Slate"** in the top-right user menu or in the **Export & Backup Center**.
- To restore the standard demonstration dataset anytime, click **"Reload Demo Data"**.

---

## 🏛️ Comprehensive Direct Tax Lifecycle Coverage

```mermaid
flowchart TD
    A[NOTICE / TAX COMMUNICATION RECEIVED] --> B[CAPTURE & OCR INGESTION]
    B --> C[METADATA & ISSUE EXTRACTION]
    C --> D[DUPLICATE DETECTION & MATTER CREATION]
    D --> E[TAX & BUSINESS OWNER ASSIGNMENT]
    E --> F[INFORMATION REQUEST & CHECKLIST]
    F --> G[EMAIL NOTIFICATION & SLA TRACKING]
    G --> H[INFORMATION & DOCUMENT RECEIPT]
    H --> I[REMINDER & ESCALATION ENGINE]
    I --> J[EVIDENCE MATRIX VALIDATION]
    J --> K[AI GAP ANALYSIS & TAX ANALYSIS]
    K --> L[AI RESPONSE BUILDER DRAFTING]
    L --> M[TAX REVIEW & MAKER-CHECKER APPROVAL]
    M --> N[E-PROCEEDINGS SUBMISSION]
    N --> O[ACKNOWLEDGEMENT RECORDING]
    O --> P[COMPLIANCE CLOSURE]
    P --> Q[ASSESSMENT MONITORING & ORDER TRACKING]
    Q --> R[DEMAND / REFUND / EXPOSURE LEDGER]
    R --> S[LITIGATION & APPEALS CIT(A) / ITAT / HC / SC]
    S --> T[CONTINGENT LIABILITY & IND AS 37 QUARTERLY MIS]
    T --> U[YEAR-WISE CORPORATE TAX MEMORY]
    U --> V[FULL BACKUP, RESTORE & ARCHIVE]
```

---

## 🛠️ Key Modules & Capabilities

### 1. 🛡️ Tax Control Tower (Executive Dashboard)
- Answers the **5 Core Tax Leader Questions**:
  1. **What Came In?** (New notices, queries, and statutory communications)
  2. **What Is Due?** (Statutory deadlines, internal review targets, and hearings)
  3. **What Is Stuck?** (Pending checklists, overdue requests, and blocked dependencies)
  4. **What Is Risky?** (Disputed exposure, critical section risks, and high-value assessments)
  5. **What Needs My Decision?** (Draft submissions awaiting manager review or head approval)
- Dynamic drill-down filters by **Legal Entity** and **Assessment Year (AY)**.
- Stage-by-stage pipeline visualization across the 8 lifecycle stages.

### 2. 📥 Central Tax Communication & Notice Inbox
- Ingest notices via PDF, high-res scan image, text, or e-Filing API.
- Multimodal OCR & metadata extraction:
  - Assessee Entity, PAN, TAN, AY, FY, Notice DIN, Section (e.g. 143(2), 142(1), 148, 154, 270A).
  - Issuing Authority (NFAC Delhi, Jurisdictional AO).
  - Statutory response deadlines & hearing dates.
  - Automated extraction of disputed tax issues, questions, and required evidence.
- **Cryptographic Duplicate Detection**: Checks DIN, notice number, entity, AY, section, and file fingerprint to prevent duplicate dossier creation.

### 3. 📂 Tax Matter System of Record & Issue Engine
- Unique identifier per tax matter (e.g., `DT-2026-0027`).
- Full immutable chronological audit trail for every action, status change, and note.
- Multi-issue granular tracking (e.g., `ISS-01: Section 43B`, `ISS-02: Section 14A`, `ISS-03: Section 80JJAA`, `ISS-04: Section 56(2)(viib)`).
- Kanban Board and Structured Data Table views with advanced search and risk-level filters.
- **Legal Hold** flag preventing accidental archiving or destruction during active scrutiny/litigation.

### 4. 📋 Information Requests, Checklists & Automated SLA Engine
- Auto-generates department-specific questionnaires for Business Focal Points (Finance, HR, Payroll, Treasury, M&A).
- Multi-stage lifecycle: `REQUESTED` → `ACKNOWLEDGED` → `PARTIALLY_RECEIVED` → `UNDER_REVIEW` → `COMPLETE` → `VALIDATED`.
- **Configurable SLA Reminders & Escalations**:
  - Day 0: Initial Request Dispatched
  - Day 3: Reminder 1 (Friendly reminder)
  - Day 5: Reminder 2 (Escalation warning)
  - Day 7: Final Reminder (Urgent action)
  - Day 8: Management Escalation (Notifies Business Head & CFO)
- Simulated business response adapter for complete offline/demo demonstration.

### 5. 🔒 Evidence Room & Immutability Matrix
- Secure evidence vault categorized into Notice, Ledger, Invoice, Agreement, Reconciliation, Tax Audit Form 3CD, Challans, and Case Law.
- Document confidentiality classifications: `INTERNAL`, `CONFIDENTIAL`, `HIGHLY_CONFIDENTIAL`, `LITIGATION_CONFIDENTIAL`, `LEGAL_PRIVILEGED`.
- **Issue-to-Annexure Assertion Mapping Matrix**: Maps factual assertions to supporting documents and automatically assigns formal Annexure numbers (Annexure 1, 2, 3...).
- Cryptographic locking: Once a submission is recorded, referenced evidence documents are immutably locked against modification.

### 6. ✍️ AI Response Builder & Question Coverage Verifier
- Formulates formal clause-by-clause legal submissions addressed to the **National Faceless Assessment Centre (NFAC) / Assessing Officer**.
- Grounded strictly in:
  - Assessee facts & General Ledger extracts
  - Verified documentary evidence & Bank TRRN Challans
  - Statutory provisions of the Income-tax Act, 1961
  - Preceding year accepted positions (Rule of Consistency under *Radhasoami Satsang*)
  - Binding Supreme Court & High Court precedents (*Alom Extrusions*, *South Indian Bank*, *Smifs Securities*, etc.)
- **100% Question Coverage Checklist**: Guarantees no notice question is left unanswered.
- **Maker-Checker Protocol**: Response must pass Tax Reviewer check and Head of Tax digital authorization before e-filing.

### 7. 📤 e-Proceedings Submissions & Ack Register
- Records official filing mode (`E_PROCEEDINGS_PORTAL`, `EMAIL_SUBMISSION`, `PHYSICAL_TAPPAL`, `ITBA_API`).
- Generates and stores ITBA Acknowledgement Numbers, transaction hashes, and submission timestamps.
- **Distinction between Compliance Closed vs Matter Closed**: Submitting a response closes statutory compliance while assessment monitoring remains active.

### 8. ⚖️ Litigation, Appeals & Hearing Management
- Tracks disputes across appellate stages: `Assessment` → `Rectification` → `CIT(Appeals)` → `ITAT` → `High Court` → `Supreme Court`.
- Tracks Appeal Numbers, Grounds of Appeal, External Senior Counsels, and Stay of Demand status (20% Section 220(6) pre-deposits).
- Hearing calendar with bench details, hearing objectives, and outcome records.

### 9. 📊 Contingent Liability & Quarterly Exposure Movement (Ind AS 37)
- Authoritative financial movement ledger reconciling Gross Demands, Amounts Paid Under Protest / Stayed, and Net Contingent Liability.
- Quarter-on-quarter movement statements with mandatory accounting explanations.
- Automatically generates statutory footnote disclosures for Corporate Financial Statements and Statutory Auditors.

### 10. 🧠 Corporate Tax Memory & Knowledge Centre
- Institutional repository of historical submissions, standard operating procedures, and indexed case laws.
- **Recurring Issue Detection**: Highlights persistent multi-year disputes (e.g., Section 43B disallowances across AY 2021-22 to AY 2025-26) and retrieves prior-year winning arguments.

### 11. 🤖 AI Tax Copilot (Gemini 3.7 Flash)
- Natural language interactive assistant with full contextual memory of active corporate tax matters.
- Assists in drafting rebuttal grounds, Section 270AA penalty immunity applications, and adjournment petitions.
- Displays confidence score, applicable statutory sections, and `[VERIFICATION REQUIRED]` tags for citations requiring human validation.

### 12. 📦 Data Portability, Excel/PDF Reporting & Full Backup/Restore
- **Multi-Sheet Excel Export**: Generates complete Excel workbooks covering Matters, Notices, Issues, Checklists, Litigation, Demands, and Audit Logs.
- **Executive Landscape MIS PDF**: Professional A4 landscape management report ready for Board and CFO review.
- **Full System Backup (ZIP)**: Generates a complete, structured archive including `README.txt`, JSON databases, and CSV records.
- **Database Restore & Historical Import**: Allows restoring full backups or importing legacy Excel/CSV notice trackers.

---

## 💻 Quick Start & Developer Execution

### 1. Launch Standalone Executable (Windows)
Double-click `TaxCommandCentre.exe` or execute from PowerShell:
```powershell
.\TaxCommandCentre.exe
```

### 2. Or Run in Development Mode via Node.js
```bash
npm install
npm run dev
```
Navigate to: `http://localhost:3000`

### 3. Rebuild Executable (.exe)
```bash
npm run package:exe
```

---

## 🧪 38-Step End-to-End Acceptance Test Walkthrough

To verify the complete direct tax lifecycle in Demo Mode:

1. **Ingest Notice**: Go to **Communication Inbox** → Click **Analyze Document** (or upload a PDF/Image).
2. **AI Notice Analysis**: Verify extracted Entity, PAN, AY (2024-25), DIN, Section 143(2), and disputed issues (Section 43B, Section 14A, Section 80JJAA).
3. **Dossier Creation**: Click **Confirm & Register Tax Matter**.
4. **Issue Management**: Open **Tax Matters** → View created matter `DT-2026-0027`.
5. **Checklists & SLA**: Navigate to **Information Requests** → Run **AI Evidence Gap Analysis**.
6. **Simulate Reminder & Escalation**: Trigger **Send Reminder** and **Escalate** to demonstrate multi-tier SLA alerting.
7. **Receive Business Evidence**: Click **Simulate Reply** to receive verified bank challans and ledgers.
8. **Map Evidence**: Go to **Evidence Room** → **Evidence Matrix** → Link verified challans to Section 43B assertion as **Annexure 1**.
9. **Draft Submission**: Open **Response Builder** → Click **AI Draft Submission** to generate the formal NFAC rebuttal.
10. **Check Question Coverage**: Verify **100% Question Coverage** checklist.
11. **Maker-Checker Approval**: Submit for review → Approve as Head of Tax.
12. **e-Filing Submission**: Click **Submit via e-Proceedings** → Generate ITBA acknowledgement.
13. **Compliance Closure**: Click **Close Compliance** while keeping assessment monitoring active.
14. **Appellate & Order Tracking**: Record Assessment Order → Initiate Appeal before **CIT(Appeals)**.
15. **Contingent Liability Update**: Open **Contingent Liability** → Review Ind AS 37 movement statement.
16. **Executive Reporting**: Download the **Multi-Sheet Excel Workbook** and **Executive MIS PDF**.
17. **Full Data Backup**: Click **Download Complete Tax Data (ZIP)** to verify the backup repository.

---

## 👥 User Roles & Access Control Matrix (RBAC)

| Role | View | Create | Edit | Review | Approve | Submit | Export | Archive | Administer |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Super Admin** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Head of Tax** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Tax Manager** | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ❌ |
| **Tax User** | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Tax Reviewer** | ✅ | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Business Group Head**| ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Finance User** | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| **External Consultant**| ✅ | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ |

*(Switch users dynamically in the top navigation bar to test role-specific interfaces.)*

---

## 🔒 Security & Compliance Governance

- **Zero Secret Exposure**: All API keys, tokens, and credentials reside server-side in environment configurations.
- **Data Protection**: AES-256 storage compatibility with role-based document access restrictions.
- **Audit Immutability**: Every login, edit, checklist update, submission, and export action is logged with timestamp, user identity, and cryptographic reference.
- **Legal Privilege Protection**: Dedicated confidentiality tiers for attorney-client and litigation-sensitive dossiers.

---

## 📄 License & Intellectual Property

Designed for enterprise corporate direct tax governance. © 2026 Tax Command Centre. All rights reserved.
# Tally Converter

Converts Excel, CSV, PDF, and image (JPG/PNG) accounting documents into
TallyPrime-compatible import XML - running entirely offline on your
Windows PC. No data leaves your computer.

```
Excel / CSV / PDF / JPG / PNG
        |
Read accounting data
        |
OCR when necessary (local Tesseract)
        |
Extract transactions
        |
Normalize accounting data
        |
Validate
        |
Map Tally ledgers/items
        |
Human review
        |
Generate TallyPrime-compatible XML
        |
Export XML
        |
Import into TallyPrime
```

## Important: test before relying on this for real books

The generated XML follows TallyPrime's documented voucher-import
structure (ENVELOPE / HEADER / BODY / DATA / TALLYMESSAGE / VOUCHER),
but different TallyPrime versions and company configurations can
require different fields. **Before using this for real accounting
data, test the generated XML against a TallyPrime test/sample
company** (Gateway of Tally &rarr; Import Data) and adjust the ledger
role mappings in Settings/Mappings as needed for your setup.

## What this does NOT do

- It never invents data. If a field (date, party, amount, GSTIN,
  ledger, item, tax, bank reference) can't be confidently determined,
  the transaction is marked `REVIEW_REQUIRED` instead of guessed.
- It never sends anything to TallyPrime or anywhere else without you
  explicitly clicking "Send to Tally" - the default is always
  **Export XML Only**.
- It never uses cloud OCR or any external API. OCR runs locally via
  Tesseract.

## Quick start (for developers/technical users)

See [INSTALLATION.md](INSTALLATION.md) for the full step-by-step guide
covering both "just run it from source" and "build the Windows
installer" paths. In short:

To execute the automated test suites verifying room gates, search indexing, access control, and database operations:
```bash
pnpm test
```
```bash
pnpm check
```

---

## 👤 Author & Developer Attribution
- **Developer:** CA Ankit Tandon
- **Course:** ICAI AICA Level-2 Certification
- **Rights:** Developed and Built by CA Ankit Tandon · All Rights Reserved
# Backend
cd backend
python -m venv venv
venv\Scripts\activate        # Windows
pip install -r requirements.txt --break-system-packages  # or without the flag in a venv
python run.py

# Frontend (separate terminal, for development only)
cd frontend
npm install
npm run dev
```

Then open the URL printed in the backend terminal (defaults to
`http://127.0.0.1:8000`).

## For end users

If you received `TallyConverterSetup.exe` from your developer/IT team,
see [USER_GUIDE.md](USER_GUIDE.md) - you don't need Python, Node.js,
or anything else installed.

## Documentation

- [INSTALLATION.md](INSTALLATION.md) - setting up a dev environment,
  installing Tesseract, and building the Windows installer
- [USER_GUIDE.md](USER_GUIDE.md) - how to import files, review
  transactions, map ledgers, and export/import into Tally
- [DEVELOPER_GUIDE.md](DEVELOPER_GUIDE.md) - architecture, project
  layout, how to extend voucher types, running tests

## License / ownership

This project was generated as a starting point for your own internal
tool. There is no license file included - add one appropriate to your
situation before distributing it outside your organization.
