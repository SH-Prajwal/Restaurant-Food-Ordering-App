# 🍽️ Indian Restaurant Management System

A full-stack MERN (MongoDB, Express, React, Node.js) application for managing a restaurant with separate customer and admin interfaces.

## ✨ Features

### Customer Features

- **Authentication**: Login/Signup with email or mobile number
- **Browse Menu**: View food items organized by categories (Breakfast, Starters, Main Course, Breads, Rice & Biryani, Desserts)
- **Cart Management**: Add items to cart, update quantities, remove items
- **Checkout**: View itemized bill with GST calculation
- **Order History**: View all past orders with details

### Admin Features

- **Menu Management**: Add new food categories and items
- **Category Management**: Create and delete categories
- **Item Management**: Add, view, and delete food items
- **Availability Control**: Mark items as available or unavailable

## 🛠️ Tech Stack

**Frontend:**

- React 18
- React Router DOM (routing)
- Tailwind CSS (styling)
- Axios (API calls)
- React Icons
- React Toastify (notifications)
- Vite (build tool)

**Backend:**

- Node.js
- Express.js
- MongoDB with Mongoose
- JWT (authentication)
- Bcrypt.js (password hashing)
- CORS
- Validator

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** package manager
- **MongoDB Atlas Account** (Free) - We'll set this up below

> **Note:** You DON'T need to install MongoDB locally. We'll use MongoDB Atlas (free cloud database).

## 🚀 Installation & Setup

### 1. Setup MongoDB Atlas (Free Cloud Database)

Since you don't have MongoDB installed locally, follow these steps to create a free cloud database:

#### Step 1.1: Create MongoDB Atlas Account

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register)
2. Sign up for a free account (no credit card required)
3. Verify your email

#### Step 1.2: Create a Cluster

1. After login, click **"Build a Database"**
2. Choose **"M0 FREE"** tier (totally free forever)
3. Select a cloud provider (AWS, Google Cloud, or Azure) - any is fine
4. Choose a region closest to you (e.g., Mumbai for India)
5. Name your cluster (or keep default) and click **"Create"**
6. Wait 1-3 minutes for cluster creation

#### Step 1.3: Create Database User

1. You'll see **"Security Quickstart"**
2. Under **"How would you like to authenticate your connection?"**
   - Choose **"Username and Password"**
   - Create a username (e.g., `restaurantUser`)
   - Create a password (e.g., `Restaurant123`) - **Remember this!**
   - Click **"Create User"**

#### Step 1.4: Add Your IP Address

1. Under **"Where would you like to connect from?"**
   - Choose **"My Local Environment"**
   - Click **"Add My Current IP Address"**
   - Alternatively, to allow from anywhere (less secure but easier for development):
     - Click **"Add IP Address"**
     - Enter `0.0.0.0/0`
     - Description: "Allow All"
     - Click **"Add Entry"**
2. Click **"Finish and Close"**

#### Step 1.5: Get Connection String

1. Click **"Connect"** button on your cluster
2. Choose **"Drivers"**
3. Select **"Node.js"** and version **"4.1 or later"**
4. Copy the connection string (looks like):
   ```
   mongodb+srv://restaurantUser:<password>@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority
   ```
5. **Replace** `<password>` with your actual password
6. **Add** the database name before the `?`. Example:
   ```
   mongodb+srv://restaurantUser:Restaurant123@cluster0.xxxxx.mongodb.net/restaurant_db?retryWrites=true&w=majority
   ```

### 2. Clone or Navigate to Project Directory

```bash
cd "C:\Users\prajw\Downloads\SI"
```

### 3. Install Backend Dependencies

```bash
cd server
npm install
```

This will install all required packages (Express, Mongoose, JWT, etc.)

### 4. Install Frontend Dependencies

```bash
cd ../client
npm install
```

This will install all required packages (React, Tailwind, Axios, etc.)

### 5. Configure Environment Variables

Navigate to the server folder and edit the `.env` file:

```bash
cd ../server
notepad .env
```

**Replace the content with your MongoDB Atlas connection string:**

