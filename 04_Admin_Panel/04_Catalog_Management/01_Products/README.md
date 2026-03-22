# Products

The Products module enables admins to create, manage, and maintain the product catalog, including pricing, inventory, variants, and SEO configuration.

---
## Empty State

![Empty State](empty_state_add_product.png)

### Features

- Displayed when no products exist  
- CTA: **Add Product**  
- Helps onboard admin

---

## Product List

![Product List](admin_product_list.png)

### Features

- View all products in a tabular format  
- Displays product image, name, category, price, stock status  
- Search and filter functionality  
- Inline actions: Edit / Delete  
- Export products  

---

## Add Product

![Add Product](add_product.png)

### Sections

**1. Product Information**
- Product Name  
- Description  

**2. Images**
- Upload product images  
- Drag & drop support  

**3. Pricing**
- Price  
- Discount Price  
- Tax toggle  

**4. Variants**
- Add product options (e.g., Size)  
- Multiple values (S, M, L, XL)  

**5. Shipping**
- Weight  
- Country  
- Digital product toggle  

**6. Categories**
- Assign categories  
- Create new category  

**7. Tags**
- Add searchable tags  

**8. SEO**
- Meta title  
- Meta description  

---

## Product Added Success

![Success](product_added_message.png)

### Features

- Confirmation message after product creation  
- Visual success feedback  

---

## Delete Product

![Delete](delete_product.png)

### Features

- Confirmation modal before deletion  
- Prevents accidental removal  

---

## Export Products

### Features

- Export product data in Excel format  
- Includes all product details  

---

## Purpose

- Centralized catalog management  
- Supports product lifecycle from creation to deletion  
- Enables business teams to manage inventory and pricing efficiently

---

## Business Logic

- Product must have a name and price to be created  
- Discount price cannot exceed actual price  
- At least one image is required  
- Variants must be defined before assigning values  
- Categories must exist before assigning to product

## Edge Cases

- Missing mandatory fields → show validation errors  
- Invalid pricing (discount > price) → block submission  
- No images uploaded → prevent product creation  
- Duplicate product names → allow but flag (optional)  
- Large image uploads → handle with size restrictions

## System Behavior

- Changes are saved only on explicit action (Save Product)  
- Product appears in list immediately after creation  
- Deleted products are removed from active catalog  
- Export reflects latest product data  
