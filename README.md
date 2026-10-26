# Procedure Card

A crowdsourced log of what medical procedures cost. People report a procedure, the provider, the amount billed, and the amount actually paid, and the app shows averages across the reports.

## Features

- Report a procedure with provider, amount charged, insurance carrier, and amount actually paid
- See average charged and average paid amounts across reports
- List of every report with charged and paid side by side
- The API can filter to a single procedure name with a query parameter
- Entries are saved to a local JSON file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

Then open http://localhost:3007. `npm run dev` runs the same command.

## How it works

- `index.html` contains the report form, the averages, and the list of reports. It calls the API at `http://localhost:3007`.
- `server.js` is an Express app that serves the page and exposes:
  - `POST /api/procedures` to save a report.
  - `GET /api/procedures` to return reports plus `count`, `avgCharged`, and `avgPaid`. Add `?procedure=Knee%20Surgery` to filter by exact procedure name.
- Data is written to `data.json`, created on first run and ignored by git.
- `utils.js` holds validation and file helpers that are not yet wired into `server.js`.

## Status

Prototype. All figures come from what users enter; there is no hospital, insurer, or claims data.

## License

MIT, see [LICENSE](LICENSE).