```env
MONGODB_URI=mongodb+srv://restaurantUser:Restaurant123@cluster0.xxxxx.mongodb.net/restaurant_db?retryWrites=true&w=majority
JWT_SECRET=your_super_secret_jwt_key_here_change_in_production
PORT=5000
```

**Important:**

- Replace the `MONGODB_URI` with YOUR connection string from Step 1.5
- Make sure to replace `<password>` with your actual password
- Add `/restaurant_db` before the `?` in the connection string

### 6. Seed the Database

This will populate your MongoDB Atlas database with initial categories, food items, and admin account:

```bash
npm run seed
```

**Default Admin Credentials:**

- Email: `admin@restaurant.com`
- Password: `Admin@123`

You should see output like:

```
Connected to MongoDB
Cleared existing data
Admin user created
Categories created
Food items created
========================================
Database seeded successfully!
========================================
```

If you see **"Connected to MongoDB"**, your Atlas connection is working! ✅

## 🎯 Running the Application

> **Note:** Since you're using MongoDB Atlas (cloud database), you DON'T need to start MongoDB locally.

### Start the Backend Server

Open a terminal in the `server` folder:

```bash
cd server
npm run dev
```

The server will start on `http://localhost:5000`

### Start the Frontend

Open another terminal in the `client` folder:

```bash
cd client
npm run dev
```

The React app will start on `http://localhost:3000`

### Access the Application

Open your browser and navigate to: **http://localhost:3000**

## 📖 Usage Guide

### For Customers

1. **Sign Up / Login**

   - Click "Sign Up" to create a new account
   - Choose either Email or Mobile number registration
   - Enter your credentials and password (minimum 6 characters)
   - After signup, you'll be automatically logged in

2. **Browse Menu**

   - View food items organized by categories
   - Click on category tabs to filter items
   - Each item displays name, description, price, and image

3. **Add to Cart**

   - Click "Add" button on any food item
   - Item is added to your cart (indicated by cart icon count in navbar)

4. **Manage Cart**

   - Click the cart icon in navbar to view cart
   - Use +/- buttons to adjust quantities
   - Click trash icon to remove items
   - View subtotal and proceed to checkout

5. **Checkout**

   - Review your order items
   - View itemized bill with:
     - Individual item prices × quantity
     - Subtotal
     - GST (5%)
     - Total amount
   - Click "Place Order" to confirm

6. **Order Confirmation**

   - See "Order Placed Successfully" message
   - Automatically redirected to Order History

7. **View Order History**
   - Click "Orders" in navbar
   - View all past orders with:
     - Order ID and date
     - Items ordered with quantities
     - Bill breakdown
     - Order status

### For Admin

1. **Login**

   - Use admin credentials:
     - Email: `admin@restaurant.com`
     - Password: `Admin@123`
   - You'll be redirected to Admin Dashboard

2. **Add New Category**

   - Fill in category name
   - Enter description
   - Add image URL (optional)
   - Click "Add Category"

3. **Add Food Item**

   - Enter item name and description
   - Set price
   - Select category from dropdown
   - Add image URL
   - Check/uncheck "Available" status
   - Click "Add Item"

4. **Manage Existing Items**
   - View all categories in a table
   - View all food items with their details
   - Delete items or categories using trash icon
   - Note: Cannot delete categories that have items

## 🌐 API Endpoints

### Authentication

- `POST /api/auth/signup` - Register new user
- `POST /api/auth/login` - Login user

### Menu (Public)

- `GET /api/menu/categories` - Get all categories
- `GET /api/menu/items` - Get all food items
- `GET /api/menu/items/category/:categoryId` - Get items by category

### Menu (Admin Only)

- `POST /api/menu/category` - Create category
- `POST /api/menu/item` - Create food item
- `PUT /api/menu/item/:id` - Update food item
- `DELETE /api/menu/item/:id` - Delete food item
- `DELETE /api/menu/category/:id` - Delete category

### Orders (Customer)

- `POST /api/orders/create` - Create new order
- `GET /api/orders/my-orders` - Get user's orders

## 🎨 Default Menu Categories

The seeded database includes these Indian food categories:

