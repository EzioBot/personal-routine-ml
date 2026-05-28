# Personal Routine ML

This project analyzes my 2024-2025 weekly routine data and uses it to forecast the next week's routine and performance score. The main goal is to understand how time spent on sleeping, studying, classes, gaming, work, learning, books, exercise, and other activities affects weekly productivity.

## Files

- `yearly record.xlsx` - main data source with separate sheets for 2024 and 2025.
- `yearly record - 2024.csv` - older single-year CSV export kept as a reference.
- `weekly_routine_forecast_2024.ipynb` - the notebook that cleans the data, trains the model, and predicts next week.

## What the Notebook Does

1. Loads the Excel workbook.
2. Reads the 2024 and 2025 sheets.
3. Finds the weekly activity table automatically.
4. Cleans activity names and percentage values.
5. Converts the data into one row per week.
6. Creates useful features like academic focus, productive time, screen leisure, and sleep balance.
7. Builds a routine performance score.
8. Trains a ridge regression model to predict the next week.
9. Shows charts, forecast tables, and short notes about the prediction.

## Problems and Fixes

- Problem: The workbook is not a clean dataset because it has notes, empty rows, multiple sheets, and spreadsheet formatting.
  Fix: The notebook reads the Excel file directly, detects the activity table in each yearly sheet, and extracts only the useful weekly records.

- Problem: Excel stores percentages as decimals, for example `0.25` instead of `25%`.
  Fix: The parser converts Excel decimal percentages into normal percentage values.

- Problem: Some activity names had spelling or formatting issues.
  Fix: The notebook standardizes the activity names before analysis.

- Problem: The data was arranged as activities by columns instead of normal machine-learning rows.
  Fix: The notebook reshapes it into weekly records, where each row represents one week.

- Problem: Some weeks are missing in the 2025 sheet.
  Fix: The model skips non-adjacent gaps so it only learns real next-week transitions.

- Problem: There was no direct performance label.
  Fix: A transparent performance score was created from study time, work, learning, books, exercise, sleep balance, and leisure time.

- Problem: The dataset is still small even with two years of records.
  Fix: A simple ridge regression model was used because it is stable and less likely to overfit small personal data.

## How to Use

Open `weekly_routine_forecast_2024.ipynb`, edit the current week's percentages in the first code cell, then run the notebook from top to bottom. The final sections will show the predicted next-week routine, performance score, and improvement notes.
