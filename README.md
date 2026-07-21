# ⚡ Smart Electricity Contract Cost Optimizer

## 📋 About the Project
Just over a year ago, a smart electricity meter was installed at home, reporting hourly energy usage data. With the electricity contract up for renewal, this project utilizes financial analysis and data processing techniques in Python to clean the messy historical usage dataset, analyze consumption patterns, and evaluate three different contract types (**No Flex**, **Monthly Flex**, and **Hourly Flex**) to identify which option minimizes the annual electricity cost.

## 📊 Dataset & Inputs
The project processes a raw, unsorted, and poorly structured historical dataset containing 8,760 hourly readings (one full year) alongside contract pricing tiers.
* **Raw Data Structure:** Messy text strings combining timestamps, extra whitespaces, random underscores, and energy values (e.g., `_1AM  Friday 19th-Dec-2014___0.209  kwh  `).
* **Contract Types Evaluated:**
  1. No Flex (Flat Rate):** Constant cost per kWh for the entire year ($0.21 / kWh).
  2. Monthly Flex:** Rates fluctuate depending on the month.
  3. Hourly Flex:** Rates fluctuate based on the time of day.

## 🛠 Tech Stack
* **Programming Language:** Python
* **Data Manipulation & Cleaning:** Pandas, NumPy
* **Environment:** Jupyter Notebook

## 📈 Key Analysis Steps & Code Pipeline
1. **Data Ingestion & Cleaning:**
   * Loaded raw records from Excel.
   * Stripped unwanted whitespaces and special characters (`_`) using string operations.
   * Extracted numerical kWh usage values and parsed complex datetime formats containing ordinal suffixes (e.g., `24th-Mar-2014`) into standard timestamps.
2. **Feature Engineering:**
   * Generated additional temporal features including `Month`, `Day_of_Week`, `Day`, and `Hour` to support granular aggregations.
3. **Exploratory Data Analysis & Questions Addressed:**
   * Calculated average hourly usage ($\approx 0.782 \text{ kWh}$).
   * Analyzed specific consumption metrics, such as average usage in February ($\approx 0.834 \text{ kWh}$) and peak usage patterns by day of the week (Sunday highest).
   * Computed rolling window consumption metrics (highest continuous 4-hour usage).
4. **Contract Cost Simulation & Optimization:**
   * Merged hourly and monthly usage profiles with respective contract rate tables.
   * Calculated total annual expenses for each contract structure:
     * **Hourly Flex:** $1,368.98 (Lowest cost option)
     * **Monthly Flex:** $1,421.21
     * **No Flex (Flat Rate):** $1,438.10
