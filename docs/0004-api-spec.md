# API Specification

This document outlines the API specification for the fur.ink backend.

Currently, there is no support for user-created API tokens or bot accounts, so all API requests must be authenticated using a user account. You may use user account tokens to make requests on behalf of a user, but this is not recommended as this would be horribly insecure.

## Authentication

Authentication is handled via JSON Web Tokens (JWT). The JWT is passed in the `Authorization` header as a Bearer token.

In general, POST and DELETE endpoints will require some form of authentication. GET endpoints usually do not require authentication unless otherwise specified.

## Permissions

Permissions are handled via access roles. Each user has a set of access roles for each shop they have access to.

Shop owners and admins can manage access roles for their shop via the use of permissions.

### Access Roles

Access roles are a mapping of a user ID to a set of permissions. The following roles are provided by default:

-   `shops/owner`: This role is assigned to the user who created the shop. This role cannot be removed if a single owner remains.
-   `shops/admin`: This role is assigned to users who have been granted admin access to the shop. Admins can manage access roles for the shop as well as view orders and manage listings.

### Policies

Access roles describe sets of permissions, known as policies, that the users holding that role have. Here is a list of policies:

-   `shops/listings/read`: This policy grants users read access to a shop's listings. The `everyone` role has this policy by default.
-   `shops/listings/write`: This policy grants users write access to a shop's listings.
-   `shops/posts/read`: This policy grants users read access to a shop's posts.
-   `shops/posts/write`: This policy grants users write access to a shop's posts.
-   `shops/acl/read`: This policy grants users read access to the shop's ACL.
-   `shops/acl/write`: This policy grants users write access to the shop's ACL.

## Response Format

All request and response bodies will be in JSON format (`application/json`). The exact format of the response will depend on the endpoint, and is specified in the endpoint documentation.

### Errors

If an error occurs, the response will be in the following format:

```json
{
	"error": {
		"code": 400,
		"message": "Bad Request",
		"details": "Body is missing required field 'name'"
	}
}
```

**Note:** The `details` field is not guaranteed to be present, but when it is, it will contain more information about the error.

## Endpoints

This section outlines the endpoints for the fur.ink backend. Parameters are denoted with a colon (`:`) and are required.

Endpoints are typically specified using the following format:

> -   `METHOD /path/to/endpoint`: Description of endpoint
>     -   Parameter `paramName`: Description of parameter
>     -   Argument `argumentName` (optional, default: 50): Description of a query argument
>     -   Body: Description of the request body

If an endpoint is protected, it will be specified as such.

### Pagination

Some endpoints have pagination enabled. Where this is referenced, you can use the following query arguments to control the pagination:

> -   `limit` (optional, default: 50): The maximum number of results to return per page
> -   `page` (optional, default: 1): The page number to return

### Users

-   `GET /users/:id`: Get a specific user by ID
    -   Parameter `id`: the user ID
-   `GET /users/:id/shops`: Get a list of shops owned by a specific user.
    -   Parameter `id`: the user ID
    -   This endpoint is paginated
-   `POST /users`: Create a new user. The exact semantics of this endpoint are to be decided.

#### User Orders

-   `GET /users/:id/orders`: Get a list of orders for a specific user
    -   Parameter `id`: the user ID
    -   This endpoint is paginated

#### Protected Endpoints

These endpoints are only available to the user with the specified ID and will require authentication.

-   `GET /users/:id/orders/:orderId`: Get a specific order for a specific user by ID
-   `PUT /users/:id`: Update a specific user by ID
-   `DELETE /users/:id`: Delete a specific user by ID

### Shops

-   `GET /shops`: Get a list of shops matching the specified query parameters
    -   `name`: Filter by shop name
    -   `owner`: Filter by shop owner ID
    -   `tags`: Filter by shop tags
-   `GET /shops/:id`: Get a specific shop by ID

#### Protected Endpoints

These endpoints are only available to users with the `owner` access role for the given shop and will require authentication.

-   `POST /shops`: Create a new shop
-   `PUT /shops/:id`: Update a specific shop by ID
-   `DELETE /shops/:id`: Delete a specific shop by ID

### Shop Categories

These endpoints are only available to users with the `owner` access role for a specific shop.

-   `POST /shops/:shopId/categories`: Create a new category for a specific shop
-   `PUT /shops/:shopId/categories/:id`: Update a specific category for a specific shop by ID
-   `DELETE /shops/:shopId/categories/:id`: Delete a specific category for a specific shop by ID

### Shop ACLs

These endpoints are only available to users with the `owner` access role for a specific shop.

-   `GET /shops/:shopId/acl`: Get the access roles for a specific shop
-   `GET /shops/:shopId/acl/:userId`: Get the access permissions for a specific user in a specific shop

#### Protected Endpoints

-   `POST /shops/:shopId/acl/:userId`: Add an access role for a specific user in a specific shop
-   `PUT /shops/:shopId/acl/:id`: Update a specific access role for a specific shop by ID
-   `DELETE /shops/:shopId/acl/:id`: Delete a specific access role for a specific shop by ID
-   `DELETE /shops/:shopId/acl/:userId`: Remove an access role for a specific user in a specific shop by ID

### Shop Posts

-   `GET /shops/:shopId/posts`: Get a list of posts for a specific shop
    -   This endpoint is paginated
-   `GET /shops/:shopId/posts/:id`: Get a specific post for a specific shop by ID
-   `GET /shops/:shopId/categories/:categoryId/posts`: Get a list of posts for a specific category in a specific shop
    -   This endpoint is paginated

#### Protected Endpoints

These endpoints are only available to users with the `owner` access role for a specific shop.

-   `POST /shops/:shopId/posts`: Create a new post for a specific shop
-   `PUT /shops/:shopId/posts/:id`: Update a specific post for a specific shop by ID
-   `DELETE /shops/:shopId/posts/:id`: Delete a specific post for a specific shop by ID

### Shop Listings

-   `GET /shops/:shopId/listings`: Get a list of all listings for a specific shop
    -   This endpoint is paginated
-   `GET /shops/:shopId/listings/:id`: Get a specific listing for a specific shop by ID
-   `GET /shops/:shopId/categories/:categoryId/listings`: Get all listings for a specific category in a specific shop
    -   This endpoint is paginated

#### Protected Endpoints

These endpoints are only available to users with the `owner` access role for a specific shop.

-   `POST /shops/:shopId/listings`: Create a new listing for a specific shop
-   `PUT /shops/:shopId/listings/:id`: Update a specific listing for a specific shop by ID
-   `DELETE /shops/:shopId/listings/:id`: Delete a specific listing for a specific shop by ID

### Shop Audit Logs

These endpoints are only available to users with the `owner` access role for a specific shop.

-   `GET /shops/:shopId/logs`: Get a list of audit logs for a specific shop
    -   Param `shopId`: the shop ID
