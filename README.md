# MovieLens-Dataset-Exploratory-Data-Analysis

This project focuses on data preparation, feature engineering, and exploratory data analysis (EDA) of the MovieLens dataset. The primary goal is to clean and enrich the data to uncover insights and prepare a dataset that could support a future recommendation system.

## Project Objective

To demonstrate proficiency in data wrangling and analysis by:
1.  **Preparing** and cleaning a real-world dataset.
2.  **Engineering** at least 6 new, useful features from the raw data.
3.  **Analyzing** the dataset to find at least 6 meaningful insights.
4.  **Reporting** on the findings and their relevance for a recommendation system.

---

## Dataset

The project uses a subset of the **MovieLens dataset** from the [GroupLens research group](httpss://grouplens.org/datasets/movielens/), which includes:

* `movies.csv`: Contains `movieId`, `title`, and `genres`.
* `ratings.csv`: Contains `userId`, `movieId`, `rating`, and `timestamp`.
* `tags.csv`: Contains user-generated tags for movies.
* `links.csv`: Contains links to external movie databases (IMDb, TMDb).

---

## Project Workflow

1.  **Data Preparation:**
    * Loaded `movies.csv` and `ratings.csv` into Pandas DataFrames.
    * Merged the two datasets on `movieId` to create a unified DataFrame.
    * Checked for and handled missing values.
    * Converted the Unix `timestamp` column into a readable `datetime` format.

2.  **Feature Engineering:**
    * Created several new features to add depth to the dataset.
    * The goal was to create variables that could explain *why* a user might like a movie.

3.  **Exploratory Data Analysis (EDA):**
    * Used the original and new features to ask questions about the data.
    * Visualizations (histograms, bar charts, etc.) were created using Matplotlib and Seaborn to identify trends and patterns.

---

## Key Features Created

Here are some of the new features engineered for this analysis:

* `**release_year**`: Extracted the 4-digit year from the `title` string (e.g., "Toy Story (1995)" $\to$ 1995) to analyze trends over time.
* `**primary_genre**`: Isolated the *first* genre listed (e.g., "Action|Adventure|Sci-Fi" $\to$ "Action") to simplify genre-based analysis.
* `**genre_count**`: Counted the total number of genres for each movie (e.g., "Action|Adventure|Sci-Fi" $\to$ 3).
* `**movie_avg_rating**`: Calculated the mean rating for each unique movie. This is a key indicator of movie quality/popularity.
* `**movie_rating_count**`: Counted the total number of ratings each movie received. This acts as a "confidence" score for the `movie_avg_rating`.
* `**user_avg_rating**`: Calculated the mean rating given by each unique user. This helps identify "tough critics" vs. "easy raters."

---

Here’s a **concise version of the key insights**, written in a clean, professional style suitable for your **GitHub README.md** file:

---

## 🔍 Key Insights from EDA

1. **Ratings Skew Positive:**
   Most ratings fall between 3 and 4, indicating users generally rate movies favorably.

2. **Few Movies Dominate Ratings:**
   Popular titles like *Forrest Gump* and *The Shawshank Redemption* receive disproportionately high numbers of ratings.

3. **Users Are Moderate Raters:**
   Average user ratings center around 3.5, showing balanced and consistent rating behavior.

4. **High-Rated Genres:**
   *Film-Noir*, *Mystery*, *Crime*, and *Documentary* movies receive the highest average ratings.

5. **Popular Genres:**
   *Action*, *Drama*, and *Comedy* dominate by number of ratings, reflecting mainstream audience preferences.

6. **Release Year Trends:**
   1994–1995 mark peak years for movie releases in the dataset, reflecting a surge in popular titles.

7. **Genre Diversity Correlation:**
   Movies with more genres tend to have slightly higher ratings, suggesting broader audience appeal.


---

## How These Features Support a Recommendation System

* **Content-Based Filtering:** Features like `primary_genre`, `release_year`, and `genre_count` are perfect for this. If a user likes a movie with the "Action" genre from the 1990s, we can recommend other, similar movies.
* **Collaborative Filtering:** Features like `user_avg_rating` and `movie_avg_rating` are essential for normalizing data. A 4-star rating from a "tough critic" (avg 2.5 stars) should be weighted more heavily than a 4-star rating from someone who gives 4+ stars to everything.
* **Building a "Top N" List:** `movie_avg_rating` and `movie_rating_count` are used to build reliable "Top 10" lists, filtering out movies with high scores but very few reviews.

---

## Tools and Libraries Used

* **Python 3.x**
* **Pandas:** For data manipulation and analysis.
* **NumPy:** For numerical operations.
* **Matplotlib & Seaborn:** For data visualization.
* **Jupyter Notebook:** As the development environment.

## Repository Contents

* `MovieLens_Analysis.ipynb`: The main Jupyter Notebook containing all Python code, analysis, and visualizations.
* `Analysis_Report.pdf`: A 6-page summary report of the features, insights, and recommendations.
* `cleaned_feature_engineered_movies_ratings.csv`: The final, cleaned dataset with all new features.
* `data/` (directory): Contains the original raw `.csv` files from MovieLens (e.g., `movies.csv`, `ratings.csv`).
