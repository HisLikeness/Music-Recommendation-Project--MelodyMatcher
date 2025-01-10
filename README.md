# Music-Recommendation-Project--MelodyMatcher
A music recommendation algorithm that leverages the Spotify dataset to suggest music based on user preferences and music attributes.

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

#### Step 1 - Data Loading and Exploration
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
# Exploratory Data Analysis (EDA) on Spotify Dataset
The primary objective of this stage is to uncover trends in sound features, examine the popularity of top genres and artists, and visualize the dataset using various plots and word clouds.
#### Tasks performed include:
#### 1. Visualize the Distribution of Tracks Across Decades
- **Plot Used:** Count Plot
- **Code:**
  ```python
  sns.countplot(data['decade'])
  ```
- This visualization provides an overview of how tracks are distributed across different decades.

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

This project stage lays a strong foundation for understanding the dataset and prepares for the clustering and recommendation system implementation in the subsequent phases.

### Step 3: Clustering (Focus)
The core of the project lies in grouping similar songs based on audio features. Key highlights include:

#### 1. Feature Selection:
- Choosing relevant features for clustering: tempo, energy, danceability, valence, instrumentalness, etc.
- Normalizing features to ensure uniformity in clustering.

#### 2. Modeling:
- Applying K-Means clustering to partition genre and songs into distinct groups.
- Optimizing the number of clusters using techniques like the elbow method.

#### 3. Cluster Visualization:
- Visualizing clusters in 2D or 3D feature space to understand song groupings.
-  Identifying genre and artist concentration within clusters.

### Next Steps
- Cluster Analysis
- Cluster-Based Recommendation
- use the Spotify dataset and implement a recommendation system using song features.

### Dependencies
Ensure the following Python libraries are installed:
- `numpy`
- `pandas`
-  Matplotlib
- Seaborn
- WordCloud
- Plotly
- scikit-learn
- spotipy


## How to Run
1. Clone the repository or download the project files.
2. Place the dataset files in the specified directory.
3. Execute the notebook using Jupyter Notebook or any Python environment.

---
