# 🍷 Client App for Liquor Shop

A modern, feature-rich e-commerce web application for a liquor shop built with React. This client-side application provides an intuitive interface for customers to browse, search, and purchase various types of alcoholic beverages including wine, rum, whisky, vodka, beer, and brandy.

## 📋 Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Integration](#api-integration)
- [Available Scripts](#available-scripts)
- [Environment Variables](#environment-variables)
- [Contributing](#contributing)

## ✨ Features

### User Authentication
- **User Registration**: New customers can sign up with personal details including name, email, phone, address (state, city, pin code)
- **User Login**: Secure login system with email and password
- **Session Management**: Persistent login using localStorage
- **Protected Routes**: Cart and checkout features available only to authenticated users

### Product Browsing
- **Category Navigation**: Browse products by main categories (Wine, Rum, Whisky, Vodka, Beer, Brandy)
- **Sub-category Filtering**: Further refine search by sub-types within each category
  - **Wine**: White, Red, Rosé, Sparkling, Dessert
  - **Rum**: Dark, Flavored, Gold, Light, Overproof, Premium, Spiced
  - **Whisky**: American, Australian, Canadian, Danish, English, Finnish, Georgian, German, Indian, Irish, Mexican, Japanese, Scotch, Swedish, Taiwanese, Welsh
  - **Vodka**: Plain, Fruit, Herbal, Flavored
  - **Beer**: Boza, Cauim, Chhaang, Chicha, Gruit, Kvass, Oshikundu, Pulque, Sahti, Sato
  - **Brandy**: Cognac, Armagnac, Calvados, Spanish, Obstler, Pisco, Armenian, Cypriot, Pomace

### Shopping Experience
- **Product Cards**: Visual product display with images, names, prices, and categories
- **Product Details Modal**: Click on any product to view detailed information
- **Add to Cart**: Authenticated users can add products to their shopping cart
- **Checkout Page**: View all items added to the cart
- **Image Carousel**: Engaging homepage with auto-playing promotional images

### Responsive Design
- Mobile-friendly interface
- Modern UI with Material-UI components
- Smooth animations and transitions using react-spring

## 🛠 Technology Stack

### Frontend Framework
- **React** (v16.13.0) - Core UI library
- **React Router DOM** (v5.1.2) - Client-side routing
- **React Scripts** (v3.4.0) - Build tooling and development server

### UI Components & Styling
- **Material-UI Core** (v4.9.4) - UI component library
- **Material-UI Icons** (v4.9.1) - Icon components
- **W3.CSS** - Additional styling framework
- **React Responsive Modal** (v4.0.1) - Modal dialogs
- **React Owl Carousel** (v2.3.1) - Image carousel

### Animations
- **React Spring** (v8.0.27) - Spring-physics based animations
- **React Transition Group** (v4.3.0) - Animation transitions

### HTTP Client
- **Axios** (v0.19.2) - Promise-based HTTP requests

### Testing
- **@testing-library/react** (v9.3.2) - React component testing
- **@testing-library/jest-dom** (v4.2.4) - Custom Jest matchers
- **@testing-library/user-event** (v7.1.2) - User interaction simulation

## 📦 Prerequisites

Before running this application, ensure you have the following installed:

- **Node.js** (v12.x or higher)
- **npm** (v6.x or higher) or **yarn** (v1.22.x or higher)
- **Backend API Server** running on `http://localhost:3000`

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/theQuarky/client-app-for-liquor-shop.git
   cd client-app-for-liquor-shop
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Ensure Backend API is Running**
   
   This application requires a backend API server running on `http://localhost:3000`. The backend should provide the following endpoints:
   - `POST /v1/users/register` - User registration
   - `POST /v1/users/login` - User login
   - `GET /v1/products/:type` - Get products by type
   - `GET /v1/products/:type/:sub_type` - Get products by type and sub-type

## 🎯 Usage

### Development Mode

Start the development server:

```bash
npm start
# or
yarn start
```

The application will open automatically in your browser at [http://localhost:3000](http://localhost:3000).

The page will reload when you make changes, and you'll see any lint errors in the console.

### Building for Production

Create an optimized production build:

```bash
npm run build
# or
yarn build
```

This builds the app for production to the `build` folder. The build is minified and optimized for best performance.

## 📁 Project Structure

```
client-app-for-liquor-shop/
├── public/
│   ├── favicon.ico
│   ├── index.html
│   ├── manifest.json
│   └── robots.txt
├── src/
│   ├── Components/
│   │   ├── checkOut.js         # Shopping cart checkout page
│   │   ├── footer.js            # Footer component
│   │   ├── login.js             # User login modal
│   │   ├── login.css            # Login/signup styling
│   │   ├── product.js           # Individual product card component
│   │   ├── product.css          # Product styling
│   │   ├── productsByType.js    # Products filtered by category
│   │   ├── productsBySubType.js # Products filtered by sub-category
│   │   ├── showCase.js          # Homepage carousel
│   │   ├── showCase.css         # Carousel styling
│   │   └── signUp.js            # User registration modal
│   ├── assets/                  # Static assets
│   ├── App.js                   # Main application component with routing
│   ├── App.css                  # Application styling
│   ├── App.test.js              # Application tests
│   ├── index.js                 # Application entry point
│   ├── index.css                # Global styles
│   ├── serviceWorker.js         # PWA service worker
│   └── setupTests.js            # Test configuration
├── package.json                 # Project dependencies and scripts
├── .gitignore                   # Git ignore rules
└── README.md                    # Project documentation
```

## 🔌 API Integration

The application communicates with a backend REST API for the following operations:

### Authentication Endpoints

**User Registration**
```
POST http://localhost:3000/v1/users/register
Body: {
  name: string,
  phone_no: string,
  email: string,
  password: string,
  state: string,
  city: string,
  pin_code: string
}
```

**User Login**
```
POST http://localhost:3000/v1/users/login
Body: {
  email: string,
  password: string
}
Response: {
  token: string,
  data: { name: string, email: string, ... }
}
```

### Product Endpoints

**Get Products by Type**
```
GET http://localhost:3000/v1/products/:type
Example: GET http://localhost:3000/v1/products/wine
```

**Get Products by Type and Sub-Type**
```
GET http://localhost:3000/v1/products/:type/:sub_type
Example: GET http://localhost:3000/v1/products/wine/red
```

### Data Storage

The application uses browser localStorage for:
- **user-login**: Stores authentication token and user data
- **kart**: Stores shopping cart items (product names separated by '-----')

## 📜 Available Scripts

In the project directory, you can run:

### `npm start` or `yarn start`

Runs the app in development mode at [http://localhost:3000](http://localhost:3000).
- Hot reload on file changes
- Displays lint errors in console

### `npm test` or `yarn test`

Launches the test runner in interactive watch mode.
See [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build` or `yarn build`

Builds the app for production to the `build` folder.
- Optimizes React in production mode
- Minifies files and adds content hashes to filenames
- Ready for deployment

### `npm run eject` or `yarn eject`

**⚠️ Note: This is a one-way operation. Once you eject, you can't go back!**

Ejects from Create React App configuration, giving you full control over webpack, Babel, ESLint configurations.

## 🔧 Environment Variables

While this project doesn't use a `.env` file by default, you may want to configure:

- **API_BASE_URL**: Backend API base URL (currently hardcoded as `http://localhost:3000`)

To make the API URL configurable, create a `.env` file in the root directory:

```
REACT_APP_API_BASE_URL=http://localhost:3000
```

Then update API calls in the components to use:
```javascript
const API_BASE_URL = process.env.REACT_APP_API_BASE_URL || 'http://localhost:3000';
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the MIT License.

## 🐛 Known Issues

- API endpoints are hardcoded to `http://localhost:3000`
- Shopping cart stores only product names, not quantities or complete product details
- No payment gateway integration
- Image uploads require backend server access

## 🚀 Future Enhancements

- Add payment gateway integration
- Implement advanced search and filtering
- Add product ratings and reviews
- Improve shopping cart with quantity management
- Add order history and tracking
- Implement wishlist functionality
- Add email verification for registration
- Enhance mobile responsiveness
- Add product recommendations

## 📞 Support

For support, please open an issue in the GitHub repository or contact the maintainers.

---

**Built with ❤️ using React** | This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app)
