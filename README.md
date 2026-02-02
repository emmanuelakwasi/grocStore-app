# GrocStore - Full-Stack E-Commerce Platform

A full-stack grocery e-commerce platform that brings local sellers and customers together. Features include dual-role authentication (customers & sellers), secure payment processing, and a scalable cloud infrastructure. Built by a team of 4 developers.

## Live Demo

- **Backend API**: Deployed on Vercel

##  Key Features

### User Experience
- **Dual Authentication System**: Separate JWT-based auth flows for customers and sellers with role-based access control protecting 15+ API routes
- **Payment Processing**: Stripe Checkout integration with webhook verification handles both online payments and cash-on-delivery orders securely
- **Product Management**: Cloudinary-powered image uploads let sellers add multiple product photos and manage their inventory easily
- **Shopping Cart**: Persistent cart storage in MongoDB keeps items synced across browser sessions and devices
- **Order Management**: Complete order tracking system with status updates, payment verification, and full order history

### Technical Highlights
- **RESTful API**: 6 modular route handlers (users, sellers, products, cart, orders, addresses) with middleware-based auth
- **Database Design**: MongoDB schemas with proper references and indexing for fast queries across 4 core collections
- **Image Handling**: Automated upload workflow using Multer and Cloudinary eliminates server storage needs entirely
- **Payment Security**: Stripe webhook signature verification ensures payment events are legitimate and prevents fraud
- **Responsive UI**: Mobile-first design with Tailwind CSS works seamlessly on phones, tablets, and desktops

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI library with hooks and context API
- **Vite** - Lightning-fast build tool and dev server
- **React Router v7** - Client-side routing with nested routes
- **Tailwind CSS 4** - Utility-first styling framework
- **Axios** - HTTP client with credential management
- **React Hot Toast** - User feedback notifications

### Backend
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - Stateless authentication tokens
- **Stripe API** - Payment processing and webhooks
- **Cloudinary** - Cloud-based image management
- **Multer** - File upload middleware
- **bcryptjs** - Password hashing
- **Cookie Parser** - Secure cookie handling

### DevOps & Deployment
- **Vercel** - Frontend and backend hosting
- **MongoDB Atlas** - Cloud database hosting
- **Environment Variables** - Secure configuration management

## 📁 Project Structure

```
grocStore/
├── client/                 # React frontend application
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Route-based page components
│   │   ├── context/        # React Context for state management
│   │   ├── assets/         # Images and static files
│   │   └── api.js          # API configuration
│   └── dist/               # Production build output
│
└── server/                 # Node.js backend application
    ├── controllers/        # Business logic handlers
    ├── models/            # MongoDB schemas
    ├── routes/             # API endpoint definitions
    ├── middlewares/        # Authentication & validation
    └── configs/            # Database & service configurations
```

## 🎯 Core Functionality

### User Features
- User registration and authentication
- Product browsing with category filtering
- Advanced search functionality
- Shopping cart with persistent storage
- Multiple address management
- Order placement (COD & Online)
- Order history and tracking
- Real-time payment processing

### Seller Features
- Seller authentication dashboard
- Product creation with image uploads
- Inventory management
- Order fulfillment tracking
- Sales analytics view

## 🔐 Security Features

- **Password Hashing**: bcryptjs with salt rounds for secure password storage
- **JWT Tokens**: Stateless authentication with HTTP-only cookies
- **CORS Protection**: Configured allowed origins for API security
- **Payment Verification**: Stripe webhook signature validation
- **Input Validation**: Server-side validation for all user inputs
- **Role-Based Access**: Middleware protection for seller and user routes

## 📊 Database Schema

### User Model
- Authentication credentials
- Cart items (key-value pairs)
- Timestamps

### Product Model
- Product details (name, description, price)
- Offer pricing
- Image URLs array
- Category classification
- Stock status
- Timestamps

### Order Model
- User reference
- Product items with quantities
- Total amount calculation
- Delivery address
- Payment status and method
- Order status tracking
- Timestamps

