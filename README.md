# cs623team6

Team members: Junhe Zhang, Marlene Hasslinger

## Schema
![schema](https://github.com/marlenehasslinger/cs623team6/blob/main/schema.png?raw=true)

## ERD incuding cardinalities and relationship types
![erd](https://github.com/marlenehasslinger/cs623team6/blob/main/erdFinalProject.jpeg?raw=true)


SQL code (tested in postgre without syntax errors):

## CREATE TABLE AND INSERT DATA
CREATE TABLE Product (ProdId CHAR(10), PName VARCHAR(30), Price DECIMAL);
ALTER TABLE Product ADD CONSTRAINT pk_product PRIMARY KEY (ProdId);

INSERT INTO Product VALUES ('p1', 'tape', 2.5);
INSERT INTO Product VALUES ('p2', 'tv', 250);
INSERT INTO Product VALUES ('p3', 'ver', 80);

CREATE TABLE Depot (DepId CHAR(10), Addr VARCHAR(30), Volume Integer);
ALTER TABLE Depot ADD CONSTRAINT pk_depot PRIMARY KEY (DepId);
INSERT INTO Depot VALUES ('d1', 'New York', 9000);
INSERT INTO Depot VALUES ('d2', 'Syracuse', 6000);
INSERT INTO Depot VALUES ('d4', 'New York', 2000);

CREATE TABLE Stock (ProdId CHAR(10), DepId CHAR(10), Quantity Integer);
ALTER TABLE Stock ADD CONSTRAINT pk_stock PRIMARY KEY (ProdId, DepId);
INSERT INTO Stock VALUES ('p1', 'd1', 1000);
INSERT INTO Stock VALUES ('p1', 'd2', -100);
INSERT INTO Stock VALUES ('p1', 'd4', 1200);
INSERT INTO Stock VALUES ('p3', 'd1', 3000);
INSERT INTO Stock VALUES ('p3', 'd4', 2000);
INSERT INTO Stock VALUES ('p2', 'd4', 1500);
INSERT INTO Stock VALUES ('p2', 'd1', -400);
INSERT INTO Stock VALUES ('p2', 'd2', 2000);
ALTER TABLE Stock ADD CONSTRAINT fk_stock_prodId_product  FOREIGN KEY (ProdId) REFERENCES Product(ProdId) ON DELETE CASCADE; 
ALTER TABLE Stock ADD CONSTRAINT fk_stock_depId_Depot  FOREIGN KEY (DepId) REFERENCES Depot(DepId) ON DELETE CASCADE; 

 
