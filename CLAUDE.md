# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**iTrust Academy** is an enterprise IT training platform with a React 19 frontend and Django 6.0 backend. The stack uses TypeScript strict mode, Tailwind CSS v4 with CSS-first configuration, Radix UI primitives, and Framer Motion animations.

## Commands

### Frontend (React + Vite)

| Command | Description |
|---------|-------------|
| `npm run dev` | Start dev server (port 5174) with hot reload |
| `npm run build` | Production build to `dist/` |
| `npm run lint` | ESLint with react-refresh rules |
| `npm test` | Run Vitest unit tests (14 tests) |
| `npm run test:watch` | Tests in watch mode |
| `npx vitest run tests/unit/utils.test.ts` | Run single test file |
| `npx vitest run --reporter=verbose` | Verbose test output |

### Backend (Django)

| Command | Description |
|---------|-------------|
| `cd backend && python manage.py runserver` | Start Django server (port 8000) |
| `python manage.py migrate` | Run database migrations |
| `python manage.py init_db` | Initialize DB with seed data |
| `python test_register_login.py` | Test auth endpoints |
| `python manage.py createsuperuser` | Create admin user |

## Architecture

### Component Hierarchy

```
src/components/
├── pages/          # Route-level components (HomePage, CourseDetailPage, etc.)
├── sections/       # Reusable page sections (Hero, CourseCatalog, Features)
├── layout/         # Header, Footer, Container, Section wrappers
├── ui/             # Radix/shadcn primitives (Button, Card, Dialog, etc.)
├── forms/          # Auth modals (LoginModal, RegisterModal)
└── hooks/          # useAuth, useCourses, useCategories
```

### Data Flow

```
Django REST API
    ↓
apiClient (Axios + JWT interceptors) in src/lib/api.ts
    ↓
React Query hooks (useCourses, useCategories)
    ↓
Section components (sections/*.tsx)
    ↓
Page components (pages/*.tsx)
```

### State Management

- **Server state**: React Query (TanStack Query) for API data
- **Auth state**: Zustand store with localStorage persistence (key: `itrust-auth`)
- **Local UI state**: React `useState`
- **Form state**: react-hook-form + Zod validation

## Key Patterns

### Component Variants (CVA)

All UI component variants are defined in `src/components/ui/variants.ts` using class-variance-authority:

```typescript
import { buttonVariants } from "@/components/ui/variants"
// Use: <button className={buttonVariants({ variant: "outline", size: "sm" })} />
```

### Animation Variants

Framer Motion variants are centralized in `src/lib/animations.ts`:

```typescript
import { fadeInUp, staggerContainer } from "@/lib/animations"
// Use: <motion.div variants={fadeInUp} />
```

### Class Styling

Always use the `cn()` utility for class merging:

```typescript
import { cn } from "@/lib/utils"
// Use: className={cn("base-class", conditional && "conditional-class", className)}
```

### Icons

Use **Lucide React** exclusively. Never use emojis in code.

```typescript
import { CheckCircle, Loader2 } from "lucide-react"
```

### Form Validation

Use Zod schemas with react-hook-form. **Critical**: Always provide empty string defaults:

```typescript
const form = useForm({
  resolver: zodResolver(schema),
  defaultValues: { email: "", password: "" }, // Required!
})
```

## Critical Constraints

### TypeScript

- Strict mode is enabled. Avoid `any`; use `unknown` with type guards.
- Prefer `interface` over `type` (except for unions/intersections).

### Fast Refresh

**NEVER export constants from component files**. This breaks React Fast Refresh.

```typescript
// ❌ WRONG - in a component file
export const MAX_ITEMS = 10
export function Component() { ... }

// ✅ CORRECT - move constants to variants.ts or data files
// Component file only exports the component
export function Component() { ... }
```

### Accessibility

- All dialogs require `DialogTitle` and `DialogDescription` (Radix UI requirement):

```typescript
<DialogContent>
  <DialogHeader>
    <DialogTitle>Title Here</DialogTitle>
    <DialogDescription>Description here</DialogDescription>
  </DialogHeader>
</DialogContent>
```

- Respect `prefers-reduced-motion` using the `useReducedMotion` hook.
- External links must use: `rel="noopener noreferrer" target="_blank"`.

### Async Operations

- Disable buttons during async operations
- Show loading indicator on buttons (use `Loader2` icon with `className="animate-spin"`)
- Always have `onError` handler with toast feedback

### UI States

Every list needs an empty state. Always handle: loading, error, empty, success.

## Design Philosophy

**Intentional Minimalism**: Whitespace is structural, not decorative. Every element earns its place.

**Library Discipline**: Use Radix/shadcn primitives. Never rebuild components that exist in the library. Wrap/style them instead.

**Anti-Generic**: Bold, distinctive design choices. No template aesthetics. No ":emoji:" — Lucide icons only.

## Frontend/Backend Integration

### API Proxy

Vite proxies `/api` to Django in `vite.config.ts`:

```typescript
proxy: {
  '/api': {
    target: 'http://localhost:8000',
    changeOrigin: true,
  }
}
```

### Authentication

- JWT tokens stored in `localStorage` under key `itrust-auth`
- Token auto-refreshes via axios interceptors in `src/lib/api.ts`
- Protected routes use `PrivateRoute` component

### Environment Variables

Frontend uses `VITE_` prefix in `.env`:

```
VITE_API_URL=/api/v1
VITE_APP_ENV=development
```

## File Patterns

### Import Order

1. React/Node built-ins
2. Third-party libraries
3. Absolute imports (`@/`)
4. Relative imports

### Naming Conventions

- **Components**: PascalCase (`Hero.tsx`, `CourseCard.tsx`)
- **Hooks**: camelCase with `use` prefix (`useAuth.ts`)
- **Utilities**: camelCase (`formatPrice.ts`)
- **Files**: kebab-case (`course-catalog.tsx`)

### Testing

- Unit tests in `tests/unit/*.test.ts`
- E2E tests in Python using Playwright
- Run single test: `npx vitest run tests/unit/<file>.test.ts`

## Tailwind CSS v4

- Theme tokens defined in `src/app/globals.css` using CSS variables
- Brand color: `#f27a1a` (burnt orange)
- No `tailwind.config.js` — CSS-first configuration in `globals.css`

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Port 5174 in use | `fuser -k 5174/tcp` to kill process |
| Lint errors in component | Check for exported constants breaking fast-refresh |
| Dialog accessibility warnings | Add `DialogTitle` and `DialogDescription` |
| Form not submitting | Check Zod schema and `defaultValues` (need empty strings) |
| JWT auth failing | Check `localStorage.getItem("itrust-auth")` for token |
