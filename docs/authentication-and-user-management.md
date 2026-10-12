# Authentication & User Management Module Documentation

**Application:** Arya College ClubSphere  
**Module:** Authentication & User Management  
**Branch:** `feature/auth-user-management`  
**Developer:** Avantika Mishra  

---

## 1. Overview & Responsibilities

The **Authentication & User Management** module is the foundational security layer for Arya College ClubSphere. It governs identity verification, credential security, role-based authorization, session lifecycles, and user directory administration across all 26 campus clubs.

### Key Responsibilities
- **Authentication:** Secure sign-in (`/login`) and sign-out (`/logout`) workflows with session management.
- **Authorization & RBAC:** Centralized filtering via `AuthenticationFilter` enforcing role boundaries across Admin, Club Head, Club Member, and Student areas.
- **User Lifecycle Management:** Creation of user accounts, role updates, and active/inactive status toggling from the administrative directory (`/admin/users`).
- **Credential Protection:** BCrypt hashing (cost factor 10) with automatic, safe hashing upgrade mechanisms for legacy seed credentials.
- **Deep Linking & User Experience:** Preservation of user-intended destinations through safe internal redirect handling, password visibility controls, and interactive credential helpers.

---

## 2. Architecture & Components

```
                +---------------------------------------+
                |           Web Browser / Client        |
                +---------------------------------------+
                                    |
                                    v
                +---------------------------------------+
                |          AuthenticationFilter         |
                |   - Public Asset & Endpoint Whitelist |
                |   - RBAC Role-Based Route Guards      |
                |   - Deep-Link Redirect Preservation   |
                +---------------------------------------+
                                    |
          +-------------------------+-------------------------+
          |                                                   |
          v                                                   v
+-------------------+                               +--------------------+
|   LoginServlet    |                               |    AdminServlet    |
|   LogoutServlet   |                               | (/user/create,     |
|                   |                               |  /user/change-role,|
+-------------------+                               |  /user/toggle-status)
          |                                         +--------------------+
          +-------------------------+-------------------------+
                                    |
                                    v
                        +----------------------+
                        |     UserService      |
                        +----------------------+
                        | - login()            |
                        | - registerUser()     |
                        | - changeRole()       |
                        | - changeStatus()     |
                        | - changePassword()   |
                        +----------------------+
                                    |
                                    v
                        +----------------------+
                        |       UserDAO        |
                        | (JDBC PreparedStmts) |
                        +----------------------+
                                    |
                                    v
                        +----------------------+
                        |   MySQL Database     |
                        |   (users table)      |
                        +----------------------+
```

### Component Breakdown
1. **Controllers & Servlets:**
   - `com.clubsphere.controller.LoginServlet`: Authenticates credentials, manages session fixation mitigation, records audit logs, and redirects users to target destinations or dashboards.
   - `com.clubsphere.controller.LogoutServlet`: Logs logout events, invalidates active HTTP sessions, and redirects to login with confirmation feedback.
   - `com.clubsphere.controller.AdminServlet`: Handles administrative endpoints `/user/create`, `/user/change-role`, and `/user/toggle-status`.
2. **Security Filter:**
   - `com.clubsphere.filter.AuthenticationFilter`: Intercepts all requests (`/*`), verifies session state, enforces RBAC policies per URI prefix, and attaches encoded return URLs to redirect unauthenticated users cleanly.
3. **Business Logic & Persistence:**
   - `com.clubsphere.service.UserService`: Orchestrates authentication, credential upgrades, registration constraints, and status updates.
   - `com.clubsphere.dao.UserDAO`: Executes parameterized SQL queries with HikariCP connection pooling, providing robust CRUD operations and uniqueness checks.
4. **Utilities & Models:**
   - `com.clubsphere.util.PasswordUtil`: BCrypt hashing and verification utility.
   - `com.clubsphere.model.User`: Encapsulates user identity, contact information, role, and active status.
5. **Views:**
   - `src/main/webapp/login.jsp`: Modern sign-in form with accessibility associations, show/hide password visibility toggle, redirect field preservation, and 1-click credential autofill buttons.
   - `src/main/webapp/WEB-INF/views/admin/users.jsp`: Administrative user directory table with role filtering, role dropdown updater, status toggle actions, and validation-ready registration modal.

---

## 3. Role-Based Access Control (RBAC) Matrix

| Endpoint / Area | Public (Unauthenticated) | STUDENT | CLUB_MEMBER | CLUB_HEAD | ADMIN |
|---|:---:|:---:|:---:|:---:|:---:|
| `/`, `/index.jsp` | ✅ | ✅ | ✅ | ✅ | ✅ |
| `/login`, `/logout` | ✅ | ✅ | ✅ | ✅ | ✅ |
| `/clubs`, `/events` | ✅ | ✅ | ✅ | ✅ | ✅ |
| `/student/*` | ❌ (Redirects) | ✅ | ✅ | ✅ | ✅ |
| `/club-member/*` | ❌ (Redirects) | ❌ (403) | ✅ | ✅ | ✅ |
| `/club-head/*` | ❌ (Redirects) | ❌ (403) | ❌ (403) | ✅ | ✅ |
| `/admin/*` | ❌ (Redirects) | ❌ (403) | ❌ (403) | ❌ (403) | ✅ |

---

## 4. Security Enhancements & Best Practices

1. **Session Fixation Prevention:**  
   During login in `LoginServlet`, existing sessions are explicitly invalidated before instantiating a fresh authenticated session (`req.getSession(true)`), preventing session fixation exploits.
2. **Open Redirect Defense:**  
   The `redirect` parameter is validated to ensure it only allows safe, internal paths starting with the application's context path or relative `/`, strictly disallowing absolute protocol schemes (`http://`, `https://`, `//`) and `javascript:` URIs.
3. **Safe BCrypt Hash Upgrade:**  
   In `UserService.login`, non-standard and legacy hashes are upgraded to standard BCrypt with exception safety, preventing `IllegalArgumentException` from halting login execution.
4. **Self-Lockout Guard:**  
   Administrators are prevented from deactivating their own currently logged-in account in `/admin/user/toggle-status`.
5. **Registration Uniqueness Constraints:**  
   User creation checks for both unique username and email before attempting database insertion, providing clean user-facing error feedback rather than uncaught database constraint violations.
6. **Form Accessibility & Usability:**  
   Explicit `for`/`id` bindings on all form inputs, password visibility toggle for improved usability, and instant credential autofill for developer and evaluation testing.