### Address Model
- User reference
- Multiple address storage
- Contact information

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher)
- MongoDB Atlas account (or local MongoDB)
- Stripe account (for payments)
- Cloudinary account (for image storage)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/grocStore.git
cd grocStore
```

2. **Install frontend dependencies**
```bash
cd client
npm install
```

3. **Install backend dependencies**
```bash
cd ../server
npm install
```

4. **Environment Setup**

Create `.env` files in both `client/` and `server/` directories:

**server/.env**
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

**client/.env**
```env
VITE_BACKEND_URL=http://localhost:5000
VITE_CURRENCY=₹
```

5. **Run the application**

Start the backend server:
```bash
cd server
npm start
```

Start the frontend dev server:
```bash
cd client
npm run dev
```

The application will be available at `http://localhost:5173`

## 🏗️ Architecture Decisions

### Why This Stack?
- **React + Vite**: Vite gives us 10x faster hot reload compared to Create React App, plus better production builds
- **MongoDB**: NoSQL fits perfectly for flexible product data and storing cart items as nested objects
- **JWT with Cookies**: HTTP-only cookies beat localStorage for security - prevents XSS attacks on auth tokens
- **Stripe Webhooks**: Webhook verification is more reliable than polling for payment confirmations
- **Cloudinary**: Cloud storage means no server load for images, plus we get CDN benefits automatically

### Performance Optimizations
- Lazy loading for product images
- Optimistic UI updates for cart operations
- Efficient MongoDB queries with selective field projection
- CORS preflight caching
- Vite's code splitting for reduced bundle size

## 🤝 Team Collaboration

Built by a team of 4 developers working together on:
- **Modular Setup**: Clear separation between frontend and backend let us work in parallel without conflicts
- **API Contracts**: Defined API endpoints upfront so frontend and backend could develop features independently
- **Git Workflow**: Feature branches kept our code organized and made code reviews straightforward
- **Code Consistency**: Agreed on patterns early so the codebase stays maintainable as it grows

## 📈 Future Enhancements

- [ ] Real-time inventory updates using WebSockets
- [ ] Advanced search with Elasticsearch integration
- [ ] Recommendation engine based on purchase history
- [ ] Email notifications for order updates
- [ ] Admin dashboard for analytics
- [ ] Multi-vendor marketplace expansion
- [ ] Mobile app with React Native
- [ ] Automated testing suite (Jest, React Testing Library)

## 📝 API Endpoints

### Authentication
- `POST /api/user/signup` - User registration
- `POST /api/user/login` - User login
- `GET /api/user/is-auth` - Verify user authentication
- `POST /api/seller/login` - Seller login
- `GET /api/seller/is-auth` - Verify seller authentication

### Products
- `GET /api/product/list` - Get all products
- `POST /api/product/add` - Add new product (seller only)
- `POST /api/product/id` - Get product by ID
- `POST /api/product/remove` - Remove product (seller only)

### Cart
- `POST /api/cart/add` - Add item to cart
- `POST /api/cart/remove` - Remove item from cart
- `POST /api/cart/get` - Get user cart

### Orders
- `POST /api/order/cod` - Place COD order
- `POST /api/order/stripe` - Create Stripe checkout session
- `POST /stripe` - Stripe webhook endpoint
- `GET /api/order/user-orders` - Get user orders
- `GET /api/order/all-orders` - Get all orders (seller only)

### Address
- `POST /api/address/add` - Add delivery address
- `GET /api/address/list` - Get user addresses

## 🐛 Known Issues & Solutions

- **CORS Errors**: Ensure backend CORS configuration includes your frontend URL
- **Image Upload Failures**: Verify Cloudinary credentials and file size limits
- **Payment Webhooks**: Configure Stripe webhook URL in dashboard for production

## 📄 License

This project is open source and available under the MIT License.

## 👥 Contributors

Built with ❤️ by a team of 4 developers

---

Built with modern web technologies and production-ready practices. Perfect for showcasing full-stack skills in internships, hackathons, and portfolio presentations.

