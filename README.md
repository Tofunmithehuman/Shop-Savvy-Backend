Shop Savvy Backend
This is the backend for an e-commerce website built with Node.js, Express, and MongoDB. It provides APIs for user authentication, product management, order processing, and admin functionality, using Mongoose for data modeling and JWT for authentication.

Project Structure
backend/
├── config/
│   └── db.js                    # MongoDB connection configuration
├── controllers/
│   ├── userController.js        # User operations (register, login, manage users)
│   ├── productController.js     # Product operations (CRUD)
│   └── orderController.js       # Order operations (create, view, update status)
├── middleware/
│   ├── auth.js                  # Authentication middleware for protected routes
│   ├── admin.js                 # Admin-only middleware
│   └── error.js                 # Error handling middleware
├── models/
│   ├── User.js                  # User Mongoose schema
│   ├── Product.js               # Product Mongoose schema
│   └── Order.js                 # Order Mongoose schema
├── routes/
│   ├── userRoutes.js            # User-related API routes
│   ├── productRoutes.js         # Product-related API routes
│   └── orderRoutes.js           # Order-related API routes
├── .env                         # Environment variables (e.g., MONGO_URI, JWT_SECRET)
├── .gitignore                   # Git ignore file
├── package.json                 # Node.js dependencies and scripts
├── index.js                     # Main Express server file
└── README.md                    # This file

Key Components

Models: Mongoose schemas for User, Product, and Order define the data structure.
Controllers: Handle business logic for user authentication, product CRUD, and order management.
Routes: Define API endpoints for users, products, and orders, with appropriate middleware.
Middleware:
auth.js: Verifies JWT tokens for protected routes.
admin.js: Restricts access to admin-only routes.
error.js: Centralized error handling.


Config: db.js manages MongoDB connection.

Setup Instructions
Prerequisites

Node.js (v16 or higher)
MongoDB (local or MongoDB Atlas)
npm or yarn

Installation

Clone the repository and navigate to the backend/ directory:
cd backend


Install dependencies:
npm install


Create a .env file in the backend/ directory with the following:
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=5000


MONGO_URI: Connection string for MongoDB (e.g., mongodb://localhost/ecommerce or MongoDB Atlas URI).
JWT_SECRET: A secure string for signing JWT tokens.
PORT: Port for the server (default: 5000).


Start the server:
npm start

The server will run on http://localhost:5000.


API Endpoints
User Routes (/api/users)

POST /register: Register a new user.
POST /login: Log in a user and return a JWT token.
GET / (admin): Get all users.
DELETE /:id (admin): Delete a user.

Product Routes (/api/products)

GET /: Get all products.
GET /:id: Get a product by ID.
POST / (admin): Create a new product.
PUT /:id (admin): Update a product.
DELETE /:id (admin): Delete a product.

Order Routes (/api/orders)

POST / (authenticated): Create a new order.
GET / (authenticated): Get orders for the authenticated user.
GET /admin (admin): Get all orders.
PUT /:id (admin): Update order status.

Admin Access

To access admin routes, create a user via POST /api/users/register.
Manually set the user's role to admin in MongoDB (e.g., using MongoDB Compass or a script).
Use the admin user's JWT token for admin routes.

Dependencies

express: Web framework for Node.js.
mongoose: MongoDB object modeling.
jsonwebtoken: JWT for authentication.
bcryptjs: Password hashing.
cors: Enable cross-origin requests.
dotenv: Environment variable management.

Install dependencies via package.json:
{
  "dependencies": {
    "bcryptjs": "^2.4.3",
    "cors": "^2.8.5",
    "dotenv": "^16.0.3",
    "express": "^4.18.2",
    "jsonwebtoken": "^9.0.0",
    "mongoose": "^7.6.3"
  }
}

Notes

Security: Add input validation (e.g., express-validator) and sanitization for production.
Image Uploads: For product images, integrate Cloudinary or AWS S3 with multer.
Testing: Write unit and integration tests using Jest and Supertest.
Scalability: Add pagination for large datasets and caching for frequently accessed data.
Error Handling: The error.js middleware logs errors and returns a generic response.

Running the Server

Development: npm start (uses nodemon if installed).
Production: Use a process manager like PM2 and configure a reverse proxy (e.g., Nginx).

For issues or contributions, please open a pull request or issue on the repository.
