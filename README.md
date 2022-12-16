
# Data Modeling and ETL pipeline for SparkifyDB

## Introduction


In this project, we are going to create a Data pipeline, where we will create Star schema for Sparkify Data Analysis. After creating this pipeline extract the logs and songs data, then we will process this data, and stored this data into our created database.


## Database Schema

1. Songplays table:

    ```
        CREATE TABLE IF NOT EXISTS songplays
        (
            songplay_id SERIAL PRIMARY KEY,
            start_time TIMESTAMP NOT NULL,
            user_id INTEGER NOT NULL,
            level VARCHAR,
            song_id VARCHAR,
            artist_id VARCHAR,
            session_id INTEGER NOT NULL,
            location VARCHAR,
            user_agent VARCHAR NOT NULL
        );
    ```
2. Users table

    ```
        CREATE TABLE IF NOT EXISTS users
        (
            user_id INTEGER PRIMARY KEY,
            first_name VARCHAR,
            last_name VARCHAR,
            gender VARCHAR,
            level VARCHAR
        );
    ```

3. Songs table

    ```
        CREATE TABLE IF NOT EXISTS songs
        (
            song_id VARCHAR PRIMARY KEY,
            title VARCHAR NOT NULL,
            artist_id VARCHAR NOT NULL,
            year INTEGER,
            duration NUMERIC NOT NULL
        );
    ```

4. Artists table

    ```
        CREATE TABLE IF NOT EXISTS artists
        (
            artist_id VARCHAR PRIMARY KEY,
            name VARCHAR NOT NULL,
            location VARCHAR,
            latitude FLOAT,
            longitude FLOAT
        );
    ```

5. Timetable table

    ```
        CREATE TABLE IF NOT EXISTS timetable
        (
            start_time TIMESTAMP PRIMARY KEY,
            hour INTEGER,
            day INTEGER,
            week INTEGER,
            month INTEGER,
            year INTEGER,
            weekday INTEGER
        );
    ```

## Project Structure

In this project, we have multiple project files, according to the functionalities.

1. create_tables.py
    This file contains code for creating the database Schema.

2. sql_queries.py
    This file contains all the queries, inlcuding creating tables, and inserting, and getting values from the tables.
    
3. etl.py
    This file contains different functions of loading the dataset, process the dataset and in the end storing that information into the database.
    
## Usage

You can first `Create the DB Schema` by running the following command.

``` bash
    python create_tables.py
```

Then you can perform the ETL tasks, using the following command.

``` bash
    python etl.py
```
