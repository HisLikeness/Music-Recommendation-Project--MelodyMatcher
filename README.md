# Music-Recommendation-Project--MelodyMatcher
A music recommendation algorithm that leverages the Spotify dataset to suggest music based on user preferences and music attributes. The goal of this project is to provide song recommendations by clustering tracks based on musical features such as acousticness, danceability, energy, and more. By analyzing trends and grouping tracks with similar characteristics, the system offers curated suggestions to users.

## Project Overview
This project aims to develop a music recommendation algorithm leveraging the Spotify dataset. The key stages include:
1. **Data Loading and Exploration**: Understanding the structure of the dataset.
2. **Exploratory Data Analysis (EDA)**: Identifying trends, visualizing genres and artists, and analyzing sound features over decades.
3. **Clustering Techniques**: Grouping songs and genres based on their characteristics.
4. **Recommendation System Development**: Implementing a system to suggest similar songs using song features and the Spotify API.

### Step 1: Data Loading and Exploration- This stage of the project focuses on loading and exploring the Spotify dataset. This phase is foundational for understanding the structure and contents of the data, which will be crucial for subsequent analysis and development of the recommendation algorithm.
#### Objectives
- Load the Spotify dataset into a Python environment.
- Explore the structure and contents of the dataset to prepare for further analysis.

#### Datasets Used
- `data.csv`: Contains general song-level data.
- `data_by_genres.csv`: Aggregates data by genres.
- `data_by_year.csv`: Provides yearly trends in song features.
- `data_by_artist.csv`: Contains artist-level information.

1. **Imported Necessary Libraries**: 
   ```python
   import numpy as np
   import pandas as pd
   ```

2. **Loaded the Datasets**: 
   Used `pd.read_csv()` to load the datasets into pandas DataFrames.
   ```python
   data = pd.read_csv("Final Project Datasets - Spotify\\data.csv")
   genre_data = pd.read_csv("Final Project Datasets - Spotify\\data_by_genres.csv")
   year_data = pd.read_csv("Final Project Datasets - Spotify\\data_by_year.csv")
   artist_data = pd.read_csv("Final Project Datasets - Spotify\\data_by_artist.csv")
   ```
3. **Explored Data Structure**: 
   - Examined the first few rows of each dataset using `.head()`.
   - Checked the shape and column names of the datasets.
     
#### Observations
- The `data.csv` file contains detailed song-level features such as tempo, energy, and popularity.
- The `data_by_genres.csv` and `data_by_year.csv` files provide aggregated insights, useful for trend analysis.
- The `data_by_artist.csv` file focuses on artist-level information.


### Step 2 - Exploration Data Analysis
The primary objective of this stage is to uncover trends in sound features, examine the popularity of top genres and artists, and visualize the dataset using various plots and word clouds.
#### Tasks performed include:
#### 1. Visualize the Distribution of Tracks Across Decades
- **Plot Used:** Count Plot
- **Code:**
  ```python
  sns.countplot(data['decade'])
  ```
- This visualization provides an overview of how tracks are distributed across decades.

#### 2. Plot Trends of Sound Features Over Decades
- **Sound Features Analyzed:**
  - Acousticness
  - Danceability
  - Energy
  - Instrumentalness
  - Liveness
  - Valence
- **Plot Used:** Line Plot
- **Code:**
  ```python
  px.line(year_data, x='year', y=sound_features, title='Trend of various sound features over decades')
  ```
- This plot showcases how the selected sound features have evolved over time.

#### 3. Plot Trend of Loudness Over Decades
- **Plot Used:** Line Plot
- **Code:**
  ```python
  px.line(year_data, x='year', y='loudness', title='Trend of loudness over decades')
  ```
- This visualization illustrates changes in loudness across decades.

#### 4. Analyze Top 10 Genres Based on Popularity
- **Analysis Performed:**
  - Identified top 10 genres based on popularity.
  - Plotted trends of key sound features (valence, energy, danceability, acousticness) for these genres.
- **Plot Used:** Grouped Bar Chart
- **Code:**
  ```python
  px.bar(top10_genres, x='genres', y=['valence', 'energy', 'danceability', 'acousticness'], barmode='group', title='Trend of various sound features over top 10 genres')
  ```

#### 5. Generate Word Cloud for Genres
- **Library Used:** WordCloud
- **Code:**
  ```python
  WordCloud(width=800, height=800, background_color='white', stopwords=stopwords, max_words=40, min_font_size=10).generate(comment_words)
  ```
- **Visualization:**
  ```python
  plt.imshow(wordcloud)
  ```
- This visualization highlights the most frequent genres in the dataset.

#### 6. Generate Word Cloud for Artists
- **Library Used:** WordCloud
- **Code:**
  ```python
  WordCloud(width=800, height=800, background_color='white', stopwords=stopwords, min_word_length=3, max_words=40, min_font_size=10).generate(comment_words)
  ```
- **Visualization:**
  ```python
  plt.imshow(wordcloud)
  ```
- This visualization highlights the most frequent artists in the dataset.

#### 7. Identify Top 10 Artists with the Most Songs Produced
- **Analysis Performed:**
  - Displayed the count and names of the top 10 artists with the highest number of songs produced.
- **Code:**
  ```python
  top10_most_song_produced_artists[['count','artists']].sort_values('count', ascending=False)
  ```

#### 8. Identify Top 10 Artists with the Highest Popularity Score
- **Analysis Performed:**
  - Displayed the popularity score and names of the top 10 most popular artists.
- **Code:**
  ```python
  top10_popular_artists[['popularity','artists']].sort_values('popularity', ascending=False)
  ```
