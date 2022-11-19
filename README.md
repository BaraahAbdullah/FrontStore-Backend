
# Build a Frontstore Backend...



## Project Summary:

Build a JavaScript API based on a requirements given by the stakeholders. You will architect the database, tables, and columns to fulfill the requirements. Create a RESTful API to be accessible to the frontend developer. You will also have written test, secured user information with encryption, and provide tokens for integration into the frontend.



## API Documentation


1- Product:
- Add new Product:

    example:

    ```http
    POST /products
  ```


    Body: {
    "name": "new product",
    "price": 250,
    "category": "product type"
    }
- View Product by id:

    example:

    ```http
        GET /products/{product_id}
    ```
- view all Products:
    example:

    ```http
        GET /products
    ```


2- User:

- Add New user:
    example:
    ```http
    POST /users
  ```
    Body: {
    "firstname": "firstName",
    "lastname": "lastName" ,
    "password": "password"
    }

- View user by ID:
    example:
    ```http
    GET /users/{user_id}
  ```

- View all users:
    example:
    
    ```http
        GET /users
     ```

- View User's Orders:
    example:
    ```http
        GET /users/{user_id}/orders 

     ```
3- Order:

- Add new Order:
    example:
    ```http
        POST /orders 

     ```

    Body: {
    "status" : "active",
    "user_id" : 1
    }


## API Endpoints

#### Products

- Index
  '/products' [Get]
- Show
  '/products/:id' [Get]
- Create
  '/products' [token required] [Post]
  (body: {name: string, price:number, category:string})

#### Users

- Index
  '/users' [token required] [Get]
- Show
  '/users/:id' [token required] [Get]
- Create '/user' [Post]
  (body:{firstname: string, lastname: string, password: string})
- Current Order by user
  '/users/:user_id/orders' [token required] [Get]

#### Orders

- Create Order
  '/orders' [token required] [post] (body:{user_id: number, status: 'active' | 'complete', order_products: {product_id:number, quantity:number}[]})

## Data Shapes

#### Product

- id
- name
- price
- category

#### User

- id
- first_name
- last_name
- password

#### Orders

- id
- user_id
- status of order (active or complete)
- id of each product in the order
- quantity of each product in the order

## Database Tables

- products (id: serial primary key, name: varchar not null, price: int not null, category: varchar)
- users (id: serial primary key, firstName: varchar, lastName: varchar, password: varchar)
- orders (id: serial primary key, user_id: int[foreign key to users table], status: varchar(10)[checks its content to be 'active' or 'complete'])
- order_products (id: serial primary key, order_id: foreign key to orders table, product_id: foreign key to products table, quantity: int)

## Deployment

To deploy this project run

```bash
  npm i
```

Create two Database by using **psql shell**
```shell
CREATE DATABASE storefronts_dev;
CREATE DATABASE storefronts_test;
```

**rename ".env-example" to ".env"**

Run DB Megration
```shell
db-migrate up
``` 
Finally run the project 

```shell
npm start
```
 Then open your browser and go to `http://localhost:3000` or use postman
 
## Authors

- [@BarahAbdullah](https://github.com/BaraahAbdullah)

