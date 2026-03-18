## Coupon Logic

This section defines the discount system behavior, including coupon logic, bank offers, eligibility rules, and conflict handling to ensure a seamless and conversion-driven pricing experience.

---

### 1. Coupon Types

Coupons can be categorized as:

- Percentage discount (e.g., 10% off)
- Flat discount (e.g., ₹200 off)
- Product-specific offers
- Category-specific offers
- First-time user offers

---

### 2. Coupon Visibility

Coupons are displayed to users in the checkout interface.

**States:**
- Eligible coupons → Active and selectable
- Non-eligible coupons → Visible but grayed out

**Purpose:**
- Improves transparency
- Encourages users to meet eligibility criteria (e.g., increase cart value)

---

### 3. Eligibility Criteria

Coupons are validated based on:

- Minimum order value
- Applicable products or categories
- User eligibility (e.g., new user, first purchase)
- Coupon validity period (expiry date)
- Usage limits (per user / global limit)

---

### 4. Application Methods

Users can apply coupons in two ways:

- Manual entry of coupon code
- Selecting from available coupon list

---

### 5. System Behavior

- Valid coupon → applied instantly and pricing is updated
- Invalid coupon → error message displayed
- Expired or ineligible coupon → cannot be applied

---

### 6. Single Coupon Constraint

- Only one coupon can be applied per order
- Applying a new coupon replaces the existing one

---

### 7. Auto-Apply Logic (Optional Enhancement)

- System can automatically apply the best eligible coupon
- Prioritizes maximum discount for the user

---

### 8. Conflict Handling

When multiple coupons are available:

- System enforces single coupon rule
- Prevents stacking of multiple discounts
- Ensures consistent pricing logic

---

### 9. Edge Cases

- Coupon becomes invalid after cart update
- Coupon removed if eligibility conditions are no longer met
- Price recalculates dynamically in real time

---

### 10. Bank Offers

Bank offers are payment-method-based discounts designed to influence purchase decisions and improve conversion rates.

---

#### Visibility (Checkout Stage)

- Bank offers are displayed during checkout before payment
- Users can view available offers such as:
  - Instant discounts on specific bank cards
  - Cashback offers
  - No-cost EMI options

**Purpose:**
- Reduce drop-offs by showing potential savings early
- Encourage users to choose eligible payment methods

---

#### Validation (Payment Stage)

- Bank offers are applied only when the user selects an eligible payment method

**System Behavior:**
- If user selects eligible card → offer is applied
- If user selects non-eligible card → offer is removed
- Changing payment method triggers recalculation of final price

---

#### Eligibility Criteria

- Specific bank or card type (e.g., HDFC Credit Card)
- Minimum transaction amount
- Offer validity period

---

#### Stacking Rules

- Bank offers may be combined with coupons (based on configuration)
- Final pricing reflects both discounts if applicable

---

#### UX Consideration

Displaying bank offers upfront creates a perception of savings and nudges users toward completing the purchase, while final validation ensures business rules are enforced.

---

### Key Focus Areas

- Real-time validation
- Transparent discount visibility
- Business rule enforcement
- Multi-layer discount handling (coupon + bank offers)
- Conversion optimization through pricing strategy
