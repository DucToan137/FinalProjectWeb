# 🛍️ E-Commerce Platform with Admin Dashboard

A full-featured e-commerce web application built with Node.js, Express, MongoDB, and Tailwind CSS. This platform provides a complete shopping experience with integrated payment gateways and a comprehensive admin management system.

## ✨ Key Features

### 🛒 Customer Features

- **Product Catalog**: Browse products with advanced filtering by categories and brands
- **Product Search**: ElasticSearch integration for fast and accurate product search
- **Shopping Cart**: Real-time cart management with quantity updates
- **User Authentication**:
  - Local authentication with email/password
  - Google OAuth2 integration
  - Password reset via email
- **Product Reviews**: Rate and review purchased products
- **Order Management**: Track order status and history
- **Address Management**: Save and manage multiple shipping addresses
- **User Profile**: Update personal information and avatar

### 👨‍💼 Admin Features

- **Dashboard**: Real-time analytics and business metrics
- **Product Management**:
  - Add, edit, and delete products
  - Multi-image upload support
  - Inventory tracking
  - Restore deleted products
- **Category & Brand Management**: Organize products efficiently
- **Order Management**: Process and track orders by status
- **User Management**: View and manage customer accounts (lock/unlock users)
- **Revenue Analytics**:
  - Time-based revenue reports
  - Top-selling products analysis
  - Visual charts using Chart.js
- **Admin Profile**: Manage admin account settings

## 🛠️ Technology Stack

**Backend:**

- Node.js & Express.js
- MongoDB with Mongoose ODM
- Passport.js (Local & Google OAuth2)
- JWT for authentication
- ElasticSearch for product search

**Frontend:**

- EJS templating engine
- Tailwind CSS & Flowbite UI
- Vanilla JavaScript
- Chart.js for analytics
- Swiper.js for image carousels

**File Storage:**

- Firebase for image hosting
- Multer for file uploads

**Development Tools:**

- Docker Compose for MongoDB
- Nodemon for development
- Migrate-mongo for database migrations

## 📦 Installation

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (or use Docker setup)

### Setup Steps

**1. Clone the repository:**

```bash
git clone https://github.com/DucToan137/FinalProjectWeb.git
cd FinalProjectWeb
```

**2. Install dependencies:**

```bash
npm install
```

**3. Set up environment variables:**

Create a `.env` file in the root directory with the following variables:

```env
# Server Configuration
PORT=3000
BASE_URL=http://localhost:3000

# MongoDB
MONGO_URI=mongodb://admin:admin@localhost:27023/ecommerce?authSource=admin

# Firebase Configuration
FIREBASE_API_KEY=your_firebase_api_key
FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
FIREBASE_PROJECT_ID=your_firebase_project_id
FIREBASE_STORAGE_BUCKET=your_firebase_storage_bucket
FIREBASE_MESSAGING_SENDER_ID=your_firebase_messaging_sender_id
FIREBASE_APP_ID=your_firebase_app_id

# Google OAuth2
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# Email Configuration
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_app_password

# ElasticSearch
ELASTIC_SEARCH_NODE=http://localhost:9200
```

**4. Start MongoDB with Docker:**

```bash
docker-compose up -d
```

**5. Run database migrations:**

```bash
npx migrate-mongo up
```

**6. Build Tailwind CSS:**

```bash
npm run watch
```

In a separate terminal, start the server:

**7. Start the application:**

```bash
# Development mode with auto-reload
npm run dev

# Production mode
npm start
```

**8. Access the application:**

- Customer Portal: `http://localhost:3000`
- Admin Dashboard: `http://localhost:3000/admin/dashboard`

## 🚀 Usage

### Default Accounts

After running migrations, you can use these accounts:

**Admin Account:**

- Email: `admin@example.com`
- Password: Check migration files or create your own

**Customer Account:**

- Register a new account at `http://localhost:3000/user/register`
- Or login with Google OAuth2

### Key Routes

**Customer Routes:**

- `/` - Home page
- `/products/get` - Product catalog
- `/productDetails/:id` - Product details
- `/carts/get` - Shopping cart
- `/orders/get` - Order history
- `/user/login` - Login page
- `/user/register` - Registration page
- `/user/profile` - User profile

