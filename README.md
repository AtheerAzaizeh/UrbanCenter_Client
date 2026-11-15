# UrbanCenter — Civic Issue Reporting Platform (Client)

UrbanCenter connects citizens with their city. A citizen reports a problem — a pothole, a broken streetlight, illegal dumping and more — with a photo and the exact location, and the responsible city department sees the report in real time, sets its priority and updates its status until it is resolved.

This repository contains the **React client**. The REST API and real-time server are in **[UrbanCenter_Server](https://github.com/AtheerAzaizeh/UrbanCenter_Server)**.

---

## Features

- **Two roles.** Citizens submit reports and follow their status. Authority users (city departments) see and handle only the reports in their own category.
- **Three-step report wizard.** Report details (7 categories and 21 issue types, description, priority, location from the browser's geolocation), photo upload, and contact details, with validation on every step.
- **Live reports table.** A Material UI Data Grid with colour-coded status and priority, image preview, and dialogs for updating or deleting a report.
- **Real-time notifications with sound.** Over Socket.IO, a department is alerted the moment a new report arrives in its category, and a citizen is alerted when the status of their report changes.
- **Readable addresses.** Coordinates are turned into street addresses with the OpenStreetMap Nominatim API.
- **Resolved reports view.** Every resolved report with its comments and attached images.

## Tech stack

| Area | Technologies |
| --- | --- |
| UI | React 18, Material UI 6, MUI X Data Grid, Sass modules |
| Routing & state | React Router 7, Redux Toolkit, React Context (auth & user) |
| Data | Axios (REST), Socket.IO client (real time), OpenStreetMap Nominatim |
| Tooling | Create React App |

## Screens

| Screen | What it does |
| --- | --- |
| Sign in / Sign up | Register as a citizen, or as an authority user for one report category |
| Reports dashboard | Live table of reports with status, priority, location and image |
| Start Report | The three-step wizard for submitting a new report |
| Resolved Reports | Resolved reports together with their comments |

## Getting started

**Prerequisites:** Node.js 18+ and a running [UrbanCenter server](https://github.com/AtheerAzaizeh/UrbanCenter_Server).

```bash
git clone https://github.com/AtheerAzaizeh/UrbanCenter_Client.git
cd UrbanCenter_Client
npm install
```

Point the client at your server in `src/consts.js`:

```js
export const SERVER_URL = 'http://localhost:8080';
```

Then start the development server:

```bash
npm start
```

`npm run build` creates a production build in `build/`. In production the server serves this build from its `view/build` folder.

## Project structure

```
src/
├── components/   # Report wizard, reports table, dialogs (update, delete, image upload/preview), loaders
├── contexts/     # AuthContext and UserContext
├── pages/        # Dashboard layout, sign-in, report page
├── store/        # Redux store, actions, reducers and API calls
├── consts.js     # Server URL
└── App.js        # Routes and protected pages
```

## Author

**Atheer Azaizeh** · [github.com/AtheerAzaizeh](https://github.com/AtheerAzaizeh)
