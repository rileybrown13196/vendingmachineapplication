# vendingmachineapplication
Simple vending machine application that allows users to insert quarters, select products and dispense the selected item
BACKEND:

Modify the application properties to connect to your DB. View Screenshot attached for example.
I connected using MySQL. 

You will need to do the following: 
replace {YourDBName} with the DB name you are using.
replace {YourUsername} with the DB username you are using.
replace {YourPassword} with the DB password you are using.

If not using MySQL, you will also need to replace the last line of the db configuration to the correct dialect instead of MySQL5Dialect.




FRONTEND: 

PreRequisites: @angular/cli

install dependencies:
npm install

Start the app:
ng serve



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
