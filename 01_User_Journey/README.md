## User Journey Overview

This section outlines the end-to-end customer journey aligned with the business requirements defined in the system, covering pre-purchase, purchase, and post-purchase lifecycle.

---

### 1. Discovery & Product Exploration
- Browse products via home, search, and recommendations
- Product listing page (PLP) with filters and sorting
- Product detail page (PDP) with product information and availability

**Additional Actions:**
- Add/remove items from wishlist

---

### 2. Cart & Intent Formation
- Add to cart
- Modify quantity / remove items
- View pricing and estimated shipping

**System Behavior:**
- Cart persists for logged-in users

---

### 3. User Authentication (Mandatory)
- Login / Signup required before checkout

**System Behavior:**
- Users must authenticate to proceed
- Supports email/mobile OTP and social login
- Redirect back to checkout post-login

---

### 4. Checkout & Validation
- Address selection / entry
- Delivery validation
- Coupon application
- Tax and pricing calculation

**Key Validations:**
- Inventory validation before payment
- Mandatory fields enforcement
- CTA enabled only after all validations pass

---

### 5. Payment Processing
- Select payment method (Card, UPI, Net Banking, Wallets)
- Handle payment success / failure
- Retry and failure handling

---

### 6. Order Confirmation
- Order ID generation
- Confirmation via UI, email, and SMS
- Invoice generation

---

### 7. Order Management & Tracking
- View order history
- Track order status (Placed → Packed → Shipped → Delivered)
- Receive shipment and delivery updates

---

### 8. Account & Profile Management
Accessible via user profile:

- Manage personal details
- Manage multiple addresses
- View and manage wishlist
- Access saved payment methods
- View order history and tracking

---

### 9. Returns & Refunds
- Raise return request within return window
- Select return reason and upload images
- Refund processed via original payment method

---

### Coverage

This journey aligns with business requirements including user management, product catalog, checkout, payment processing, order management, and returns, ensuring a complete lifecycle from discovery to post-purchase experience.
