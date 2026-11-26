Chapter 4: Frontend Architecture, UI and Responsive Design

← Back to Main README

4.1 Introduction

The frontend is the part of Laurelite Importation Hub that customers and administrators interact with directly.

I developed the frontend using React and Vite, with a component-based structure that makes the application easier to organise, maintain and expand.

My focus was to create an interface that is visually appealing, functional and responsive across different screen sizes.

The frontend communicates with the backend API to retrieve information, authenticate users, manage shopping activities and process application requests.

4.2 Frontend Technology Stack

The frontend uses the following technologies and libraries:

Technology	Purpose
React	User interface development
Vite	Development server and production build
JavaScript	Application logic
React Router DOM	Page navigation and routing
Axios	Backend API communication
React Icons	Interface icons
Recharts	Dashboard charts and visualisations
Socket.IO Client	Real-time communication
Google OAuth	Google authentication
CSS	Layout, styling and responsiveness

4.3 Frontend Project Structure

I organised the frontend into separate directories based on their responsibilities.

The main structure includes:

frontend/
│
├── public/
│
├── src/
│   ├── assets/
│   │
│   ├── components/
│   │   └── layout/
│   │
│   ├── context/
│   │
│   ├── pages/
│   │
│   ├── services/
│   │
│   ├── styles/
│   │
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
│
├── .env
├── package.json
├── vite.config.js
└── index.html

4.3.1 Components

The components directory contains reusable interface elements.

The layout subdirectory contains shared layout components used across different sections of the application.

4.3.2 Pages

The pages directory contains the main application screens, including customer-facing pages and administrative pages.

4.3.3 Context

The context directory contains shared application state, including authentication and shopping cart state.

4.3.4 Services

The services directory provides a place for application service logic and supporting operations.

4.3.5 Styles

The styles directory contains styling resources used by the frontend.

4.4 Application Entry Point and Providers

The application starts from main.jsx and renders the main React application.

The frontend uses shared providers to make important functionality available across the application.

These include:

* React StrictMode.
* Google OAuth Provider.
* Authentication Context.
* Cart Context.

This arrangement allows different components to access shared application functionality without unnecessarily duplicating logic.

4.5 Application Routing

React Router DOM manages navigation throughout the application.

The routes are organised around public pages, customer pages, administrative pages and additional application sections.

4.5.1 Public Routes

Public routes include:

Route	Purpose
/	Homepage
/products	Product listing
/product/:id	Individual product details
/love-digitals	Brand or information page
/contact	Contact page
/privacy-policy	Privacy policy
/copyright-policy	Copyright policy
/login	Customer login
/register	Account registration
/verify-email	Email verification
/forgot-password	Password recovery
/reset-password	Password reset

4.5.2 Customer Routes

Customer-facing routes include:

Route	Purpose
/cart	Shopping cart
/wishlist	Saved products
/orders	Customer orders
/orders/:id	Individual order details
/profile	Customer profile
/wallet	Customer wallet
/wallet/return	Wallet funding return
/notifications	Customer notifications
/support	Customer support
/payment-return	Payment return and verification flow

4.5.3 Administrative Routes

The administrative section includes:

Route	Purpose
/admin	Administrative dashboard
/admin/orders	Order management
/admin/products/:id/edit	Product editing
/admin/cancellations	Cancellation management
/admin/categories	Category management
/admin/customers	Customer management
/admin/customers/:customerId	Customer details
/admin/customers/:customerId/wallet	Customer wallet management
/admin/reports	Reports
/admin/activities	Administrative activity records
/admin/settings	Store settings
/admin/support	Support management

4.5.4 Additional Product Routes

The application also includes:

* /seller/upload — seller-related product upload route.
* /add-product — administrative product creation route.

The existence of the seller upload route does not mean a complete seller management system is operational. Seller functionality remains an area of further development.

4.6 Authentication Context

The Authentication Context manages shared user authentication state across the frontend.

Its responsibilities include:

* Maintaining the authenticated user information.
* Restoring user information from local storage.
* Supporting login and logout operations.
* Updating user information.
* Making authentication state available to components.
* Supporting the application’s real-time communication setup.

The application uses the userInfo local storage key to maintain relevant user session information.

4.7 Cart Context

The Cart Context provides shared shopping cart functionality.

It allows different components to access and update cart information without needing to pass cart data through multiple layers of components.

This helps maintain consistency between the product pages, cart interface and other shopping-related sections.

4.8 Protected Routes and Navigation Control

The application uses route protection to restrict access to selected sections.

The PrivateRoute implementation checks authentication requirements before allowing access to protected pages.

Administrative access is further restricted through administrator-specific checks, including the adminOnly condition.

This provides frontend navigation control, while the backend also performs its own authentication and authorisation checks.

4.9 API Communication

The frontend communicates with the backend through HTTP requests.

Axios is used for API communication.

The production frontend uses the configured API base URL:

VITE_API_URL=https://api.lovedigitals.online

This allows the frontend to communicate with the deployed backend instead of relying on the local development server.

4.10 Real-Time Frontend Communication

The frontend integrates Socket.IO Client to support real-time communication.

The authentication context and socket connection work together to support the application’s messaging functionality.

This allows the interface to receive and send supported real-time events without requiring users to refresh the page for every update.

4.11 Responsive Design

One of my priorities was making the website usable across mobile phones, tablets and desktop screens.

I used CSS media queries and responsive layout adjustments to adapt the interface to different viewport sizes.

The responsive styling includes breakpoint adjustments across approximately 350px to 1150px.

These adjustments help the interface adapt to different screen widths and maintain a usable layout.

The responsive implementation was an important part of the frontend development process, although individual pages and devices should continue to be tested as the application evolves.

4.12 Production Build and Frontend Deployment

Vite generates the production frontend build using:

npm run build

This creates a dist directory containing the optimised production files.

The generated files are deployed to the frontend AWS EC2 instance, where Nginx serves the application.

The deployed frontend is available at:

https://lovedigitals.online

4.13 Frontend Architecture Considerations

The frontend structure provides several benefits:

* Reusable components.
* Separation of page and layout responsibilities.
* Shared authentication and cart state.
* Centralised navigation.
* Protected customer and administrative sections.
* Easier styling and responsive adjustments.
* Clear communication with the backend API.

These decisions make it easier to maintain the existing application and introduce additional features.

4.14 Conclusion

The frontend is an important part of the Laurelite Importation Hub experience.

Using React, Vite, shared contexts, reusable components and responsive CSS, I developed an interface that connects customers and administrators to the application’s backend functionality.

The frontend architecture also provides a foundation for continued improvements as the platform grows.

⸻

← Previous: System Architecture | Back to Main README | Next: Backend Architecture →
