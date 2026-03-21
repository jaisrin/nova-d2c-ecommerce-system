# Checkout Experience

## Overview

The checkout experience is the final stage of the purchase journey where users provide delivery details, apply offers, validate pricing, and complete payment. This module ensures accuracy, transparency, and successful order placement.

---

## Checkout Flow

Cart → Authentication → Address Selection → Coupon Application → Pricing Validation → Payment → Order Confirmation

---

## 1. Address Selection & Validation

### Overview

The address selection follows a two-step interaction model to ensure delivery accuracy. While a default address is pre-selected for convenience, the user must explicitly confirm the address before proceeding.

---

### Wireframe

**Checkout – Initial State**


![Select Address](address.png)

**Address Selection Screen**

![Checkout Address Step](checkout_address.png)
---

### System Behavior

- Default address is pre-selected but NOT auto-confirmed
- User must explicitly confirm address
- Only one address can be selected at a time
- Address selection is mandatory before proceeding

---

### Validation Logic

- Block checkout if no address is selected
- Show inline error:
  **"Please select a delivery address to proceed"**

---

### Business Logic

- Prevents incorrect deliveries
- Ensures delivery feasibility before payment
- Reduces return-to-origin (RTO)

---

### Edge Cases

- No saved addresses → force add new address
- Address not serviceable (pincode restriction)
- User edits or deletes address mid-checkout

---

## 2. Coupons & Offers

### Overview

Users can apply discounts either manually or by selecting from available coupons.

---

### Wireframe

![Coupons](coupons.png)

---

### System Behavior

- Users can apply coupons in two ways:

  1. Manual entry via coupon input field  
  2. Selection from available coupon list  

- Eligible coupons are highlighted
- Ineligible coupons are disabled
- Only one coupon can be applied at a time
- Applying coupon updates pricing instantly
- Removing coupon recalculates total

---

### Business Logic

- Coupon eligibility based on:
  - Minimum cart value
  - Product/category constraints
  - User eligibility (e.g., first-time user)

- Supports:
  - Flat discounts
  - Percentage discounts

- Payment offers:
  - Applied only when eligible payment method is selected

---

### Validation Logic

- Invalid or expired coupons cannot be applied
- Coupon is revalidated on cart updates
- Only one coupon allowed at a time

---

### Edge Cases

- Coupon becomes invalid after cart change
- Payment method mismatch for bank offers
- Network failure during coupon validation

---

## 3. Pricing & Billing

### Overview

The pricing module calculates the final payable amount based on cart value, discounts, and shipping rules.

---

### System Behavior

- Subtotal = sum of (item price × quantity)
- Discount applied based on coupon
- Shipping calculated based on threshold
- Final total updated dynamically

---

### Business Logic

- Free shipping above threshold (e.g., INR 899)
- Prepaid discounts may apply
- Taxes included in final pricing

---

### Validation Logic

- Pricing must refresh on any cart change
- Prevent mismatch between frontend and backend pricing

---

### Edge Cases

- Price updated after inventory or backend sync
- Shipping not available for location

---

## 4. Payment

### Overview

The payment step enables users to complete the transaction using multiple payment methods. It supports saved payment options, new payment entry, OTP-based authentication, and real-time validation based on applied offers and business rules.

---

### Wireframe

![Payment](payment.png)

![OTP Screen](otp_payment.png)

![Payment Failure](error_payment.png)

---

### UI Components

**Delivery Summary:**
- Selected delivery address
- “Change Address” CTA (editable even at payment stage)

**Payment Methods:**
- Saved cards (masked)
- Add new card
- UPI (GPay, PhonePe, Paytm)
- Net banking
- Cash on Delivery (COD)

**New Card Form:**
- Cardholder name
- Card number
- Expiry (Month/Year)
- CVV
- Save card toggle

**OTP Screen (if applicable):**
- OTP input field
- Verify CTA
- Resend OTP option

**CTA:**
- Dynamic “Pay” button based on method

---

### System Behavior

- User can:
  - Select saved payment method
  - Add a new method
- Address can be edited during payment to reduce drop-offs
- Payment method selection dynamically updates applicable offers

**Payment Flow:**
1. User clicks “Pay”
2. Redirect to payment gateway (if required)
3. OTP authentication triggered (for cards/secure payments)
4. User enters OTP
5. Gateway returns success/failure response

---

### Business Logic

- Supported methods:
  - Cards, UPI, Net Banking, COD
- Prepaid incentives may apply
- Bank/UPI offers:
  - Valid only for eligible payment methods
- Order is created only after successful payment (except COD)

---

### Validation Logic

- Payment method selection is mandatory
- Card details must be valid (format + expiry + CVV)
- OTP must be correct for successful authentication

**Coupon–Payment Dependency:**
- If coupon is tied to specific payment method:
  - Validate against selected method
  - Show error if mismatch:
    **"Selected offer is not applicable for this payment method"**

---

### Error Handling

**Payment Failure Screen:**
- Display clear failure message:
  _“Oops! Your payment didn’t go through.”_
- Provide options:
  - Retry payment
  - Try another payment method

**OTP Errors:**
- Invalid OTP → show inline error
- Expired OTP → allow resend

**Other Failures:**
- Gateway timeout → show pending state + retry
- Network failure → retry mechanism

---

### Edge Cases

- Payment success but order not created (requires reconciliation)
- Double payment attempts
- User exits during OTP/payment
- Network interruption during transaction
- COD not available for certain locations/cart values
- Saved card expired
- OTP not received / delayed

---

### Product Thinking

- OTP adds security layer for transactions
- Retry and alternate payment options reduce drop-offs
- Allowing address edit at payment stage improves conversion
- Clear failure messaging builds user trust
- Validating coupon–payment dependency prevents misuse of offers

## 5. Order Confirmation

### Overview

Order confirmation is the final step of the checkout process, where the system confirms successful order placement and provides users with essential order details, next steps, and navigation options.

---

### Wireframe

![Order Confirmation](order_confirmation.png)

---

### UI Components

**Success Message:**
- “Thank you for your order!”
- Confirmation indicator (visual/illustration)

**Order Details:**
- Order ID
- Confirmation message
- Instruction to track order

**Primary CTAs:**
- Track Order (redirects to Order Tracking page)
- Continue Shopping (redirects to homepage)

---

### System Behavior

- Triggered only after:
  - Successful payment (for prepaid orders)
  - Order creation (for COD orders)

- System performs:
  - Order ID generation
  - Order record creation
  - Inventory deduction
  - Confirmation screen rendering

- Notifications triggered:
  - Email confirmation
  - SMS confirmation (if enabled)

---

### Business Logic

- Order is considered “Placed” at this stage
- Inventory is locked/deducted
- Payment status updated:
  - Paid (Prepaid)
  - Pending (COD)

---

### Validation Logic

- Confirmation page should load only after successful backend validation
- Prevent duplicate order creation on refresh

---

### Edge Cases

- Payment success but confirmation page fails to load
- Duplicate order creation due to multiple retries
- Network interruption after payment success
- Delay in notification delivery (email/SMS)

---

### Product Thinking

- Clear confirmation builds user trust
- Immediate access to tracking improves post-purchase experience
- Dual CTAs guide users toward next actions (track vs explore)
- Reduces anxiety after payment completion
