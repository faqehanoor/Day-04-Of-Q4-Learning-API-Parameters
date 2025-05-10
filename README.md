## API Parameters Documentation

## Introduction
This repository contains the FastAPI project for managing and interacting with items via various API parameters. The API allows you to query items, fetch item details, and update item information using different types of HTTP requests.

## Requirements
Before running the application, make sure you have the following installed:

## Python 3.7+

## FastAPI

## Uvicorn

## Pydantic

You can install the required dependencies by running:

## pip install fastapi uvicorn pydantic
Project Structure

/fastdca_p1
  ├── main.py         # Main FastAPI app file containing API routes
  └── README.md       # Project documentation
  
## API Endpoints

1. GET /items/{item_id}
Description: Fetch item details based on a unique item ID.

Parameters:

item_id (Path) - A unique identifier for the item (greater than or equal to 1).

Response:

Example:

GET /items/1
Response:

{
  "item_id": 1
}

## 2. GET /items/
Description: Fetch a list of items with optional query filters.

Parameters:

q (Query) - Optional query string to search for items (min length: 3, max length: 50).

skip (Query) - Optional parameter to skip a number of items (default: 0).

limit (Query) - Optional parameter to limit the number of items (default: 10, max: 100).

Response:

JSON object containing the query, skip, and limit parameters.

Example:

GET /items?q=book&skip=0&limit=10
Response:

{
  "q": "book",
  "skip": 0,
  "limit": 10
}

## 3. PUT /items/validated/{item_id}
Description: Update item details using the provided item_id.

## Parameters:

item_id (Path) - A unique identifier for the item (greater than or equal to 1).

q (Query) - Optional query string to update additional information.

item (Body) - Optional JSON object containing item data (name, description, price).

Response:

## JSON object containing the updated item_id, q (if provided), and item data.

Example:

PUT /items/validated/1?q=updated&item={"name": "Updated Book", "description": "Updated description", "price": 19.99}
Response:

{
  "item_id": 1,
  "q": "updated",
  "item": {
    "name": "Updated Book",
    "description": "Updated description",
    "price": 19.99
  }
}

## Running the Application
To run the FastAPI server, use the following command:

uvicorn main:app --reload
This will start the server at http://127.0.0.1:8000. You can access the interactive API documentation at:

http://127.0.0.1:8000/docs

## Conclusion

This FastAPI project is designed to demonstrate how to use API parameters for CRUD operations on items. You can extend the functionality to suit your needs, such as adding authentication, more complex queries, or connecting to a database.

For more details, refer to the FastAPI documentation: FastAPI Docs

