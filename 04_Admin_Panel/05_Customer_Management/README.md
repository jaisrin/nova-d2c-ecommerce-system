# Customer Management

The Customer Management module enables admins to view, manage, and analyze customer information, including order history, contact details, and engagement.

---

## Customers List

![Customers](admin_customers.png)

### Features

- View all customers in a tabular format  
- Displays name, location, number of orders, total spend  
- Search and filter functionality  
- Segmentation tabs (New, Returning, Region-based)  
- Export customer data  
- Status column (Active / Inactive)  

---

## Add Customer

![Add Customer](admin_add_customer.png)

### Features

- Add basic customer details (name, email, phone)  
- Add address information  
- Add internal notes  
- Manual onboarding of customers  

---

## Customer Added Success

![Success](admin_customer_added_success.png)

### Features

- Confirmation after successful creation  
- Visual success feedback  

---

## Customer Details

![Customer Details](admin_customer_details.png)

### Features

- View complete customer profile  
- Customer metadata (location, tenure, rating)  
- Order history with status and pricing  
- Add internal notes for tracking  
- Tag customers (e.g., VIP, Region)  
- Edit customer details  
- Deactivate customer option  

---

## Customer Status Management

Customers are managed using a **status-based approach** instead of deletion.

### Status Types

- Active  
- Inactive  

### Features

- Admin can deactivate a customer  
- Inactive customers cannot place new orders  
- Customer data and order history remain intact  

---

## Business Logic

- Customer must have name and valid contact details  
- Email should be unique per customer  
- Orders are permanently linked to customer profile  
- Customers cannot be deleted to preserve transactional integrity  
- Customers can be deactivated instead of deleted  

---

## Validation & Error Handling

- Email format validation  
- Prevent duplicate email entries  
- Mandatory field validation  
- Inline error messages for invalid inputs  

---

## Edge Cases

- Duplicate email → blocked with validation error  
- Missing contact details → prevent submission  
- Customer with no orders → allowed  
- Deactivated customer → cannot place new orders  

---

## Design Decision: No Delete Option

The system does not provide a delete option for customers.

### Reasoning

- Customer data is linked to orders and financial records  
- Deleting a customer would break historical data integrity  
- Audit and compliance requirements require retention of user data  
- Customer insights and analytics depend on historical records  

### Solution

- A **deactivation model** is used instead of deletion  
- Ensures data is preserved while restricting further activity  

---

## Purpose

- Centralized customer data management  
- Enables customer tracking and segmentation  
- Supports customer service and operational decisions  
- Ensures data integrity and compliance  
