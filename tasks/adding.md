# Adding

## 1. Write a statement adding a new individual to the PERSON table while preserving the sequential numbering of records.

```sql
INSERT INTO Person (Person_ID, Last_Name, First_Name,
Phone, Address) VALUES ((
        SELECT MAX(Person_ID) + 1
        FROM Person
        ),
        'Lee', 'Robert', '972-701-5939', '1782 Charla Lane, Dallas, TX 75240 ')
```

## 2. Write a statement that adds an “(s)” to the beginning of the comment for each order that is a student

```sql
UPDATE Order_Info
SET Comments = CONCAT('(s)', COALESCE(comments, ''))
FROM Employee
WHERE Employee.Employee_ID = Order_Info.Employee_ID and Spec = 'student'
```

## 3. Create a new table in the database for storing data on documents of individuals (type and number of document). When creating a link from it to the PERSON table, specify the delete cascade property

````sql
CREATE TABLE Documents(
 Document_ID INTEGER NOT NULL,
 Name VARCHAR(50),
 Number INTEGER,
 Person_ID INTEGER NOT NULL,
 CONSTRAINT Document_PK PRIMARY KEY (Document_ID)
);
ALTER TABLE Documents ADD CONSTRAINT FK_Docs_Person
FOREIGN KEY (Person_ID)
REFERENCES Person(Person_ID) ON DELETE CASCADE;
````