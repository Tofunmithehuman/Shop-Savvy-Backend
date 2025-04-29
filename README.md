# 🛒 Shop Savvy Backend

This is the **backend** of the Shop Savvy e-commerce platform, built with **Node.js**, **Express**, and **MongoDB**. It provides RESTful APIs for user authentication, product management, order processing, and admin functionality using JWT for secure access and Mongoose for MongoDB data modeling.

---

## 🔧 Tech Stack

- **Node.js** – JavaScript runtime
- **Express** – Web framework
- **MongoDB** & **Mongoose** – NoSQL database and ODM
- **JWT (jsonwebtoken)** – Token-based authentication
- **bcryptjs** – Password hashing
- **dotenv** – Environment variable management
- **CORS** – Cross-origin resource sharing

---

## 🗂️ Project Structure

```
backend/
├── config/                    # MongoDB connection setup
│   └── db.js
├── controllers/              # Route handlers (business logic)
│   ├── userController.js
│   ├── productController.js
│   └── orderController.js
├── middleware/               # Auth & error middleware
│   ├── auth.js
│   ├── admin.js
│   └── error.js
├── models/                   # Mongoose schemas
│   ├── User.js
│   ├── Product.js
│   └── Order.js
├── routes/                   # Express route definitions
│   ├── userRoutes.js
│   ├── productRoutes.js
│   └── orderRoutes.js
├── .env                      # Environment variables
├── .gitignore
├── package.json              # Dependencies & scripts
├── index.js                  # Server entry point
└── README.md
```

---

## 🚀 Features

### 👤 User

- Register and log in with JWT-based authentication
- Role-based access control (admin/user)
- Admins can manage users

### 🛍️ Products

- Full CRUD operations (admin-only)
- Public product browsing and retrieval

### 📦 Orders

- Authenticated users can place and view orders
- Admins can view and update all orders

---

## 📍 API Endpoints

### 🔐 User Routes – `/api/users`

| Method | Endpoint      | Access       | Description              |
|--------|---------------|--------------|--------------------------|
| POST   | `/register`   | Public       | Register a new user      |
| POST   | `/login`      | Public       | Login & receive token    |
| GET    | `/`           | Admin only   | Get all users            |
| DELETE | `/:id`        | Admin only   | Delete a user            |

---

### 🛒 Product Routes – `/api/products`

| Method | Endpoint     | Access     | Description               |
|--------|--------------|------------|---------------------------|
| GET    | `/`          | Public     | Get all products          |
| GET    | `/:id`       | Public     | Get product by ID         |
| POST   | `/`          | Admin only | Create a new product      |
| PUT    | `/:id`       | Admin only | Update a product          |
| DELETE | `/:id`       | Admin only | Delete a product          |

---

### 📦 Order Routes – `/api/orders`

| Method | Endpoint      | Access       | Description                     |
|--------|---------------|--------------|---------------------------------|
| POST   | `/`           | Authenticated | Place a new order               |
| GET    | `/`           | Authenticated | Get logged-in user’s orders     |
| GET    | `/admin`      | Admin only   | Get all orders                  |
| PUT    | `/:id`        | Admin only   | Update order status             |

---

## 🔐 Admin Access

1. Register a user using `/api/users/register`
2. Manually update the user's role to `admin` in MongoDB (using MongoDB Compass or a script)
3. Use this admin’s JWT token to access admin-only endpoints

---

## ⚙️ Setup Instructions

### 📦 Prerequisites

- Node.js **v16+**
- MongoDB (local or **MongoDB Atlas**)
- npm or yarn

### 🧰 Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd backend

# Install dependencies
npm install
```

### 🛠️ Environment Setup

Create a `.env` file in `backend/`:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=5000
```

### 🚀 Start the Server

```bash
npm start
```

Server runs at: `http://localhost:5000`

---

## 📦 Dependencies

```json
"dependencies": {
  "bcryptjs": "^2.4.3",
  "cors": "^2.8.5",
  "dotenv": "^16.0.3",
  "express": "^4.18.2",
  "jsonwebtoken": "^9.0.0",
  "mongoose": "^7.6.3"
}
```

---

## 🧪 Testing & Deployment

### ✅ Testing Suggestions

- Use **Jest** and **Supertest** for unit and integration testing
- Test:
  - Auth flows
  - Protected routes
  - CRUD operations

### 🚀 Deployment Tips

- Use **PM2** for production process management
- Configure a **reverse proxy** (e.g., **Nginx**)
- Add **rate limiting** and **input validation** (e.g., `express-validator`)

---

## 📌 Notes & Enhancements

- 🛡️ **Security**: Sanitize input and validate data before DB writes
- 🖼️ **Image Uploads**: Use Cloudinary, S3, or multer for product images
- ⚡ **Scalability**: Implement pagination and caching (e.g., Redis)
- 🐞 **Error Handling**: Centralized with `middleware/error.js`

---

## 🤝 Contributing

Found a bug or want to contribute?

- Open an **issue** or **pull request** on GitHub
- Follow code formatting and ensure routes are tested
