## Preparation

## PostgreSQL installation

The database will work in docker, this makes installation very easy. In order for the PostgreSQL to become available on port `5432` with credentials `root`:`root` and database name equal `db`, go to the directory with the [`docker-compose.yml`](files/docker-compose.yml) file and run the following command:

``` bash
docker-compose up -d
```

  ### PostgreSQL connection

To work with PostgreSQL, you need to connect to it. To do this, you need to do the following:

1. Select in the settings, connection to PostgreSQL.

![image-20210524184749504](images/image-20210524184749504.png)

2. Enter data into the form.

![image-20210524184902177](images/image-20210524184902177.png)

3. Check the connection.

![image-20210524185058272](images/image-20210524185058272.png)

### Database initialization

After all the programs are working correctly, you need to create a database.

1. Select in the settings, New Database.

![image-20210524195757557](images/image-20210524195757557.png)

2. Enter the name for the database.

![image-20210524195856896](images/image-20210524195856896.png)

3. Open its console.

![image-20210524195921849](images/image-20210524195921849.png)

4. Enter the [script](files/init.sql) that initialize the database.

![image-20210524200007755](images/image-20210524200007755.png)
