### ETL Pipeline for Market Capitalization Analysis

Overview
This project implements an ETL (Extract, Transform, Load) pipeline to analyze the market capitalization of the world's largest banks. The pipeline extracts data from a web source, transforms it by converting the market capitalization into multiple currencies, and loads the final dataset into both a CSV file and an SQLite database for further analysis.

The project showcases how to efficiently process and manage data from extraction to querying, with clear steps and reusable components.

## Features
# Data Extraction:

Scrapes tabular data from a Wikipedia page listing the largest banks by market capitalization.
Dynamically handles table structure changes by identifying and renaming relevant columns.

# Data Transformation:

Converts market capitalization data from USD into GBP, EUR, and INR using an exchange rate file.
Rounds transformed values to the nearest billion or specified precision.

# Data Loading:

Saves the transformed data into a CSV file.
Loads the final dataset into an SQLite database for advanced querying.

# SQL Queries:

Prints the full dataset.
Calculates the average market capitalization in GBP.
Lists the names of the top 5 banks.

## Project Structure

ETL_Pipeline_Project/
│
├── banks_project.py           # Main Python script containing the ETL pipeline
├── exchange_rate.csv          # CSV file containing exchange rates for currency conversion
├── code_log.txt               # Log file recording the execution process
├── Largest_banks_data.csv     # Output CSV file with the transformed data
├── Banks.db                   # SQLite database containing the final data table
├── README.md                  # Project description file

