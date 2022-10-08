Project Submission - Manasa Velugotla

Concepts from Data Modeling with Postgres are used to implement this project and below are the concepts used :- 

1) Data Modeling with Postgres 
2) Dimension Modeling - Star Schema 
3) ETL pipeline using Python


Preface: 

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.


Underlying data:

Song_data - Located in 'data/song_data', contains a series of files that are partitioned by the first three letters of each song's track ID. 

Log_data - located in 'data/log_data', contains a series of log files in JSON format based on the songs dataset. They are partitioned by year and month. 


Data Model - STAR SCHEMA:
    Followed a relational model structure by organizing data in tables. Implemented a Star schema data modeling approach for this scenario, classifying the tables into Fact and Dimensions. 

Fact table - 
   songplays:- records in log data associated with song plays i.e, with page = NextSong
   Columns: songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

Dimension tables-
    users:- users in the app
    Columns: user_id, first_name, last_name, gender, level
   
    songs:- songs in music database
    Columns: song_id, title, artist_id, year, duration
   
    artists - artists in music database
    Columns: artist_id, name, location, latitude, longitude
  
    time - timestamps of records in songplays broken down into specific units
    Columns: start_time, hour, day, week, month, year, weekday


Project files and implementation:-

1) Data - The underlying data for this project is to be imported from the "data" folder and all files are in "json" format.
2) sql_queries.py - Underlying queries that build the above Fact and Dimension tables using Drop, Create and Insert statments. These queries are utilized in create_tables.py, etl.ipynb and etl.py 
3) create_tables.py - A python script that creates the database & calls the create and drop table queries from "sql_queries.py". Run this script prior to running the ETL script each time
4) test.ipynb - Sanity checks in place to verify if the table/data is loaded into the database as intended. Run this every time post execution of the python scripts and check for any errors 
5) etl.ipynb - this notebook is build to read and load a single file from "song_data" and "log_data" JSON files into tables created in step 3. 
6) etl.py - script to read and proecess all files lving in "song_data" and "log_data" and load them into the fact and dimension tables
7) readme - discusses the project at hand
8) Runner_file - notebook to execute the scripts "create_tables.py" & "etl.py"


Implementation- 

1) Set up queries to Drop, create and insert data with defined constraints. 
2) Ran "create_tables.py" from the Runner_file to drop any previously existing tables, if any, and create new.
3) Executed "test.ipynb" to confirm creation of tables and verify the table structure created above
4) Completed the "etl.ipynb" to load single files from "data/song_data" and "data/log_data"  folders
5) Executed "test.ipynb" to verify the data inserted above 
6) Completed the etl script - "etl.py" by utilizing the code that has been built from "etl.ipynb" where the entire series of datasets are processed from the data folders. 
Note - From the Runner_file, first re-run the "create_tables.py" to reset the tables followed by the "etl.py" script.
7) Executed "test.ipynb" to verify the data insertions from all the files above.