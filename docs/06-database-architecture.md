Chapter 6: Database Architecture and Data Models

← Back to Main README

6.1 Introduction

The database is one of the most important parts of Laurelite Importation Hub because it stores and manages the information required by the application.

I used MongoDB with Mongoose to design the database structure and manage application records.

The database supports customer accounts, products, categories, shopping carts, orders, payments, wallets, refunds, messaging, notifications and administrative activities.

My goal was to organise the data in a way that supports the application’s current functionality while allowing room for future expansion.

6.2 Database Technology

MongoDB

MongoDB is a NoSQL document-oriented database that stores information in flexible document structures.

I selected MongoDB because its document model works well with the different data structures required by an e-commerce application.

Mongoose

Mongoose provides the object data modelling layer between the Node.js backend and MongoDB.

It allows me to define schemas, apply validation rules, manage references between collections and perform database operations.

The application uses MongoDB Atlas as its managed database service.

6.3 Database Model Overview

The application contains 13 main Mongoose models.

No.	Model	Responsibility
1	User	Customer and administrator accounts
2	Product	Product information
3	Category	Product categories
4	Cart	Customer shopping carts
5	Order	Customer orders
6	Wallet	Customer wallet balances
7	WalletTransaction	Wallet transaction records
8	Refund	Refund records and processing
9	Conversation	Customer and administrator conversations
10	Message	Individual messages
11	Notification	Customer notifications
12	AdminActivity	Administrative activity records
13	StoreSettings	Store configuration

6.4 User Model

The User model stores account information and authentication-related data.

Important fields include:

* First name and last name.
* Email address.
* Password.
* Google authentication provider information.
* Email verification status.
* OTP verification code and expiry.
* Password reset information.
* Administrator status through isAdmin.
* Preliminary seller-related status through isSeller.
* Profile image.
* Phone number.
* WhatsApp contact.
* Date of birth.
* Delivery addresses.
* Wishlist containing Product references.

Password Security

The model uses a Mongoose pre-save hook to hash passwords with bcryptjs.

It also provides a password comparison method used during authentication.

The isAdmin and isSeller fields serve different purposes. The seller field is preliminary groundwork and does not represent a complete operational seller management system.

6.5 Product Model

The Product model stores information about products available on the platform.

Its fields support:

* Product name.
* Description.
* Price.
* Product images.
* Category reference.
* Seller reference.
* Stock quantity.
* Product variants.
* SKU.
* Specifications.
* Product availability.
* Import country.
* Estimated delivery days.
* Shipping information.
* Featured product status.
* Embedded customer reviews.
* Product ratings.

The product schema also supports local and imported product classifications.

The import country field has China as its default value.

Product Search

A text index is defined on the product name:

productSchema.index({ name: "text" });

This supports text-based product search functionality.

6.6 Category Model

The Category model stores product category information.

It includes a category name with a uniqueness constraint to prevent duplicate category names.

This helps organise products and supports category-based browsing.

6.7 Cart Model

The Cart model stores customer shopping cart information.

It includes:

* User reference.
* Product references.
* Selected product variants.
* Product attributes.
* Quantity.
* Price information.
* Cart reminder fields.

The cart structure allows the application to associate selected products with individual customer accounts.

6.8 Order Model

The Order model stores customer order information and supports the application’s order management process.

Important fields include:

* Customer reference.
* Ordered products.
* Product and variant information.
* Seller reference.
* Commission information.
* Seller earnings.
* Order totals.
* Shipping information.
* Order status.
* Delivery information.
* Tracking information.
* Cancellation details.
* Payment status.
* Payment reference.
* Payment method.
* Payment channel.
* Payment breakdown.

Commission Structure

The order structure includes commission calculations and seller earnings.

The commission rate used in the documented order logic is:

const COMMISSION_RATE = 0.1;

This represents a 10% commission calculation in the seller-related order logic. It does not mean the complete seller marketplace is operational.

6.9 Wallet Model

The Wallet model stores customer wallet information.

Important fields include:

* User reference.
* Wallet balance.
* Currency.
* Wallet status.
* Creation and update timestamps.

Balance Representation

Wallet balances are stored using balanceKobo.

This means monetary values are represented in kobo rather than floating-point naira values.

For example:

* ₦1,000 = 100,000 kobo.
* ₦5,000 = 500,000 kobo.
* ₦10,000 = 1,000,000 kobo.

