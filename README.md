# 📚 SQL Analysis — Books, Ratings & Reviews

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![SQL](https://img.shields.io/badge/SQL-SQLite%20(in%20memory)-lightgrey?logo=sqlite)
![Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter)
![Data](https://img.shields.io/badge/Data-CSV%20snapshots-yellow)
![License](https://img.shields.io/badge/License-MIT-green)

This project explores a book-platform dataset using **SQL** to extract insights about **publications, authors, publishers, ratings and user behaviour**.  
It was developed as part of the **TripleTen Data Analytics Bootcamp**. For easy reproducibility on GitHub, the analysis reads **CSV snapshots** and builds an **in-memory SQLite** database so all queries can be executed with `pd.read_sql`.

💻 **Repository:** [https://github.com/MarcelaMaris/Project-14C-Tripleten-SQL](https://github.com/MarcelaMaris/Project-14C-Tripleten-SQL)

---

## 🎯 Objectives
- Inspect the schema and validate basic data integrity.  
- Answer key questions via SQL: catalogue recency, popularity/quality by books, authors and publishers, and engagement patterns.  
- Communicate findings with compact visuals and clear takeaways.

---

## 🧭 Analysis Features
- 📅 **Books per year** — trend of publications, highlighting a contemporary catalogue.  
- ⭐ **Ratings distribution** — overall sentiment and skew.  
- ✍️ **Top authors** — average rating with an adaptive volume threshold for robustness.  
- 🏢 **Publishers’ quality** — average rating for substantial catalogues (>50 pages), with readability tweaks for long labels.

---

## 🗃️ Dataset
**Tables**
- `books`: `book_id`, `author_id`, `title`, `num_pages`, `publication_date`, `publisher_id`  
- `authors`: `author_id`, `author`  
- `publishers`: `publisher_id`, `publisher`  
- `ratings`: `rating_id`, `book_id`, `username`, `rating`  
- `reviews`: `review_id`, `book_id`, `username`, `text`

**Notes on reproducibility**  
Original data were provided in PostgreSQL during the bootcamp. This repository ships **CSV snapshots** in `data/samples/`. The notebook creates an **in-memory SQLite** engine so queries can be run locally without credentials.

---

## 📌 Conclusions
- **Contemporary catalogue:** **819** books were published **after 1 January 2000** (≈**82%**), with a clear year-on-year increase post-2000.  
- **Positive sentiment:** ratings are skewed towards **4–5**, with a lighter tail below **3**.  
- **Authors:** among high-volume authors, **J.K. Rowling/Mary GrandPré (~4.29)** and **J.R.R. Tolkien (~4.24)** show consistently strong reception, while **Stephenie Meyer (~3.66)** indicates a more polarised audience.  
- **Publishers (quality):** for catalogues with **≥5 books >50 pages**, average ratings are tightly clustered (**~4.13–4.45**). Leaders include **Harper Voyager (4.45)**, **Vertigo (4.37)**, **HarperCollins Publishers (4.32)**, **Harper Perennial Modern Classics (4.31)** and **Random House (4.25)**.  
- **Publishers (volume):** **Penguin Books** released the highest number of substantial titles (>50 pages).  
- **Engagement:** users who rated **>50** books write about **24** text reviews on average — a valuable community segment to activate.

---

## 📝 Recommendations
- **Personalised discovery:** prioritise recommendations from consistently high-scoring authors/publishers; surface “evergreen” titles with both volume and quality.  
- **Editorial highlights:** feature top publishers (e.g., Harper Voyager, Vertigo) and high-performing authors in themed collections.  
- **Review activation:** nudge highly engaged raters (>50 ratings) to write more reviews (lightweight prompts, badges), enriching community content.  
- **A/B test recommender tweaks:** experiment with small ranking boosts for high-quality clusters and measure uplift in add-to-list/checkout events.  
- **Next steps for data depth:** add genre/topic labels and light sentiment analysis to refine recommendations further.

---

## 💡 Key Business Impact
- Clear picture of **catalogue recency** and **overall sentiment**.  
- Identified **high-performing authors/publishers** to drive discovery and curation.  
- Highlighted a **high-engagement user cohort** for community growth and retention initiatives.  
- Portable notebook design enables **easy review and reuse** by stakeholders and recruiters.

---

## 🛠️ Tech Stack
- **Data & SQL:** Python, Pandas, SQLite (via `pd.read_sql`)  
- **Notebook & viz:** Jupyter, Matplotlib  
- **Reproducibility:** CSV snapshots (`data/samples/`) + in-memory SQLite engine

---

## ⚙️ How to run locally

**Requirements:** Python 3.10+

Clone the repo and install dependencies.

### Using conda
```bash
conda create -n tripleten-sql python=3.10 -y
conda activate tripleten-sql
pip install pandas matplotlib jupyter
