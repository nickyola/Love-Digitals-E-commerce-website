Laurelite Importation Hub

<p align="center">
  <strong>A modern, responsive e-commerce platform built to make online shopping easier and more accessible.</strong>
</p>
<p align="center">
  <a href="https://lovedigitals.online">🌐 Live Website</a> ·
  <a href="#key-features">Key Features</a> ·
  <a href="#technology-stack">Technology Stack</a> ·
  <a href="#system-architecture">System Architecture</a> ·
  <a href="#project-documentation">Documentation</a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/React-Frontend-61DAFB?logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Vite-Build_Tool-646CFF?logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Node.js-Backend-339933?logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Express.js-Framework-000000?logo=express&logoColor=white" alt="Express" />
  <img src="https://img.shields.io/badge/MongoDB-Database-47A248?logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/AWS-Cloud-232F3E?logo=amazonaws&logoColor=white" alt="AWS" />
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Paystack-Payments-00C3F7" alt="Paystack" />
  <img src="https://img.shields.io/badge/Cloudinary-Media_Storage-3448C5?logo=cloudinary&logoColor=white" alt="Cloudinary" />
  <img src="https://img.shields.io/badge/Socket.IO-Realtime-010101?logo=socketdotio&logoColor=white" alt="Socket.IO" />
  <img src="https://img.shields.io/badge/Git-Version_Control-F05032?logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub-Repository-181717?logo=github&logoColor=white" alt="GitHub" />
</p>

⸻

Table of Contents

Use the links below to jump directly to any section.

1. Project Overview
2. Project Motivation
3. Key Features
    * Customer Experience
    * Payment and Wallet System
    * Administration
    * Real-Time Communication
4. Technology Stack
    * Frontend
    * Backend and Database
    * Authentication, Payments and Integrations
    * Cloud Infrastructure and DevOps
    * SEO and Search Visibility
    * Technology Summary
5. System Architecture
6. Deployment and Infrastructure
7. Security
8. Project Documentation
9. Future Development
10. Live Application
11. Author’s Note

⸻

Project Overview

Laurelite Importation Hub is a full-stack e-commerce platform I designed and developed to provide customers with a convenient way to discover products, shop online, manage their orders and make payments.

The platform combines a retail shopping experience with the foundation for a broader multi-vendor marketplace.

Built with React and Vite on the frontend, Node.js and Express on the backend, and MongoDB for data management, the application is deployed on AWS infrastructure and integrates services for payments, authentication, media storage and real-time communication.

My goal was to build a practical, scalable foundation that can support a growing online shopping business while providing customers with a smooth and responsive experience.

↑ Back to Table of Contents

⸻

Project Motivation

I wanted to build something beyond another ordinary e-commerce website.

Many online shopping platforms follow similar layouts and experiences. I wanted to create a platform with its own identity, a responsive interface and practical features that make shopping easier for customers.

The development process challenged me across several areas of software engineering, including:

* Frontend engineering and responsive interface development.
* Backend development and REST API design.
* Database architecture and data modelling.
* Authentication and application security.
* Payment gateway and wallet integration.
* Real-time communication.
* Cloud infrastructure and AWS deployment.
* Production troubleshooting and maintenance.

From the first stages of development to deploying the application, this project has been a practical journey of learning, problem-solving and turning an idea into a working product.

↑ Back to Table of Contents

⸻

Key Features

Laurelite Importation Hub brings together customer shopping functionality, payment processing, wallet management and administrative operations.

Customer Experience

* User registration and email OTP verification.
* Google authentication.
* Secure login and password recovery.
* Product browsing and category navigation.
* Product search and product details.
* Shopping cart and wishlist.
* Order placement and order tracking.
* Customer wallet.
* Order payment and payment verification.
* Notifications and customer support.
* Customer profile and address management.

Payment and Wallet System

* Paystack payment integration.
* Wallet creation and funding.
* Wallet balance verification.
* Wallet-based order checkout.
* Transaction history.
* Administrative wallet management.
* Refund processing through supported payment methods.
* Payment webhook signature verification.
* Transaction safeguards and idempotency handling.

Production testing: The payment and wallet routes and flows have been tested end-to-end in the production environment.

Administration

The administrative functionality provides tools for managing important platform operations, including:

* Administrative dashboard.
* Product and category management.
* Customer management.
* Order management.
* Cancellation and refund management.
* Wallet administration.
* Reports and activity records.
* Store settings.
* Customer support management.

Real-Time Communication

* Socket.IO integration.
* Real-time messaging infrastructure.
* Online-user tracking.
* Customer and administrator communication.

↑ Back to Table of Contents

⸻

Technology Stack

The platform uses a combination of frontend, backend, database, cloud and third-party technologies.

Frontend

<p>
  <img src="https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white" alt="CSS3" />
</p>

* React
* Vite
* JavaScript
* CSS
* React Router DOM
* React Context API
* React Icons

Backend and Database

<p>
  <img src="https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Express.js-000000?logo=express&logoColor=white" alt="Express" />
  <img src="https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/Mongoose-880000" alt="Mongoose" />
</p>

