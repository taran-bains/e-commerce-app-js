# Taran Bains' and Prince Wang's API Documentation
This API serves our EV commerce site, providing functionality to login to a user
account, buy a product, access all previous transactions, and receive recommendations for similar vehicles.

## Login Endpoint
### /user
**Request Format:**
```json
{
  "username": "example_user",
  "password": "secure_password"
}
```
**Request Type:** POST

**Returned Data Format**:
```json
{
  "userId": "123456",
}
```

**Description:**
Allows users to log in to their account.

**Example Request:**
```json
{
  "username": "john_doe",
  "password": "P@ssw0rd"
}
```

**Example Response:**
```json
{
  "userId": "789012",
}
```

**Error Handling:**
*Status Code: 401 Unauthorized*
```json
{
  "error": "Invalid credentials"
}
```

## Purchase Endpoint
**Request Format:**
```json
{
  "productId": "abc123",
  "userId": "user123"
}
```

**Request Type:** *POST*

**Returned Data Format**:
```json
{
  "orderId": "789xyz",
  "totalAmount": 110500.00
}
```

**Description:** *Allows users to buy a product.*

**Example Request:**
```json
{
  "productId": "ev_car_001",
  "userId": "user18375"
}
```

**Example Response:**
```json
{
  "orderId": "xyz789",
  "amount": 45000.00
}
```

**Error Handling:**
Status Code: 404 Not Found
```json
{
  "error": "Product not found"
}
```

## Transaction History Endpoint

**Request Type:** *GET*

**Returned Data Format**:
```json
{
  "transactions": [
    {
      "orderId": "123abc",
      "date": "2023-11-01",
      "totalAmount": 110200.00
    },
    {
      "orderId": "456def",
      "date": "2023-11-03",
      "totalAmount": 55000.00
    }
  ]
}
```

**Description:** *Allows users to access all previous transactions.*

**Example Request:**
```json
{
  "userId": "789012"
}

```

**Example Response:**
```json
{
  "transactions": [
    {
      "orderId": "123abc",
      "date": "2023-11-01",
      "totalAmount": 110200.00
    },
    {
      "orderId": "456def",
      "date": "2023-11-03",
      "totalAmount": 55000.00
    }
  ]
}
```

**Error Handling:**
Status Code: 404 Not Found
```json
{
  "error": "User not found"
}
```

## Vehicle Recommendations Endpoint

**Request Formatt:**
```json
{
  "selectedVehicleId": "ev_car_001"
}
```

**Request Type:** *GET*

**Returned Data Format**:
```json
{
  "recommendations": [
    {
      "productId": "ev_car_002",
      "modelName": "Tesla Model S"
    },
    {
      "productId": "ev_car_003",
      "modelName": "Nissan Leaf"
    }
  ]
}
```

**Description:** *Provides recommendations for similar vehicles after clicking on a certain vehicle.*

**Example Request:**
```json
{
  "selectedVehicleId": "ev_car_001"
}
```

**Example Response:**
```json
{
  "recommendations": [
    {
      "productId": "ev_car_002",
      "modelName": "Tesla Model S"
    },
    {
      "productId": "ev_car_003",
      "modelName": "Nissan Leaf"
    }
  ]
}
```

**Error Handling:**
Status Code: 404 Not Found
```json
{
  "error": "Vehicle not found"
}
```

# Display main view API
Display the items on a “main view” page. See wireframe, has navbar and slogan with image background, shop with categorized electric vehicles and customizable views.

**Request Format:** /Go-back

**Request Type:** GET

**Returned Data Format**: JSON

**Description:**
The "Display main view" API is designed to retrieve and display the items on the main view page of the application. The main view page includes a navigation bar, a slogan with an image background, a shop section with categorized electric vehicles, and customizable views for users.

**Example Request:** GET /api/display-main-view

**Example Response:**
```json
{
  "navbar": {
    "links": [
      {"text": "Home", "url": "/home"},
      {"text": "Shop", "url": "/shop"},
      {"text": "Contact", "url": "/contact"}
    ]
  },
}
```
**Error Handling:**
No error message

# Detail item API
Clicking on any individual item should bring the user to a view which provides
more detailed information about said item.

**Request Format:** /Cars

**Request Type:** GET

**Returned Data Format**: JSON

**Description:**
This endpoint retrieves detailed information about a specific item, identified by its unique identifier or some other relevant parameter. The detailed information may include specifications, features, pricing, and any other pertinent details associated with the item.

**Example Request:** GET /api/Cars/{item_id}

**Example Response:**
```json
{
  "item_id": "12345",
  "name": "Example Car",
  "brand": "Example Brand",
  "model": "XYZ",
  "year": 2023,
  "color": "Blue",
  "price": "$30,000",
  "specifications": {
    "engine": "V6",
    "transmission": "Automatic",
    "fuel_type": "Gasoline",
    "mileage": "25 mpg"
  },
  "features": [
    "Leather seats",
    "Bluetooth connectivity",
    "Backup camera"
  ],
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. ..."
}
```
**Error Handling:**
No error message

# Filter API
Users must be able to search and filter the available items

**Request Format:** /Filter

**Request Type:** GET

**Returned Data Format**: JSON

**Description:**
The GET request is used to retrieve filtered items based on the specified search criteria. Clients can include parameters in the request URL to filter the available items according to their requirements.

**Example Request:** /Filter?category=electronics&price_range=100-500&brand=XYZ

**Example Response:**
```json
{
  "items": [
    {
      "id": 1,
      "name": "SUV1",
      "category": "electronics",
      "price": 299.99,
      "brand": "XYZ"
    },
    {
      "id": 2,
      "name": "SUV2",
      "category": "electronics",
      "price": 499.99,
      "brand": "XYZ"
    }
  ]
}
```

**Error Handling:**
No error message

# Feedback API
Average review out of 5 stars displayed under every vehicle in main view (not in wireframe) and to the side in detailed view

**Request Format:** /Review

**Request Type:** GET/POST

**Returned Data Format**: JSON

**Description:**
GET: Retrieve average review information for vehicles.
This endpoint retrieves the average review rating for each vehicle, which is displayed under every vehicle in the main view and to the side in detailed view. The response includes the average rating, the total number of reviews, and any additional relevant information.

POST: Submit a new review for a vehicle.
This endpoint allows users to submit a new review for a specific vehicle. The request should include parameters such as the vehicle ID, user ID, and the review rating. The API will process the new review and update the average rating for the respective vehicle.


**Example Request:**
GET /Review

POST /Review
Content-Type: application/json
```json
{
  "vehicle_id": "123456",
  "user_id": "789",
  "rating": 4.5,
  "comment": "Great vehicle, smooth ride!"
}
```

**Example Response:**
```json
{
  "vehicle_id": "123456",
  "average_rating": 4.2,
  "total_reviews": 50,
  "additional_info": "Additional information about the vehicle or reviews can be included here."
}
```

**Error Handling:**
No error message