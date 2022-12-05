_(Udacity: Data Engineering Nano Degree) | 12/4/22_
_This is a project part of Udacity's Data Engineering Nano Degree_

# Project-1b: Data Modeling with NoSQL (Apache Cassandra)

---

## Overview

The purpose of this project is to handle large sets of data for a music streaming startput called "Sparkify".  A NoSQL database was created using Apache Cassandra in order to answer queries regarding the data and to create an ETL pipeline.  A series of tests were included in the queries to catch any potential errors in the Python and CQL code.  The data model aimed to answer the following questions: 

* Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338 and itemInSession=4
* Give me only the following: name of artist, song (sorted by itemInSession) and user(first and lastName) for userid = 10, sessionid = 182
* Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

---

## Method: Data Preprocessing, ETL Pipeline Creation, and Data Modeling

The data needed to complete this task were stored in csv files which were all partitioned by date.  As you will see in this repository, the ETL pipeline were created in a Jupyter Notebook called, Project_1B_Project_Template.ipynb

Copies of the data from the partitioned CSV files were merged to a single csv file called event_datafile_new.csv, which is used to populate the denormalized Cassandra tables to answer the questions as previously mentioned.  The 3 tables created in this model are as follows:

1. **`songinfo_session_item`** includes artist, song title, and song length for a given `sessionId` and `userId`.
2. **`songinfo_user_session`** includes artist, song, user for given `userId` and `sessionId`, where the data was ordered by `itemInSession`
3. **`userinfo_song`** includes the names for a given song


## Tools Used To Complete This Task

* Jupyter Notebook
* Python 3
* Apache Cassandra