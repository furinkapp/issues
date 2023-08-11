# Users
- GET /users: Get a list of all users
- GET /users/:id: Get a specific user by ID
- GET /users/:id/shops: Get all shops for a specific user
- GET /users/:id/orders/:orderId: Get a specific order for a specific user by ID
- GET /users/:id/listings/:listingId: Get a specific listing for a specific user by ID
- POST /users: Create a new user
- PUT /users/:id: Update a specific user by ID
- DELETE /users/:id: Delete a specific user by ID

# Shops
- GET /shops: Get a list of all shops
- GET /shops/:id: Get a specific shop by ID
- POST /shops: Create a new shop
- PUT /shops/:id: Update a specific shop by ID
- DELETE /shops/:id: Delete a specific shop by ID

# Shop Categories
- GET /shops/:shopId/categories: Get a list of all categories for a specific shop
- GET /shops/:shopId/categories/:id: Get a specific category for a specific shop by ID
- POST /shops/:shopId/categories: Create a new category for a specific shop
- PUT /shops/:shopId/categories/:id: Update a specific category for a specific shop by ID
- DELETE /shops/:shopId/categories/:id: Delete a specific category for a specific shop by ID

# Shop Access Roles
- GET /shops/:shopId/access-roles: Get a list of all access roles for a specific shop
- GET /shops/:shopId/access-roles/:id: Get a specific access role for a specific shop by ID
- GET /shops/:shopId/access-roles/:userId: Get the access role for a specific user in a specific shop by ID
- POST /shops/:shopId/access-roles: Create a new access role for a specific shop
- POST /shops/:shopId/access-roles/:userId: Add an access role for a specific user in a specific shop
- PUT /shops/:shopId/access-roles/:id: Update a specific access role for a specific shop by ID
- DELETE /shops/:shopId/access-roles/:id: Delete a specific access role for a specific shop by ID
- DELETE /shops/:shopId/access-roles/:userId: Remove an access role for a specific user in a specific shop by ID

# Shop Posts
- GET /shops/:shopId/posts: Get a list of all posts for a specific shop
- GET /shops/:shopId/posts/:id: Get a specific post for a specific shop by ID
- GET /shops/:shopId/categories/:categoryId/posts: Get all posts for a specific category in a specific shop
- POST /shops/:shopId/posts: Create a new post for a specific shop
- PUT /shops/:shopId/posts/:id: Update a specific post for a specific shop by ID
- DELETE /shops/:shopId/posts/:id: Delete a specific post for a specific shop by ID

# Shop Listings
- GET /shops/:shopId/listings: Get a list of all listings for a specific shop
- GET /shops/:shopId/listings/:id: Get a specific listing for a specific shop by ID
- GET /shops/:shopId/categories/:categoryId/listings: Get all listings for a specific category in a specific shop
- POST /shops/:shopId/listings: Create a new listing for a specific shop
- PUT /shops/:shopId/listings/:id: Update a specific listing for a specific shop by ID
- DELETE /shops/:shopId/listings/:id: Delete a specific listing for a specific shop by ID

# Shop Audit Logs
- GET /shops/:shopId/audit-logs: Get a list of all audit logs for a specific shop
- GET /shops/:shopId/audit-logs/:id: Get a specific audit log for a specific shop by ID
- POST /shops/:shopId/audit-logs: Create a new audit log for a specific shop
- PUT /shops/:shopId/audit-logs/:id: Update a specific audit log for a specific shop by ID
- DELETE /shops/:shopId/audit-logs/:id: Delete a specific audit log for a specific shop by ID

# Orders
- GET /orders: Get a list of all orders
- GET /orders/:id: Get a specific order by ID
- POST /orders: Create a new order
- PUT /orders/:id: Update a specific order by ID
- DELETE /orders/:id: Delete a specific order by ID

# Order Items
- GET /orders/:orderId/items: Get a list of all items for a specific order
- GET /orders/:orderId/items/:id: Get a specific item for a specific order by ID
- POST /orders/:orderId/items: Create a new item for a specific order
- PUT /orders/:orderId/items/:id: Update a specific item for a specific order by ID
- DELETE /orders/:orderId/items/:id: Delete a specific item for a specific order by ID
