# Ecommerce API Test Suite - Postman

A hands-on API testing project built using Postman, focused on 
authentication flows, token handling, and secure endpoint validation 
using a real-world ecommerce API.

---

## Project Overview

This project simulates a real-world API testing scenario for an 
ecommerce application. It covers the complete authentication flow 
from logging in and extracting a token, to using that token to access 
protected resources.

---

## What This Project Covers

- Login API testing using POST request with credentials
- Extracting Bearer Token from login response using test scripts
- Storing token in Postman environment variables for reuse
- Validating secure endpoints using Bearer Token authentication
- Testing product listing and saving product ID for chained requests
- Writing test scripts for response validation (status codes, 
  response body, data types)

---

## Tech Stack

- Postman
- JavaScript (pm API for test scripts)
- dummyjson.com (free public REST API)

---

## API Endpoints Tested

| Method | Endpoint              | Description                  |
|--------|-----------------------|------------------------------|
| POST   | /auth/login           | Login and extract token       |
| GET    | /auth/me              | Get logged-in user profile    |
| GET    | /products             | Get product listing           |

---

## Environment Variables Used

| Variable  | Description                        |
|-----------|------------------------------------|
| base_url  | https://dummyjson.com              |
| token     | Bearer token extracted after login |
| productId | Product ID saved for chained calls |

---

## How to Run

1. Clone or download this repository
2. Open Postman
3. Click **Import** and upload:
   - `ecommerce-api-collection.json`
   - `ecommerce-environment.json`
4. Select the **Ecommerce Environment** from the top right dropdown
5. Open the collection and run requests in order:
   - Login first (token gets saved automatically)
   - Then run GET Profile and GET Products

---

## Key Concepts Demonstrated

**Token Extraction via Script**
```javascript
let jsondata = pm.response.json();
pm.environment.set("token", jsondata.accessToken);
```

**Response Assertion**
```javascript
pm.test("Status code is 200", function() {
    pm.response.to.have.status(200);
});
```
---

## Project Structure

```
├── ecommerce-api-collection.json                        # Postman collection
├── ecommerce-environment.postman_environment.json       # Environment variables
└── README.md
```

---

## Author

**Prathamesh Sawant**  
QA Engineer | Transitioning to SDET / API Automation  
prathameshvs2000@gmail.com  
