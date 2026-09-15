# Shopify Stock Data - Exploratory Data Analysis

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on Shopify stock market data.

The analysis uses Python to load, clean, analyze, and understand historical Shopify stock prices and trading volume.

The dataset contains **2469 rows** with stock information such as Open, High, Low, Close, Adjusted Close, Volume, and Date.

---

## 🎯 Objectives

The main objectives of this project are:

* Load the Shopify stock dataset
* Explore the structure of the dataset
* Check data types and missing values
* Check for duplicate records
* Convert the date column into datetime format
* Sort the data by date
* Calculate daily price changes
* Calculate daily returns
* Analyze trading volume
* Identify anomalous trading days
* Calculate mean, variance, and standard deviation of daily returns

---

## 🛠️ Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Google Colab / Jupyter Notebook

The notebook imports NumPy, Pandas, and Matplotlib for the analysis.

---

## 📂 Dataset

The dataset used in this project is:

```text
shopify_stock.csv
```

The dataset contains the following columns:

| Column      | Description            |
| ----------- | ---------------------- |
| `date`      | Trading date           |
| `open`      | Opening stock price    |
| `high`      | Highest stock price    |
| `low`       | Lowest stock price     |
| `close`     | Closing stock price    |
| `adj_close` | Adjusted closing price |
| `volume`    | Trading volume         |

The data covers dates from **May 21, 2015 to March 14, 2025**.

---

## 🚀 How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
```

### Step 2: Open the Project

Open the project folder in:

* Google Colab
* Jupyter Notebook
* VS Code

### Step 3: Install Required Libraries

If the libraries are not already installed, run:

```bash
pip install numpy pandas matplotlib
```

### Step 4: Add the Dataset

Place the following file in the required location:

```text
shopify_stock.csv
```

The notebook loads the dataset using:

```python
df = pd.read_csv("/content/shopify_stock.csv")
```

### Step 5: Open the Notebook

Open:

```text
Task3_EDA.ipynb
```

### Step 6: Run the Cells

Run the notebook cells from top to bottom.

---

## 🔍 Analysis Performed

### 1. Data Loading

The Shopify stock CSV file is loaded into a Pandas DataFrame.

```python
df = pd.read_csv("/content/shopify_stock.csv")
```

---

### 2. Dataset Shape

The dataset initially contains:

```text
2469 rows
7 columns
```

The notebook's DataFrame shape output is `(2469, 8)` after adding a derived column later in the analysis.

---

### 3. Data Exploration

The project uses:

```python
df.head()
```

to view the first few records.

It also uses:

```python
df.info()
```

to understand column types and non-null values. All seven original columns contain 2469 non-null values.

---

### 4. Statistical Summary

The project uses:

```python
df.describe()
```

to calculate statistical information such as:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

For example, the mean closing price is approximately **48.46** and the maximum closing price is approximately **169.06**.

---

### 5. Date Conversion

The `date` column is converted into a datetime format:

```python
df["date"] = pd.to_datetime(df["date"], utc=True)
```

This allows the dates to be handled correctly during time-based analysis.

---

### 6. Missing Value Check

Missing values are checked using:

```python
df.isnull().sum()
```

The analysis shows **0 missing values** in all columns.

The notebook also applies:

```python
df = df.dropna()
```

---

### 7. Duplicate Check

Duplicate records are checked using:

```python
df.duplicated().sum()
```

The result is:

```text
0
```

Therefore, no duplicate records were identified.

The notebook also applies:

```python
df = df.drop_duplicates()
```

---

### 8. Sorting by Date

The dataset is sorted chronologically:

```python
df = df.sort_values("date")
```

---

### 9. Daily Price Change

A new column called `Daily_Delta` is created:

```python
df["Daily_Delta"] = df["close"] - df["open"]
```

This represents the difference between the closing and opening prices for each trading day.

---

### 10. Daily Return

The project calculates daily return using:

```python
df["Daily_Return"] = (
    (df["close"] - df["open"]) / df["open"]
) * 100
```

This gives the daily price change as a percentage.

Example:

| Date       |  Open | Close | Daily Delta | Daily Return |
| ---------- | ----: | ----: | ----------: | -----------: |
| 2015-05-21 | 2.800 | 2.568 |      -0.232 |       -8.29% |
| 2015-05-22 | 2.607 | 2.831 |       0.224 |        8.59% |
| 2015-05-26 | 2.980 | 2.965 |      -0.015 |       -0.50% |

---

### 11. Trading Volume Analysis

The project calculates:

* Average trading volume
* Maximum trading volume
* Minimum trading volume

Results:

```text
Average Volume  : 16,570,491.78
Maximum Volume  : 208,959,000
Minimum Volume  : 1,039,000
```

---

### 12. Anomalous Trading Days

A threshold is created using twice the average trading volume:

```python
threshold = 2 * avg_volume
```

Trading days with volume greater than this threshold are identified as anomalous:

```python
anomalous_days = df[df["volume"] > threshold]
```

The analysis displays the date, open price, close price, volume, daily delta, and daily return for anomalous days.

---

### 13. Return Statistics

The project calculates:

```python
df["Daily_Return"].mean()
df["Daily_Return"].var()
df["Daily_Return"].std()
```

Results:

```text
Mean Return        : 0.0864
Variance           : 9.7331
Standard Deviation : 3.1198
```

---

## 📊 Key Findings

Based on the analysis:

* The dataset contains 2469 historical trading records.
* There are no missing values in the original dataset.
* No duplicate records were identified.
* The stock data contains Open, High, Low, Close, Adjusted Close, and Volume information.
* Daily price changes and percentage returns were calculated.
* Trading volume varies considerably across the dataset.
* Anomalous trading days were identified using a volume threshold.
* The calculated mean daily return is approximately **0.0864%**.
* The standard deviation of daily return is approximately **3.1198%**.

---

## 📁 Project Structure

```text
Shopify-Stock-EDA/
│
├── Task3_EDA.ipynb
├── shopify_stock.csv
└── README.md
```

---

## ▶️ How to Reproduce

1. Download or clone this repository.
2. Add `shopify_stock.csv`.
3. Open `Task3_EDA.ipynb`.
4. Install NumPy, Pandas, and Matplotlib if required.
5. Run all notebook cells sequentially.
6. Review the data-cleaning, return, volume, anomaly, and statistical analysis results.

---

## 👩‍💻 Author

**Prathibaa P**

---

## 📌 Note

This project is an **Exploratory Data Analysis** project intended for learning and analyzing historical stock data. It does not provide financial or investment advice.
