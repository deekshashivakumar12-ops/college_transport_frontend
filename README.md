# CampusTrack — Bus Tracking System Frontend

## Files
- `index.html` — role-based login
- `register.html` — admin/student/driver registration, photo preview, show/hide passwords
- `dashboard.html` — administrator workspace
- `student-dashboard.html` — student workspace
- `driver-dashboard.html` — driver workspace
- `style.css` — responsive light-yellow design
- `app.js` — frontend state, validation, password hashing, page rendering and local reports

## Run locally
1. Put your college photo at `assets/college-photo.jpg` (create the `assets` folder). If you do not add a photo, the login still has a yellow fallback background.
2. Open the folder in VS Code.
3. Use the VS Code Live Server extension or another localhost static server. Web Crypto may not work when opened directly as a `file://` URL.
4. Open `index.html`.

## First admin account
For frontend development only, the registration form accepts the invitation code `CHANGE-ME-ADMIN-INVITE`. Change this string before sharing the code. This is **not secure** because it is visible in JavaScript. Production admin accounts and invitation codes must be created/validated on the server.

## Important production requirements
This is a feature-rich frontend, not a production-secure transport service. It stores records in browser `localStorage`, which a user can inspect or change. Client-side hashing and role checks do not provide trusted access control. Before using real people or transport records:
- Implement a backend API (for example, Python Flask) and a database.
- Hash passwords on the server with Argon2id or bcrypt; never send password hashes back to the browser.
- Enforce roles and permissions on every server endpoint; use secure, HttpOnly, SameSite cookies and HTTPS.
- Validate and authorize all requests server-side; add rate limiting and account recovery.
- Store audit logs on the server with restricted write access.
- Store photos in controlled file/object storage; validate type/size on the server.
- Connect real GPS hardware/API for live tracking and ETA.
- Add backups, privacy notice, retention rules, and appropriate consent.
- Avoid storing sensitive production records in localStorage.

The included local PBKDF2 hashing is for frontend-only account flow demonstration and is not a substitute for backend password storage. The built-in admin invite code is a development convenience only.
