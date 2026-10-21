# 🍽️ QuickBite — Online Food Ordering Platform

QuickBite is a full-stack food ordering platform made of three parts: a customer-facing storefront, an admin panel for restaurant staff, and a REST API that powers both. Customers can browse a menu, fill a cart, pay online, and follow their order. Staff can manage the menu and move orders through each stage.

> Rename "QuickBite" to whatever you like — it's only a placeholder.

---

## ✨ Features

**For customers**
- Browse the menu by category
- Sign up / log in with secure token-based sessions
- Add and remove items from a persistent cart
- Checkout with Stripe and verify payment status
- View personal order history

**For admins**
- Add new dishes with image upload
- View and delete existing menu items
- See every incoming order and update its status

---

## 🧰 Tech Stack

| Layer | Technologies |
|-------|--------------|
| Storefront | React, Vite, React Router, Context API |
| Admin panel | React, Vite |
| API | Node.js, Express |
| Database | MongoDB with Mongoose |
| Auth | JWT, bcrypt |
| Payments | Stripe |
| File uploads | Multer |

---

## 📁 Project Structure

```
├── backend/                 # Express API, models, routes, uploads
├── frontend/                # Customer storefront (React + Vite)
└── admin/
    └── vite-project/        # Admin dashboard (React + Vite)
```

---

## ⚙️ Setup Guide

### Requirements
- Node.js 18+
- npm 9+
- A MongoDB database (local install or MongoDB Atlas)
- A Stripe account (test keys are fine)

### Step 1 — Clone the repo
```bash
git clone <your-repo-url>
cd <your-project-folder>
```

### Step 2 — Start the API
```bash
cd backend
npm install
```

Create a `backend/.env` file:
```env
JWT_SECRET=choose_a_long_random_string
```

> If your MongoDB connection string is set inside the backend's database config file, update it there with your own URI.

Run it:
```bash
npm run server
```
API is now live at `http://localhost:4000`.

### Step 3 — Start the storefront
```bash
cd frontend
npm install
npm run dev
```
Open `http://localhost:5173`.

### Step 4 — Start the admin panel
```bash
cd admin/vite-project
npm install
npm run dev
```
Vite will pick the next free port (usually `http://localhost:5174`).

---

## 🔌 API Reference

| Area | Base path | Endpoints |
|------|-----------|-----------|
| Users | `/api/user` | `POST /register`, `POST /login` |
| Food | `/api/food` | `POST /add`, `GET /list`, `POST /remove` |
| Cart | `/api/cart` | `POST /add`, `POST /remove`, `POST /get` |
| Orders | `/api/order` | `POST /place`, `POST /verify`, `POST /userorders`, `GET /list` |

Cart and order actions require a valid JWT sent with the request.

---

## 🔐 Security Notes

- Passwords are salted and hashed with bcrypt before being stored.
- Secrets live in `.env` files — never commit them.
- Protected routes pass through an auth middleware that validates the JWT.
- Uploaded dish images are stored on the server's local disk via Multer.

---

## 🛣️ Ideas for Improvement

- Admin login and role-based access
- Order tracking with live status updates
- Cloud image storage (e.g. Cloudinary or S3)
- Search, filters, and ratings on menu items
- Docker setup for one-command startup

---

