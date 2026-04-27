# Ecommerce API Test Suite – Postman

A hands-on API testing project built using Postman, simulating a complete real-world e-commerce business flow from user login to adding products to cart and validating the full order flow.

## Project Overview

This project covers an end-to-end API testing scenario for an e-commerce application across two flows:

**Flow 1:** User authentication and secure endpoint access

**Flow 2:** Product listing, Add to Cart, and cart validation

Both flows are chained together and executed as a full automated suite using Postman Collection Runner.

## Business Flow Tested

```
Login → Extract Token → Fetch Products → Extract Product ID → Add to Cart → Validate Cart → Negative Scenarios
```

## What This Project Covers

**Authentication Flow**

- Login API testing using POST request with credentials
- Extracting Bearer Token from login response via test scripts
- Storing token in environment variables for reuse across requests
- Validating secure endpoints using Bearer Token authentication

**Cart Flow**

- Fetching product listing using GET request
- Extracting dynamic product ID and saving to environment variable
- Sending POST request with JSON body to Add to Cart
- Validating cart details including cart ID, products, and cart total
- Chaining requests using environment variables

**Negative Testing**

- Missing or invalid Bearer Token to validate 401 response
- Wrong product ID to validate error response
- Ensuring error messages are correct and meaningful

**Test Execution**

- Written test scripts for status code and response body validation
- Ran complete business flow using Collection Runner
- Debugged API failures and validated fix

## Tech Stack

- Postman
- JavaScript (pm API for test scripts)
- dummyjson.com (free public REST API)

## API Endpoints Tested

| Method | Endpoint           | Description                    |
|--------|--------------------|--------------------------------|
| POST   | /auth/login        | Login and extract Bearer Token |
| GET    | /auth/me           | Get logged-in user profile     |
| GET    | /products          | Fetch product listing          |
| POST   | /carts/add         | Add product to cart            |
| GET    | /carts/{{cart_id}} | Get cart details and validate  |

## Environment Variables Used

| Variable   | Description                            |
|------------|----------------------------------------|
| base_url   | https://dummyjson.com                  |
| token      | Bearer token extracted after login     |
| product_id | Product ID extracted from product list |
| cart_id    | Cart ID extracted after Add to Cart    |

## Key Scripts Used

**Token Extraction**

```javascript
let jsondata = pm.response.json();
pm.environment.set("token", jsondata.accessToken);
```

**Status Code Assertion**

```javascript
pm.test("Status code is 200", function() {
    pm.response.to.have.status(200);
});
```

**Saving Dynamic Value**

```javascript
let jsondata = pm.response.json();
pm.environment.set("product_id", jsondata.products[0].id);
```

## How to Run

1. Clone or download this repository
2. Open Postman
3. Click Import and upload ecommerce-api-collection.json and ecommerce-environment.json
4. Select Ecommerce Environment from the top right dropdown
5. Run requests in this order: Login, Get Products, Add to Cart, Get Cart Details
6. Or use Collection Runner to run the full flow at once

## Project Structure

```
├── ecommerce-api-collection.json    # Postman collection
├── ecommerce-environment.json       # Environment variables
└── README.md
```

## Author

**Prathamesh Sawant**

QA Engineer | Transitioning to SDET / API Automation

prathameshvs2000@gmail.com
