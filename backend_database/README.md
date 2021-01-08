# Setup
Create docker container containing postgres
```
$ docker run --name db-postgres -e POSTGRES_PASSWORD=postgres -d -p 5432:5432 postgres
```
Go inside your container and create a database:
```
psql -h 127.0.0.1 -p 5432 -U postgres
```
And write the following:
```
postgres-# CREATE DATABASE airflow;
postgres-# CREATE USER airflow WITH PASSWORD 'airflow';
postgres-# GRANT ALL PRIVILEGES ON DATABASE airflow TO airflow;
```
In airflow.cfg file look for sql_alchemy_conn and update it to point to your PostgreSQL serv:
```
sql_alchemy_conn = postgresql+psycopg2://airflow:airflow@localhost:5432/airflow
```
Now you are ready to init the airflow application using postgres:
```
$ airflow initdb
```
If everything was right, access the psql command line again, enter in airflow database with ``\c`` airflow command and type ``\dt`` command to list all tables of that database. You should see a list of airflow tables, currently it is 23.
