		**Project Idea: E-commerce Application**

**Description:** Develop a full-stack e-commerce application that allows users to browse and purchase products online. The application should have the following key features:

1. **Product Catalog**: Users should be able to view a catalog of products, including product details, images, and pricing.
2. **Shopping Cart**: Users should be able to add products to a shopping cart, update quantities, and remove items.
3. **Checkout Process**: Users should be able to proceed to checkout, enter their shipping and payment information, and complete the purchase.
4. **Order Management**: Users should be able to view their order history and track the status of their orders.
5. **Admin Dashboard**: Administrators should be able to manage the product catalog, orders, and user accounts.
6. **User Accounts**: Users should be able to create accounts, log in, and manage their profile information and order history.
7. **Payment Integration**: The application should integrate with a payment gateway (e.g., Stripe, PayPal) to handle secure online payments.

**Technology Stack:**

- Frontend: React.js
- Backend: Quarkus (Java)
- Database: PostgreSQL
- Payment Gateway: Stripe or PayPal
- Authentication: JWT-based authentication
- Deployment: Docker and Kubernetes

**Project Structure:**

1. **Frontend (React.js):**
    
    - Product catalog (browse, search, filter)
    - Shopping cart (add, update, remove items)
    - Checkout process (shipping, payment, order confirmation)
    - User accounts (registration, login, profile management)
    - Order history (view, track orders)
    - Admin dashboard (manage products, orders, users)
2. **Backend (Quarkus):**
    
    - Product management (CRUD operations)
    - Shopping cart and checkout (order processing, payment integration)
    - User management (authentication, authorization)
    - Order management (order history, status updates)
    - Admin dashboard (product, order, and user management)
    - Integration with the database (PostgreSQL)
3. **Database (PostgreSQL):**
    
    - Products table
    - Orders table
    - Customers table
    - Payments table
    - Admin users table

This project will allow you to practice the following concepts from the "Fullstack React and Quarkus" book:

- Building a full-stack e-commerce application using React.js and Quarkus
- Implementing product catalog and shopping cart features
- Integrating a payment gateway (Stripe or PayPal) for secure online payments
- Designing and implementing a relational database schema for e-commerce
- Developing user authentication and authorization
- Creating an admin dashboard for managing products, orders, and users
- Deploying the application using Docker and Kubernetes

- [x] Custom Id generation strategy
- [x] Migration (flyway)
- [ ] Payments module
	- [ ] schema
		- [ ] id
		- [ ] order
		- [ ] status
		- [ ] ways
	- [ ] Payment Way
		- [ ] id
		- [ ] value
		- [ ] wayType
	- [ ] Create
	- [ ] Get
	- [ ] Update
	- [ ] Soft Delete
	- [ ] Delete
- [ ] Users module
	- [x] Roles
		- [x] Admin
		- [x] Customer
	- [ ] Create
	- [x] Get
	- [ ] Update
	- [ ] Soft delete
	- [ ] delete
	- [ ] validation for dto
- [ ] Orders module
	- [ ] Schema
		- [ ] Id
		- [ ] products
		- [ ] total
		- [ ] payment
		- [ ] user
	- [ ] Create
	- [ ] Get
	- [ ] Update
	- [ ] Soft Delete
	- [ ] Delete
- [ ] Products module
	- [ ] Schema
		- [ ] Id
		- [x] name
		- [x] price
		- [ ] image
	- [ ] Soft deletes
	- [ ] Create
	- [ ] Get
	- [ ] Update
	- [ ] Delete
- [ ] Security login users
- [ ] Map exceptions
	- [ ] Database exceptions (hibernate exceptions)
- [ ] Make tests for each behavior (or feature)
- [ ] For every perceived bug, make tests
- [ ] Include the `Version` field to entities
- [ ] Refactor entities for composition instead of inheritance