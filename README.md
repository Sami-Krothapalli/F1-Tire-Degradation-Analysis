# F1 Tire Degradation Analysis

This repository contains a STAT 444 final project analyzing Formula 1 tire degradation using race-lap data. The project asks whether F1 tires gradually lose performance over a stint or whether there is evidence of a sudden tire-performance "cliff" where lap times become much slower.

## Project Overview

The analysis uses lap-level Formula 1 data from the AeroSpeed Analytics Kaggle dataset. Each observation represents one lap completed by one driver during a race.

The main response variable is `PaceDelta_Adjusted`, which measures how much faster or slower a lap was than expected after accounting for race progress, driver, Grand Prix, and year. This adjustment is important because raw lap times are affected by circuit length, driver/team pace, season, and fuel burn.

## Methods

The project compares three statistical methods:

- **Regression splines**: model the smooth nonlinear relationship between tire life and adjusted pace.
- **Segmented regression**: estimates possible breakpoints where the tire-degradation rate changes.
- **Regression tree**: predicts adjusted pace delta using tire, speed, team, race, and year variables.

Model performance is compared using test RMSE.

## Main Findings

The results suggest that tire degradation is real and nonlinear, but the data do not show one universal sudden tire cliff. Soft and medium tires begin losing pace earlier, while hard tires remain more stable for longer. The regression tree achieved the lowest RMSE, while the spline and segmented regression models were more useful for interpreting the tire-degradation pattern directly.

## Repository Structure

```text
.
├── README.md
├── f1_tire_degradation.ipynb
├── F1_Tire_Degradation_Report.pdf
├── data/
│   └── F1 Dataset/
│       └── f1_race_laps.csv
└── report/
    ├── f1_tire_degradation_report.tex
    ├── f1_tire_degradation_report.pdf
    ├── f1_tire_degradation_report.aux
    ├── f1_tire_degradation_report.log
    ├── f1_tire_degradation_report.out
    └── figures/
        ├── Figure1.png
        ├── Figure2.png
        ├── Figure3.png
        ├── Figure4.png
        ├── Figure5.png
        └── Figure6.png
```

## Running the Notebook

Create and activate a Python virtual environment, then install the required packages:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install pandas numpy matplotlib seaborn statsmodels scikit-learn jupyter ipykernel
```

Open `f1_tire_degradation.ipynb` in VS Code or Jupyter and run the cells from top to bottom.

## Compiling the Report

The LaTeX report source is in the `report/` folder. To recompile the PDF:

```bash
cd report
pdflatex f1_tire_degradation_report.tex
pdflatex f1_tire_degradation_report.tex
```

The second compile updates labels, figure references, and PDF outlines.

The `.aux`, `.log`, and `.out` files are LaTeX build files. They do not need to be submitted, but they are kept in `report/` because LaTeX recreates them during compilation.

## Data Source

AeroSpeed Analytics Formula 1 dataset from Kaggle: `shivmahlan/aerospeed-analytics`.
