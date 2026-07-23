# Crime Report API — Archived Educational Prototype

An early Node.js and MongoDB backend experiment for user registration and location-based incident-report records.

> **Status:** incomplete educational prototype. The current branch does not implement the full citizen-reporting platform described in older notes and should not be deployed or used with real personal, location, allegation, or incident data.

## Implemented components

- Express server setup
- MongoDB connection through Mongoose
- User and incident-report schemas
- Password hashing with bcrypt
- JWT creation during signup
- Environment-variable based configuration

## Current limitations

The current code does not establish a complete or production-ready system. Missing or incomplete areas include:

- login and token-verification middleware
- authenticated report submission
- report listing and status tracking
- role-based authorization
- strict request validation
- rate limiting and abuse controls
- a complete frontend
- automated tests and CI
- production privacy, retention, and audit controls

These features must not be advertised as completed.

## Local configuration

Copy the safe template and use local development credentials:

```bash
cp backend/.env.example backend/.env
```

Example values:

```env
MONGO_URI=mongodb://127.0.0.1:27017/crime_report
JWT_SECRET=replace-with-a-long-random-secret
PORT=5000
```

Never commit the resulting `.env` file.

## Security notice

A credentials file and a hard-coded administrator seed existed in an earlier revision. They have been removed from the current branch, and environment files are now ignored. Any database credential or signing secret that appeared in Git history must still be treated as compromised and rotated; deleting the current file does not invalidate previously exposed credentials or remove them from historical commits.

Additional issues still requiring work include unrestricted CORS, incomplete input validation, missing authentication middleware, weak startup validation, and absent abuse controls.

## Appropriate use

This repository is suitable only for reviewing an early learning prototype. A real incident-reporting system would require legal review, evidence-retention policies, secure media handling, strict access controls, auditability, abuse prevention, and tested operational procedures.

## License

Educational and portfolio use only unless a separate license file states otherwise.
