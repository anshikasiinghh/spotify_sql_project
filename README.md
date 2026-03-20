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
</> SQL
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

🧱 Database Setup
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
🎯 Business Questions Solved

This project answers 15 real-world analytical questions categorized into three levels:

🟢 Beginner Level (SQL Fundamentals)

