# Marketplace API Documentation

Welcome to the Marketplace API documentation! This guide will help you integrate and utilize our marketplace platform efficiently. Our API provides a range of functionalities to create an account, manage listings, search for items, and facilitate secure transactions. Let's dive into the details!

## Table of Contents

1. [Introduction](#introduction)
2. [Authentication](#authentication)
3. [Creating an Account](#creating-an-account)
4. [Logging In](#logging-in)
5. [Listing Items](#listing-items)
6. [Searching for Items](#searching-for-items)
7. [Viewing Item Details](#viewing-item-details)
8. [Contacting the Seller](#contacting-the-seller)
9. [Purchasing Items](#purchasing-items)
10. [Admin Panel](#admin-panel)

## Introduction <a name="introduction"></a>

The Marketplace API allows developers to build applications and services that interact with our marketplace platform. Whether you're a seller, buyer, or administrator, our API provides the necessary endpoints to fulfill your requirements. Here's an overview of the key functionalities:

- **User Management**: Create an account, log in, and manage user profiles.
- **Listing Management**: Add items for sale, set prices, and manage listings.
- **Search**: Find items based on criteria such as price, category, and location.
- **Item Details**: Retrieve detailed information about a specific item.
- **Communication**: Contact sellers to inquire about listings.
- **Transaction**: Facilitate secure payment methods for purchasing items.
- **Administration**: Access an admin panel to manage listings, users, and transactions.

Let's get started with authentication.

## Authentication <a name="authentication"></a>

To access protected endpoints, you need to authenticate your requests. We use token-based authentication for secure communication. When you create an account or log in, you will receive an access token that should be included in the `Authorization` header of your API requests.

```http
GET /api/endpoint
Authorization: Bearer {access_token}
```

Replace `{access_token}` with the token obtained during the authentication process.

## Creating an Account <a name="creating-an-account"></a>

To join our marketplace, you need to create a user account. Follow these steps to create an account:

1. **Endpoint**: `POST /api/users`
2. **Request Body**:

```json
{
  "name": "Your Name",
  "email": "your@email.com",
  "phone_number": "+62xxxxxxx",
  "gender": "Male",
  "address": "Your Shipping Address",
  "password": "yourpassword"
}
```

3. **Response**:

```json
{
  "id": "user_id",
  "name": "Your Name",
  "email": "your@email.com",
  "phone_number": "+62xxxxxxx",
  "gender": "Male",
  "address": "Your Shipping Address",
  "createdAt": "timestamp"
}
```

Note: Replace the placeholders with appropriate values.

## Logging In <a name="logging-in"></a>

Once you have an account, you can log in to the marketplace to access protected resources. Here's how:

1. **Endpoint**: `POST /api/login`
2. **Request Body**:

```json
{
  "email": "your@email.com",
  "password": "yourpassword"
}
```

3. **Response**:

```json
{
  "accessToken": "access_token",
  "expiresIn": "expiration_time"
}
```

Save the `access_token` for future API requests.

## Listing Items <a name="listing-items"></a>

As a seller, you can list items for sale on our marketplace. Follow these steps to create a listing:

1. **Endpoint**: `POST /api/listings`
2. **Request Body**:

```json
{
  "title": "Item Title",
  "description": "Item Description",
  "price": 9.99,
  "category": "Category Name",
  "location": "Location Name"
}
```

3. **Response**:

```json
{
  "id": "listing_id",
  "title": "Item Title",
  "description": "Item Description",
  "price": 9.99,
  "category": "Category Name",
  "location": "Location Name",
  "sellerId": "user_id",
  "createdAt": "timestamp"
}
```

You have successfully listed an item for sale.

## Searching for Items <a name="searching-for-items"></a>

Users can search for items based on various criteria. Use the following endpoint to retrieve a list of matching items:

1. **Endpoint**: `GET /api/listings`
2. **Query Parameters**:

   - `price`: Filter items by price range.
   - `category`: Filter items by category.
   - `location`: Filter items by location.

3. **Response**:

```json
{
  "items": [
    {
      "id": "listing_id",
      "title": "Item Title",
      "description": "Item Description",
      "price": 9.99,
      "category": "Category Name",
      "location": "Location Name",
      "sellerId": "user_id",
      "createdAt": "timestamp"
    },
    ...
  ]
}
```

You can customize the search results based on your requirements.

## Viewing Item Details <a name="viewing-item-details"></a>

To retrieve detailed information about a specific item, use the following endpoint:

1. **Endpoint**: `GET /api/listings/{listing_id}`
2. **Response**:

```json
{
  "id": "listing_id",
  "title": "Item Title",
  "description": "Item Description",
  "price": 9.99,
  "category": "Category Name",
  "location": "Location Name",
  "sellerId": "user_id",
  "createdAt": "timestamp"
}
```

This provides comprehensive information about the item.

## Contacting the Seller <a name="contacting-the-seller"></a>

If you have questions or want to negotiate with the seller, you can contact them using their provided information. You can find the seller's ID in the item details response. Use your preferred communication method, such as email or direct messaging, to contact the seller.

## Purchasing Items <a name="purchasing-items"></a>

To purchase an item, follow these steps:

1. **Endpoint**: `POST /api/purchases`
2. **Request Body**:

```json
{
  "listingId": "listing_id",
  "paymentMethod": "payment_method",
  "shippingAddress": "shipping_address"
}
```

3. **Response**:

```json
{
  "id": "purchase_id",
  "listingId": "listing_id",
  "buyerId": "buyer_id",
  "paymentMethod": "payment_method",
  "shippingAddress": "shipping_address",
  "status": "pending",
  "createdAt": "timestamp"
}
```

The purchase request has been initiated. Further details will be provided by the seller.

## Admin Panel <a name="admin-panel"></a>

Our marketplace provides an admin panel for administrators to manage listings, users, and transactions efficiently. Please refer to our dedicated admin panel documentation for detailed information on how to access and use the admin functionalities.

That's it! You now have the necessary information to utilize our marketplace API effectively. If you have any questions or need further assistance, please refer to our support resources or contact our support team.

Happy selling and buying on our marketplace!