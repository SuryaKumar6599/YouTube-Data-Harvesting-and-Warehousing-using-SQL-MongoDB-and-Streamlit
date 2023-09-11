# YouTube-Data-Harvesting-and-Warehousing 🔴
Python scripting, Data Collection, MongoDB, Streamlit, API integration, Data Managment using MongoDB (Atlas) and SQL

Here's a stepwise walkthrough of the code:

1. Importing necessary libraries:
```python
from googleapiclient.discovery import build
from googleapiclient.errors import HttpError
import pymongo
import psycopg2
import pandas as pd
import streamlit as st
```
The code imports the required libraries for working with the YouTube API (using `googleapiclient`), MongoDB (using `pymongo`), PostgreSQL (using `psycopg2`), data manipulation (using `pandas`), and building web apps (using `streamlit`).

2. API and database connections:
```python
api_key = "YOUR_API_KEY"
api_service_name = "youtube"
api_version = "v3"
youtube = build(api_service_name, api_version, developerKey=api_key)

ytproject = psycopg2.connect(host='localhost', user='postgres', password='1234', database='youtube')  # PostgreSQL connection
project = pymongo.MongoClient("mongodb://localhost:27017/")  # MongoDB connection
```
This code initializes connections to the YouTube API using an API key and connects to PostgreSQL and MongoDB databases.

3. Functions for Retrieving Data:
The script defines functions to fetch channel, playlist, video, and comment details from the YouTube API.
- `youtube_channel(youtube, channel_id)`: Retrieves details about a YouTube channel.
- `get_playlists(youtube, channel_id)`: Retrieves details about playlists belonging to a channel.
- `channel_videoId(youtube, playlist_Id)`: Retrieves video IDs from a playlist.
- `video_details(youtube, video_Id)`: Retrieves details about a video.
- `get_comments_in_videos(youtube, video_id)`: Retrieves comments for a video.

4. Functions for Data Import:
Functions are provided to import data retrieved from the YouTube API into MongoDB and PostgreSQL databases.
- `channel_Details(channel_id)`: Retrieves channel details, playlists, videos, and comments using the API functions and stores them in the respective collections in MongoDB.
- `channel_table()`, `playlist_table()`, `videos_table()`, `comments_table()`: Create tables in the PostgreSQL database and insert data from the corresponding collections in MongoDB.

5. Channel IDs:
The code specifies channel IDs for which data will be collected and stored in databases.

6. Functions for Data Display:
Several functions are defined to display data stored in the PostgreSQL database.
- `display_channels()`: Retrieves and displays data from the "channel" table.
- `display_videos()`: Retrieves and displays data from the "videos" table.
- `display_playlists()`: Retrieves and displays data from the "playlists" table.
- `display_comments()`: Retrieves and displays data from the "comments" table.

7. Required Data to View:
A function (q1()) executes a SQL query to retrieve specific data from the "videos" table.

8. Execution:
The script concludes with function calls to create tables and import data into the PostgreSQL database. It also displays data from the corresponding tables in the PostgreSQL database.
- `tables()`: Creates tables and imports data into the PostgreSQL database.
- `display_channels()`, `display_videos()`, `display_playlists()`, `display_comments()`: Displays the data from the corresponding tables in the PostgreSQL database.

Please note that this code assumes that you have set up the necessary API key, database connections, and have the required databases and collections available. You may need to adapt the code to suit your specific setup and requirements.
