# spotify_sql_project
”
🎧 Spotify SQL Data Analysis Project (Beginner → Advanced)

📌 Overview
This project demonstrates my ability to perform Exploratory Data Analysis (EDA) and solve real-world business problems using SQL on a Spotify-inspired dataset.
The analysis progresses from basic data exploration → intermediate aggregations → advanced analytical queries, showcasing a structured approach to problem-solving as a Data Analyst.

🎯 Objectives
.Practice and demonstrate SQL skills across difficulty levels
.Solve real-world analytical problems
.Write optimized and readable SQL queries
.Derive actionable insights from data

🛠️ Tech Stack
.SQL (PostgreSQL / MySQL compatible)
.DBMS: PostgreSQL / MySQL 
.Tools Used: DBeaver / MySQL Workbench / pgAdmin

📂 Dataset Description

The dataset simulates Spotify-like streaming data and contains:
```SQL
Artist VARCHAR(100),
Track VARCHAR(300),
Album VARCHAR(350),
Album_type VARCHAR(500),
Danceability FLOAT,
Energy FLOAT,
Loudness FLOAT,
Speechiness FLOAT,
Acousticness FLOAT,
Instrumentalness FLOAT,
Liveness FLOAT,
Valence FLOAT,
Tempo FLOAT,
Duration_min FLOAT,
Title VARCHAR(500),
Channel VARCHAR(250),
Viewss BIGINT,
Likes BIGINT,
Commentss BIGINT,
Licensed BOOLEAN,
official_video BOOLEAN,
Stream BIGINT,
EnergyLiveness FLOAT,
most_playedon VARCHAR(150)
```

🧱 Database Setup

```
DROP TABLE IF EXISTS spotify;

CREATE TABLE spotify(
    Artist VARCHAR(100),
    Track VARCHAR(300),
    Album VARCHAR(350),
    Album_type VARCHAR(500),
    Danceability FLOAT,
    Energy FLOAT,
    Loudness FLOAT,
    Speechiness FLOAT,
    Acousticness FLOAT,
    Instrumentalness FLOAT,
    Liveness FLOAT,
    Valence FLOAT,
    Tempo FLOAT,
    Duration_min FLOAT,
    Title VARCHAR(500),
    Channel VARCHAR(250),
    Viewss BIGINT,
    Likes BIGINT,
    Commentss BIGINT,
    Licensed BOOLEAN,
    official_video BOOLEAN,
    Stream BIGINT,
    EnergyLiveness FLOAT,
    most_playedon VARCHAR(150)
);
```

🔍 Exploratory Data Analysis (EDA)
Before solving business problems, I performed initial exploration:
```
-- Total records
SELECT COUNT(*) FROM spotify;

-- Unique artists & albums
SELECT COUNT(DISTINCT artist) FROM spotify;
SELECT COUNT(DISTINCT album) FROM spotify;

-- Distribution checks
SELECT DISTINCT album_type FROM spotify;
SELECT DISTINCT most_playedon FROM spotify;

-- Feature averages
SELECT AVG(energy), AVG(loudness), AVG(speechiness), AVG(acousticness)
FROM spotify;

-- Track duration insights
SELECT MAX(duration_min), MIN(duration_min) FROM spotify;
```
💡 Key Observations
.Dataset contains multiple platforms (Spotify & YouTube)
.Wide variation in engagement metrics (views, likes, streams)
.Audio features (energy, danceability, etc.) allow behavioral analysis

🎯 Business Questions Solved

This project answers 13 real-world analytical questions categorized into three levels:

🟢 Beginner Level (SQL Fundamentals)
1. Tracks with more than 1 Billion Streams
   ```
   SELECT track, stream
FROM spotify
WHERE stream >= 1000000000;
 ```
2. Albums with their respective artists
```
SELECT album, artist
FROM spotify;
```
3. Total albums per artist (Top creators)
```
SELECT artist, COUNT(album) AS total_albums
FROM spotify
GROUP BY artist
ORDER BY total_albums DESC;
```
4. Total comments on licensed tracks
```
SELECT SUM(commentss) AS total_comments
FROM spotify
WHERE licensed = TRUE;
```
5. Tracks from "Single" album type
```
SELECT track, album_type
FROM spotify
WHERE album_type = 'single';
```
6.Count the total number of tracks by each artist.
```
select
artist,
count(track) as count_track
from spotify
group by 1
order by 2 desc
```
🟡 Intermediate Level Analysis
7. Average danceability per album
```
SELECT album, AVG(danceability) AS avg_danceability
FROM spotify
GROUP BY album;
```
8. Top 5 highest energy tracks
```
SELECT track, MAX(energy) AS energy
FROM spotify
GROUP BY track
ORDER BY energy DESC
LIMIT 5;
```
9.List all tracks along with their views and likes where official_video = TRUE.
```
select
track,
sum(viewss)as sum_view,
sum(likes) as sum_like,
official_video
from spotify
where official_video = 'true'
group by 1,4
```
10.For each album, calculate the total views of all associated tracks.
```
select
album,
track,
sum(viewss) as sum_view
from spotify
group by 1,2
order by 3 desc
```
🔴 Advanced Level Analysis
11. Top 3 most viewed tracks per artist
```
select*from
(select
artist,
track,
sum(viewss),
dense_rank() over(partition by artist order by sum(viewss) desc)as ranking
from spotify
group by 1,2)
where ranking <= 3
```
12.Write a query to find tracks where the liveness score is above the average.
```select 
track,
liveness
from spotify
where liveness > (select avg(liveness) from spotify)
group by 1,2
order by 2
````
13.Use a WITH clause to calculate the difference between the highest and lowest energy values for tracks in each album.
```
with energy_1
as
(select
track,
album,
max(energy) as highest_energy,
min(energy) as lowest_energy
from spotify
group by 1,2)

select
album,
highest_energy - lowest_energy as energy_difference
from energy_1
order by 2 desc
```

📊 Key Business Insights
.🎵 High-energy tracks dominate top-performing content
.📈 Some artists consistently outperform across all engagement metrics
.🎥 Official videos significantly boost views & likes
.📱 Platform comparison reveals Spotify vs YouTube consumption behavior
.🔍 Engagement ≠ popularity → deeper metrics matter

🚀 Skills Demonstrated
.SQL Fundamentals (Filtering, Aggregations)
.Intermediate SQL (GROUP BY, CASE WHEN, Subqueries)
.Advanced SQL (CTEs, Window Functions, Ranking)
.Exploratory Data Analysis (EDA)
.Business-Oriented Thinking

📁 Project Structure
```
spotify-sql-project/
│
├── schema.sql
├── eda.sql
├── beginner.sql
├── intermediate.sql
├── advanced.sql
└── README.md
```



