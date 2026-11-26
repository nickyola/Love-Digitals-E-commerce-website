# Love-Digitals-E-commerce-website
A full-stack e-commerce platform built with React, Node.js, Express, and MongoDB, featuring secure authentication, Paystack payments, customer wallets, refunds, real-time communication, and AWS deployment.


Laurelite Importation Hub

<p align="center">
  <strong>A modern, responsive e-commerce platform built to make online shopping easier and more accessible.</strong>
</p>
<p align="center">
  <a href="https://lovedigitals.online">Live Website</a> ·
  <a href="#documentation">Documentation</a> ·
  <a href="#technology-stack">Technology Stack</a> ·
  <a href="#project-overview">Project Overview</a>
</p>

⸻

Technology Stack

Frontend

Backend and Database

Authentication, Payments and Integrations

Cloud Infrastructure and DevOps

⸻

Table of Contents

* Project Overview
* Project Motivation
* Key Features
* Technology Stack
* System Architecture
* Deployment and Infrastructure
* Security
* Documentation
* Future Development
* Live Application
* Author’s Note

⸻

Project Overview

Laurelite Importation Hub is a full-stack e-commerce platform I designed and developed to provide customers with a convenient way to discover products, shop online, manage their orders and make payments.

The platform combines a retail shopping experience with the foundation for a broader multi-vendor marketplace.

It is built with React and Vite on the frontend, Node.js and Express on the backend, and MongoDB for data management. The application is deployed on AWS infrastructure and uses integrated services for payments, authentication, media storage and real-time communication.

Project Motivation

I wanted to build something beyond another ordinary e-commerce website.

Many online shopping platforms follow similar layouts and experiences. I wanted to create a platform with its own identity, a responsive interface and practical features that make shopping easier for customers.

The development process challenged me across frontend engineering, backend development, database design, payment integration, cloud infrastructure, deployment and production troubleshooting.

This project represents my journey of turning an idea into a deployed application.

Key Features

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
* Wallet funding and balance verification.
* Wallet-based order checkout.
* Transaction history.
* Administrative wallet management.
* Refund processing through supported payment methods.
* Payment webhook verification and transaction safeguards.

Administration

* Administrative dashboard.
* Product and category management.
* Customer management.
* Order management.
* Cancellation and refund management.
* Wallet administration.
* Reports and activity records.
* Store settings and customer support management.

Real-Time Communication

* Socket.IO integration.
* Real-time messaging infrastructure.
* Online-user tracking.
* Customer and administrator communication.

Technology Stack

Area	Technologies
Frontend	React, Vite, JavaScript, CSS
Backend	Node.js, Express.js
Database	MongoDB, Mongoose
Authentication	JWT, bcryptjs, Google OAuth
Payments	Paystack
Media storage	Cloudinary
Real-time communication	Socket.IO
Email	Nodemailer, Mailtrap for testing
Cloud	AWS EC2, VPC, Security Groups
Server	Ubuntu, Nginx, PM2
SSL	Certbot, Let’s Encrypt
Monitoring	Datadog
Version control	Git, GitHub
SEO	Google Search Console, metadata, robots.txt, sitemap.xml

System Architecture

The application follows a client-server architecture.

* Frontend: React application built with Vite.
* Backend: REST API developed with Node.js and Express.
* Database: MongoDB Atlas with Mongoose models.
* Authentication: JWT-based authentication and Google OAuth.
* Payments: Paystack integration.
* Media: Cloudinary.
* Real-time services: Socket.IO.
* Hosting: Separate AWS EC2 instances for the frontend and backend.
* Web server: Nginx.
* Process management: PM2.

Deployment and Infrastructure

The application is deployed on Amazon Web Services.

The production setup includes:

* AWS EC2 instances.
* Custom VPC and security group configuration.
* Ubuntu server environments.
* Nginx for frontend delivery and reverse proxy configuration.
* PM2 for backend process management.
* MongoDB Atlas for database hosting.
* Domain and DNS configuration.
* HTTPS using Let’s Encrypt SSL certificates.

Production URLs

* Website: https://lovedigitals.online
* API: https://api.lovedigitals.online

Security

Security considerations were incorporated throughout development.

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

Documentation

The technical documentation explains how I planned, designed, developed, deployed and maintained the application.

Chapter	Documentation
01	Project Overview
02	Business Requirements and Functional Features
03	System Architecture and Technology Stack
04	Frontend Architecture and Responsive Design
05	Backend Architecture and API Structure
06	Database Architecture and Data Models
07	Authentication, Authorisation and Security
08	Payments, Wallet System and Refund Management
09	Deployment, AWS Infrastructure and CI/CD
10	SEO, Search Visibility and Maintenance

Back to top

Future Development

The platform is designed with room for further expansion.

Some of the areas I intend to develop include:

* A fully operational multi-vendor seller experience.
* Seller registration, approval and management.
* Seller dashboards and product management workflows.
* Expanded China sourcing and preorder capabilities.
* Integration with Nigerian preorder agents operating in China.
* Further improvements to product discovery and marketplace operations.

These are future development areas, not features being presented as fully operational in the current release.

Live Application

Explore the deployed application:

https://lovedigitals.online

Author’s Note

Building Laurelite Importation Hub has been a major part of my growth as a developer.

From designing the interface and building the backend to integrating payments, configuring AWS infrastructure, deploying the application and troubleshooting production issues, every stage taught me something new.

It was not always easy, but I kept building, learning and improving.

This project is a practical demonstration of my experience across full-stack development, cloud engineering and DevOps.

⸻

<p align="center">
  <strong>Laurelite Importation Hub</strong><br>
  Built with determination, patience and plenty of debugging.
</p>
<p align="center">
  <a href="#table-of-contents">Back to Table of Contents ↑</a>
</p>

