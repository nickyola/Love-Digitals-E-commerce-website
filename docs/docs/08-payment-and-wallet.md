Chapter 8: Payments, Wallet System and Refund Management

← Back to Main README

8.1 Introduction

Payment processing is one of the most important components of Laurelite Importation Hub.

I wanted customers to have a reliable way to pay for orders, fund their wallets, monitor transactions and receive refunds where applicable.

To achieve this, I integrated Paystack into the backend and developed a customer wallet system with separate transaction records and administrative management functionality.

The payment architecture supports both direct order payments and wallet-based checkout.

All payment-related routes and flows documented in this chapter have been implemented, deployed and tested end-to-end in production.

8.2 Payment Technology Stack

The payment and wallet system uses:

Technology	Purpose
Paystack	Payment processing
Axios	Paystack API communication
Node.js	Backend execution
Express.js	Payment API routes
MongoDB	Financial records
Mongoose	Database modelling
MongoDB Transactions	Atomic financial operations
JWT	Protected financial endpoints

8.3 Paystack Integration

Paystack provides the payment infrastructure for the application.

The backend communicates with Paystack through API requests using Axios.

The Paystack secret key is stored in the backend environment configuration:

PAYSTACK_SECRET_KEY=your_paystack_secret_key

The secret key is kept on the backend and is not exposed through the frontend application.

The integration supports payment initialisation, payment verification and refund-related operations.

8.4 Direct Order Payment

Customers can pay for orders through the integrated Paystack payment flow.

The backend exposes the following endpoints:

Method	Endpoint	Purpose
POST	/api/payments/initialize	Initialise order payment
POST	/api/payments/verify	Verify payment

Payment Initialisation

When a customer initiates payment, the backend:

1. Receives the order and payment information.
2. Validates the relevant order details.
3. Communicates with Paystack.
4. Initialises the payment transaction.
5. Returns the payment information required to continue checkout.

Payment Verification

After payment, the backend verifies the transaction with Paystack.

The verification process checks important details, including:

* Payment status.
* Transaction reference.
* Amount paid.
* Currency.

The expected currency is NGN.

After successful verification, the order payment information is updated.

Important order fields include:

* isPaid
* paymentStatus
* paymentReference
* paymentMethod
* paymentChannel
* paidAt
* receiptNumber

The application also supports payment receipt email delivery and records receiptSentAt where applicable.

Payment Return Route

The frontend uses the following route for the payment return process:

/payment-return

This allows the application to handle the customer return flow and communicate with the backend for payment verification.

8.5 Customer Wallet Architecture

I implemented a customer wallet system to give customers another way to pay for orders on the platform.

The wallet is managed separately from the customer’s ordinary account information.

Wallet Model

The Wallet model includes:

* User reference.
* Wallet balance.
* Currency.
* Wallet status.
* Creation timestamp.
* Update timestamp.

The wallet balance is stored using:

balanceKobo

This means monetary values are stored in kobo rather than floating-point naira values.

For example:

Naira	Kobo
₦100	10,000
₦1,000	100,000
₦5,000	500,000
₦10,000	1,000,000

The wallet uses NGN as its currency and supports active and frozen statuses.

Wallet Creation

The backend includes a getOrCreateWallet utility.

This utility retrieves a customer’s existing wallet or creates one when necessary.

A newly created wallet starts with a zero balance.

Wallet Balance Endpoint

GET /api/wallet/my

This endpoint retrieves the authenticated customer’s wallet information.

8.6 Wallet Funding

Customers can fund their wallets through Paystack.

The wallet funding functionality includes the following endpoints:

Method	Endpoint	Purpose
POST	/api/wallet/fund	Initialise wallet funding
POST	/api/wallet/verify-funding	Verify wallet funding

The application enforces a minimum wallet funding amount of ₦100.

Wallet Funding Process

The process follows these steps:

1. Customer enters the amount to fund.
2. Backend validates the amount.
3. Amount is converted into kobo.
4. Paystack payment is initialised.
5. Customer completes payment.
6. Backend verifies the transaction.
7. The wallet is credited after successful verification.
8. A wallet transaction record is created.

The application uses:

utils/creditWalletFunding.js

to support the wallet funding operation.

MongoDB transactions and idempotency safeguards help ensure that a successful funding operation is not credited repeatedly.

Wallet Return Route

The frontend uses:

/wallet/return

to handle the return flow after wallet funding.

8.7 Paystack Webhook Integration

The application includes a Paystack webhook endpoint:

POST /api/refunds/paystack/webhook

The webhook handles relevant payment and refund events.

The implementation validates the webhook signature using HMAC SHA-512 and the configured Paystack secret.

Supported event types include:

* charge.success
* refund.pending
* refund.processing
* refund.needs-attention
* refund.processed
* refund.failed

Webhook handling helps the backend receive and process relevant payment and refund updates from Paystack.

8.8 Wallet-Based Order Checkout

One of the important wallet features is the ability to pay for orders directly using the customer’s wallet balance.

The implementation is handled through:

controllers/walletCheckoutController.js

The endpoint is:

POST /api/wallet/pay-for-order

Wallet Checkout Validation

Before processing a wallet payment, the backend checks:

* Whether the order exists.
* Whether the authenticated user owns the order.
* Whether the order has already been paid.
* Whether the order is cancelled.
* Whether the order has a pending payment restriction.
* Whether the customer’s wallet exists.
* Whether the wallet is active.
* Whether the wallet has sufficient funds.

