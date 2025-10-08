# 📁 Data README

## Overview
This folder contains **CSV snapshots** of the original PostgreSQL tables used in the analysis.  
They are small, versioned files intended for **reproducible** execution of the notebook without database access.

- Location: `data/samples/`
- Consumers: `notebooks/Project_14C_SQL.ipynb` (Section 2 builds an in-memory SQLite DB from these CSVs)

## Source & licence
- **Source:** educational dataset provided during the **TripleTen Data Analytics Bootcamp**.
- **Licence/Usage:** for **educational and portfolio** purposes. No personal data (PII) is included.

## Files
| File | Rows (approx.) | Description |
|---|---:|---|
| `books.csv` | ~1,000 | Book catalogue with author and publisher references. |
| `authors.csv` | ~636 | Author dictionary. |
| `publishers.csv` | ~340 | Publisher dictionary. |
| `ratings.csv` | ~6,456 | User star ratings for books. |
| `reviews.csv` | ~2,793 | Free-text user reviews for books. |

> Row counts are indicative and may vary slightly depending on the snapshot.

## Schemas
**books.csv**
- `book_id` (int) — primary key  
- `author_id` (int) — FK → `authors.author_id`  
- `title` (str)  
- `num_pages` (int)  
- `publication_date` (YYYY-MM-DD)  
- `publisher_id` (int) — FK → `publishers.publisher_id`

**authors.csv**
- `author_id` (int) — primary key  
- `author` (str)

**publishers.csv**
- `publisher_id` (int) — primary key  
- `publisher` (str)

**ratings.csv**
- `rating_id` (int) — primary key  
- `book_id` (int) — FK → `books.book_id`  
- `username` (str) — pseudonymous handle  
- `rating` (int) — typically 1–5

**reviews.csv**
- `review_id` (int) — primary key  
- `book_id` (int) — FK → `books.book_id`  
- `username` (str) — pseudonymous handle  
- `text` (str) — free-text review

## How the notebook reads these files
The notebook loads `data/samples/*.csv` and constructs an **in-memory SQLite** database so that all SQL cells can run with:
```python
pd.read_sql("<SQL here>", con=engine)
