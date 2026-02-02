# GrocStore Frontend

React-based frontend application for the GrocStore e-commerce platform, built with Vite for optimal development experience and production performance.

## Tech Stack

- **React 19** - Latest React with hooks and context API
- **Vite 6** - Next-generation build tool with instant HMR
- **React Router v7** - Declarative routing with nested routes
- **Tailwind CSS 4** - Utility-first CSS framework
- **Axios** - Promise-based HTTP client
- **React Hot Toast** - Elegant toast notifications

## Features

- Responsive design optimized for mobile, tablet, and desktop
- Real-time cart synchronization with backend
- JWT-based authentication with secure cookie handling
- Dynamic product catalog with category filtering
- Stripe payment integration
- Order tracking and history
- Seller dashboard interface

## Development

```bash
npm install
npm run dev
```

## Build for Production

```bash
npm run build
```

The production build will be output to the `dist/` directory, ready for deployment.

## Project Structure

- `src/components/` - Reusable UI components (Navbar, Footer, Login, etc.)
- `src/pages/` - Route-based page components
- `src/context/` - React Context for global state management
- `src/assets/` - Static assets and image files
- `src/api.js` - Axios configuration and base URL setup
