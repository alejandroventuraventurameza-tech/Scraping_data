# UNMSM Admissions Scraper

## What does the project do?

This project automates the extraction of applicant results from the official UNMSM (Universidad Nacional Mayor de San Marcos) admissions website for the 2026-II cycle. Using Selenium, it navigates the site, iterates over every available academic program, paginates through all result pages, and consolidates the data into a single Excel file.

Target URL: `https://admision.unmsm.edu.pe/Website20262/A/A.html`

## How to install the dependencies?

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

## How to run the script?

1. Create the output folder if it does not exist:

```bash
mkdir output
```

2. Open `scraper.ipynb` in Jupyter Notebook or JupyterLab and run all cells in order:

```
Cell 1 — Install dependencies
Cell 2 — Launch Chrome browser
Cell 3 — Load the main page and collect all program URLs
Cell 4 — Define the scraping function per program
Cell 5 — Run the full scraping loop and export to Excel
```

> The browser window will open automatically. Do not close it while the scraper is running.

## What does the output contain?

The script generates a file at `output/resultados_sanmarcos.xlsx` with one row per applicant across all programs. The columns are:

| Column | Description |
|---|---|
| `Carrera` | Name of the academic program |
| `Código` | Applicant ID code |
| `Apellidos y Nombres` | Full name of the applicant |
| `Escuela` | School or faculty of origin |
| `Puntaje` | Admission score (extracted from `data-score` HTML attribute) |
| `Mérito E.P.` | Merit rank within the program (from `data-merit` HTML attribute) |
| `Observación` | Admission status or observation (e.g., ingresante, eliminado) |