**Admin Routes:**

- `/admin/dashboard` - Admin dashboard
- `/admin/products` - Product management
- `/admin/categories` - Category management
- `/admin/brands` - Brand management
- `/admin/orders/:status` - Order management
- `/admin/users` - User management
- `/admin/revenue/time` - Revenue analytics
- `/admin/profile` - Admin profile

## 📁 Project Structure

```
FinalProject-Web/
├── src/
│   ├── Address/              # Address management
│   │   └── Shop/
│   ├── Banner/               # Banner management
│   ├── Brand/                # Brand management
│   │   └── Admin/
│   ├── Cart/                 # Shopping cart
│   │   └── Shop/
│   ├── Category/             # Category management
│   │   └── Admin/
│   ├── Config/               # Configuration files
│   │   ├── elasticSearch.js
│   │   ├── firebase.js
│   │   ├── mongooseDB.js
│   │   ├── multer.js
│   │   └── paypal.js
│   ├── Factory/              # Service factory pattern
│   ├── HomePage/             # Home page controllers
│   │   ├── Admin/
│   │   └── Shop/
│   ├── ImagesProduct/        # Product images
│   ├── middleWare/           # Authentication & Authorization
│   │   ├── Authentication/
│   │   └── Authorization/
│   ├── Model/                # Mongoose schemas
│   │   ├── Address.js
│   │   ├── Banner.js
│   │   ├── Brand.js
│   │   ├── Cart.js
│   │   ├── Category.js
│   │   ├── Order.js
│   │   ├── Product.js
│   │   ├── Review.js
│   │   └── User.js
│   ├── Order/                # Order management
│   │   ├── Admin/
│   │   └── Shop/
│   ├── Product/              # Product management
│   │   ├── Admin/
│   │   └── Shop/
│   ├── Review/               # Product reviews
│   │   └── Shop/
│   ├── Revenue/              # Revenue analytics
│   │   └── Admin/
│   ├── User/                 # User management
│   │   ├── Admin/
│   │   └── Shop/
│   └── Utils/                # Utility functions
├── views/                    # EJS templates
│   ├── admin/
│   │   ├── Brand/
│   │   ├── Category/
│   │   ├── Order/
│   │   ├── Product/
│   │   ├── Revenue/
│   │   └── User/
│   ├── payment/
│   ├── account.ejs
│   ├── cart.ejs
│   ├── home.ejs
│   ├── login.ejs
│   ├── products.ejs
│   └── ...
├── public/                   # Static files
│   ├── assets/
│   │   ├── css/
│   │   ├── images/
│   │   └── icons/
│   └── js/
│       ├── admin/
│       ├── cart/
│       ├── products/
│       └── ...
├── migrations/               # Database migrations
├── docker-compose.yaml       # Docker configuration
├── package.json
├── server.js                 # Entry point
└── tailwind.config.cjs       # Tailwind CSS config
```

## 🔐 Security Features

- **Password Security**: Bcrypt hashing for user passwords
- **Session Management**: Express-session with secure cookie configuration
- **Authentication**: Passport.js with local and OAuth2 strategies
- **Authorization**: Role-based access control (Admin/Customer)
- **JWT Tokens**: For password reset and secure operations
- **Input Validation**: Server-side validation for all user inputs
- **HTTPS Support**: Ready for production deployment with SSL

## 🧪 Testing

```bash
npm test
```

## 📊 Database Schema

### Main Collections:

- **Users**: Customer and admin accounts
- **Products**: Product catalog with variants
- **Categories**: Product categorization
- **Brands**: Product brands
- **Orders**: Order records and tracking
- **Carts**: Shopping cart items
- **Reviews**: Product reviews and ratings
- **Addresses**: Customer shipping addresses

## 🌟 Highlights

- **Scalable Architecture**: Modular design following MVC pattern
- **Responsive Design**: Mobile-first approach with Tailwind CSS
- **Real-time Updates**: Dynamic UI updates without page refresh
- **SEO Friendly**: Server-side rendering with EJS
- **Admin Analytics**: Comprehensive business insights
- **Search Optimization**: ElasticSearch for lightning-fast searches
- **Image Management**: Firebase integration for scalable image storage

## 📝 License

This project is licensed under the ISC License.
