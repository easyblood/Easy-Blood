# Easy Blood — Backend

## What this adds
- Management and staff login
- Secure password hashing (bcrypt)
- JWT session authentication
- Patient/report database (SQLite)
- Report creation and search API
- Public QR verification endpoint
- PDF upload endpoint
- Role protection for management-only actions

## Run on a computer/server
1. Install Node.js 20+.
2. Open a terminal in the `server` folder.
3. Run `npm install`.
4. Set environment variables from `.env.example`.
5. Run `npm start`.
6. API health check: `GET /api/health`.

## Important security
Change `JWT_SECRET` and the management password before real use.
Do not publish the SQLite database, `.env`, or the uploads folder as a static public website.
Use HTTPS.
For real patient data, deploy on a trusted server and add backups, audit logs, rate limiting, and appropriate privacy/security controls.

## QR flow
Management/staff creates a report -> server creates a random verification token -> QR points to the public verification page -> patient scans QR -> frontend calls:
GET /api/reports/verify/:token

The existing `LabCorner.html` remains the Easy Blood UI and can be connected to these endpoints.