* Node.js
* Express.js
* MongoDB Atlas
* Mongoose
* REST API architecture

Authentication, Payments and Integrations

<p>
  <img src="https://img.shields.io/badge/JWT-000000?logo=jsonwebtokens&logoColor=white" alt="JWT" />
  <img src="https://img.shields.io/badge/Google_OAuth-4285F4?logo=google&logoColor=white" alt="Google OAuth" />
  <img src="https://img.shields.io/badge/Paystack-00C3F7" alt="Paystack" />
  <img src="https://img.shields.io/badge/Cloudinary-3448C5?logo=cloudinary&logoColor=white" alt="Cloudinary" />
  <img src="https://img.shields.io/badge/Socket.IO-010101?logo=socketdotio&logoColor=white" alt="Socket.IO" />
  <img src="https://img.shields.io/badge/Nodemailer-22A699" alt="Nodemailer" />
  <img src="https://img.shields.io/badge/Mailtrap-Testing-22A699" alt="Mailtrap" />
</p>

* JSON Web Tokens (JWT)
* bcryptjs
* Google OAuth
* Paystack
* Cloudinary
* Socket.IO
* Nodemailer
* Mailtrap for email testing

Cloud Infrastructure and DevOps

<p>
  <img src="https://img.shields.io/badge/AWS_EC2-FF9900?logo=amazonec2&logoColor=white" alt="AWS EC2" />
  <img src="https://img.shields.io/badge/AWS_VPC-232F3E?logo=amazonaws&logoColor=white" alt="AWS VPC" />
  <img src="https://img.shields.io/badge/Ubuntu-E95420?logo=ubuntu&logoColor=white" alt="Ubuntu" />
  <img src="https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white" alt="Nginx" />
  <img src="https://img.shields.io/badge/PM2-2B037A" alt="PM2" />
  <img src="https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white" alt="GitHub" />
  <img src="https://img.shields.io/badge/MobaXterm-SSH-444444" alt="MobaXterm" />
  <img src="https://img.shields.io/badge/Certbot-003A70" alt="Certbot" />
  <img src="https://img.shields.io/badge/Datadog-632CA6?logo=datadog&logoColor=white" alt="Datadog" />
</p>

* Amazon Web Services (AWS)
* EC2
* Virtual Private Cloud (VPC)
* Security Groups
* Ubuntu
* Nginx
* PM2
* Git and GitHub
* MobaXterm
* Certbot and Let’s Encrypt
* Datadog

SEO and Search Visibility

<p>
  <img src="https://img.shields.io/badge/Google_Search_Console-458CF5?logo=googlesearchconsole&logoColor=white" alt="Google Search Console" />
  <img src="https://img.shields.io/badge/XML-Sitemap-orange" alt="XML Sitemap" />
  <img src="https://img.shields.io/badge/SEO-Technical_SEO-4285F4" alt="Technical SEO" />
</p>

* Search engine metadata.
* Canonical URL configuration.
* Open Graph metadata.
* robots.txt.
* sitemap.xml.
* Google Search Console.

Technology Summary

Area	Technologies
Frontend	React, Vite, JavaScript, CSS
Backend	Node.js, Express.js
Database	MongoDB, Mongoose
Authentication	JWT, bcryptjs, Google OAuth
Payments	Paystack
Media Storage	Cloudinary
Real-Time Communication	Socket.IO
Email	Nodemailer, Mailtrap for testing
Cloud	AWS EC2, VPC, Security Groups
Server	Ubuntu, Nginx, PM2
SSL	Certbot, Let’s Encrypt
Monitoring	Datadog
Version Control	Git, GitHub
SEO	Google Search Console, metadata, robots.txt, sitemap.xml

↑ Back to Table of Contents

⸻

System Architecture

Laurelite Importation Hub follows a client-server architecture in which the frontend communicates with the backend through API requests.

Architecture Components

Component	Technology	Responsibility
Frontend	React and Vite	User interface and client-side application
Backend	Node.js and Express	Business logic and API operations
Database	MongoDB Atlas	Application data storage
Authentication	JWT and Google OAuth	User identity and access
Payments	Paystack	Payment processing
Media Storage	Cloudinary	Image and media management
Real-Time Services	Socket.IO	Real-time communication
Web Server	Nginx	Frontend delivery and server configuration
Process Manager	PM2	Backend process management
Hosting	AWS EC2	Application infrastructure

High-Level Architecture Diagram

flowchart TD
    A[Customer / Administrator] --> B[React + Vite Frontend]
    B --> C[HTTPS API Requests]
    C --> D[Node.js + Express Backend]
    D --> E[(MongoDB Atlas)]
    D --> F[Paystack]
    D --> G[Cloudinary]
    D --> H[Socket.IO]
    I[AWS EC2 - Frontend] --> B
    J[AWS EC2 - Backend] --> D
    K[Nginx] --> I
    L[PM2] --> J

The frontend and backend are hosted on separate AWS EC2 instances, while MongoDB Atlas provides the managed database service.

↑ Back to Table of Contents

⸻

Deployment and Infrastructure

The application is deployed on Amazon Web Services (AWS).