The wallet uses NGN as its currency and supports active and frozen statuses.

The schema also includes safeguards against negative wallet balances.

6.10 WalletTransaction Model

The WalletTransaction model records activities affecting customer wallet balances.

Supported transaction types include:

* Funding.
* Purchase.
* Refund.
* Adjustment.
* Reversal.

The model also records:

* User and wallet references.
* Transaction direction.
* Amount in kobo.
* Previous and resulting balances.
* Transaction status.
* Related order or refund.
* Idempotency information.
* Additional metadata.

Keeping wallet transactions separate from the wallet balance provides a record of how wallet balances change over time.

6.11 Refund Model

The Refund model stores refund-related information.

It supports different refund methods, including:

* Paystack.
* Manual bank or supported transfer processing.
* Customer wallet credit.

Important information includes:

* Related order.
* Refund amount.
* Refund method.
* Refund status.
* Bank transfer information where applicable.
* Supporting evidence.
* Administrator responsible for processing.
* Refund history.
* Idempotency information.

The refund model supports the administrative refund workflow and helps maintain records of refund operations.

6.12 Conversation Model

The Conversation model manages conversations between customers and administrators.

It includes information such as:

* Conversation participants.
* Conversation type.
* Support or direct conversation classification.
* Conversation status.
* Assigned administrator.
* Support mode.

The support mode includes values such as AI and Human.

The presence of an AI mode in the schema should not be interpreted as proof that a complete AI support service is integrated.

6.13 Message Model

The Message model stores individual messages associated with conversations.

It includes:

* Conversation reference.
* Sender information.
* Sender type.
* Receiver information.
* Message content.
* Message type.

The sender type supports user, administrator and AI classifications.

Message content has a maximum length of 5,000 characters.

6.14 Notification Model

The Notification model stores notification information associated with customers.

It includes:

* User reference.
* Notification type.
* Notification message.
* Read status.

This allows the application to maintain notification records and track whether customers have read them.

6.15 AdminActivity Model

The AdminActivity model records administrative actions performed within the platform.

Important fields include:

* Administrator reference.
* Action performed.
* Activity category.
* Target record.
* Additional metadata.
* IP address.
* User-agent information.

The model also includes indexes to support activity record retrieval.

This provides a way to review important administrative operations.

6.16 StoreSettings Model

The StoreSettings model stores configuration information for the platform.

Its fields include:

* Store name.
* Store logo.
* Contact information.
* Store address.
* Currency.
* Timezone.
* Notification preferences.
* Store policies.

The default currency is NGN, and the configured timezone is Africa/Lagos.

6.17 Data Relationships

The database uses references to connect related records.

Some important relationships include:

* A user can have a wallet.
* A user can have a shopping cart.
* A user can create multiple orders.
* Products can belong to categories.
* Products can be referenced in multiple orders.
* Wallet transactions belong to wallet-related accounts.
* Refunds are associated with orders.
* Conversations contain messages.
* Notifications are associated with users.
* Administrative activities reference administrators.

These relationships allow the backend to retrieve related information and maintain connections between application records.

6.18 Database Integrity and Transaction Safeguards

Financial operations require careful handling to maintain accurate records.

The application uses MongoDB transactions for supported wallet and payment-related operations.

Additional safeguards include:

* Wallet balance validation.
* Non-negative balance constraints.
* Transaction status tracking.
* Idempotency keys.
* Order ownership validation.
* Refund amount validation.
* Related transaction records.

These measures help prevent inconsistent financial records and duplicate transaction processing.

6.19 Future Database Expansion

As the platform grows, the database can be expanded to support additional business functionality.

Potential areas include:

* Dedicated seller account management.
* Seller approval and verification records.
* Expanded seller product management.
* China preorder and sourcing workflows.
* Preorder agent management.
* Additional delivery and logistics information.

These areas represent future development opportunities rather than existing dedicated database workflows.

6.20 Conclusion

The database architecture provides the foundation for the major operations of Laurelite Importation Hub.

By organising application information into dedicated Mongoose models, I created a structured approach to managing customers, products, orders, wallets, payments, refunds and administrative operations.

The database design also provides room for future expansion as the business and application continue to grow.

⸻

← Previous: Backend Architecture | Back to Main README | Next: Authentication and Security →
