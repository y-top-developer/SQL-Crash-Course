# Views

## 1. Create a Dogs view with the following attributes: name, breed, age, last name, and first name of the owner

```sql
CREATE VIEW Dogs
AS SELECT Nick, Breed, Age, Last_Name, First_Name
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
JOIN Person ON Pet.Owner_ID = Person.Person_ID
WHERE Name = 'DOG'
```

## 2. Create the Employee Rating view: last name, first name, number of completed orders, average score (by rating)

```sql
CREATE VIEW Rate
AS SELECT Last_Name, First_Name, COUNT(Order_ID), AVG(Mark)
FROM Order_Info
JOIN Person ON Order_Info.Employee_ID = Person.Person_ID
WHERE Is_Done = 1
GROUP BY Employee_ID, Last_Name, First_Name
```

## 3. Create the Customers view: last name, first name, phone number, address

```sql
CREATE VIEW Customers
AS SELECT Last_Name, First_Name, Phone, Address
FROM Person
WHERE Person_ID NOT IN (
                        SELECT Employee_ID
                        FROM Employee_Service
                        )
```