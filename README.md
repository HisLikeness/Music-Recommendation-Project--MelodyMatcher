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

#### Steps Completed
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

### Next Steps
- Perform exploratory data analysis (EDA) to:
  - Analyze trends in sound features over decades.
  - Examine the popularity of top genres and artists.
  - Visualize the dataset using tools like word clouds.
- Begin clustering to group similar songs and genres.

### Dependencies
Ensure the following Python libraries are installed:
- `numpy`
- `pandas`

## How to Run
1. Clone the repository or download the project files.
2. Place the dataset files in the specified directory.
3. Execute the notebook using Jupyter Notebook or any Python environment.

---
