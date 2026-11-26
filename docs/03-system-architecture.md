Chapter 3: System Architecture and Technology Stack

← Back to Main README

3.1 Introduction

This chapter explains the overall architecture of Laurelite Importation Hub, the technologies used to build it and how the different components communicate.

I designed the application using a client-server architecture, separating the frontend, backend and database responsibilities.

This structure makes the application easier to maintain, troubleshoot and expand as new features are introduced.

3.2 High-Level System Architecture

The application consists of the following major components:

1. Frontend application: Handles the user interface and customer interactions.
2. Backend application: Processes requests, applies business logic and communicates with external services.
3. Database: Stores application data and manages relationships between records.
4. External integrations: Support payments, authentication, email delivery and media storage.
5. Real-time communication: Supports messaging and live communication features.
6. Cloud infrastructure: Hosts and serves the production application.

Architecture Overview

                    USERS
                      |
                      v
             Laurelite Website
                React + Vite
                      |
                      v
               HTTPS / API
                      |
                      v
              Nginx / Backend
                      |
                      v
             Node.js + Express
                      |
        +-------------+-------------+
        |             |             |
        v             v             v
     MongoDB       Paystack      Cloudinary
     Atlas         Payments      Media Storage
        |
        |
        v
   Application Data
        Additional Services
        - Google OAuth
        - Email Services
        - Socket.IO
        - Datadog Monitoring

3.3 Frontend Technology Stack

The frontend is responsible for rendering the application interface and providing the interactions customers and administrators use.

3.3.1 React

I used React to build the user interface.

The application is organised into reusable components, pages, contexts and supporting services. This makes it easier to maintain shared functionality and update individual sections without rebuilding the entire interface.

3.3.2 Vite

Vite serves as the frontend development and build tool.

It provides the development environment and generates the production build used during deployment.

The production build is generated with:

npm run build

The resulting dist directory contains the files served by Nginx.

3.3.3 React Router DOM

React Router DOM handles navigation between the application’s pages and protected sections.

3.3.4 Other Frontend Libraries

Additional frontend dependencies include:

* React Icons for interface icons.
* Recharts for charts and dashboard visualisations.
* Socket.IO Client for real-time communication.
* Google OAuth integration for Google authentication.
* Axios for HTTP requests.

3.4 Backend Technology Stack

The backend handles the application’s business logic, API requests, authentication, database operations and integrations.

3.4.1 Node.js

Node.js provides the JavaScript runtime environment used to execute the backend application.

3.4.2 Express.js

Express.js provides the backend framework used to define API routes, middleware and request handlers.

3.4.3 Mongoose

Mongoose provides the object data modelling layer for MongoDB.

It allows the application to define schemas, validate data, manage relationships and perform database operations.

3.4.4 Backend Supporting Libraries

Other backend dependencies include:

Library	Purpose
Axios	HTTP requests and external API communication
JSON Web Token	Authentication tokens
bcryptjs	Password hashing
Nodemailer	Email delivery
Multer	File upload handling
Cloudinary Storage	Cloud media uploads
Socket.IO	Real-time communication
node-cron	Scheduled background tasks
Helmet	HTTP security headers
Morgan	HTTP request logging
CORS	Cross-origin request configuration
dotenv	Environment variable management
google-auth-library	Google authentication verification

3.5 Database Technology

MongoDB Atlas

I selected MongoDB as the application’s database because it provides a flexible document-oriented structure suitable for the different data requirements of an e-commerce platform.

The application uses MongoDB Atlas as its managed database service.

Mongoose Data Models

Mongoose models define how important application records are stored and validated.

The database contains models for areas such as:

* Users.
* Products.
* Categories.
* Shopping carts.
* Orders.
* Wallets.
* Wallet transactions.
* Refunds.
* Conversations.
* Messages.
* Notifications.
* Administrative activities.
* Store settings.

The detailed database design is covered in Chapter 6.

3.6 External Services and Integrations

The platform uses external services to support functionality that would otherwise require additional infrastructure.

3.6.1 Paystack

Paystack handles online payment processing.

The integration supports order payments, wallet funding, payment verification and supported refund operations.

3.6.2 Cloudinary

Cloudinary provides cloud-based image and media storage for the application.

3.6.3 Google OAuth

Google authentication allows customers to sign in using their Google accounts.

3.6.4 Email Services

Nodemailer handles application email functionality, including authentication-related messages and other supported notifications.

Mailtrap was used during email integration testing.

3.6.5 Socket.IO

Socket.IO provides the real-time communication layer used by the application’s messaging functionality.

3.7 Real-Time Communication Architecture

The application uses Socket.IO on both the backend and frontend.

The backend manages socket connections, identifies connected users and supports communication between users and administrators.

The implementation includes:

* User connection and disconnection handling.
* Online-user tracking.
* User and administrator communication rooms.
* Message events.
* Typing indicators.

The frontend uses Socket.IO Client to communicate with the backend in real time.

3.8 Cloud Infrastructure and Deployment Technologies

The production application is hosted on Amazon Web Services.

The infrastructure includes:

3.8.1 Amazon EC2

Amazon EC2 provides the virtual server environments used to host the frontend and backend applications.

3.8.2 Amazon VPC

A Virtual Private Cloud provides the network environment in which the EC2 instances operate.

3.8.3 Security Groups

Security Groups control network traffic allowed to reach the cloud instances.

3.8.4 Ubuntu

Ubuntu is used as the server operating system.

3.8.5 Nginx

Nginx handles frontend static file delivery and backend reverse proxy configuration.

3.8.6 PM2

PM2 manages the Node.js backend process and supports process monitoring and restarts.

3.8.7 Certbot and Let’s Encrypt

Certbot and Let’s Encrypt provide SSL certificate management for HTTPS connections.

3.8.8 Domain and DNS

The application domain is managed through Namecheap DNS configuration.

3.9 Development and Engineering Tools

The following tools supported the development process:

Tool	Purpose
Visual Studio Code	Code editing and development
Git	Version control
GitHub	Source code repository
npm	Package management
Postman	API testing
MobaXterm	SSH access and server administration
ESLint	JavaScript code analysis
Datadog	Application and infrastructure monitoring

3.10 Monitoring and Operational Visibility

Datadog was used during the monitoring setup to collect application and infrastructure metrics and logs.

Slack and email alert integrations were also configured to support operational notifications.

Monitoring helps identify performance issues and provides visibility into the behaviour of the deployed application.

3.11 Search Engine Optimisation Infrastructure

The production website includes SEO-related configuration such as:

* Page titles and meta descriptions.
* Canonical URL metadata.
* Open Graph metadata.
* robots.txt.
* sitemap.xml.
* Google Search Console verification and sitemap submission.

These improvements are covered in detail in Chapter 10.

3.12 Architecture Considerations

The architecture separates responsibilities between the frontend, backend, database and external services.

This provides several advantages:

* Independent frontend and backend deployment.
* Reusable application components.
* Centralised API processing.
* Structured database management.
* Integration with external services.
* Easier maintenance and future expansion.

The architecture provides a foundation for growth, although larger-scale capacity and performance will require continued monitoring and testing.

3.13 Conclusion

The system architecture brings together frontend engineering, backend development, database management, external integrations and cloud infrastructure.

Each technology was selected to support a specific responsibility within the application.

Understanding how these components work together is important when maintaining, troubleshooting or extending Laurelite Importation Hub.

⸻

← Previous: Business Requirements | Back to Main README | Next: Frontend Architecture →
