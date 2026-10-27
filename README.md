# Activity 10 — Error Resolution Log

## Error 1: Insufficient Permissions (403 Forbidden)

### A - Before Fix
![Figure E01-BEFORE](E01-BEFORE.png)

* **Figure E01-BEFORE:** `GET /api/mothers` returning `403 Forbidden`.
* **Issue:** Attempted to access the mothers list using a "mother" role token, which lacks the required privileges.

### B - Diagnose
* **Cause:** The endpoint is protected by FastAPI's role-based access control (RBAC). The API rejected the request because the authenticated user's role (mother) is not included in the allowed roles (worker, admin). This proves the system's authorization is working correctly.

### C - After Fix
![Figure E01-AFTER](E01-AFTER.png)

* **Figure E01-AFTER:** `GET /api/mothers/45` returning `201 Created` after authorizing with an Admin role.
* **Fix:** Logged in again using the `admin@gmail.com` account to obtain a valid Admin JWT. Updated the Swagger Authorize token. Then, successfully retrieved a specific mother's record to verify access.
* **Response:** `201 Created` with the correct data for "Maria Santos" (ID 45).

### D - Record
* **Committed to GitHub with commit message:** `docs(activity10): add error resolution log E01`
