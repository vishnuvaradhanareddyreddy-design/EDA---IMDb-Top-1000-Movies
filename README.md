# IMDb Top 1000 Movies Exploratory Data Analysis 🎬📊

This project contains a documented Jupyter notebook for **CSB314 - Exploratory Data Analysis**, Minor Project 02 (CA 03). It explores the supplied `imdb_top_1000.csv` file, checks its data quality, creates analysis features, summarizes ratings and genres, and demonstrates the statistical methods listed in the assignment.

The file is a selected list of 1,000 highly rated movies. Results describe this file and should not be treated as findings about every movie.

## 📁 Project files

| File | Description |
| --- | --- |
| `imdb_top_1000_eda.ipynb` | Main notebook with detailed Markdown explanations, code, generated tables and plots, observations, and conclusions. |
| `imdb_top_1000.csv` | Movie dataset used by the notebook. Keep it beside the notebook. |

## 🎯 Project objectives

- Understand the table structure and check the movie-title key.
- Report missing values, parsing issues, and invalid values.
- Create features from release year, runtime, genres, votes, and gross.
- Summarize ratings and movie counts by genre and decade.
- Demonstrate grouping, aggregation, transformation, pivot tables, crosstabs, and reshaping.
- Apply descriptive statistics, distribution analysis, sampling, correlation, and outlier methods.
- Explain the limits of a selected top-1000 movie list.

## 🗃️ Dataset description

The supplied file contains 1,000 rows and 16 columns, including:

| Column | Description |
| --- | --- |
| `Series_Title` | Movie title used as the row identifier in this file. |
| `Released_Year` | Release year stored as text in the source. |
| `Certificate` | Movie certificate or content rating, with some missing values. |
| `Runtime` | Runtime stored as text with the `min` suffix. |
| `Genre` | One or more comma-separated genre labels. |
| `IMDB_Rating` | IMDb rating recorded in this dataset snapshot. |
| `Meta_score` | Metascore, with some missing values. |
| `Director`, `Star1`-`Star4` | Director and cast fields. |
| `No_of_Votes` | Vote count recorded in the snapshot. |
| `Gross` | Gross amount stored as text with comma separators. |
| `Overview`, `Poster_Link` | Movie description and poster URL. |

The file name and columns match a commonly distributed Kaggle dataset, [IMDb Dataset of Top 1000 Movies and TV Shows](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows). The exact provenance and licence were not included with the supplied CSV. Check the source page and licence details before redistributing it.

## ⚙️ Requirements

Use Python 3 with Jupyter Notebook, JupyterLab, or VS Code. The notebook uses Pandas, NumPy, Matplotlib, and Seaborn.

```bash
python -m pip install pandas numpy matplotlib seaborn jupyter
```

## ▶️ How to run

1. Keep `imdb_top_1000_eda.ipynb` and `imdb_top_1000.csv` in the same folder.
2. Open the notebook in Jupyter Notebook, JupyterLab, or VS Code.
3. Select a Python 3 kernel.
4. Run all cells from top to bottom.

The notebook uses a relative path for the CSV and does not rely on a computer-specific folder.

## 🧮 Derived features

The notebook creates the following features in a working copy, leaving the original file unchanged:

| Feature | Formula | Purpose and note |
| --- | --- | --- |
| `release_year_numeric` | Convert `Released_Year` to a number | Supports year summaries; unparseable source values remain missing. |
| `runtime_minutes` | Remove ` min` and convert to number | Supports runtime summaries. |
| `gross_amount` | Remove commas and convert to number | Parses the source `Gross` field; currency and reporting basis are not inferred. |
| `genre_count` | Count comma-separated genre labels | Describes the number of genre labels for a movie. |
| `primary_genre` | First listed genre | Provides one group per movie for selected summaries. |
| `release_decade` | Round release year down to its decade | Supports decade comparisons. |
| `log_vote_count` | `log10(No_of_Votes + 1)` | Helps display the highly skewed vote-count scale. |

## 📚 Notebook sections

1. Problem and objectives
2. Dataset source and description
3. Import libraries and load data
4. Dataset understanding and row grain
5. Data quality assessment
6. Feature engineering
7. Grouping, aggregation, and transformation
8. Pivot table and crosstab
9. Data reshaping
10. Data integration and join checks
11. Descriptive statistics
12. Distribution analysis
13. Empirical rule demonstration
14. Sampling and the Central Limit Theorem
15. Correlation and relationship analysis
16. Outlier detection and treatment
17. Findings, limitations, and future scope
18. Conclusion

## 📈 Interpretation notes

- The `Released_Year` value for *Apollo 13* is malformed in the supplied file. It is left missing after parsing rather than being manually corrected.
- Certificate, Metascore, and Gross contain missing values; these are not filled with invented values.
- `Gross` is parsed numerically, but the supplied file does not establish its currency or reporting basis in the notebook.
- A movie can have more than one genre. Genre-exploded data can contain multiple rows per movie, so distinct movie counts are used where appropriate.
- Primary-genre summaries use the first genre listed in the source field. This is a grouping choice, not a claim that it is the only genre for the movie.
- The empirical-rule and distribution-shape examples are simulated and labelled. They are not IMDb observations.
- Correlation shows association and does not prove cause and effect.
- The notebook demonstrates joins only with a summary derived from the same file because no second raw table was supplied.

## ⚠️ Limitations

This is a selected top-1000 list rather than a random sample of movies. The results cannot be generalized to all films. Rankings and metadata may have changed since the dataset snapshot was collected. Missing values, the malformed year, multi-valued genres, and unverified Gross units also limit interpretation.

## 🔗 Source and licence

Potential matching source page: [IMDb Dataset of Top 1000 Movies and TV Shows - Kaggle](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows).

No separate licence file was supplied with this CSV. Confirm that the source page corresponds to this exact file and review its current usage terms before sharing or redistributing the data.
