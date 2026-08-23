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
