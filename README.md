# Manage-an-E-commerce-Database
The project focuses on creating a relational database for a virtual client who is into Sports equipment. 
CREATE DATABASE AthleteZone;
USE AthleteZone;
CREATE TABLE Customers (
		CustomerID INT AUTO_INCREMENT PRIMARY KEY,
		FirstName VARCHAR(50) NOT NULL,
        LastName VARCHAR(50) NOT NULL,
        EmailAddress VARCHAR(100) NOT NULL UNIQUE,
        JoinDate DATE NOT NULL
        );
INSERT INTO Customers (CustomerID, FirstName, Lastname, EmailAddress, JoinDate)
VALUE 
	('001', 'Tamuno', 'Briggs', 'tamuno.briggs@email.com', '2023-07-15'),
    ('002', 'Ibifubara', 'Jack', 'ibifubara.jack@email.com', '2022-09-10'),
    ('003', 'Preye', 'Amadi', 'preye.amadi@email.com', '2021-05-22'),
    ('004', 'Kelechi', 'Wokoma', 'kelechi.wokoma@email.com', '2024-01-08'),
    ('005', 'Tonye', 'George', 'tonye.george@email.com', '2020-11-30'),
    ('006', 'Soberekon', 'Hart', 'soberekon.hart@email.com', '2023-03-18');
    SELECT * FROM Customers;

CREATE TABLE Products (
		ProductID INT AUTO_INCREMENT PRIMARY KEY,
        ProductName VARCHAR(100) NOT NULL,
        Price DECIMAL(10, 2) NOT NULL,
        StockQuantity INT NOT NULL
        );
INSERT INTO Products (ProductName, Price, StockQuantity) 
VALUES 
    ('Football', 24.99, 100),
    ('Basketball', 29.50, 80),
    ('Tennis Racket', 89.99, 50),
    ('Badminton Shuttlecock', 12.75, 150),
    ('Baseball Bat', 45.99, 60),
    ('Gym Dumbbells', 99.99, 30);

CREATE TABLE Orders (
		OrderID INT AUTO_INCREMENT PRIMARY KEY,
		CustomerID INT,
		ProductID INT,
        OrderDate DATE NOT NULL,
        Quantity INT NOT NULL,
        FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID),
        FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);
INSERT INTO Orders (CustomerID, ProductID, OrderDate, Quantity) 
VALUES 
    (1, 2, '2024-01-15', 3),
    (2, 5, '2023-12-20', 1),
    (3, 1, '2024-02-10', 2),
    (4, 4, '2023-11-05', 5),
    (5, 3, '2024-01-28', 4),
    (6, 6, '2023-10-18', 2);
SELECT * FROM Orders;
SELECT * FROM Products;
#UPDATE
UPDATE Customers 
SET EmailAddress = 'soboyintown2000@yahoo.com'
WHERE CustomerID = 1;

UPDATE Products
SET Price = '26.5'
WHERE ProductID = 2;

UPDATE Orders
SET Quantity = '7'
WHERE OrderID = 5;

DELETE FROM Customers
WHERE CustomerID = 2;
DELETE FROM orders WHERE CustomerID = 5;
DELETE FROM customers WHERE CustomerID = 5;