The production environment uses separate EC2 instances for the frontend and backend, allowing both application components to run independently.

Production Infrastructure

The production setup includes:

* AWS EC2 instances.
* Custom VPC and Security Group configuration.
* Ubuntu server environments.
* Nginx for frontend delivery and reverse proxy configuration.
* PM2 for backend process management.
* MongoDB Atlas for database hosting.
* Domain and DNS configuration.
* HTTPS using Let’s Encrypt SSL certificates.

Production URLs

Component	URL
Live Website	https://lovedigitals.online
Backend API	https://api.lovedigitals.online

Deployment Approach

The deployment workflow involved:

1. Preparing the frontend production build.
2. Configuring the AWS server environments.
3. Deploying the frontend application.
4. Deploying and running the backend API.
5. Connecting the backend to MongoDB Atlas.
6. Configuring domain names and DNS records.
7. Setting up HTTPS certificates.
8. Managing the backend process with PM2.
9. Verifying the production application and its integrations.

Git and GitHub are used for source control and tracking development changes. A fully automated CI/CD pipeline is not being presented as an operational feature in this documentation.

↑ Back to Table of Contents

⸻

Security

Security considerations were incorporated throughout the development of Laurelite Importation Hub.

Some of the implemented measures include:

* Password hashing with bcryptjs.
* JWT-based authentication.
* Protected application routes.
* Administrator access controls.
* Email verification.
* Password recovery verification.
* Helmet security middleware.
* Environment-based secret management.
* Paystack webhook signature verification.
* Payment verification and idempotency safeguards.

The backend is responsible for enforcing access permissions on protected operations. Frontend route protection complements these backend controls.

Security remains an ongoing responsibility as the platform evolves and additional functionality is introduced.

↑ Back to Table of Contents

⸻

Project Documentation

The technical documentation for Laurelite Importation Hub is organised into ten chapters.

Each chapter covers a specific part of the planning, architecture, implementation, deployment or maintenance process.

Select a chapter to open its full documentation.

Chapter	Topic	Documentation
01	Project Overview	Read Chapter 01 →
02	Business Requirements and Functional Features	Read Chapter 02 →
03	System Architecture and Technology Stack	Read Chapter 03 →
04	Frontend Architecture and Responsive Design	Read Chapter 04 →
05	Backend Architecture and API Structure	Read Chapter 05 →
06	Database Architecture and Data Models	Read Chapter 06 →
07	Authentication, Authorisation and Security	Read Chapter 07 →
08	Payments, Wallet System and Refund Management	Read Chapter 08 →
09	Deployment, AWS Infrastructure and CI/CD	Read Chapter 09 →
10	SEO, Search Visibility and Maintenance	Read Chapter 10 →

Documentation Navigation

Navigate	Link
Start documentation	Chapter 01 — Project Overview
Explore the architecture	Chapter 03 — System Architecture
Understand the backend	Chapter 05 — Backend Architecture
Explore the database	Chapter 06 — Database Architecture
Review payment implementation	Chapter 08 — Payments and Wallet
Explore deployment	Chapter 09 — AWS Infrastructure

↑ Back to Table of Contents

⸻

Future Development

Laurelite Importation Hub is designed with room for further expansion.

Some of the areas I intend to develop include:

Multi-Vendor Marketplace

* Fully operational seller experience.
* Seller registration, verification and approval.
* Seller dashboards.
* Seller product management workflows.
* Seller order and earnings management.

China Sourcing and Preorder Marketplace

One of the broader business goals behind Laurelite Importation Hub is to make shopping from China easier for Nigerians.

The long-term vision includes:

* Expanded China sourcing and preorder capabilities.
* Integration with Nigerian preorder agents operating in China.
* Access to product sourcing opportunities at competitive prices.
* A more convenient process for Nigerians who want to purchase products from Chinese marketplaces.

These are future development areas, not features being presented as fully operational in the current release.

↑ Back to Table of Contents

⸻

Live Application

Explore the deployed application:

<p align="center">
  <a href="https://lovedigitals.online">
    <strong>🌐 Visit Laurelite Importation Hub</strong>
  </a>
</p>

Website: https://lovedigitals.online

API: https://api.lovedigitals.online

↑ Back to Table of Contents

⸻

Author’s Note

Building Laurelite Importation Hub has been a major part of my growth as a developer.

From designing the interface and building the backend to integrating payments, configuring AWS infrastructure, deploying the application and troubleshooting production issues, every stage taught me something new.

It was not always easy. There were challenges, debugging sessions, unexpected errors and moments when I had to go back, rethink and rebuild.

But I kept learning, improving and pushing forward until the idea became a live application.

This project is a practical demonstration of my experience across full-stack development, backend engineering, cloud engineering and DevOps.

And most importantly, it reminds me that I can take an idea, commit to it and build something real.

⸻

<p align="center">
  <strong>Laurelite Importation Hub</strong>
</p>
<p align="center">
  Built with determination, patience and plenty of debugging. 😂
</p>
<p align="center">
  <a href="#table-of-contents">↑ Back to Top</a>
</p>
