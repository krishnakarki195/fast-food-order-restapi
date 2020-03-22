# fast-food-order-restapi
Requirements
Creating a database should be left to the end. Mock this dependency using Mockito and a service layer.
Endpoint Specification
Create a new order
Endpoint: /api/orders Type: POST Request Body:

{
    "customerName": "Hungry Man Jr",
    "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
}


Response Body:

{
    "id": "1",
    "customerName": "Hungry Man Jr",
    "createdAt": "2011-12-03T10:15:30",
    "status": "PENDING",
    "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
    "lastUpdated": "2011-12-03T10:15:30"
}


# Get all orders
Endpoint: /api/orders Type: GET Request Body: NA Response Body:

Requests[
    {
        "id": "22",
        "customerName": "Master Yoda",
        "createdAt": "2019-11-06T15:15:30",
        "status": "PENDING",
        "description": "Veggie  burger with egg",
        "lastUpdated": "2011-12-03T10:15:30"
    },
    {
        "id": "35",
        "customerName": "William Shakespear",
        "createdAt": "2020-13-03T09:15:30",
        "status": "PENDING",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "lastUpdated": "2011-12-03T10:15:30"
    },
    {
        "id": "35",
        "customerName": "William Shakespear",
        "createdAt": "2020-13-03T09:15:30",
        "status": "CANCELLED",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "note": "Forgot wallet, wanted to pay with a roll of tissue"
        "lastUpdated": "2011-12-03T10:15:30"
    }
    ...
}

Get one order details
Endpoint: /api/orders/{id} Type: GET Request Body: NA Response Body:


{
        "id": "35",
        "customerName": "William Shakespear",
        "createdAt": "2020-13-03T09:15:30",
        "status": "CANCELLED",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "note": "Forgot wallet, wanted to pay with a roll of tissue"
        "lastUpdated": "2011-12-03T10:15:30"
}

Update order
Endpoint: /api/orders/{id} Type: PUT Notes: Request Body: All attributes are optional, but must have at least one

{
        "customerName": "Baby Yoda",
        "status": "CANCELLED",
        "note": "Got name wrong, thought it was Master Yoda. He was insulted and cancelled"
}

## Advanced
# Get all orders filtered by status
Endpoint: /api/orders?status=CANCELLED Type: GET Request Body: NA Response Body:


Requests[
    {
        "id": "35",
        "customerName": "Tony Romo",
        "createdAt": "2020-13-03T09:15:30",
        "status": "CANCELLED",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "note": "Got upset that he didn't win the Super Bowl",
        "lastUpdated": "2011-12-03T10:15:30"
    },
    {
        "id": "35",
        "customerName": "Anakin Skywalker",
        "createdAt": "2020-13-03T09:15:30",
        "status": "CANCELLED",
        "description": "Salad warmed in microwave",
        "note": "Suddenly went to the dark side"
        "lastUpdated": "2011-12-03T10:15:30"
    }
    ...
}

# Get all orders filtered by start and min date
Endpoint: /api/orders?startDate=01/01/2019&endDate=12/31/2019 Type: GET Request Body: NA Response Body:


Requests[
    {
        "id": "22",
        "customerName": "Master Yoda",
        "createdAt": "2019-11-06T15:15:30",
        "status": "PENDING",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "lastUpdated": "2011-12-03T10:15:30"
    },
    {
        "id": "35",
        "customerName": "Doogie Houser",
        "createdAt": "2020-13-03T09:15:30",
        "status": "PENDING",
        "description": "Meat patty with no bun",
        "note": null,
        "lastUpdated": "2011-12-03T10:15:30"
    },
    {
        "id": "35",
        "customerName": "William Shakespear",
        "createdAt": "2020-13-03T09:15:30",
        "status": "CANCELLED",
        "description": "Burger, double meat, extra pickles, doughnut buns, diet coke",
        "note": "Forgot wallet, wanted to pay with a roll of tissue"
        "lastUpdated": "2011-12-03T10:15:30"
    }
    ...
}
# Nightmare Mode
Add FoodItem entity
Add List of FoodItems to each order when creating an order and when retrieving order details response
Add orderTotal to Order entity that's calculated based on individual FoodItems
The restaurant closes at 10pm, throw an error when orders are submitted past the close time
Add pagination
