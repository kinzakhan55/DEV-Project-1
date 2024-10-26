This MySQL code defines the schema for an ecommerce_app database, with tables designed to handle various aspects of an e-commerce platform. Each table stores distinct, relevant data for different functionalities such as users, products, orders, and more. Here's an overview of each table's purpose and structure:

1. user_roles Table

Stores different user roles (e.g., admin, customer) for role-based access control.

Fields:

id: Primary key, auto-incremented.

role_name: Name of the role.

created_at, updated_at: Timestamps for tracking role creation and updates.



2. users Table

Contains information about users registered on the platform.

Fields:

id: Primary key, auto-incremented.

role_id: Foreign key referencing user_roles, defining the user's role.

full_name, email, password, phone_number: User details.

status: Enum to track user activity status (e.g., active, inactive, block).



3. categories Table

Manages product categories and subcategories.

Fields:

id: Primary key, auto-incremented.

category_name: Name of the category.

url_slug: Unique slug for SEO-friendly URLs.

parent_cat_id: Foreign key allowing for hierarchical categories (e.g., main and subcategories).

status: Enum to indicate whether the category is active or inactive.



4. products Table

Stores main product details.

Fields:

id: Primary key, auto-incremented.

product_name, url_slug, description: Product details.

category_id: Foreign key linking to the categories table.

price, stock_quantity: Pricing and inventory data.

status: Enum to set the product status as active or inactive.



5. product_variants Table

Manages different variants of products (e.g., different colors or sizes).

Fields:

id: Primary key, auto-incremented.

product_id: Foreign key referencing the products table.

color, size: Specific variant attributes.

price, stock_quantity: Pricing and inventory details per variant.



6. carts Table

Holds information about items added to a user’s cart.

Fields:

id: Primary key, auto-incremented.

user_id: Foreign key referencing the users table.

product_id, product_variant_id: Foreign keys to products and their variants.

quantity: Number of items in the cart for each product or variant.



7. shipping_addresses Table

Stores multiple shipping addresses for users.

Fields:

id: Primary key, auto-incremented.

user_id: Foreign key referencing the users table.

full_address, state, city, zip_code: Address details.



8. orders Table

Records order information, including amounts and statuses.

Fields:

id: Primary key, auto-incremented.

order_number: Unique identifier for each order.

user_id: Foreign key to identify the user placing the order.

total_amount, discount_amount, gross_amount, shipping_amount, net_amount: Financial details of the order.

status: Enum to indicate the order’s processing status.

payment_status, payment_type, payment_transaction_id: Payment-related information.



9. order_items Table

Contains details of individual items in each order.

Fields:

id: Primary key, auto-incremented.

order_id: Foreign key linking to the orders table.

product_id, product_variant_id: Foreign keys to products and their variants.

product_name, color, size: Item details at the time of purchase.

price, quantity, total_amount: Pricing and quantity details for each item.



10. order_shipping_addresses Table

Tracks the shipping address used for each order.

Fields:

id: Primary key, auto-incremented.

order_id: Foreign key linking to the orders table.

shipping_address_id: Foreign key referencing shipping_addresses.

full_address, state, city, zip_code: Address details at the time of the order.



11. wishlist Table

Allows users to save products to a wishlist.

Fields:

id: Primary key, auto-incremented.

user_id: Foreign key linking to users.

product_id, product_variant_id: Foreign keys to specific products and variants.



12. offers Table

Manages discount coupons and promotional offers.

Fields:

id: Primary key, auto-incremented.

coupon_code: Unique code for the offer.

discount_type: Type of discount (either a fixed amount or percentage).

discount_value, start_date, end_date: Discount amount and validity period.

description, status: Offer description and status (e.g., active, inactive).



This schema provides a comprehensive foundation for handling users, product management, orders, payments, and discounts in an e-commerce application. Each table is structured with constraints to ensure data integrity and proper relationships between different entities.
