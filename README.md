# ECE2112_Programming-Assignment-3 

<br>Advance Computer Programming - S.Y. '24-'25  
<br> Name: `K. A. Gas*ng-n` || Section: `2 ECE - C`

### ----- Contents of this Assignment ----- 
Download this `csv` file first: 
<br><br>[cars.csv](https://github.com/Kai-Ash2k6/ECE2112_Programming-Assignment-3/blob/data/cars.csv)
    
    1. Problem 1 – Load and inspect `cars.csv` using pandas (display table, head, tail).
    2. Problem 2 – Data selection and filtering with pandas (iloc, loc, conditional selection).
### ---------------- Notes ----------------
    
    - I debugged my code multiple times and used module notes, YouTube tutorials, and 
      other online references to understand concepts I was not confident with.
    - This repository is part of my journey in learning basic Python and pandas for data handling.

### .... Analysis / Notes .....
    
    1. Problem 1
    - Uses pandas to read a CSV file into a DataFrame.
    - Displays the full table (interactive environments show DataFrame; in scripts use print()).
    - Uses .head() and .tail() to quickly inspect the first and last rows of the dataset.
    - Generalization / Conclusion:
          This problem demonstrates how pandas gives quick inspection tools for tabular data which helps during data cleaning and exploration.

    2. Problem 2
    - Illustrates row/column selection by position (.iloc) and by condition (.loc).
    - Demonstrates filtering single rows and selecting specific columns.
    - Also shows how to combine multiple conditions using bitwise operators (| for OR).
    - Generalization / Conclusion:
          Mastering selection and filtering is essential for data preprocessing tasks and exploratory data analysis (EDA).

### .... Mini Tutorial .....

## ** Problem 1: Load & Inspect `cars.csv` **

Step 1 — Import pandas

```python
import pandas as pd
````

Step 2 — Read the CSV file

```python
cars = pd.read_csv('cars.csv')
```

Step 3 — Display the original table and quick views

```python
print("The original Table is \n")
cars

print('The First Five Rows in the Original Table is: \n')

# This function will display the 1st five rows from the data stored in cars
cars.head()

print('The Last Five Rows in the Original Table is: \n')

# This function will display the LAST five rows from the data stored in cars
cars.tail()
```

Notes:

* In a script run (non-interactive), use `print(cars)` to ensure the dataframe is printed to the terminal.
* `.head()` and `.tail()` are fast ways to peek into the dataset.

---

## \*\* Problem 2: Data Selection & Filtering in pandas \*\*

### Code (full)

```python
import pandas as pd

# only reads the csv file
cars = pd.read_csv('cars.csv')

# a. Display the first five rows with odd-numbered columns (columns 1, 3, 5, 7…)
print('\n This is the first five rows with odd-numbered columns of cars: \n')
cars.iloc[:5, 1::2]

# b. Display the row that contains the ‘Model’ of ‘Mazda RX4’.
print('\n This is the data of Mazda RX4: \n')
cars.loc[cars["Model"] == 'Mazda RX4']

# c. How many cylinders (‘cyl’) does the car model ‘Camaro Z28’ have?
print('\n Showing how many cylinders Camaro Z28 has: \n')
cars.loc[cars["Model"] == "Camaro Z28", ['Model', 'cyl']]

# d. Determine how many cylinders (‘cyl’) and what gear type (‘gear’) do the car models 
# ‘Mazda RX4 Wag’, ‘Ford Pantera L’ and ‘Honda Civic’ have.
print('\n The number of cylinders and gear type of the three cars: \n')

cars.loc[(cars['Model'] == 'Mazda RX4 Wag') |       # | - means BITWISE OR
         (cars['Model'] == 'Ford Pantera L') |
         (cars["Model"] == "Honda Civic"),
          ['Model','cyl','gear']]
```

### Step-by-step notes & tips

1. `.iloc[:5, 1::2]`

   * `.iloc[row_slice, col_slice]` selects by integer position.
   * `:5` → first 5 rows; `1::2` → start at column index 1 and take every 2nd column (odd-numbered columns if counting from 0).

2. `cars.loc[cars["Model"] == 'Mazda RX4']`

   * `.loc[condition]` selects rows where `condition` is True. Here we filter by model name.

3. `cars.loc[cars["Model"] == "Camaro Z28", ['Model', 'cyl']]`

   * Selects only the `Model` and `cyl` columns for the row(s) matching Camaro Z28.

4. Combining conditions: `|`, `&`, `~`

   * In pandas use bitwise operators: `|` (OR), `&` (AND), and `~` (NOT).
   * Example: `(cars['Model'] == 'A') | (cars['Model'] == 'B')` picks rows where model is A **or** B.
   * **Do not** use `||` (Python has no `||` and it will cause a syntax error).

5. Shorter alternative for multiple equality checks:

```python
cars.loc[cars['Model'].isin(['Mazda RX4 Wag', 'Ford Pantera L', 'Honda Civic']), ['Model','cyl','gear']]
```

`isin()` is cleaner when checking membership in a list.

## Example expected outputs (conceptual)

* Part a → a DataFrame slice showing the first 5 rows and only the odd-numbered columns.
* Part b → the row(s) where `Model == 'Mazda RX4'`.
* Part c → a 1-row result showing `Model` and `cyl` for `Camaro Z28`.
* Part d → 3 rows listing `Model`, `cyl`, and `gear` for the three specified models.

## How to run (step-by-step)

* Put the code into files, e.g.:

  * `assignment3_problem1.py` (Problem 1)
  * `assignment3_problem2.py` (Problem 2)
* Ensure `cars.csv` is in the same directory as your scripts.
* Open a terminal in that folder.
* Run the script:

```bash
python assignment3_problem1.py
python assignment3_problem2.py
```

* If running in Jupyter Notebook, run the cells to display DataFrames inline.

## Requirements

* Python 3.x
* pandas

```bash
pip install pandas
```

# ---------------- End of Assignment #3 README ----------------

```

Want me to:
- save this as `README.md` and give you the file content ready to download, or  
- combine Problems 1 & 2 into a single script file with clean prints and `.to_string()` for better console output?
```
