_(Udacity: Data Engineering Nano Degree) | 11-26-2022_
_This is a project part of Udacity's Data Engineering Nano Degree_

# Project-1: Data Modeling with Postgres

---

## Overview

The purpose of this project is to handle large sets of data for a music streaming startput called "Sparkify".  The dataset is in the JSON format and contains two parts:

* **./data/song_data**: static data about artists and songs
* **./data/log_data**: event data of service usage i.e. who listened to what song, when, where, and with which client


A sample of the formatting contained within the JSON data files is as follows:

Song Dataset

```json
{
    num_songs:1
    artist_id:"ARD7TVE1187B99BFB1"
    artist_latitude:null
    artist_longitude:null
    artist_location:"California - LA"
    artist_name:"Casual"
    song_id:"SOMZWCG12A8C13C480"
    title:"I Didn't Mean To"
    duration:218.93179
    year:0
}
```

Log Dataset
```json
{
    "artist":null,
    "auth":"LoggedIn",
    "firstName":"Walter",
    "gender":"M",
    "itemInSession":0,
    "lastName":"Frye",
    "length":null,
    "level":"free",
    "location":"San Francisco-Oakland-Hayward, CA",
    "method":"GET",
    "page":"Home",
    "registration":1540919166796.0,
    "sessionId":38,
    "song":null,
    "status":200,
    "ts":1541105830796,
    "userAgent":"\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"",
    "userId":"39"
}
```

---

## About the Database

The schema of the Sparkify database is a star schema, meaning it has one fact table containing key business data, with dimension tables surrounding it.  Therefore, the fact table answers what songs the users are listening to.

---

## Schema

# 1. Fact Tables

# Songplays

|   Column    |            Type             | Nullable |
| ----------- | --------------------------- | -------- |
| songplay_id | serial                      | null     |
| start_time  | timestamp                   | null     |
| user_id     | varchar                     | not null |
| level       | varchar                     | null     |
| song_id     | varchar                     | not null |
| artist_id   | varchar                     | not null |
| session_id  | int                         | not null |
| location    | varchar                     | null     |
| user_agent  | varchar                     | null     |

Primary Key: songplay_id

# 2. Dimension Tables


# Users

|   Column   |       Type        | Nullable |
| ---------- | ----------------- | -------- |
| user_id    | integer           | not null |
| first_name | varchar           | null     |
| last_name  | varchar           | null     |
| gender     | varchar           | null     |
| level      | varchar           | null     |

Primary Key: user_id

# Songs

|  Column   |         Type          | Nullable |
| --------- | --------------------- | -------- |
| song_id   | varchar               | not null |
| title     | varchar               | null     |
| artist_id | varchar               | null     |
| year      | integer               | null     |
| duration  | decimal               | null     |

Primary Key: song_id

# Artists

|  Column   |         Type          | Nullable |
| --------- | --------------------- | -------- |
| artist_id | varchar               | not null |
| name      | varchar               | null     |
| location  | varchar               | null     |
| latitude  | double precision      | null     |
| longitude | double precision      | null     |

Primary Key: artist_id

# Time
|   Column   |            Type             | Nullable |
| ---------- | --------------------------- | -------- |
| start_time | timestamp                   | not null |
| hour       | integer                     | null     |
| day        | integer                     | null     |
| week       | integer                     | null     |
| month      | integer                     | null     |
| year       | integer                     | null     |
| weekday    | integer                     | null     |

## Technologies Needed

- Python 3
- PostgreSQL database
- Anaconda Notebook

## Running Files

The file etl.ipynb cannot be run unless the files create_tables.py and sql_queries.py have been ran.

To run create_tables.py, enter this script in the terminal window:

``` sh
python3 create_tables.py
```

To run sql_queries.py, enter this script in the terminal window:

``` sh
python 3 sql_queries.py
```

## Testing

Utilize test.ipynb in order to ensure that the database is being populated accordingly.