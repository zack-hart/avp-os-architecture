# Advanced Volleyball Performance Operating System

> *Note: The source code for this application is held in a private repository for security and API protection. This repository serves as the architectural overview and technical documentation.*

**A full-stack, data-driven performance management PWA built with React, TypeScript, Node.js, and PostgreSQL.**

## Executive Summary
AVP-OS is a dual-door (Desktop/Mobile) Progressive Web Application (PWA) engineered to manage athletic telemetry, training loads, and readiness metrics. The application utilizes a decoupled backend running Node.js/Express, communicating with a serverless PostgreSQL relational database. The frontend features complex, algorithmic state management capable of calculating real-time Central Nervous System (CNS) saturation, dynamic jump decay, and autonomous volume regulation. 

## Technical Stack & Infrastructure
*   **Frontend:** React (TypeScript) / Vite / PWA (Installable iOS/Android Native Experience)
*   **Backend API:** Node.js / Express.js
*   **Database:** PostgreSQL (Relational schema via Neon.tech Serverless Driver)
*   **Authentication & Security:** Custom Gateway Middleware (Master Key API Access)
*   **UI/UX Architecture:** Dynamic theme rendering, glassmorphism, and responsive masonry layouts

## Core Engineering Achievements

### 1. Algorithmic State Management & Business Logic
*   **The Predictive Brain (Command Center):** Engineered frontend logic to ingest raw telemetry and algorithmically calculate Acute:Chronic Workload Ratios (ACWR). The system features a Tournament Peaking Algorithm that dynamically alters volume tolerances based on competition proximity.
*   **Dynamic Autoregulation (The STOP RULE):** Implemented a complex state override monitor. If an athlete logs a velocity drop during execution, the system overrides the planned workout, caps the volume early, and dynamically recalculates the CNS metabolic cost.
*   **Microcycle Close Engine:** Built an automated weekly analysis script that evaluates "Red Days" and KPI drop-offs to generate mathematical scaling multipliers for the following week's jump and sprint capacities.

### 2. Decoupled RESTful API Architecture
*   **Client-Server Separation:** Engineered a strict separation of concerns between the React frontend and the Node.js backend. The frontend operates independently, relying on structured HTTP requests to the Express API for data retrieval and mutation.
*   **Serverless Database Integration:** Integrated the `@neondatabase/serverless` driver to manage connection pooling and routing to a remote PostgreSQL cluster, ensuring high availability and scalable data storage.

### 3. API Security & Access Control
*   **Gateway Authentication:** Implemented a secure gateway pattern on the Express backend. All protected API routes require a cryptographically verified `API_MASTER_KEY` passed via environment variables, preventing unauthorized data access.
*   **Environment Segregation:** Strictly enforced `.env` segregation for both the Vite frontend (`VITE_API_URL`) and Node.js backend (`DATABASE_URL`), ensuring sensitive credentials are never exposed in source control.

## Core Project Structure
Demonstrating clean separation of concerns between frontend client, backend API, and static assets.

```text
avp-os/
├── api/                  # Node.js/Express Backend
│   ├── server.js         # RESTful API routes and database connection logic
│   └── .env              # Secure backend credentials (Not in version control)
├── src/                  # React Frontend (TypeScript)
│   ├── api.ts            # Centralized API service module for HTTP requests
│   ├── App.tsx           # Main desktop component tree
│   └── MobileApp.tsx     # Dedicated PWA mobile layout tree
├── vite.config.ts        # Frontend build pipeline and PWA configuration
└── package.json          # Dependency management