Wallet Checkout Process

After successful validation:

1. The order amount is calculated.
2. The wallet balance is checked.
3. The required amount is debited.
4. Stock quantities are updated.
5. Relevant cart information is cleared.
6. The order payment status is updated.
7. The wallet transaction is recorded.

The operation uses a MongoDB transaction to help maintain consistency across the related database updates.

Idempotency

The wallet checkout process uses an idempotency key based on the order identifier:

wallet-order-{orderId}

This helps prevent duplicate wallet debits when the same order payment request is processed more than once.

The wallet debit utility is:

utils/debitWallet.js

8.9 Wallet Transaction History

Customers can retrieve their wallet transaction history through:

GET /api/wallet/transactions

The WalletTransaction model records activities affecting wallet balances.

Supported transaction types include:

* Funding.
* Purchase.
* Refund.
* Adjustment.
* Reversal.

Transaction records contain information such as:

* Transaction type.
* Credit or debit direction.
* Amount in kobo.
* Previous balance.
* Resulting balance.
* Transaction status.
* Related order or refund.
* Idempotency information.
* Additional metadata.

Keeping transaction records separate from the wallet balance provides a history of financial activities.

8.10 Administrative Wallet Management

The application includes administrative wallet management functionality.

The administrator can view customer wallets, inspect transactions and make authorised wallet adjustments.

Administrative Wallet Endpoints

Method	Endpoint	Purpose
GET	/api/wallet/admin/all	Retrieve customer wallets
GET	/api/wallet/admin/:userId	View a customer’s wallet
GET	/api/wallet/admin/:userId/transactions	View wallet transactions
POST	/api/wallet/admin/:userId/adjust	Adjust a wallet balance

Wallet Adjustments

The wallet adjustment functionality supports administrative credit and debit operations.

The implementation includes:

* A maximum adjustment amount of ₦1,000,000.
* Adjustment reason.
* Transaction direction.
* Idempotency information.
* Administrator identification.
* Transaction records.

These records provide visibility into administrative wallet changes.

8.11 Refund Management

I implemented refund management to support situations where customers are eligible to receive money back for their orders.

The refund system supports three methods:

1. Paystack refunds.
2. Manual refunds.
3. Wallet refunds.

The refund controller checks that the relevant cancellation request has been approved and that the original order was paid before processing the refund.

8.11.1 Paystack Refunds

The administrative endpoint is:

POST /api/refunds/admin/paystack/:orderId

This initiates a refund through the Paystack integration.

The application also supports webhook updates for relevant refund processing events.

8.11.2 Manual Refunds

The administrative endpoint is:

POST /api/refunds/admin/manual/:orderId

This method records manual refund information, including bank or supported transfer details.

The endpoint records the refund operation and its supporting information. It does not itself execute an external bank transfer.

8.11.3 Wallet Refunds

The administrative endpoint is:

POST /api/refunds/admin/wallet/:orderId

This method credits the customer’s wallet when a wallet refund is selected.

Before processing, the backend validates:

* The original order.
* The order payment status.
* The approved cancellation request.
* The remaining refundable amount.
* The customer’s wallet status.

The operation uses a MongoDB transaction and idempotency safeguards to maintain consistency between the wallet credit and refund records.

8.12 Refund Status Management

The refund system supports the following statuses:

* pending
* processing
* needs_attention
* processed
* failed

These statuses help track the progress of refund operations.

The administrative refund endpoints include:

GET /api/refunds/admin

and:

GET /api/refunds/admin/order/:orderId

These endpoints allow administrators to retrieve refund records and inspect refund information associated with an order.

8.13 Production Implementation and Testing

The payment and wallet system is not just a collection of backend routes.

I implemented, deployed and tested the payment-related workflows end-to-end in the production environment.

This includes:

* Paystack order payment initialisation.
* Order payment verification.
* Payment status updates.
* Payment receipt handling.
* Wallet creation and balance retrieval.
* Wallet funding.
* Wallet funding verification.
* Paystack webhook processing.
* Wallet-based order checkout.
* Wallet transaction history.
* Administrative wallet management.
* Wallet adjustments.
* Paystack refunds.
* Manual refund processing.
* Wallet refunds.
* Refund status management.

Testing these workflows in production was important because financial operations require more than checking whether an API endpoint responds successfully. The complete process must work correctly across the frontend, backend, payment provider and database.

8.14 Financial Integrity and Transaction Safeguards

The wallet and refund architecture includes several safeguards to protect financial records.

These include:

* Storing monetary values in kobo.
* Validating wallet balances.
* Preventing negative balances.
* Checking order ownership.
* Verifying payment status.
* Validating refundable amounts.
* Using MongoDB transactions for supported operations.
* Using idempotency keys.
* Recording wallet transactions.
* Validating Paystack webhook signatures.

These measures help maintain consistency and reduce the risk of duplicate or incorrect financial operations.

8.15 Conclusion

The payment and wallet system is one of the major functional components of Laurelite Importation Hub.

By integrating Paystack with a dedicated wallet architecture, I implemented direct order payments, wallet funding, wallet checkout, transaction history, administrative wallet management and refund processing.

The complete payment-related workflows have been deployed and tested end-to-end in production.

This gives the platform a financial infrastructure that supports its current shopping operations and provides a foundation for future expansion.

⸻

← Previous: Authentication and Security | Back to Main README | Next: Deployment and AWS Infrastructure →
