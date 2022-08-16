# Data Driven Travel
Create a Travel-app class and automate testing with data driven from SQL database<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[java api](https://docs.oracle.com/javase/7/docs/api/),
[sql](https://www.w3schools.com/sql/)

## Steps
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)
* Run as JUnit test the file `TravelAppTest.java` for sanity testing the local database

## Database Schema

**Animal table**
- Hunger INT
- ID CHAR(36)
- Name VARCHAR(100)
- OwnerID CHAR(36)
- Species CHAR(1)


**Owner table** 
- ID CHAR(36)
- Name VARCHAR(100)
- Town VARCHAR(100)

**To create the animal table**<br>
`CREATE TABLE Animal(Hunger INT,ID CHAR(36), Name VARCHAR(100), OwnerID CHAR(36), Species CHAR(1), PRIMARY KEY(ID), FOREIGN KEY(OwnerID) REFERENCES Owner(ID));`

**To create the owner table**<br>
`CREATE TABLE Owner(Town VARCHAR(100), ID CHAR(36), Name VARCHAR(100), PRIMARY KEY(ID))`

**To insert a new Owner row**<br>
`INSERT INTO Owner (ID, Name, Town) VALUES('af3fb932-05cd-41a9-ada1-60b7b7122f26', 'FLOZ', 'Bridgenorth');`

`INSERT INTO Animal (Hunger, ID, Name, OwnerID, Species) VALUES(0, '94fccc18-a20a-4ea1-bc06-67fd463fa835', 'Jess', 'af3fb932-05cd-41a9-ada1-60b7b7122f26', 'C');`

`INSERT INTO Animal (Hunger, ID, Name, OwnerID, Species) VALUES(0, 'f467fbc6-2cc1-4c3d-80ca-f2829944b0f8', 'Milo', 'af3fb932-05cd-41a9-ada1-60b7b7122f26', 'D');`

**To query an animal**<br>
`SELECT Hunger, ID, Species FROM Animal WHERE Name = 'Jess';`

**To query all pets for an owner**<br>
`SELECT animal.Name, animal.Species FROM Animal animal, Owner owner WHERE owner.Name = 'FLOZ';`