#### Outcomes
- Trends in sound features and loudness over decades were identified and visualized.
- The most popular genres and their sound characteristics were analyzed.
- Word clouds provided a clear representation of prominent genres and artists.
- Insights into the most prolific and popular artists were gathered.

#### Tools and Libraries Used
- **Visualization:** Seaborn, Plotly Express, Matplotlib,
- **Text Analysis:** WordCloud
- **Data Handling:** Pandas, NumPy

This project stage laid a strong foundation for understanding the dataset and preparing for the clustering and recommendation system implementation in the subsequent phases.

### Step 3: Clustering 
The clustering phase is a critical part of the recommendation system, enabling the grouping of similar tracks based on their characteristics.

#### **Methodology**
The techniques used for the groupings include:
1. **Text Feature Combination:**
   - Combined `artist`, `song`, and `lyrics/text` columns to create a comprehensive textual feature.
2. **Vectorization:**
   - Used `TfidfVectorizer` to transform the text data into numerical format, capturing the importance of terms.
3. **Scaling:**
   - Applied `MaxAbsScaler` to handle sparse data efficiently.
4. **K-Means Clustering:**
   - Clustered tracks into 25 groups using `KMeans` with `k-means++` initialization to optimize convergence.
   - Each cluster represents a group of songs sharing similar textual and musical attributes.

#### **Cluster Analysis** includes:
- **Cluster Composition:** Identified songs in each cluster and analyzed the themes and common features.
- **Cluster Trends:** Analyzed the distribution of clusters across decades and genres to understand underlying patterns.

#### Dimensionality Reduction and Visualization
To visualize high-dimensional song data and clusters, the following were used:
1. **Principal Component Analysis (PCA):** Reduced the dimensions of the data to two components.
2. **Scatter Plot Visualization:** Used `Plotly Express` to plot clusters, with hover data showing song and artist information.

#### **Key Findings:**
The first issue encountered in this phase was trying to use the Label encoder and One encoder to transform the all-text song dataset so that it could be fed into the K-Means clustering algorithm but this failed due to the high dimensionality of the dataset which led to using the TfidfVectorizer to convert the text data into numerical vectors, which could be used by the K-Means algorithm. This allowed us to extract features from the text data and perform clustering.

There was also a Memory issue while trying to implement the PCA because the vectorized_text_data ( a large sparse matrix) was used. This indicated that for the PCA to function properly the scaled data transformation should be used which will resolve any potential memory issue.

However, after tackling the challenges and python code produced the desired scatterplots for Music Genres and Songs that show,
- Clear separation of clusters based on textual and musical attributes.
- Insights into dominant genres and trends within clusters.


### Step 4: Recommendation System Phase
This project implements a music recommendation system using natural language processing (NLP) and collaborative filtering techniques. The system takes in a list of songs and returns a list of recommended songs based on their audio features and user preferences.

#### Features
- Song Embeddings: The system uses song embeddings to represent songs as vectors in a high-dimensional space. These embeddings are trained using a combination of audio features and user ratings.
- Collaborative Filtering: The system uses collaborative filtering to identify patterns in user behavior and recommend songs that are likely to be of interest to a particular user.
- Natural Language Processing: The system uses NLP techniques to analyze song lyrics and metadata, and to identify songs that are similar in terms of theme, mood, and style.

#### Requirements
- Python 3.8+: The system is implemented in Python 3.8+ and requires a working Python installation to run.
- Spotify API Credentials: The system requires a set of Spotify API credentials to access song metadata and audio features. These credentials can be obtained by creating a Spotify Developer account and registering an application.

#### Installation
1. Clone the repository using git: git clone https://github.com/your-username/recommendation-system.git
2. Install the required libraries using pip: pip install -r requirements.txt
3. Set up your Spotify API credentials by creating a credentials.json file in the root directory of the project. This file should contain your client ID and client secret in the following format:
```
```
{
"client_id": "your-client-id",
"client_secret": "your-client-secret"
}

4.  Run the system using Python: `python recommendation_system.py`

## Usage
-----

1.  Create a list of songs that you want to use as input for the recommendation system. This list should be in the following format:  
[
{"name": "Song 1", "artist": "Artist 1"},
{"name": "Song 2", "artist": "Artist 2"},
...
]

2. Pass this list to the `recommend_songs` function to get a list of recommended songs. This function takes in two arguments: the list of input songs and the number of recommended songs to return.
3. The `recommend_songs` function returns a list of recommended songs in the following format
[
{"name": "Recommended Song 1", "artist": "Recommended Artist 1"},
{"name": "Recommended Song 2", "artist": "Recommended Artist 2"},
...
]

4.  You can then use this list of recommended songs as you see fit. For example, you could use it to create a playlist or to recommend songs to a user.

## Dependencies
Ensure the following Python libraries are installed:
- `numpy`
- `pandas`
-  Matplotlib
- Seaborn
- WordCloud
- Plotly
- scikit-learn
- spotipy

## How to Run the Project
1. Clone the repository or download the project files.
2. Place the dataset files in the specified directory.
3. Install required dependencies.
4. Run the provided notebook step by step to reproduce the clustering and visualization results.
5. Execute the notebook using Jupyter Notebook or any Python environment.

## Future Improvements
1. **Enhanced Clustering Techniques:** Experiment with hierarchical clustering and DBSCAN for better results.
2. **Real-Time Recommendations:** Integrate with the Spotify API for live user preferences.
3. **Feature Engineering:** Incorporate additional metadata and audio features to improve clustering accuracy.

---

This project demonstrates the power of clustering in understanding musical trends and enhancing user experience through personalized recommendations.

---
