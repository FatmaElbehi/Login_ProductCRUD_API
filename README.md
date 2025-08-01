
🛠️ Login & Product CRUD API (Node.js, Express, MongoDB)

This is a secure RESTful API built with **Node.js**, **Express**, and **MongoDB** that supports user registration, login with JWT authentication, and CRUD operations on products. It includes validation, access control, and pagination. This project is ideal for learning how to implement secure API endpoints.

---

## 📦 Features

- 🔐 User Registration and Login with Password Hashing (bcrypt)
- ✅ JWT-based Authentication Middleware
- 📦 CRUD APIs for Products
- 🔎 Product Search & Pagination
- 🧪 Automated Postman Tests
- ❌ Logical Deletion (Soft Delete)

---

## 🚀 Getting Started

### 🧱 Prerequisites

- Node.js (v14+ recommended)
- MongoDB running locally on \`mongodb://127.0.0.1:27017/productDB\`

### 📂 Installation

\`\`\`bash
git clone https://github.com/FatmaElbehi/registration-and-login-application-with-crud-operation-using-MERN-stack.git
cd backend
npm install
\`\`\`

### 🧪 Run the App

\`\`\`bash
node server.js
\`\`\`

Server will run on: \`http://localhost:2000\`

---

## 🔐 Authentication

All endpoints (except \`/login\`, \`/register\`, and \`/\`) are protected. You must include the JWT \`token\` in the headers:

\`\`\`
token: <your_jwt_token>
\`\`\`

---

## 📚 API Endpoints

### ✅ Auth

#### \`POST /register\`

Registers a new user.

- Body:
  \`\`\`json
  {
    "username": "testuser",
    "password": "testpass"
  }
  \`\`\`

#### \`POST /login\`

Logs in and returns a JWT.

- Body:
  \`\`\`json
  {
    "username": "testuser",
    "password": "testpass"
  }
  \`\`\`

- Response:
  \`\`\`json
  {
    "message": "Login Successfully.",
    "token": "jwt_token_here",
    "status": true
  }
  \`\`\`

---

### 📦 Product Operations

> All product endpoints require authentication (\`token\` header)

#### \`POST /add-product\`

Add a new product.

- Body:
  \`\`\`json
  {
    "name": "Laptop",
    "desc": "A gaming laptop",
    "price": 1200,
    "discount": 10
  }
  \`\`\`

#### \`PUT /update-product/:id\`

Update an existing product.

- Body:
  \`\`\`json
  {
    "name": "Updated Laptop",
    "desc": "New description",
    "price": 999,
    "discount": 15
  }
  \`\`\`

#### \`DELETE /delete-product/:id\`

Soft delete a product (sets \`is_delete = true\`).

#### \`GET /get-product?search=&page=1\`

Search products by name and paginate results.

- Query Params:
  - \`search\`: optional, search by product name
  - \`page\`: optional, default is 1

- Response:
  \`\`\`json
  {
    "status": true,
    "title": "Product retrieved.",
    "products": [...],
    "current_page": 1,
    "total": 10,
    "pages": 2
  }
  \`\`\`

---

## 🔬 Postman Collection

Use the included Postman Collection for automated testing:

### 🧪 Collection: \`Automation API Testing for Login & Products CRUD App\`

#### Includes:

- ✅ Register Tests
  - Positive (New User)
  - Negative (User Exists / Missing Parameters)
- ✅ Login Tests
  - Positive (Correct Credentials)
  - Negative (Wrong Credentials)
- ✅ Product Tests
  - Add Product (Valid & Invalid)
  - View Products
  - Update Product (Valid & Invalid)
  - Delete Product

📥 **Import collection** into Postman and configure the following environment variables:

| Variable          | Example Value         |
|------------------|------------------------|
| \`base_url\`       | \`http://localhost:2000\`|
| \`username\`       | \`testuser\`             |
| \`password\`       | \`testpass\`             |
| \`token\`          | (set dynamically on login) |
| \`product_name\`   | \`Gaming Laptop\`        |
| \`product_desc\`   | \`High performance\`     |
| \`product_price\`  | \`1299\`                 |
| \`product_discount\` | \`10\`                |
| \`product_id\`     | (set after adding a product) |

---
🧪  **Newman CLI Integration (Automation)** \`
- 📥 Step 1: Install Newman globally:
    - npm install -g newman
- 📤 Step 2: Export Postman Collection & Environment
In Postman, click "Export Collection"

- ▶️ Step 3: Run Collection with Newman
    - newman run <collection_name.json> -e <environment_name.json>
- 📊 Step 4: Generate HTML Report
    - You can generate a visual report using Newman reporters like this:
        -   npm install -g newman-reporter-html
    - newman run collection.json -e environment.json -r cli,html

---

## 🔐 Security Notes

- Passwords are hashed using \`bcrypt\`.
- JWT tokens are signed with a secret (\`shhhhh11111\`).
- All protected routes validate JWT and ensure correct user access.
- Only the owner of a product can access or modify it.

---

## 🧹 Future Improvements

- 🧾 Add image uploads for products
- 🧍‍♂️ Add user profile management
- 📊 Admin panel for product/user stats
- 📦 Pagination customization

---

## 🧑‍💻 Author

Developed by: **FatmaElbehi**  
Email: \`fatmaelbehi9@gmail.com`

---

