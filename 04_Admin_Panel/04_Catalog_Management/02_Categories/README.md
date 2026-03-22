# Categories

The Categories module enables admins to organize products into structured groups for better navigation and discoverability.

---

## Empty State

![Empty State](admin_categories_empty.png)

### Features

- Displayed when no categories exist  
- CTA: **Add Category**  
- Guides admin to create first category  

---

## Categories List

![Categories List](admin_categories.png)

### Features

- Grid-based category display  
- Shows category name and product count  
- Search and filter functionality  
- Quick actions: Edit / Delete  

---

## Add Category

![Add Category](admin_add_category.png)

### Features

- Add category name  
- Assign products to category  
- Simple and quick creation flow  

---

## Edit Category

![Edit Category](admin_edit_category.png)

### Features

- Update category name  
- Upload / change category image  
- Manage assigned products  
- Toggle category visibility  

---

## Category Created Success

![Success](admin_category_created_success.png)

### Features

- Confirmation after successful creation  
- Visual feedback to admin  

---

## Delete Category

![Delete Confirmation](admin_delete_category.png)

### Features

- Confirmation modal before deletion  
- Prevents accidental removal  

---

## Delete Success

![Delete Success](admin_delete_category_success.png)

### Features

- Confirmation after successful deletion  

---

## Business Logic

- Category name is mandatory  
- Category names must be unique (no duplicates allowed)  
- Categories must be created before assigning to products  
- Deleting a category does not delete associated products  
- Category visibility controls frontend display  

---

## Validation & Error Handling

- Real-time validation for category name uniqueness  
- Inline error message displayed below input field  
- Error message: **"Category already exists"**  
- Prevent submission until error is resolved  

---

## Edge Cases

- Duplicate category name → blocked with validation error  
- Deleting category with active products → require confirmation  
- Empty category → allowed  
- Large image uploads → validate size  

---

## Purpose

- Enables structured catalog organization  
- Improves product discoverability  
- Supports filtering and navigation in frontend  
