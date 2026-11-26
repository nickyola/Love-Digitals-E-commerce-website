Chapter 9: Deployment, AWS Infrastructure and CI/CD

← Back to Main README

9.1 Introduction

Deploying Laurelite Importation Hub was an important part of the development process.

After building the frontend and backend locally, I needed to configure a production environment where customers could access the application online.

I used Amazon Web Services (AWS) to host the application, with separate EC2 instances for the frontend and backend.

This chapter documents the cloud infrastructure, server configuration, deployment process, domain configuration and operational tools used to run the application.

9.2 Cloud Infrastructure Technology Stack

The deployment environment uses the following technologies:

Technology	Purpose
AWS EC2	Cloud virtual servers
AWS VPC	Network environment
AWS Security Groups	Network access control
Ubuntu	Server operating system
Nginx	Web server and reverse proxy
Node.js	Backend runtime
PM2	Backend process management
MongoDB Atlas	Managed database
Certbot	SSL certificate management
Let’s Encrypt	HTTPS certificates
Namecheap	Domain and DNS management
Git and GitHub	Version control and source code management
MobaXterm	SSH access and server administration

9.3 AWS Infrastructure Overview

I deployed the frontend and backend on separate AWS EC2 instances.

This separation allows each application component to run independently while communicating through the configured API endpoint.

The infrastructure was created in the AWS Stockholm region:

eu-north-1

EC2 Instance Information

The documented production instances are:

Component	EC2 Instance ID
Frontend	i-0811fec7beba42156
Backend	i-0830e0fe04a454ad3

The frontend instance serves the React application, while the backend instance runs the Node.js and Express API.

9.4 Virtual Private Cloud and Network Configuration

I configured an AWS Virtual Private Cloud to provide the network environment for the application servers.

The VPC provides the network boundary within which the EC2 resources operate.

Security Groups

Security Groups were configured to control incoming and outgoing network traffic.

These rules are important because the production servers should only expose the network access required for their responsibilities.

SSH Access

I used MobaXterm to connect to the Ubuntu instances through SSH.

This allowed me to:

* Access the production servers.
* Manage application files.
* Install and update packages.
* Configure server services.
* Build and deploy the frontend.
* Monitor and restart the backend.

9.5 Frontend Deployment

The frontend is built with React and Vite.

Before deployment, I generated the production build locally using:

npm run build

This produces a dist directory containing the compiled frontend files.

Frontend Production Configuration

The frontend uses the production API URL:

VITE_API_URL=https://api.lovedigitals.online

This ensures that the deployed application communicates with the production backend rather than the local development API.

Frontend Server Directory

The production frontend files were deployed to the following server directories during deployment:

/var/www/laurelite-frontend

and:

/var/www/laurelite

Nginx Configuration

Nginx serves the generated frontend files.

It also handles the configured HTTPS and frontend routing requirements.

The production website is accessible at:

https://lovedigitals.online

9.6 Backend Deployment

The backend runs separately on its own AWS EC2 instance.

The production backend project directory is:

~/laurelite-backend/Laurelite-importation-hub/laurelite-importhub-backend

The application runs on the configured Node.js environment and uses port:

5000

Environment Configuration

The backend uses environment variables for production configuration.

Important variables include:

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PAYSTACK_SECRET_KEY=your_paystack_secret

Cloudinary configuration values are also maintained in the backend environment.

Sensitive credentials are not included in the frontend source code.

9.7 PM2 Process Management

I used PM2 to manage the Node.js backend process.

The production process is named:

laurelite-backend

PM2 helps keep the backend running and provides commands for checking application status, viewing logs and restarting the process.

Useful PM2 Commands

Check running processes:

pm2 list

Check process status:

pm2 status

View backend logs:

pm2 logs laurelite-backend

Restart the backend:

pm2 restart laurelite-backend

Save the current process list:

pm2 save

These commands are useful when maintaining the backend after deployment.

9.8 Domain and DNS Configuration

The application domain is managed through Namecheap.

The production environment uses two main addresses:

Component	Domain
Frontend	lovedigitals.online
Backend API	api.lovedigitals.online

DNS configuration connects these domain names to their respective hosting environments.

This allows customers to access the website through the main domain while the frontend communicates with the backend through the API subdomain.

9.9 HTTPS and SSL Configuration

I configured HTTPS for the production application using Certbot and Let’s Encrypt.

HTTPS protects communication between the user’s browser and the deployed application through encrypted connections.

Nginx works with the SSL configuration to serve the application securely.

The production website is accessible through HTTPS:

https://lovedigitals.online

The backend API is also configured for HTTPS:

https://api.lovedigitals.online

9.10 MongoDB Atlas Connection

The production backend connects to MongoDB Atlas through the configured MONGO_URI environment variable.

This keeps the database separate from the application server.

The connection allows the backend to perform database operations for:

* Customer accounts.
* Products and categories.
* Shopping carts.
* Orders.
* Wallets.
* Transactions.
* Refunds.
* Notifications.
* Administrative records.

9.11 Production Environment Configuration

The application uses separate environment configurations for local development and production.

The frontend production configuration contains the deployed API URL.

The backend production configuration contains the database connection, authentication secret, payment credentials and Cloudinary configuration.

Keeping these values in environment variables makes it easier to manage configuration without placing sensitive credentials directly in application source files.

9.12 Version Control and Deployment Workflow

Git and GitHub were used for source code version control.

The development workflow includes:

1. Making application changes locally.
2. Reviewing and testing the changes.
3. Staging modified files.
4. Committing changes.
5. Pushing the updated source code to GitHub.
6. Deploying the relevant frontend or backend updates to the production environment.

This provides a structured approach to tracking application changes.

CI/CD Status

The project includes version control and a deployment workflow, but a fully automated CI/CD pipeline should not be claimed as operational without a verified automation configuration.

The seller-related isSeller field was preliminary groundwork and should not be interpreted as evidence of a completed CI/CD pipeline.

Automated build, testing and deployment workflows remain an area for further development.

9.13 Production Monitoring

Datadog was used during the monitoring setup to collect application and infrastructure metrics and logs.

Slack and email alert integrations were also configured.

Monitoring provides operational visibility and helps identify potential application or server issues.

9.14 Production Verification

After deployment, the application was made accessible through its production domains.

The deployment process involved configuring the frontend, backend, database connection, domain, HTTPS and server processes.

The payment and wallet workflows were also tested end-to-end in production, as documented in Chapter 8.

9.15 Deployment Architecture Summary

The production environment can be summarised as follows:

                  INTERNET
                      |
                      v
             lovedigitals.online
                      |
                      v
               FRONTEND EC2
                 Ubuntu
                  Nginx
                      |
                      |
             API Requests over HTTPS
                      |
                      v
             api.lovedigitals.online
                      |
                      v
                BACKEND EC2
                  Ubuntu
              Node.js + Express
                    PM2
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
       MongoDB     Paystack   Cloudinary
        Atlas      Payments   Media

9.16 Conclusion

Deploying Laurelite Importation Hub on AWS was an important milestone in the project.

I worked across cloud infrastructure, server configuration, frontend deployment, backend process management, domain configuration, HTTPS and production troubleshooting.

The experience helped me understand how the different parts of a full-stack application come together in a real production environment.

It also strengthened my practical experience in cloud engineering, server administration and DevOps.

⸻

← Previous: Payments and Wallet System | Back to Main README | Next: SEO and Maintenance →
