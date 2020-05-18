# Udacity Data Modeling Project

## Introdaction:
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The data stored in json files and the need to create Postgres database with tables designed to optimize queries on song play analysis.

## Database Schema:
<img src="img/Data Modeling Schema.png" alt="Database Schema" width="50%"/>

The Database Schema above showing 5 tables:

1. songplays : has all the songs that the user plays.
2. users: has information about the users who uses the app.
3. songs: has information about the songs
4. artists: has information about the artist of a song.
5. time: has information about when a song has been playing.

## ETL pipeline for songs and artists:
1. I extract the song data by pandas from JSON file to DataFrame from this path : 		    
data/song_data/A/A/A/TRAAAAW128F429D538.json 
2. Select the requird cloumns from the DataFram which are: song_id, title, artist_id,  year, duration
3. Insert the data into song table.
4. repeat same steps above for artists. 

## ETL pipline for time, users, songplays:
1. I extract the log data by pandas from JSON file to DataFrame from this path : 		    
data/log_data/2018/11/2018-11-01-events.json
for time and users
2. Select the required information for both table from the DataFrame.
3. Inert the time and users data to time and users table.
4. Since the JSON log table does't has songid and artistid I need to get their ids from artist and song tables
by doing a select that get songid and artistid by joining the two tables and filter them by song title, artist name and song duration.
5. Insert songplays data from JSON file and get the artistid and songid from the select in the above step.

## Geting Started:
1. run python  create_tables.py in your terminal to drop and create all required tables.
2. run python etl.py to insert all data.

## Project Files:
1. sql_queries.py: Has all queries for droping, creating, inserting or selecting from database tables.
2. create_tables.py: Contains the code for creating the database and call sql_queries.py to drop and create database tables.
3. elt.py: Read and extract data from data/song_data and data/log_data and call sql_queries.py to select from database tables and insert to it.
4. etl.ipynb: Notebook that contains ETL processes for each table.
5. test.ipynb: Test the conniction to the database and get the result from tables.


## Resourses:
[https://www.postgresqltutorial.com/postgresql-serial/](https://www.postgresqltutorial.com/postgresql-serial/)
[https://datascience.stackexchange.com/questions/14645/convert-a-pandas-column-of-int-to-timestamp-datatype](https://datascience.stackexchange.com/questions/14645/convert-a-pandas-column-of-int-to-timestamp-datatype)
[https://stackoverflow.com/questions/30676422/passing-parameter-in-psycopg2](https://stackoverflow.com/questions/30676422/passing-parameter-in-psycopg2)
[https://stackoverflow.com/questions/23667369/drop-all-duplicate-rows-in-python-pandas](https://stackoverflow.com/questions/23667369/drop-all-duplicate-rows-in-python-pandas)
[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html)
[https://www.geeksforgeeks.org/create-a-pandas-dataframe-from-lists/](https://www.geeksforgeeks.org/create-a-pandas-dataframe-from-lists/)
[https://stackoverflow.com/questions/12555323/adding-new-column-to-existing-dataframe-in-python-pandas](https://stackoverflow.com/questions/12555323/adding-new-column-to-existing-dataframe-in-python-pandas)
[https://stackoverflow.com/questions/48614158/read-json-file-as-pandas-dataframe](https://stackoverflow.com/questions/48614158/read-json-file-as-pandas-dataframe)
https://www.postgresqltutorial.com/postgresql-upsert/
https://www.python.org/dev/peps/pep-0257/


