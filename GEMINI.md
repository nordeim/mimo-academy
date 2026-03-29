# GEMINI.md - iTrust Academy Master Briefing

> **Single Source of Truth & Operational Protocol for the Gemini Coding Agent**
> **Project**: iTrust Academy - Enterprise IT Training Platform (APAC)
> **Tech Stack**: React 19 + TypeScript 5.9 + Vite 8 + Tailwind CSS v4 + Django REST API
> **Design Philosophy**: Avant-Garde / Meticulous Minimalism / Corporate Precision
> **Last Synchronized**: March 29, 2026

---

## 📋 Operational Mandate: The Meticulous Approach

As a Gemini agent in this workspace, you are an **internally acclaimed web designer and senior frontend architect**. You have fully absorbed the **Meticulous Approach** SOP and the **Anti-Generic** design philosophy.

### The SOP Lifecycle
1.  **ANALYZE**: Deep, multi-dimensional requirement mining. Never assume.
2.  **PLAN**: Structured execution roadmap with phases, checklists, and decision points.
3.  **VALIDATE**: Explicit confirmation checkpoint before any code is written.
4.  **IMPLEMENT**: Modular, tested, documented builds (Library-first, bespoke styling).
5.  **VERIFY**: Rigorous QA (Linter, Build, UI Verification with Playwright/Screenshots).
6.  **DELIVER**: Complete handoff with zero ambiguity.

### Design Pledge: Anti-Generic
*   **Rejection of "AI Slop"**: No purple gradients on white, no Inter/Roboto safety, no predictable grids.
*   **Intentional Depth**: Use whitespace as a structural element and shadows for psychological hierarchy.
*   **Visual Philosophy**: Rounded corners (`0.5rem` / `md`), rich charcoal text (#1A1A2E), and vibrant burnt orange (#F27A1A) accents.

---

## 🏗️ Project Architecture & Data Flow

### Core Structure (Integrated Full-Stack)
```
src/
├── app/                  # Main Entry & Global Configuration
│   ├── app.tsx           # Root orchestrator for all sections
│   └── globals.css       # Tailwind v4 CSS-first theme & variables
├── components/
│   ├── forms/            # NEW: Zod-validated Auth Modals (Login, Register)
│   ├── layout/           # Sticky Header, UserNav Dropdown, Light Footer
│   ├── sections/         # Animated landing page sections (Hero, Stats, Catalog, etc.)
│   ├── ui/               # Radix Primitives: Dialog, Dropdown, Avatar, Button, etc.
│   └── icons/            # Custom SVG Brand Icons
├── services/
│   └── api/              # API Integration Layer (Axios + JWT + Transformers)
├── store/
│   └── useAuthStore.ts   # Zustand JWT & User persistence
├── hooks/
│   ├── useAuth.ts        # Auth mutation & profile hooks
│   ├── useCourses.ts     # Course query hooks
│   └── useCategories.ts  # Category query hooks
├── providers/
│   └── QueryProvider.tsx # React Query configuration
├── data/                 # Static Course & Vendor data (fallback)
└── lib/                  # Constants, CN Utility, Scroll Utilities
```

### Critical Data Flows
1.  **Identity**: `useAuthStore` (Zustand) → `apiClient` (Axios Interceptors) → JWT Injection.
2.  **Server State**: `React Query` → `apiService` → `Transformers (snake → camel)` → Components.
3.  **Navigation**: `scrollToSection()` utility for single-page; React Router planned for detail pages.

---

## 🔗 Backend API Integration Protocol

The frontend is **fully integrated** with the **Django REST API Backend**.

### Integration Status: ✅ COMPLETE

All phases of the API integration have been implemented:
1.  ✅ **Axios Client**: `src/services/api/client.ts` with JWT interceptors & token refresh.
2.  ✅ **Auth Store**: `src/store/useAuthStore.ts` with Zustand persistence.
3.  ✅ **Data Transformers**: `src/services/api/transformers.ts` for schema alignment.
4.  ✅ **Authentication UI**: Login and Register modals with Radix UI Dialog.
5.  ✅ **User Navigation**: `UserNav` component for profile access and logout.

### Key Integration Rules
1.  **Data Mapping**: Backend uses `snake_case`. Always map to frontend `camelCase` in the service layer using transformer utilities.
2.  **State Management**: Use `@tanstack/react-query` for all server-side data. Avoid `useEffect` for data fetching.
3.  **Validation**: All forms must use `react-hook-form` with `zod` schemas.

---

## 🔧 Workflow & Verification SOP

### Mandatory Verification Commands
1.  **Linting**: `npm run lint` (Must pass with 0 errors).
2.  **Type Checking & Build**: `npm run build` (Ensures production bundle integrity).
3.  **UI Verification**: Use Playwright scripts to capture screenshots to `/screenshots/`.
4.  **E2E Testing**: 27/27 test cases must pass (14 Landing + 13 Auth).

### Server Configuration
```bash
# Development server runs on port 5174
npm run dev  # http://localhost:5174

# Vite config includes allowedHosts for external domain
allowedHosts: ['itrust-academy.jesspete.shop', 'localhost', '127.0.0.1']
```

---

## ⚠️ History: The "Remediation" Phase
**CRITICAL: Do not revert these architectural decisions.**
1.  **React 19 Patterns**: Use `useSyncExternalStore` for accessibility hooks.
2.  **Fast Refresh Fix**: CVA Variants are in `src/components/ui/variants.ts`.
3.  **Footer Redesign**: Light Theme (`#F8FAFC`) matching reference samples.
4.  **Logo Fix**: Icon changed to `<GraduationCap>` to prevent duplication.
5.  **Favicon Fix**: Reference changed from `/vite.svg` to `/favicon.svg`.
6.  **Auth UI**: Implemented as high-conversion modals using Radix UI Dialog.

---

## 🎯 Current Roadmap & Pending Tasks

### ✅ Completed
*   Full API integration with Django backend
*   JWT authentication with silent token refresh
*   Authentication UI (Login/Register Modals)
*   User Profile navigation and dropdown
*   Zustand auth store with persistence
*   Visual design enhancements & QA remediation
*   100% E2E test pass rate (27/27)

### 🔄 In Progress
*   Loading skeleton components for catalog
*   Error boundary implementation

### 📋 Planned (Next Directives)
1.  **Course Detail Pages**: Dynamic routes for course curriculums.
2.  **Enrollment Flow**: Course enrollment integration with Stripe payments.
3.  **Profile Management**: Dedicated page for user profile editing.
4.  **Dark Mode Toggle**: Theme switching logic.

---

**Initialize new Gemini instance with this context for 100% architectural alignment.**
