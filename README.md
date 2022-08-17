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

**Booking table**
- ID CHAR(36)
- Date DATE
- Destination VARCHAR(100)
- FlightClass CHAR(1)
- FlightType CHAR(1)
- FlightCompany VARCHAR(100)
- PassengerType CHAR(1)
- PassengerID CHAR(36)

**Passenger table** 
- ID CHAR(36)
- FName VARCHAR(100)
- LName VARCHAR(100)
- Age INT

**Flight table**
- Date DATE



**To create the Booking table**<br>
`CREATE TABLE Booking(ID CHAR(36), Date DATE, Destination VARCHAR(100), FlightClass CHAR(1), FlightType CHAR(1),FlightCompany VARCHAR(100), PassengerType CHAR(1), PassengerID CHAR(36), PRIMARY KEY(ID), FOREIGN KEY(PassengerID) REFERENCES Passenger(ID));`

**To create the Passenger table**<br>
`CREATE TABLE Passenger(ID CHAR(36), FName VARCHAR(100), LName VARCHAR(100), Age INT, PRIMARY KEY(ID))`

**To insert a new Passenger row**<br>
`INSERT INTO Passenger (ID, FName, LName, Age) VALUES('c57fe08d-598a-48fa-9d33-e061b2c4445e', 'FLOZ', 'FLOZ', 48);`

`INSERT INTO Passenger (ID, FName, LName, Age) VALUES('f5dc73b9-a10c-4efb-9421-b219f6d44df9', 'Con', 'BonZoop', 6);`

`INSERT INTO Booking (ID, Date, Destination, FlightClass, FlightType, FlightCompany, PassengerType, PassengerID) VALUES('5e4d9031-5bfd-4b55-8424-2c464e36339d', '2022-08-17', 'Spain', 'F', 'S', 'Jet2', 'A', 'c57fe08d-598a-48fa-9d33-e061b2c4445e');`

`INSERT INTO Booking (ID, Date, Destination, FlightClass, FlightType, FlightCompany, PassengerType, PassengerID) VALUES('baf11299-906f-4592-abf4-8edc29b38c5d', '2022-08-17', 'Kuwait', 'E', 'S', 'QatarAir', 'C', 'f5dc73b9-a10c-4efb-9421-b219f6d44df9');`

`INSERT INTO Booking (ID, Date, Destination, FlightClass, FlightType, FlightCompany, PassengerType, PassengerID) VALUES('5b65ee2b-6e24-4218-aa00-0b637d782158', '2022-08-30', 'Iceland', 'B', 'R', 'AirIcelandia', 'A', 'c57fe08d-598a-48fa-9d33-e061b2c4445e');`

`SELECT Booking.Destination, Booking.FlightClass FROM Booking booking, Passenger passenger WHERE passenger.FName = 'FLOZ' AND passenger.ID = booking.PassengerID;`

`SELECT Booking.Destination, Booking.FlightClass FROM Booking booking, Passenger passenger WHERE passenger.LName = 'BonZoop' AND passenger.ID = booking.PassengerID;`

`SELECT Booking.Destination, Booking.FlightClass, Booking.FlightType FROM Booking booking WHERE booking.Date = '2022-08-17'`
