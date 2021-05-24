# Function

## 1. How many pets are there at age 1 year, 2 year, etc.?

```sql
SELECT Age, COUNT(*)
FROM Pet
GROUP BY Age
```

## 2. How many cats, dogs, etc. aged 1 year, 2 year, etc. ?

```sql
SELECT Age, Name, COUNT(*)
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
GROUP BY Age, Name
ORDER BY Age ASC
```

## 3. Pet breeds with an average age of less then 6 years

```sql
SELECT AVG(Age), name
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
GROUP BY Name
HAVING AVG(Age) < 6
```

## 4. Last names of employees who completed more than five orders

```sql
SELECT Last_Name, COUNT(*)
FROM Order_Info
JOIN Person ON Order_Info.Employee_ID = Person.Person_ID
WHERE Order_Info.is_done = 1
GROUP BY Person.Person_ID
HAVING COUNT(Order_Info.Order_ID) > 5
```
