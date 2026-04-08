# 🅿️ ParkIt

> A full-stack parking booking platform that lets users find, book, and list parking spots in their city — built with React, Node.js, Express, MongoDB, and JWT authentication.


## 📌 What is ParkIt?

ParkIt is a two-sided parking marketplace:

- **Drivers** can search for available parking spots by city, view details, and book slots for a specific time range.
- **Parking owners** can list their parking spaces, set fees, and manage bookings.
- All users get a personal dashboard to track their active bookings and listings.

---

## ✨ Features

- 🔐 JWT-based authentication (register / login)
- 🔍 Search and browse all available parking spots
- 📅 Book parking with start time, end time, and slot count
- 💰 Automatic price calculation based on duration and fee
- 🏗️ List your own parking space for rent
- 📋 View and manage your bookings
- 🗑️ Cancel bookings and remove listings
- 📱 Fully responsive UI

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 18, React Router v6 |
| Styling | Inline styles (Georgia serif design system) |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Auth | JSON Web Tokens (JWT) |
| State | React Context API (AuthContext) |

---

## 📁 Folder Structure

```
parkit/
├── client/                   # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Navbar.jsx        # Shared navbar with profile dropdown
│   │   ├── auth/
│   │   │   └── AuthContext.jsx   # JWT auth state management
|   |   |   ├── Sign-in-auth.jsx
│   │   │   ├── Sign-up-auth.jsx
│   │   ├── pages/
│   │   │   ├── AllParkings.jsx
│   │   │   ├── BookParking.jsx
│   │   │   ├── MyBookings.jsx
│   │   │   ├── MyOwnedParkings.jsx
│   │   │   └── RentParking.jsx
│   │   │   ├── MainPage.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│
├── server/                   # Express backend
│   ├── controllers/
│   │   ├── Parking-controller.js
│   │   ├── Booking-controller.js
│   │   └── User-controller.js
│   ├── models/
│   │   ├── Parking-model.js
│   │   ├── Booking-model.js
│   │   └── User-model.js
│   ├── routes/
│   │   ├── Parking-routes.js
│   │   ├── Booking-routes.js
│   │   └── User-routes.js
│   ├── middleware/
│   │   └── Auth-middleware.js
│   ├── database/
│   │   ├── db.js
│   └── server.js
```

---

## ⚙️ Setup & Installation

### Prerequisites

- Node.js v18+
- MongoDB (local or [MongoDB Atlas](https://www.mongodb.com/cloud/atlas))
- npm or yarn

---

### 1. Clone the repository

```bash
git clone https://github.com/Yash-Khandelwal2004/IarkIt.git
cd parkit
```

---

### 2. Backend Setup

```bash
cd server
npm install
```

Create a `.env` file in the `server/` directory:

```env
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_super_secret_jwt_key
```

Start the backend server:

```bash
npm run dev
```

The server will run on `http://localhost:3000`

---

### 3. Frontend Setup

```bash
cd client
npm install
npm run dev
```

The frontend will run on `http://localhost:5173`

---

## 📡 API Endpoints

### 🔑 Auth Routes — `/api/user`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| POST | `/register` | No | Register a new user |
| POST | `/login` | No | Login and receive JWT token |

**Register request body:**
```json
{
  "username": "johndoe",
  "email": "john@example.com",
  "password": "yourpassword"
}
```

**Login request body:**
```json
{
  "email": "john@example.com",
  "password": "yourpassword"
}
```

**Login response:**
```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIs...",
  "user": { "name": "John", "email": "john@example.com" }
}
```

---

### 🅿️ Parking Routes — `/api/parking`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| GET | `/allparkings` | No | Get all available parking spots |
| GET | `/my-owned` | ✅ Yes | Get parkings owned by logged-in user |
| GET | `/my-booked` | ✅ Yes | Get parkings booked by logged-in user |
| POST | `/register` | ✅ Yes | List a new parking spot |
| DELETE | `/delete/:id` | ✅ Yes | Delete a parking listing |

**Register parking request body:**
```json
{
  "address": "12, MG Road, Bangalore",
  "fee": 50,
  "count": 5,
  "type": "four wheeler"
}
```

---

### 📅 Booking Routes — `/api/booking`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| POST | `/book-parking/:parkingId` | ✅ Yes | Book a parking slot |
| GET | `/my-bookings` | ✅ Yes | Get all bookings made by logged-in user |
| DELETE | `/cancel-parking/:bookingId` | ✅ Yes | Cancel a booking |

**Book parking request body:**
```json
{
  "count": 2,
  "startTime": "2025-03-01T10:00:00.000Z",
  "endTime": "2025-03-01T13:00:00.000Z"
}
```

**Book parking response:**
```json
{
  "message": "Parking booked successfully",
  "booking": {
    "_id": "...",
    "user": "...",
    "parking": "...",
    "count": 2,
    "startTime": "...",
    "endTime": "...",
    "priceAtBooking": 300,
    "status": "confirmed"
  },
  "remainingSlots": 3
}
```

> **Note:** All protected routes require the header:
> ```
> Authorization: Bearer <your_jwt_token>
> ```

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. Fork the repository
2. Create a new branch — `git checkout -b feature/your-feature-name`
3. Make your changes and commit — `git commit -m "Add: your feature"`
4. Push to your fork — `git push origin feature/your-feature-name`
5. Open a Pull Request

Please make sure your code is clean, consistent with the existing style, and tested before submitting a PR.

---

## 🐛 Found a Bug?

Open an [issue](https://github.com/Yash-Khandelwal2004/ParkIt/issues) with:
- What you expected to happen
- What actually happened
- Steps to reproduce

---

## 👤 Author

**Yash Khandelwal**
- GitHub: [@Yash-Khandelwal2004](https://github.com/Yash-Khandelwal2004)

---

