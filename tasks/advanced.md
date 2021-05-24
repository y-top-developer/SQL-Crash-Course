# Advanced

## 1. Get all grades for completed orders, the executors of which were students

```sql
SELECT Mark
FROM Order_Info
WHERE Is_Done = 1
AND Employee_ID IN (
                   SELECT Employee_ID
                   FROM Employee
                   WHERE Spec = 'student'
                   )
```

## 2. Last names of workers who have not received a single order yet

 ```sql
 SELECT Last_Name
 FROM Employee
 JOIN Person on Person.Person_ID = Employee.Person_ID
 WHERE Employee.Person_ID NOT IN (
                                 SELECT Employee_ID
                                 FROM Order_Info
                                 )
 ```

## 3. List of orders (type of service, time, Last name of the worker, pet's nick, Last name of the owner)

```sql
SELECT Name, Time_Order, Employee.Last_Name, Nick, Owner.Last_Name
FROM Order_Info
JOIN Person as Employee ON Employee.Person_ID = Order_Info.Employee_ID
JOIN Person as Owner ON Owner.Person_ID = Order_Info.Owner_ID
JOIN Pet ON Pet.Pet_ID = Order_Info.Pet_ID
JOIN Service ON Service.Service_ID = Order_Info.service_id
```

## 4. Get general list of comments available in the database

```sql
SELECT Comments FROM (
                                SELECT Comments
                                FROM Order_Info
                                UNION
                                SELECT Description
                                FROM Owner
                                UNION
                                SELECT Description
                                FROM Pet
                              ) AS Comments
WHERE LENGTH(Comments) > 0
```

## 5. Get first name and last name of workers, who get mark equal 5

```sql
SELECT First_Name, Last_Name
From Person
WHERE Exists(
            SELECT 1
            FROM Order_Info
            WHERE Mark = 5 AND Person.Person_ID = Order_Info.Employee_ID
            )
```