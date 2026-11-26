Chapter 7: Authentication, Authorisation and Application Security

← Back to Main README

7.1 Introduction

Security is an important part of Laurelite Importation Hub because the application handles customer accounts, personal information, orders, payments and wallet transactions.

I implemented an authentication and authorisation system to control access to the application and protect restricted operations.

The system uses JSON Web Tokens (JWT), bcryptjs, email OTP verification and Google authentication.

This chapter explains how these components work together to manage user identity and access.

7.2 Authentication Technology Stack

The authentication and security implementation uses:

Technology	Purpose
JSON Web Token (JWT)	User authentication
bcryptjs	Password hashing
Nodemailer	Email delivery
Google OAuth	Google authentication
Express Middleware	Request authentication and access control
Helmet	HTTP security headers
dotenv	Environment configuration

7.3 User Registration and Email Verification

The registration process is designed to prevent unverified accounts from accessing protected customer functionality.

When a user registers, the backend:

1. Receives the registration information.
2. Validates the submitted details.
3. Creates the user account.
4. Generates a six-digit verification OTP.
5. Sets the OTP expiration time to 10 minutes.
6. Sends the verification code through the email service.
7. Keeps the account unverified until verification is completed.

Email Verification

The verification process checks the submitted OTP against the stored verification information.

When the correct code is provided within its validity period:

* The user’s email verification status is updated.
* The verification code is cleared.
* The account becomes eligible for normal login.

The application also supports resending verification codes for accounts that have not completed email verification.

7.4 Password Hashing

Passwords are not stored as plain text.

I implemented password hashing using bcryptjs within the User model.

The model uses a Mongoose pre-save hook to hash passwords when they are created or changed.

The configured salt rounds are:

bcrypt.genSalt(10);

The User model also includes a password comparison method that checks a submitted password against the stored hash during login.

This ensures that the original password is not stored directly in the database.

7.5 User Login and JWT Authentication

After successful authentication, the backend generates a JSON Web Token.

The token contains the user’s identifier and is signed using the application’s JWT_SECRET environment variable.

The configured token expiration period is 30 days.

The frontend stores the relevant authentication information under the local storage key:

localStorage.getItem("userInfo");

For protected API requests, the frontend sends the token using the Bearer authentication format:

Authorization: Bearer <token>

The backend authentication middleware reads the token, verifies it and retrieves the associated user.

This allows protected controllers to identify the authenticated account before processing requests.

7.6 Google Authentication

The application also supports Google authentication.

Google OAuth is integrated into the frontend, while the backend uses google-auth-library to verify Google authentication information.

This provides customers with an additional way to access their accounts without relying exclusively on the traditional email and password login process.

7.7 Forgot Password and Password Reset

The password recovery functionality allows users who have forgotten their passwords to regain access to their accounts.

The process includes:

1. User submits their registered email address.
2. The backend initiates the password recovery process.
3. A verification code is generated.
4. The code is sent through the email service.
5. The code is checked against the stored value and expiry.
6. The user submits a new password.
7. The password is updated after successful verification.

The recovery process includes expiration handling to prevent old verification codes from remaining valid indefinitely.

7.8 Authentication Middleware

The backend uses authentication middleware to protect restricted API endpoints.

The middleware:

* Reads the incoming Authorization header.
* Extracts the Bearer token.
* Verifies the JWT signature.
* Retrieves the associated user.
* Makes the authenticated user available to subsequent request handlers.

This ensures that protected operations are not executed without the required authentication.

7.9 Administrator Authorisation

The application has administrator-specific access controls.

The administrator middleware checks the authenticated user’s isAdmin field before allowing access to restricted administrative operations.

This protects sensitive functionality such as:

* Product administration.
* Customer management.
* Order management.
* Refund processing.
* Wallet administration.
* Administrative settings.
* Reports and activity records.

The frontend also uses protected route logic to restrict access to administrative pages.

However, backend authorisation remains the main enforcement point because frontend route restrictions alone cannot protect API endpoints.

7.10 Frontend Authentication State

The frontend uses Authentication Context to maintain authentication information across the application.

Its responsibilities include:

* Restoring user information from local storage.
* Maintaining the current authenticated user.
* Supporting login and logout.
* Updating user information.
* Providing authentication state to components.
* Supporting the application’s Socket.IO connection.

This makes authentication state available throughout the React application without requiring every component to manage its own independent login state.

7.11 Seller-Related Access Groundwork

The application contains an isSeller field in the User model and preliminary seller-related middleware.

This was introduced as groundwork during development and is not a complete seller authentication or authorisation implementation.

The following areas remain part of future development:

* Seller registration.
* Seller account verification and approval.
* Complete seller-specific permissions.
* Seller dashboard access control.
* Seller account management.

The existence of the field or middleware should not be interpreted as an operational multi-vendor seller system.

7.12 Administrative Activity Logging

The application includes administrative activity logging.

Important administrative actions can be recorded with information such as:

* Administrator reference.
* Action performed.
* Activity category.
* Target record.
* Additional metadata.
* IP address.
* User-agent information.

This provides an activity history that supports administrative oversight and accountability.

7.13 Application Security Measures

Several security-related measures are incorporated into the application.

Password Protection

Passwords are hashed using bcryptjs rather than stored as plain text.

Token-Based Authentication

JWT provides authentication for protected API requests.

Environment Variables

Sensitive configuration values, including authentication secrets and payment credentials, are managed through environment variables.

Restricted Administrative Operations

Administrative middleware checks permissions before allowing access to protected operations.

HTTP Security Headers

Helmet is used to configure HTTP security headers.

Email Verification

Email verification helps establish that users have access to the email addresses used during registration.

Payment Security

Payment verification, webhook signature validation and transaction safeguards protect supported financial operations.

Detailed payment security implementation is covered in Chapter 8.

7.14 Security Considerations and Continuous Improvement

Application security requires continuous review as the platform grows.

Some areas that deserve ongoing attention include:

* Implementing appropriate request rate limiting for authentication and OTP endpoints.
* Reviewing OTP generation and verification safeguards.
* Ensuring sensitive verification values are not exposed in production logs.
* Reviewing account linking behaviour for Google authentication.
* Reviewing password update and reset logic to prevent accidental double hashing.
* Maintaining secure environment variable management.
* Reviewing access permissions as new features are introduced.

These considerations help guide continued security improvements and maintenance.

7.15 Conclusion

The authentication and security architecture provides the foundation for protecting customer accounts and restricted application operations.

By combining JWT authentication, bcryptjs password hashing, email verification, Google authentication and backend authorisation middleware, I implemented a structured approach to user identity and access control.

Security remains an ongoing responsibility, especially as the platform expands into additional marketplace functionality.

⸻

← Previous: Database Architecture | Back to Main README | Next: Payments and Wallet System →
