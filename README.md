# Data Redundancy Removal System

A browser-based Data Redundancy Removal System (DRRS) that validates new records before adding them to a local database. The app detects exact duplicates, fuzzy matches, and likely false positives so only unique or intentionally verified entries are stored.

## Project Status

The project works as a static frontend demo. It runs fully in the browser and stores records in `localStorage`.

It is not a real cloud database service yet. An outsider can access the app at any time only if you deploy `index.html` to a public static host such as GitHub Pages, Netlify, or Vercel. Because the current database is browser-local, each visitor gets their own separate database. For shared public access, authentication, and a central cloud database, add a backend API and database such as Firebase, Supabase, MongoDB Atlas, or PostgreSQL.

## Live Demo

Access the live project here:

[Data Redundancy Removal System](https://harinii0107.github.io/CodeAlpha_DataRedundancyRemovalSystem/)

## Features

- Validates new data before insertion.
- Prevents duplicate records from being added.
- Classifies records as `UNIQUE`, `DUPLICATE`, or `FALSE_POSITIVE`.
- Uses exact checks for email and phone number matches.
- Uses fuzzy matching for similar names, organizations, and notes.
- Allows false positives to be verified and appended as distinct records.
- Stores only accepted records in the browser database.
- Includes live statistics, activity logs, sample data, export, import, and purge tools.
- Runs as a single static HTML file with no build step.

## How It Works

1. The user enters a new record.
2. The validation engine normalizes the input.
3. The system compares the new record with existing records using:
   - exact email matching
   - normalized phone matching
   - fuzzy name and organization similarity
   - supporting note/category comparison
4. The system returns one of three classifications:
   - `UNIQUE`: no meaningful match found
   - `DUPLICATE`: likely the same entity and cannot be added
   - `FALSE_POSITIVE`: similar to an existing record but likely a different entity and can be added after validation
5. Only `UNIQUE` and `FALSE_POSITIVE` records can be appended to the database.

## Run Locally

Open `index.html` directly in a browser.

No server, package installation, API key, or internet connection is required.

## Public Access

To make the app accessible to outsiders:

1. Push this repository to GitHub.
2. Enable GitHub Pages from the repository settings.
3. Select the main branch and root folder.
4. Share the generated GitHub Pages URL.

Important: public static hosting only shares the app interface. It does not create a shared cloud database. For a production system, use a backend with:

- user authentication
- role-based access control
- server-side duplicate checks
- database uniqueness constraints
- audit logs
- protected API keys stored on the server

## Limitations

- Data is stored in the current browser only.
- Clearing browser storage removes the local database.
- There is no login system.
- There is no central cloud database.
- Validation is deterministic and local; it does not call an external AI service.

## Recommended Production Upgrade

For a real cloud-ready version:

- Frontend: keep this HTML/CSS/JS interface or migrate to React.
- Backend: Node.js/Express, Django, Flask, or FastAPI.
- Database: PostgreSQL, MongoDB, Firebase Firestore, or Supabase.
- Security: authentication, HTTPS, server-side validation, rate limiting, and database-level unique indexes.
- Deployment: Vercel/Netlify for frontend and Render/Railway/Fly.io for backend.

## File Structure

```text
.
├── index.html   # Main DRRS app
└── README.md    # Project documentation
```

## License

This project is suitable for educational and internship portfolio use. Add a license file before using it in production or accepting external contributions.