1. **Breakfast** - Masala Dosa, Idli Sambar, Poha, Upma
2. **Starters** - Paneer Tikka, Samosa, Veg Pakora, Aloo Tikki
3. **Main Course** - Butter Chicken, Paneer Butter Masala, Dal Makhani, Chole Bhature, Palak Paneer
4. **Breads** - Butter Naan, Garlic Naan, Tandoori Roti, Laccha Paratha
5. **Rice & Biryani** - Veg Biryani, Chicken Biryani, Jeera Rice, Veg Pulao
6. **Desserts** - Gulab Jamun, Kulfi, Rasmalai, Gajar Halwa

## 🔐 Security Features

- Password hashing with bcrypt
- JWT token-based authentication
- Protected routes for authenticated users
- Role-based access control (Admin vs Customer)
- Token expiration (7 days)
- Input validation on both frontend and backend

## 📱 Multi-User Support

The application supports:

- Multiple concurrent customer accounts
- Separate sessions on different devices
- 10+ customers can use the system simultaneously
- Each customer has isolated cart and order history

## 🐛 Troubleshooting

### MongoDB Connection Error

**If using MongoDB Atlas:**

- Double-check your connection string in `.env`
- Make sure you replaced `<password>` with your actual password
- Verify your IP address is whitelisted in Atlas (or use `0.0.0.0/0`)
- Check that you added `/restaurant_db` before the `?` in the connection string
- Ensure your internet connection is active

**Common connection string mistakes:**

```env
❌ Wrong: mongodb+srv://user:<password>@cluster...
✅ Right: mongodb+srv://user:YourActualPassword@cluster...

❌ Wrong: mongodb+srv://user:pass@cluster...?retryWrites=true
✅ Right: mongodb+srv://user:pass@cluster.../restaurant_db?retryWrites=true
```

### Port Already in Use

- Backend: Change PORT in `.env` file
- Frontend: Change port in `client/vite.config.js`

### Seed Script Issues

- Make sure your internet is working (for MongoDB Atlas)
- Verify connection string is correct in `.env`
- Delete the database collection and re-run seed: `npm run seed`

### Cannot Login

- Verify you've seeded the database
- Check admin credentials are correct
- Clear browser cache and localStorage

### Images Not Loading

- Ensure image URLs are valid and accessible
- Check internet connection
- Use different image URLs if needed

## 📂 Project Structure

```
SI/
├── server/                 # Backend
│   ├── models/            # MongoDB schemas
│   │   ├── User.js
│   │   ├── Category.js
│   │   ├── FoodItem.js
│   │   └── Order.js
│   ├── routes/            # API routes
│   │   ├── auth.js
│   │   ├── menu.js
│   │   └── orders.js
│   ├── middleware/        # Auth middleware
│   │   ├── auth.js
│   │   └── adminAuth.js
│   ├── .env              # Environment variables
│   ├── .env.example      # Environment template
│   ├── server.js         # Express server
│   ├── seed.js           # Database seeder
│   └── package.json
│
├── client/                # Frontend
│   ├── src/
│   │   ├── components/   # React components
│   │   │   ├── Navbar.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   ├── context/      # Context providers
│   │   │   ├── AuthContext.jsx
│   │   │   └── CartContext.jsx
│   │   ├── pages/        # Page components
│   │   │   ├── Login.jsx
│   │   │   ├── Signup.jsx
│   │   │   ├── CustomerDashboard.jsx
│   │   │   ├── AdminDashboard.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Checkout.jsx
│   │   │   └── OrderHistory.jsx
│   │   ├── services/     # API service
│   │   │   └── api.js
│   │   ├── App.jsx       # Main app component
│   │   ├── main.jsx      # Entry point
│   │   └── index.css     # Global styles
│   ├── index.html
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── package.json
│
└── README.md
```

## 🤝 Contributing

This is a student project for educational purposes.

## 📄 License

This project is created for academic purposes.

## 👨‍💻 Author

Created as part of a MERN stack development assignment.

## 🎓 Learning Outcomes

This project demonstrates:

- Full-stack development with MERN
- RESTful API design
- JWT authentication
- Role-based access control
- State management in React
- Responsive UI with Tailwind CSS
- Database design and relationships
- Form handling and validation

---

**Enjoy using the Restaurant Management System! 🍽️**
