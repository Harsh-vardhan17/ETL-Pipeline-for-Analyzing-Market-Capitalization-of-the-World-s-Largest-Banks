# ETL Pipeline for Market Capitalization Analysis

Overview
This project implements an ETL (Extract, Transform, Load) pipeline to analyze the market capitalization of the world's largest banks. The pipeline extracts data from a web source, transforms it by converting the market capitalization into multiple currencies, and loads the final dataset into both a CSV file and an SQLite database for further analysis.

The project showcases how to efficiently process and manage data from extraction to querying, with clear steps and reusable components.

## Features
### Data Extraction:

Scrapes tabular data from a Wikipedia page listing the largest banks by market capitalization.
Dynamically handles table structure changes by identifying and renaming relevant columns.

### Data Transformation:

Converts market capitalization data from USD into GBP, EUR, and INR using an exchange rate file.
Rounds transformed values to the nearest billion or specified precision.

### Data Loading:

Saves the transformed data into a CSV file.
Loads the final dataset into an SQLite database for advanced querying.

### SQL Queries:

Prints the full dataset.
Calculates the average market capitalization in GBP.
Lists the names of the top 5 banks.

## Project Structure
```
ETL_Pipeline_Project/
│
├── banks_project.py           # Main Python script containing the ETL pipeline
├── exchange_rate.csv          # CSV file containing exchange rates for currency conversion
├── code_log.txt               # Log file recording the execution process
├── Largest_banks_data.csv     # Output CSV file with the transformed data
├── Banks.db                   # SQLite database containing the final data table
├── README.md                  # Project description file
```

## Technologies Used

Python: Core programming language for the ETL pipeline.
Pandas: For data manipulation and transformation.
SQLite3: To store and query the transformed data.
BeautifulSoup: For web scraping.
Requests: For HTTP requests to fetch web content.
NumPy: For numerical computations and rounding operations.

## Setup and Execution

Prerequisites
Python 3.x installed on your machine.
Required Python libraries: pandas, numpy, sqlite3, beautifulsoup4, requests.
Steps to Run
Clone this repository:

(```bash
git clone https://github.com/your_username/ETL_Pipeline_Project.git```
```cd ETL_Pipeline_Project```)

Install the required Python libraries:

(```bash
pip install -r requirements.txt```)

Run the ETL pipeline:

(```bash
python banks_project.py```)

Outputs

Largest_banks_data.csv: Contains the transformed data.
Banks.db: SQLite database with the data stored in the Largest_banks table.
SQL query results will be printed in the terminal.

## ETL Pipeline Workflow

1. Extract
The extract() function scrapes the table under the "By market capitalization" section from a Wikipedia page.
Dynamically identifies and renames columns (Name, Market cap(US$ billion)).

2. Transform
The transform() function reads exchange rates from exchange_rate.csv.
Converts MC_USD_Billion into:
MC_GBP_Billion (British Pounds)
MC_EUR_Billion (Euros)
MC_INR_Billion (Indian Rupees)
Rounds the converted values to two decimal places.

3. Load
The load_to_csv() function saves the final DataFrame into Largest_banks_data.csv.
The load_to_db() function loads the data into the SQLite database Banks.db.

## SQL Queries

Print all records in the table:

```SELECT * FROM Largest_banks;```

Calculate the average market capitalization in GBP:

```SELECT AVG(MC_GBP_Billion) FROM Largest_banks;```

List the top 5 banks by name:

```SELECT Name FROM Largest_banks LIMIT 5;```

## Log File Example
The code_log.txt file tracks the ETL pipeline execution:
```
2024-12-26 16:00:00 : Starting data extraction process.
2024-12-26 16:00:10 : Data extraction complete. Initiating transformation process.
2024-12-26 16:00:20 : Data transformation complete. Returning the transformed DataFrame.
2024-12-26 16:00:30 : Data saved to CSV file at Largest_banks_data.csv.
2024-12-26 16:00:40 : SQL Connection initiated to Banks.db.
2024-12-26 16:00:50 : Data loaded to database 'Banks.db' in table 'Largest_banks'.
2024-12-26 16:01:00 : Executing query: SELECT * FROM Largest_banks.
2024-12-26 16:01:10 : Query executed successfully.
```
## Future Enhancements
Add automated scheduling to run the ETL pipeline periodically.
Implement error handling for dynamic table structure changes.
Extend support for additional currencies or regions.

# License
This project is licensed under the MIT License. You are free to use, modify, and distribute this project.
