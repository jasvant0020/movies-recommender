Movie Recommendation System

A content-based movie recommendation system built using Python and Machine Learning techniques. The system recommends movies based on similarities in their metadata such as overview, genres, keywords, cast, and director.

Project Overview

This project uses the TMDB 5000 Movies and TMDB 5000 Credits datasets to build a movie recommendation system.

The project follows a complete data preprocessing and text-based recommendation workflow:

- Load and inspect movie and credits datasets
- Merge datasets using movie titles
- Select relevant movie information
- Handle missing and duplicate values
- Extract genres, keywords, cast, and director information
- Combine movie information into a single "tags" feature
- Apply text preprocessing and stemming
- Convert text into numerical features using "CountVectorizer"
- Calculate movie similarity using cosine similarity

Dataset

The project uses:

- "tmdb_5000_movies.csv"
- "tmdb_5000_credits.csv"

Important information used from the datasets includes:

- Movie ID
- Movie title
- Movie overview
- Genres
- Keywords
- Cast
- Director

Workflow

1. Load the datasets

The movies and credits datasets are loaded using Pandas.

2. Merge datasets

The two datasets are merged using the "title" column.

3. Select relevant features

Only the following columns are retained:

movie_id
title
overview
genres
keywords
cast
crew

4. Data preprocessing

The dataset is checked for:

- Missing values
- Duplicate records

Rows containing missing values and duplicate records are removed.

5. Extract useful information

The nested JSON-like data in the "genres", "keywords", "cast", and "crew" columns is processed using Python's "ast" module.

The system extracts:

- Genre names
- Keyword names
- Top 3 cast members
- Director name

6. Create movie tags

The extracted information is combined with the movie overview into a single "tags" feature.

overview + genres + keywords + cast + director

This creates a combined textual representation of each movie.

7. Text preprocessing

The tags are:

- Converted into strings
- Converted to lowercase
- Stemmed using NLTK's Porter Stemmer

Stemming helps reduce related words to their root form.

8. Text vectorization

"CountVectorizer" from Scikit-learn converts the movie tags into numerical feature vectors.

The project uses:

CountVectorizer(
    max_features=5000,
    stop_words='english'
)

This produces a numerical representation of the movie metadata.

9. Cosine similarity

Cosine similarity is calculated between the movie vectors using Scikit-learn.

Movies with more similar feature vectors have higher similarity scores.

Technologies Used

- Python
- NumPy
- Pandas
- Scikit-learn
- NLTK
- Ast
- Jupyter Notebook

Machine Learning Concepts Used

- Data preprocessing
- Feature selection
- Feature extraction
- Text preprocessing
- Stemming
- Text vectorization
- Count Vectorization
- Cosine similarity
- Content-based recommendation

Project Structure

    movies_recommander/
    │
    ├── notebook.ipynb
    ├── tmdb_5000_movies/
    │   └── tmdb_5000_movies.csv
    │
    ├── tmdb_5000_credits/
    │   └── tmdb_5000_credits.csv
    │
    └── README.md

Future Improvements

Possible improvements for the project include:

- Build a recommendation function that accepts a movie title and returns similar movies.
- Create a user-friendly web interface.
- Deploy the recommendation system as a web application.
- Experiment with TF-IDF or other text representation techniques.
- Improve recommendations using additional movie features.
