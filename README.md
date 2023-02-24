# vendingmachineapplication
Simple vending machine application that allows users to insert quarters, select products and dispense the selected item

_________________________________________________________________________________________

OVERVIEW:
This is a simple application that allows users to insert quarters into a vending machine, view a list of products, select and product, and dispense the selected product.

_________________________________________________________________________________________


STEPS:
No Balance : The user needs to input quarters into the system. They cannot dispense a product until a balance is present. 

Has Balance: The user has input quarters into the application. They can now select a product or eject quarters if they change their mind. 
Products will be displayed with an image of the product as well as an item code. 
The user will input the item code into the text box and select submit to select the product. 
Now the user can dispense the item by pressing the dispense button. 

Sold:
If the user has inserted sufficient quarters, a message will be displayed saying "Enjoy you 'product name'".
The inventory in the database will be updated. Currently only one product is dispensed at a time. 

Sold Out:
Once the product count has reached 0, a sold out message is displayed underneath the product. The user can no longer dispense the product. If they try to, a message will be displayed stating no remaining inventory.

_________________________________________________________________________________________

BACKEND:

Modify the application properties to connect to your DB. View Screenshot attached for example.
I connected using MySQL. 

You will need to do the following: 
replace {YourDBName} with the DB name you are using.
replace {YourUsername} with the DB username you are using.
replace {YourPassword} with the DB password you are using.

If not using MySQL, you will also need to replace the last line of the db configuration to the correct dialect instead of MySQL5Dialect.

_________________________________________________________________________________________

FRONTEND: 

PreRequisites: @angular/cli

install dependencies:
npm install

Start the app:
ng serve

_________________________________________________________________________________________

DATABASE:

I used MySql to create the Database using this command. 
mysql> create database vendingmachineDB;

Hibernate created the tables with a primary key on Id when starting the application. 

Alternatively this should work:


CREATE TABLE product (
    ID BIGINT NOT NULL,
    image_url varchar(255),
    product_code INT,
    product_count INT,
    product_name varchar(255),
    PRIMARY KEY (ID)
);

CREATE TABLE purchase_log (
    ID BIGINT NOT NULL,
    product_code INT,
    product_count INT,
    product_purchased varchar(255),
    purchase_date DATETIME,
    PRIMARY KEY (ID)
);

Product I used for testing:
image_url: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKUkycaQ9oB8322OYHfxwwQ6YUUTFsTzZdmA&usqp=CAU
product_code: 11
product_count: 5
product_name: soda_cola

_________________________________________________________________________________________

TOOLS USED: 

Developing backend:
IntelliJ
Java utilizing Spring Boot.
I used the following url to generate a basic spring boot package: http://start.spring.io/

Testing Apis:
Postman

Database:
MySql

Frontend:
WebStorm
Angular CLI project 


POSTMAN TESTING EXAMPLES:

Add product to product table:
POST http://localhost:8080/product/addProduct
Body:
{
    "productName": "soda_cola",
    "productCount": 10,
    "imageUrl": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKUkycaQ9oB8322OYHfxwwQ6YUUTFsTzZdmA&usqp=CAU",
    "productCode": 11
}

Get Products:
GET http://localhost:8080/product/all
JSON Body:
{
    "productName": "soda_cola",
    "productCount": 10,
    "imageUrl": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKUkycaQ9oB8322OYHfxwwQ6YUUTFsTzZdmA&usqp=CAU",
    "productCode": 11
}

UpdateProductCount:
PUT http://localhost:8080/product/updateProductCount/11
Body:
{
    "productName": "soda_cola",
    "productCount": 10,
    "imageUrl": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQKUkycaQ9oB8322OYHfxwwQ6YUUTFsTzZdmA&usqp=CAU",
    "productCode":11
}

Add Log Entry:
POST http://localhost:8080/logging/addProductLog
Body:
{
    "productPurchased": "soda_cola",
    "productCount": 1,
    "productCode": 11
}






