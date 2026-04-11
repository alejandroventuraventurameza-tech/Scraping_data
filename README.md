# Scraping Data — Course Projects

This repository contains two data extraction projects developed for the course, combining web scraping and REST API consumption using Python.

---

## Task 1 — Web Scraping: UNMSM Admissions

### What does it do?

Automates the extraction of applicant results from the official UNMSM (Universidad Nacional Mayor de San Marcos) admissions website for the 2026-II cycle. Using Selenium, it navigates the site, iterates over every available academic program, paginates through all result pages, and consolidates the data into a single Excel file.

Target URL: `https://admision.unmsm.edu.pe/Website20262/A/A.html`

### How to install the dependencies?

Make sure you have Python and pip available (Anaconda recommended). Then run:

```bash
pip install selenium pandas openpyxl webdriver-manager
```

| Library | Purpose |
|---|---|
| `selenium` | Browser automation and web scraping |
| `pandas` | Data manipulation and Excel export |
| `openpyxl` | Excel file writing backend for pandas |
| `webdriver-manager` | Automatically downloads the correct ChromeDriver |

> **Note:** Google Chrome must be installed on your machine. ChromeDriver is downloaded automatically via `webdriver-manager`.

### How to run it?

1. Create the output folder if it does not exist:

```bash
mkdir output
```

2. Open `scraper.ipynb` in VS Code or JupyterLab and run all cells in order:

```
Cell 1 — Install dependencies
Cell 2 — Launch Chrome browser
Cell 3 — Load the main page and collect all program URLs
Cell 4 — Define the scraping function per program
Cell 5 — Run the full scraping loop and export to Excel
```

> The browser window will open automatically. Do not close it while the scraper is running.

### Output

The script generates `output/resultados_sanmarcos.xlsx` with one row per applicant across all programs.

| Column | Description |
|---|---|
| `Carrera` | Name of the academic program |
| `Código` | Applicant ID code |
| `Apellidos y Nombres` | Full name of the applicant |
| `Escuela` | School or faculty of origin |
| `Puntaje` | Admission score (extracted from `data-score` HTML attribute) |
| `Mérito E.P.` | Merit rank within the program (from `data-merit` HTML attribute) |
| `Observación` | Admission status or observation (e.g., ingresante, eliminado) |

---

## Task 2 — REST API: RAWG Video Games Database

### What does it do?

Consumes the [RAWG API](https://rawg.io/apidocs) to extract, analyze, and compare video game data. The notebook covers general exploration, category analysis, platform and genre comparisons, and personal conclusions based on the data found.

### How to install the dependencies?

```bash
pip install requests pandas
```

| Library | Purpose |
|---|---|
| `requests` | HTTP requests to the RAWG API |
| `pandas` | Data manipulation and CSV export |

### How to run it?

1. Get your free API key at [rawg.io/apidocs](https://rawg.io/apidocs)
2. Open `api/tarea_rawg_api.ipynb` in VS Code
3. Replace `YOUR_API_KEY_HERE` in the setup cell with your key
4. Run all cells in order

> ⚠️ Never commit your API key to GitHub. Keep it as a local variable only.

### Notebook structure

| Section | Description |
|---|---|
| **Part A** | Total number of games registered in RAWG (898,481) |
| **Part B** | Top 5 by Metacritic score / Top 10 games on Steam |
| **Part C1** | PC vs PS5 top 5 comparison (PC wins: 4.826 vs 4.724) |
| **Part C2** | Comparison table: The Division 2, MGS V, Splinter Cell Blacklist |
| **Part C3** | Average rating by genre: Action, RPG, Indie, Adventure |
| **Part C4** | Best games by year: 2013, 2015, 2019 (2013 wins with 93.6 Metacritic avg) |
| **Part C5** | Top 20 games of all time exported to CSV |
| **Part D** | Personal insights and conclusions |

### Output

The notebook generates `api/output/top20_rawg.csv` with the following columns:

| Column | Description |
|---|---|
| `name` | Game title |
| `rating` | User rating on RAWG (1–5 scale) |
| `metacritic` | Critic score on Metacritic (1–100 scale) |
| `release_date` | Official release date |
| `main_genre` | Primary genre assigned by RAWG |

### Key findings

- **The Elder Scrolls VI** tops the all-time chart with 4.86 despite being unreleased — pure hype bias
- **Cyberpunk 2077** ranks #12 all time, a remarkable redemption from its disastrous 2020 launch
- **RAWG genres are too broad** for taste-based filtering — tags must be combined with genres for precise results
- **Undertale** appeared in the 2015 top games with 92 Metacritic, validating its status as an indie classic
