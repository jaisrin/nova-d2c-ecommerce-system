# Admin – Order Management

## Overview

The Order Management module enables admins to manage the complete lifecycle of customer orders and returns. It acts as a centralized system for monitoring, decision-making, and operational control across forward and reverse logistics.

---

## Orders

### Orders List

The Orders List provides a centralized view of all customer orders, enabling admins to monitor, filter, and take actions.

### Wireframe

![Orders List](../assets/admin_orders.png)

#### Features

- View all orders in a tabular format  
- Filter orders by status, payment, and date  
- Search by Order ID or Customer  
- Export order data  
- Add manual orders  

#### Actions

- View Order Details  
- Delete Order (restricted)  

#### Business Logic

- Orders are displayed in reverse chronological order  
- Export respects applied filters  
- Manual orders are used for offline or system recovery scenarios  

#### Purpose

- Enables quick monitoring of order flow  
- Reduces operational friction  
- Provides a single entry point for order actions  

---

### Order Details

The Order Details screen acts as the operational control center for managing individual orders.

### Wireframe

![Order Details](../assets/admin_order_details.png)

#### Features

- View customer, payment, and delivery details  
- Update order status  
- Add internal admin notes  
- View product-level breakdown  
- Access order summary  

---

### Order Status Management

The order lifecycle is managed directly within the Order Details screen.

#### Stages

- Pending  
- Ready  
- Shipped  
- Delivered  

#### Features

- Status is updated via dropdown  
- Changes require explicit save action  
- Status updates reflect across customer systems  

#### Restrictions

- Status cannot move backward after shipping  
- Delivered orders are locked  

#### Purpose

- Maintains a single source of truth  
- Ensures consistency across systems  
- Enables controlled fulfillment flow  

---

### Admin Notes & Troubleshooting

Admins can add notes directly within the Order Details screen.

#### Features

- Internal notes (not visible to customers)  
- Used for issue tracking and coordination  

#### Use Cases

- Customer complaints  
- Delivery issues  
- Payment discrepancies  

#### Purpose

- Centralizes communication  
- Reduces dependency on external tools  
- Improves resolution time  

---

### Delete Order (Controlled)

Order deletion is allowed only in exceptional scenarios.

#### Use Cases

- Order created manually by mistake  
- Duplicate order due to API/system glitch  
- Invalid order due to system failure  

#### Conditions

- Order is unpaid or pending  
- Order is not shipped or delivered  

#### System Design

- Soft delete (hidden from UI, retained in backend)  
- Action is audit logged  

#### Purpose

- Maintains data integrity  
- Prevents clutter from invalid entries  

---

## Returns

### Returns List

The Returns List provides visibility into all return requests and their refund status.

### Wireframe

![Returns List](../assets/admin_returns.png)

#### Features

- View all return requests  
- Filter by status and date  
- Search by Return ID / Order ID / Customer  
- Export return data  
- Add manual return  

#### Columns

- Return ID  
- Order ID  
- Customer  
- Refund Amount  
- Return Reason  
- Refund Status  

#### Purpose

- Enables tracking of reverse logistics  
- Provides quick visibility into return volume  

---

### Return Details (Decision Engine)

The Return Details screen acts as a multi-stakeholder decision hub.

### Wireframe

![Return Details](../assets/admin_return_details.png)

#### Stakeholders

- Customer Support → validates issue  
- Warehouse → verifies returned item  
- Finance → processes refund  
- Admin → decision authority  

---

### Return Validation

Admins evaluate return requests based on provided data.

#### Inputs

- Return reason  
- Customer comments  
- Attachments (proof)  
- Product and quantity details  

#### Features

- Evidence-based validation  
- Partial return handling  
- Linked order reference  

#### Purpose

- Ensures fair decision-making  
- Prevents invalid returns  

---

### Refund Processing

Refunds are triggered after approval.

#### Workflow

Pending Review  
→ Approved  
→ Refund Initiated  
→ Refund Completed  

OR  

Pending Review → Rejected  

---

### Refund Logic

- Refund amount auto-calculated  
- Supports full and partial refunds  
- Processed via original payment method  

---

### SLA (Service Level Agreements)

- Return Review: 24–48 hours  
- Refund Initiation: ≤ 24 hours  
- Refund Completion:
  - UPI/Wallet: 1–2 days  
  - Cards: 3–7 days  

---

### Fraud Detection

The system flags suspicious return behavior.

#### Signals

- High return frequency  
- Quantity mismatch  
- Repeated complaints  
- Missing/invalid attachments  

#### Actions

- Reject return  
- Add notes  
- Escalate to risk team  

---

### Escalation Flow

Used for high-risk or unclear cases.

#### Flow

1. Admin flags issue  
2. Escalates to:
   - Ops Manager  
   - Finance  
   - Risk Team  

---

### Edge Cases

- Failed refund → retry + escalate  
- Partial returns → proportional refund  
- Wrong item returned → reject  
- No item received → hold + escalate  

---

## System Design Principles

- Single source of truth for orders and returns  
- State-driven UI (actions depend on status)  
- Audit-first approach (all actions logged)  
- Integrated forward and reverse logistics  

---

## Purpose

To provide a scalable and reliable system for managing orders and returns while ensuring operational efficiency, fraud control, and seamless coordination across teams.
