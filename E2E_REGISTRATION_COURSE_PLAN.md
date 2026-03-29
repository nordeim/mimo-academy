# E2E Test Plan - Registration & Course Management

> **Date**: March 29, 2026
> **Project**: iTrust Academy
> **Target URL**: http://localhost:5174/
> **Backend URL**: http://localhost:8000/api/v1/

---

## 📋 Test Plan Overview

This plan validates the core business logic of user registration and course discovery. Since the authentication UI is currently in the "Planned" phase, testing will involve a hybrid approach:
1.  **API Validation**: Direct testing of the registration and auth endpoints.
2.  **UI Discovery Validation**: Functional testing of the Course Catalog and category filtering.

---

## 🧪 Suite 1: User Registration & Auth (API Level)

**Objective**: Confirm that the backend correctly handles user identity and token issuance.

### Test Case: API-101 - User Registration
- **Given**: Valid registration data (unique email/username).
- **When**: POST request sent to `/api/v1/auth/register/`.
- **Then**: API should return 201 Created with a valid user ID.

### Test Case: API-102 - Obtain JWT Tokens
- **Given**: Registered user credentials.
- **When**: POST request sent to `/api/v1/auth/token/`.
- **Then**: API should return `access` and `refresh` tokens.

---

## 🧪 Suite 2: Course Browsing & Discovery (UI Level)

**Objective**: Verify that the Course Catalog correctly fetches and displays data from the live API.

### Test Case: UI-201 - Initial Catalog Load
- **Given**: User navigates to the homepage.
- **When**: Page loads and scrolls to `#courses`.
- **Then**: Course cards should render with data from the API (Title, Price, Rating).
- **Verify**: API loading skeleton displays then disappears.

### Test Case: UI-202 - Category Filtering
- **Given**: Course catalog is loaded.
- **When**: User clicks a category filter button (e.g., "Security").
- **Then**: The grid should update to show only courses belonging to that category.
- **Verify**: Active filter button has the primary brand color background.

---

## 🧪 Suite 3: Enrollment Readiness (Hybrid)

**Objective**: Validate the data structure and hooks are ready for the upcoming Enrollment UI.

### Test Case: API-301 - Course Detail Retrieval
- **Given**: A valid course slug.
- **When**: GET request sent to `/api/v1/courses/{slug}/`.
- **Then**: Detailed course information including modules and duration should be returned.

---

## 🛠️ Tools & Evidence

- **Tool**: `agent-browser` / `mcp_chrome-devtools`
- **Evidence**:
    - `registration-api-success.log`
    - `course-catalog-initial.png`
    - `course-catalog-filtered.png`
    - `course-api-response.json`

---

## ✅ Success Criteria

- [ ] All API tests return 2xx status codes.
- [ ] UI correctly displays course data fetched from backend.
- [ ] Filtering logic accurately updates the course grid.
- [ ] No JavaScript errors in the console during browsing.
