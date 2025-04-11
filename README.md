# SaaS Invoice Reminder Platform

This project is a SaaS-based invoice management system that enables users to authenticate via Google OAuth, view their due invoices, and trigger automated reminders using Zapier workflows.

## Features

- Google OAuth 2.0 Login (React + Node.js)
- Secure JWT-based authentication
- View due/past-due invoices per user
- Trigger invoice reminder workflows via Zapier
- MongoDB-based invoice tracking

## Tech Stack

### Frontend:

- React
- @react-oauth/google
- Axios

### Backend:

- Node.js
- Express
- MongoDB (via Mongoose)
- JWT
- google-auth-library

### Integrations:

- Zapier Webhooks

## Project Structure

```
root/
├── client/                 # React frontend
│   ├── src/
│   │   ├── App.js
│   │   ├── components/
│   │   └── pages/
│   └── package.json
├── server/                 # Node.js backend
│   ├── models/
│   │   └── Invoice.js
│   ├── routes/
│   │   ├── auth.js
│   │   └── invoice.js
│   ├── middleware/
│   │   └── auth.js
│   ├── server.js
│   └── .env
├── README.md
└── package.json
```

## Environment Variables

Create a `.env` file inside the `server` folder with:

```
MONGO_URI=your_mongo_connection_string
JWT_SECRET=your_secret_key
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

## Installation

1. Clone the repository:

```bash
git clone https://github.com/your-username/invoice-platform.git
```

2. Install dependencies:

```bash
cd server
npm install

cd ../client
npm install
```

3. Run development servers:

```bash
cd server
npm run dev

cd ../client
npm start
```

## Zapier Setup

1. Go to Zapier → Create Zap
2. Choose Webhooks by Zapier → Catch Hook
3. Paste the Zapier webhook URL into your frontend/backend POST trigger
4. Add actions like sending email via Gmail or logging to Sheets

## API Overview

- `POST /api/auth/google-login` → Logs user in using Google token and returns JWT
- `GET /api/invoices/due` → Fetches all due invoices for the authenticated user
- `POST /api/zapier/remind` → Triggers Zapier automation with invoice details

## Optional Features

- CRON-based automated reminders
- Email template customization
- Reminder tracking dashboard
