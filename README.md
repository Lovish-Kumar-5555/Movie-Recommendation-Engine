# Movie Recommendation Engine

This repository contains the teaching materials for building a simple **content-based movie recommendation engine**. It demonstrates how to convert rich movie metadata into a bag-of-words representation and surface similar titles with cosine similarity. The assets include hands-on notebooks, starter and completed Python scripts, as well as the movie metadata dataset used throughout the exercises.

## Project Overview

The workflow showcased in the notebooks and scripts walks through the following steps:

1. Load the provided dataset of 4,800+ popular movies released between 1980–2017.
2. Select descriptive features such as keywords, cast, genres, and director for each movie.
3. Merge the selected features into a single text document per title.
4. Transform the combined text using a `CountVectorizer` bag-of-words model.
5. Compute cosine similarity scores to retrieve the closest movies to a user-specified title.

The approach is intentionally lightweight, relying solely on movie metadata to keep the focus on the mechanics of feature engineering and similarity search.

## Repository Contents

| Path | Description |
| --- | --- |
| `Movie_Recommendation_Engine.ipynb` | Step-by-step tutorial notebook that explains the entire recommendation pipeline, including exploratory analysis and debugging tips. |
| `Assignment Solution.ipynb` | Complete, worked solution to the practice assignment for quick reference or self-checking. |
| `assignment.pdf` & `Building_A_Movie_Recommendation_Engine.pdf` | Lecture slides and assignment brief summarizing the learning objectives. |
| `movie_dataset.csv` | Primary dataset with metadata fields such as genres, keywords, cast members, director names, plot overview, production details, and vote statistics. |
| `movie_recommender_starter.py` | Skeleton script with clearly labelled TODO steps for learners who want to implement the recommender from scratch. |
| `movie_recommender_completed.py` | Fully implemented reference solution that can be executed from the command line to print the 50 closest matches to a chosen movie. |
| `cosine_similarity.py` | Minimal example that demonstrates how `CountVectorizer` and `cosine_similarity` work on a tiny synthetic corpus. |

## Dataset Notes

The dataset is a curated snapshot of movie metadata derived from The Movie Database (TMDb). Each row describes a single film with the following relevant columns for the recommender:

- **title**: Human-readable movie name.
- **keywords**: Important concepts or themes extracted from TMDb keywords.
- **cast**: Top-billed performers, delimited by spaces.
- **genres**: Genre labels provided by TMDb (e.g., *Action*, *Adventure*, *Sci-Fi*).
- **director**: Director of the film.

Additional columns include budget, revenue, runtime, release date, vote statistics, plot overview, production companies, and more, which you can use to experiment with alternative feature sets. Sample records for the first three movies (Avatar, Pirates of the Caribbean: At World's End, Spectre) are included in the repository inspection script shown above.

## Getting Started

### Prerequisites

- Python 3.8 or newer (Python 2 syntax appears in the legacy scripts; see the note below if you plan to run them unmodified).
- Recommended packages: `pandas`, `numpy`, `scikit-learn`, and `jupyter`.
- Optional: `virtualenv` or `conda` for isolated environments.

> **Python 2 compatibility note:** The reference scripts use the original course syntax with Python 2-style `print` statements. To execute them with Python 3 you will need to wrap those `print` statements in parentheses (or run them inside a Python 2 interpreter).

### Setup

1. Clone or download this repository.
2. Create and activate a virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn jupyter
   ```

### Running the Tutorial Notebook

1. Launch Jupyter Notebook or JupyterLab:
   ```bash
   jupyter notebook
   ```
2. Open `Movie_Recommendation_Engine.ipynb` and run the cells sequentially to follow the guided tutorial. The notebook mirrors the logic in the completed script while providing narrative explanations and visual aids.

### Executing the Completed Script

1. Ensure you have updated the `print` statements for Python 3 if necessary (see the compatibility note above).
2. Run the script from the repository root:
   ```bash
   python movie_recommender_completed.py
   ```
3. Update the `movie_user_likes` variable near the end of the script to experiment with different seed movies. The program will output the top 50 recommendations ranked by cosine similarity.

### Practicing with the Starter Script

The `movie_recommender_starter.py` file outlines each step of the workflow with placeholders so you can implement the logic yourself. Consult the completed script or the notebook if you get stuck. This is ideal for classroom exercises or self-paced practice.

## Extending the Project

Once you are comfortable with the baseline recommender, consider experimenting with the following enhancements:

- **TF-IDF weighting:** Replace the `CountVectorizer` with `TfidfVectorizer` to downweight ubiquitous terms.
- **Hybrid features:** Incorporate numerical attributes such as vote average, runtime, or release year to influence similarity scores.
- **Alternative similarity metrics:** Try cosine similarity on TF-IDF vectors, Euclidean distance on normalized numeric features, or even approximate nearest neighbour search libraries for scalability.
- **User interface:** Wrap the recommender logic in a simple web app or command-line interface that accepts user input dynamically.

## Attribution

The teaching materials were originally published by Code Heroku as part of their Introduction to Machine Learning curriculum. The dataset and slides are included here for educational purposes.

