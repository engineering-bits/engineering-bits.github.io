# Why idempotency is important for Payments

The classical example of a situation that requires idempotency is an online purchase - we need to ensure user isn't charged twice.

In a simple situation your code makes a call to payment gateway, and that might timeout.

In case of a timeout you don't know if a transaction succeeded or not.

Common approaches are:
1. query for transaction status first, if it doesn't exist or failed with retryable error - retry transaction again.
2. simply retry.

## What are the common ways to deal with this situation

1. Explicit "itempotency key" passed to payments gateway
most of the payment providers support it, if you pass it - now it's responsibility of a payments gateway to de-duplicate charges.

2. Duplicated transaction is detected from a payload a hash of user/amount etc
