# Crime Report API — Incomplete Backend Prototype

An early Node.js and MongoDB backend experiment for user registration and location-based incident-report records.

> **Status:** incomplete educational prototype. The current branch does not implement the full citizen-reporting platform described in older documentation, and the server may not start until the missing report-route module is restored or implemented.

## Implemented components

- Express server setup
- MongoDB connection through Mongoose
- User and incident-report schemas
- Password hashing with bcrypt
- JWT creation during signup
- Environment-variable based configuration

## Current structure

```text
Crime-Report-App/
├── backend/
│   ├── index.js
│   ├── models/
│   │   ├── User.js
│   │   └── Report.js
│   ├── routes/
│   │   └── authRoutes.js
│   └── package.json
└── README.md
```

The server entry point imports `./routes/reportRoutes`, but that module is not present on the current branch. Implement it or remove the import before expecting the backend to run.

## Not currently implemented

The present code does not establish:

- login
- authenticated report submission
- report listing or status tracking
- authority dashboards
- anonymous reporting
- media uploads
- geolocation services
- role-based access control
- a frontend application
- production deployment controls

These should not be advertised as completed features.

## Setup after restoring the missing route

```bash
git clone https://github.com/PseudoOzone/Crime-Report-App.git
cd Crime-Report-App/backend
npm install
```

Create a local `.env` file that is not committed:

```bash
MONGO_URI=mongodb://127.0.0.1:27017/crime_report
JWT_SECRET=replace-with-a-long-random-secret
PORT=5000
```

Run the server using the script defined in `backend/package.json`.

## API currently present

### `POST /api/auth/signup`

```json
{
  "name": "Example User",
  "email": "user@example.com",
  "password": "replace-me"
}
```

The endpoint hashes the password, stores the user, and returns a one-hour JWT. Input validation and abuse controls are not yet implemented.

## Security review notes

- A `.env` file appears in repository history. Any real credentials that were committed should be rotated; deleting the current file does not remove secrets from prior commits.
- CORS is unrestricted.
- Signup does not validate email format, password strength, field length, or unexpected input.
- There is no login route, token-verification middleware, authorization, rate limiting, or account lockout.
- `JWT_SECRET` is used without an explicit startup check.
- Database connection failure is logged, but the server can continue starting in an unusable state.
- Report fields have minimal schema validation.
- The missing `reportRoutes` import prevents a clean startup.
- There are no automated tests or CI checks.

## Recommended next steps

1. Restore or implement `backend/routes/reportRoutes.js`.
2. Add strict request validation.
3. Add login, authentication middleware, ownership checks, and role-based authorization.
4. Restrict CORS to configured origins.
5. Add rate limiting and standardized error handling.
6. Validate required environment variables before startup.
7. Add database indexes and schema constraints.
8. Add API tests with an isolated test database.
9. Rotate historical credentials and rewrite Git history when required.

## Responsible-use note

A real incident-reporting system would handle highly sensitive personal, location, and allegation data. It requires legal review, evidence-retention policies, abuse prevention, secure media handling, access controls, and auditability.

## License

Educational and portfolio use only unless a separate license file states otherwise.
