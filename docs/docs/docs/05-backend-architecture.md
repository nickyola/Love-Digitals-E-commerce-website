Chapter 5: Backend Architecture and API Structure

← Back to Main README

5.1 Introduction

The backend is the engine that powers Laurelite Importation Hub.

It handles application requests, authentication, database operations, payment processing, order management, wallet transactions, notifications and other business logic.

I developed the backend using Node.js and Express.js, with MongoDB as the primary database.

The backend exposes API endpoints that allow the React frontend to communicate with the application and retrieve or update information.

5.2 Backend Technology Stack

The backend uses the following technologies and libraries:

Technology	Purpose
Node.js	JavaScript runtime
Express.js	Backend framework
MongoDB	Database
Mongoose	Database object modelling
JWT	Authentication
bcryptjs	Password hashing
Axios	External API communication
Nodemailer	Email delivery
Multer	File upload handling
Cloudinary	Media storage
Socket.IO	Real-time communication
node-cron	Scheduled tasks
Helmet	HTTP security headers
Morgan	Request logging
CORS	Cross-origin configuration
dotenv	Environment configuration
google-auth-library	Google authentication

5.3 Backend Project Structure

I organised the backend into separate directories to keep application responsibilities clear and make the codebase easier to maintain.

The main structure follows this arrangement:

backend/
│
├── config/
│
├── controllers/
│
├── middleware/
│
├── models/
│
├── routes/
│
├── services/
│
├── utils/
│
├── server.js
│
├── package.json
└── .env

5.3.1 Controllers

Controllers contain the application logic responsible for processing incoming requests and returning responses.

Some of the controller areas include:

* Authentication.
* Products.
* Categories.
* Cart.
* Orders.
* Payments.
* Wallet.
* Wallet checkout.
* Refunds.
* Users.
* Uploads.
* Messages.
* Notifications.
* Contact.
* Reports.
* Store settings.
* Administrative activities.

5.3.2 Routes

The routes directory defines the API endpoints and connects incoming requests to their corresponding controllers and middleware.

5.3.3 Models

The models directory contains Mongoose schemas used to define and manage application data.

5.3.4 Middleware

Middleware handles operations that must take place before requests reach their final controllers.

Examples include authentication, administrator authorisation, seller-related checks and request security configuration.

5.3.5 Services and Utilities

Services and utility functions provide reusable operations that support the application’s business logic.

This helps avoid unnecessary duplication across controllers.

5.4 Server Configuration

The backend entry point is server.js.

It is responsible for configuring the Express application, connecting the database, registering middleware, mounting routes and starting the server.

The application uses environment variables to manage configuration values and sensitive credentials.

Important middleware includes:

* Helmet.
* CORS.
* Express JSON parsing.
* Morgan request logging.
* Authentication middleware.
* Administrator authorisation middleware.
* Seller-related middleware.

5.5 API Architecture

The backend exposes REST API endpoints grouped according to application functionality.

The major API prefixes include:

API Prefix	Responsibility
/api/auth	Authentication and account management
/api/products	Product operations
/api/cart	Shopping cart
/api/orders	Order management
/api/payments	Payment operations
/api/refunds	Refund management
/api/wallet	Wallet operations
/api/reports	Administrative reports
/api/settings	Store settings
/api/admin/activities	Administrative activity records
/api/contact	Contact functionality
/api/upload	File uploads
/api/users	User operations
/api/categories	Category management
/api/messages	Messaging
/api/notifications	Notifications

This organisation keeps related API functionality together and makes the backend easier to navigate.

5.6 Authentication and Authorisation

The backend uses JSON Web Tokens for authentication and bcryptjs for password hashing.

Authentication middleware checks incoming requests for valid Bearer tokens and identifies the associated user.

Administrative middleware checks whether the authenticated user has administrator privileges before allowing access to restricted operations.

The frontend also has protected routes, but backend authorisation remains important because frontend restrictions alone cannot secure API endpoints.

Detailed authentication and security implementation is covered in Chapter 7.

5.7 Product and Category Management

The product and category controllers handle product-related operations.

Product functionality includes:

* Creating products.
* Retrieving product information.
* Updating product details.
* Managing product availability.
* Retrieving product categories.
* Supporting product search.
* Managing product-related information.

The product schema also supports features such as product variants, stock information, images, reviews and ratings.

5.8 Shopping Cart and Order Management

The cart controller handles customer shopping cart operations.

These include adding products, updating quantities, removing items and retrieving cart information.

The order controller handles order-related operations, including order creation, retrieval, status management and associated order information.

The backend also supports the relationship between customer orders, payment status, delivery information and cancellation requests.

5.9 Payment and Wallet Architecture

Payment processing is handled through dedicated backend controllers and routes.

The payment architecture includes:

* Paystack payment initialisation.
* Payment verification.
* Payment status updates.
* Wallet funding.
* Wallet funding verification.
* Wallet checkout.
* Wallet transaction records.
* Administrative wallet operations.
* Refund processing.
* Payment webhook handling.

The wallet checkout and related transaction operations use safeguards such as database transactions and idempotency keys where implemented.

All payment-related routes and flows have been tested end-to-end in production.

The detailed implementation is covered in Chapter 8.

5.10 File Upload and Media Management

The backend uses Multer to handle file uploads and Cloudinary for cloud-based media storage.

This integration supports the application’s image upload functionality without requiring the application to store every uploaded image directly on its own server.

5.11 Real-Time Communication with Socket.IO

The backend integrates Socket.IO to support real-time communication.

The implementation includes:

* Socket connection management.
* JWT-based socket authentication.
* User identification.
* Online-user tracking.
* User and administrator communication rooms.
* Message events.
* Typing indicators.
* Connection and disconnection handling.

An online-users map is used to track connected users during active sessions.

5.12 Scheduled Background Tasks

The application uses node-cron for scheduled background operations.

One implemented use case is the abandoned cart reminder service.

This provides a way to execute selected application tasks automatically without requiring a user to trigger them manually.

5.13 Security and Request Handling

The backend applies security and request-handling measures to protect application operations.

These include:

* Helmet security middleware.
* CORS configuration.
* JWT authentication.
* Password hashing.
* Administrator authorisation.
* Environment-based secret management.
* Payment verification.
* Webhook signature validation.
* Transaction safeguards.

These controls help protect sensitive operations and maintain consistency across application workflows.

5.14 Seller-Related Backend Groundwork

The backend includes preliminary seller-related groundwork, including seller middleware and an isSeller field in the user model.

These additions were introduced as groundwork during development and should not be interpreted as a complete seller authorisation or management system.

Full seller registration, approval, role permissions and seller dashboard workflows remain planned development.

5.15 Production Deployment

The backend is deployed separately from the frontend on an AWS EC2 instance.

The production API is accessible at:

https://api.lovedigitals.online

The backend runs in a Node.js environment and uses PM2 for process management.

Nginx handles the configured reverse proxy and HTTPS traffic.

5.16 Conclusion

The backend architecture provides the functionality that connects the different parts of Laurelite Importation Hub.

By separating routes, controllers, models, middleware and reusable services, I created a structure that supports the application’s current functionality while providing room for future development.

It also brings together authentication, database operations, payment integrations, wallet management, refunds and real-time communication within one backend application.

⸻

← Previous: Frontend Architecture | Back to Main README | Next: Database Architecture →
