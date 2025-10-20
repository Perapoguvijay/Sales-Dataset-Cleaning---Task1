# Task-1: Sales-Dataset-Cleaning---
# 🛍️ Sales Data Cleaning and Preprocessing

This repository contains the Python script (or Jupyter Notebook) used for cleaning, transforming, and preparing a raw sales dataset for subsequent analysis and modeling. The process focuses on handling missing values, converting data types, and standardizing data formats.

---

## 🎯 Project Goal

The primary goal of this project is to transform a messy, raw sales dataset into a clean and structured format suitable for **Exploratory Data Analysis (EDA)**, **feature engineering**, and **machine learning model development**.

---

## 🛠️ Technologies & Libraries

* **Python** (3.x)
* **pandas**: For data manipulation and analysis.
* **numpy**: For numerical operations.
* **warnings**: Used to manage warnings during execution.

---

## 📁 Dataset

The dataset, assumed to be named `sales_data.csv`, contains information about various products, including their names, categories, pricing, reviews, and ratings.

### Original Columns and Data Types:

[cite_start]The initial dataset contained **16 columns**, all of which were of the `object` (string) data type, with a total of **1465 entries**[cite: 38, 39, 40, 95].

| # | Column Name | Initial Dtype | Initial Non-Null Count |
|---|---|---|---|
| 0 | `product_id` | `object` | 1465 |
| 1 | `product_name` | `object` | 1465 |
| 2 | `category` | `object` | 1465 |
| 3 | `discounted_price` | `object` | 1465 |
| 4 | `actual_price` | `object` | 1465 |
| 5 | `discount_percentage` | `object` | 1465 |
| 6 | `rating` | `object` | 1465 |
| 7 | **`rating_count`** | **`object`** | **1463 (2 missing)** |
| 8 | `about_product` | `object` | 1465 |
| 9 | `user_id` | `object` | 1465 |
| 10| `user_name` | `object` | 1465 |
| 11| `review_id` | `object` | 1465 |
| 12| `review_title` | `object` | 1465 |
| 13| `review_content` | `object` | 1465 |
| 14| `img_link` | `object` | 1465 |
| 15| `product_link` | `object` | 1465 |

---

## 🧹 Data Cleaning and Preprocessing Steps

The following major steps were executed in the provided notebook/script:

### 1. Handling Missing Values

* [cite_start]**`rating_count`**: The column initially contained **2 missing (null) values**[cite: 120].
* [cite_start]**Imputation**: The missing values in `rating_count` were imputed using the **`fillna(method='bfill')`** method, which uses the next valid observation to fill the gap (backward fill)[cite: 141]. [cite_start]This resulted in **zero missing values** for `rating_count`[cite: 156].
* [cite_start]**`rating`**: The conversion to a numeric type later revealed **one null value** in the `rating` column due to a non-numeric string (a blank space `' '`) being replaced by `NaN`[cite: 298, 315, 349].

### 2. Handling Duplicates

* [cite_start]**Row Duplicates**: Duplicate rows were identified and removed from the dataset using `sales_data.drop_duplicates(inplace=True)`[cite: 174].

### 3. Renaming Columns

* [cite_start]The column `review_title` was renamed to a more concise name, **`title`**[cite: 229, 233].

### 4. Data Type Conversion

Several columns were converted from the initial generic `object` type to more appropriate numeric types by first cleaning currency symbols and percentage signs.

| Column Name | Action Taken | Final Dtype |
|---|---|---|
| **`discounted_price`** | [cite_start]Currency symbols (e.g., '₹') were removed, and the column was converted to **`float64`**[cite: 238, 243, 339]. | `float64` |
| **`actual_price`** | [cite_start]Currency symbols were removed, and the column was converted to **`float64`**[cite: 247, 343]. | `float64` |
| **`discount_percentage`**| [cite_start]The percentage sign ('%') was removed, and the column was converted to **`float64`**[cite: 263, 346]. | `float64` |
| **`rating`** | [cite_start]**Non-numeric strings** (like spaces) were replaced, and the column was converted to **`float64`**[cite: 277, 301, 315, 350]. | `float64` |
| **`rating_count`** | (Implicitly converted after imputation) | `object` (Note: Future step should convert this to integer/float) |

---

## ✨ Final Dataset Structure

After preprocessing, the dataset (`sales_data`) maintains **1465 entries** and **16 columns**, with key numerical features now having the correct data type for analysis:

| Column Name | Final Dtype | Non-Null Count |
|---|---|---|
| `discounted_price` | `float64` | 1465 |
| `actual_price` | `float64` | 1465 |
| `discount_percentage` | `float64` | 1465 |
| `rating` | `float64` | 1464 |
| All other columns | `object` | 1465 |

[cite_start]The total memory usage for the cleaned DataFrame is **183.3+ KB**[cite: 383].
