# 🎬 Movie Recommendation System using NLP and Cosine Similarity

This project builds a **content-based movie recommender** using **natural language processing (NLP)** techniques and **cosine similarity** on movie metadata. The system recommends movies similar to a selected title by analyzing genres, cast, crew, and keywords.

<br />

---

## 📂 Datasets Used

- [`tmdb_5000_movies.csv`](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- [`tmdb_5000_credits.csv`](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

These files contain detailed metadata from TMDB including movie genres, overviews, cast, crew, and keywords.

<br />

---

## 🔄 Data Loading & Preprocessing

### 1. **Load and Explore Datasets**
- Two datasets are loaded: one for movie details, one for credit information.
- Initial inspection includes `.head()` and `.shape()` to understand structure.

### 2. **Merge Datasets**
- DataFrames are merged on the movie `title` column to unify features from both files.

### 3. **Data Cleaning**
- Missing values are dropped.
- Duplicate entries are checked and reported.

<br />

---

## 🔍 Feature Engineering

### 4. **Extracting Nested Data**
- The `genres`, `keywords`, `cast`, and `crew` columns contain nested JSON structures.
- These strings are parsed using `ast.literal_eval`, and relevant `name` fields are extracted into lists.

### 5. **Text Preprocessing**
- The `overview` is tokenized (split into words).
- All text features (`genres`, `cast`, `crew`, `keywords`) are cleaned to remove spaces for consistent vectorization.
- All relevant features are **combined into a single `tag` column**, which serves as the basis for recommendation.

<br />

---

## 🧠 Model Preparation

### 6. **Vectorization**
- `CountVectorizer` is used to convert the `tag` text data into numerical vectors.
- It captures the **top 5000 features**, excluding standard English stop words.

### 7. **Similarity Calculation**
- **Cosine similarity** is used to measure similarity between the vector representations of each movie.
- This matrix stores pairwise similarities between all movies.

<br />

---

## 🎯 Recommendation Function

### 8. **Recommender Logic**
- A recommendation function takes a movie title as input.
- It:
  - Finds the index of the input movie.
  - Calculates similarity with all other movies.
  - Sorts them in descending order of similarity.
  - Returns the top 5 most similar movies (excluding the input itself).

<br />

---

## ✅ Example Output

If you input:

```
recommend('Batman Begins')
```

The system will return 5 movies that share similar metadata characteristics with *Batman Begins*.

<br />

---

## 📦 Technologies Used

- **Pandas & NumPy** – data manipulation.
- **AST** – parsing JSON-like strings.
- **Scikit-learn** – vectorization (`CountVectorizer`) and similarity computation (`cosine_similarity`).

<br />

---

## 📌 Limitations

- Based only on textual metadata (no ratings, popularity, or viewing behavior).
- Doesn't account for time-based relevance or new releases.
- Case-sensitive movie input—recommend wrapping it in a search dropdown or autocomplete for UX.

<br />

---

## 📈 Possible Improvements

- Switch to **TF-IDF vectorization** for more nuanced term weighting.
- Incorporate **collaborative filtering** for hybrid recommendations.
- Add a **web interface** using Streamlit or Flask.

<br />

---

## 🙌 Acknowledgements

- Data sourced from [The Movie Database (TMDB)](https://www.themoviedb.org/)
- Based on a popular [Kaggle notebook](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

<br />

---

## 🚀 Run It Yourself

You can run this project in any Jupyter Notebook environment or convert it to a script. Just ensure the CSV files are in the same directory and dependencies are installed.

<br />

---

