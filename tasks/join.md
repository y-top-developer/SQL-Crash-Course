# Join

## 1.  Get data about 'Molly' with pet type

```sql
SELECT Pet.*, name
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
WHERE Nick='Molly'
```

## 2. Get list of all dogs by name, breed and age

```sql
SELECT Nick, Breed, Age
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
WHERE Name = 'DOG'
```

## 3. Get average cat's age

```sql
SELECT AVG(Age)
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
WHERE Name = 'CAT'
```

## 4. Time and executors of not done orders

```sql
SELECT Time_Order, Last_Name
FROM Order_Info
JOIN Person ON Order_Info.Employee_ID = Person.Person_ID
WHERE is_done = 0
```

## 5. List owners of dogs

```sql
SELECT First_Name, Last_Name, Phone
FROM Pet
JOIN Pet_Type ON Pet.Pet_Type_ID = Pet_Type.Pet_Type_ID
JOIN Owner ON Owner.Owner_ID = Pet.Owner_ID
JOIN Person ON Owner.Person_ID = Person.Person_ID
WHERE Name = 'DOG'
```

## 6. All types of pets and the names of representatives of these breeds

```sql
SELECT Name, Nick
FROM Pet_Type
LEFT OUTER JOIN Pet ON Pet_Type.Pet_Type_ID = Pet.Pet_Type_ID
```