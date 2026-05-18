# Turkish Super League Data Analytics & RDBMS Pipeline

Disclaimer: This project is developed strictly for educational, research, and portfolio purposes. All data is fetched live from official public sources and is used under fair use principles. It is not intended for commercial use.

An end-to-end data analytics and engineering project that automatically scrapes Turkish Super League (TSL) data, designs a relational database structure using **Many-to-Many architecture**, and provides statistical insights.

## Tech Stack
* **Language:** Python
* **Data Scraping (ETL):** BeautifulSoup, Requests
* **Data Manipulation & Analytics:** Pandas, NumPy
* **Database Management:** SQLite
* **Data Visualization:** Seaborn, Matplotlib, AdjustText

## Relational Database Modeling (3NF)
Instead of storing flat files, this project normalizes raw web data into **3rd Normal Form (3NF)** to ensure data integrity and avoid redundancy. 

Since the relationship between Teams and Matches is inherently **Many-to-Many**, the schema utilizes a Junction Table (`match_teams`):
* `teams`: Stores master data of unique football clubs.
* `matches`: Stores league weeks and match details.
* `match_teams` (Junction Table): Connects teams and matches by capturing match status (Home/Away) and goals scored dynamically.

## Portable Architecture (How to Run)
The project is built with a dynamic **Relative Path** structure. There is no need to pre-download any database file. 

## How to Run & Pipeline Workflow

This project operates as a fully automated, standalone data pipeline. It eliminates data-dependency by fetching live statistics and initializing the RDBMS structure on the fly.

### Prerequisites
Ensure you have Python 3.x installed along with the required libraries for web scraping, data manipulation, and visualization:

```bash
pip install pandas numpy beautifulsoup4 requests seaborn matplotlib adjustText
```

When you clone the repository and run `2023-2024 TSL statistic.ipynb`:
1. It automatically fetches live data via Web Scraping from the official TFF site.
2. It initializes a localized SQLite database (`tsl_analysis.db`) on the fly.
3. It creates relational tables with `FOREIGN KEY`, `UNIQUE`, and `CASCADE DELETE` constraints.
4. It executes analytical SQL `JOIN` queries and pipes data back into Pandas for reporting.
