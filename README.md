# Cancer Incidence Data Analysis

University coursework (「跨平台程式設計」/ Cross-Platform Programming course, final report, Jan 2024): exploratory data analysis of a Taiwan cancer-incidence dataset with pandas and matplotlib.

## Dataset

`0-cancer_file.csv` — 87,827 rows, 1979–2019, columns: diagnosis year, sex (all/male/female), county (national + 21 counties), cancer type (up to 35 types), age-standardized incidence rate (WHO 2000 world standard population, per 100,000), case count, average age, median age. Encoded in Big5.

The course assigned each student a pre-split slice of a larger dataset by `student_id % 4` (this file is the `0` slice) — the underlying statistics are consistent with Taiwan's national cancer registry (age-standardized incidence by year/county/cancer type), but the file itself was distributed as course material, not downloaded directly from a government open-data portal, so I can't cite an exact source URL.

## Analysis

Three scripts, each reading `0-cancer_file.csv` directly:

- **`total.py`** — National case counts by sex over time. Prints the first three years' totals, then plots male vs. female incidence trends. Finding: male incidence is consistently higher than female, and both have risen year over year.
- **`man_woman.py`** — Top 3 cancer types by total case count, separately for men and women, plotted as trend lines over time (→ `男性癌症前三名.png`, `女性癌症前三名.png`). Finding: colorectal and lung cancer matter for both sexes; liver cancer stood out for men, breast cancer for women.
- **`young.py`** — Filters for records where average age at diagnosis is under 30, grouped by cancer type. Finding: endocrine, eye, leukemia, and other nervous-system cancers are relatively more common in the under-30 group.

`癌症趨勢圖.png` is `total.py`'s output chart.

## Running It

```bash
pip install pandas matplotlib
python total.py       # prints yearly totals, opens two trend charts
python man_woman.py    # prints top-3 cancer types by sex, opens two chart windows
python young.py        # prints under-30 cancer-type counts (no chart)
```

Charts use `Microsoft JhengHei` for Chinese text (`plt.rcParams['font.sans-serif']`) — on a machine without that font installed, CJK labels will render as boxes.

## Original report

The original term-report Word document (in Chinese, written for course submission) is kept as-is at [`docs/112跨平台程式設計-期末報告.docx`](docs/112跨平台程式設計-期末報告.docx). This README's Dataset and Analysis sections are a condensed English version of its content.
