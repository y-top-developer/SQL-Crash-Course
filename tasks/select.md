# Select

## 1. Get data about 'Molly'

```sql
SELECT *
FROM Pet
WHERE Nick='Molly'
```

## 2. Nicks and breeds of all pets sorted by age

```sql
SELECT Nick, Breed
FROM Pet
ORDER BY Age ASC
```

## 3. Get pets with description 

```sql
SELECT *
FROM Pet
WHERE Length(Description) > 0
```

## 4. Get average age of poodles

```sql
SELECT AVG(Age)
FROM Pet
WHERE Breed = 'Poodle'
```

## 5. Get number of owners

```sql
SELECT COUNT(DISTINCT Pet.Owner_id)
FROM Pet
```