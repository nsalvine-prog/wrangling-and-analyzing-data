# **Project: Wrangling and Analyzing Data**

## **Introduction**
This project focuses on wrangling and analyzing real-world data from the WeRateDogs Twitter archive. The workflow involves the following core processes:

- **Data Gathering**
- **Data Assessment** (visual and programmatic)
- **Data Cleaning** (addressing quality and tidiness issues)

The objective is to collect data from multiple sources, assess its structure and issues, clean it thoroughly, and prepare one well-structured master dataset for analysis.

---

## **Data Gathering**

Three different datasets were used in this project:

### **1. twitter-archive-enhanced**
- Provided by Udacity  
- Downloaded manually and imported into Jupyter Notebook

### **2. image-predictions**
- URL provided by Udacity  
- Downloaded programmatically using the `requests` library

### **3. tweet-json**
- Extracted using Tweepy and Twitter API  
- Stored as JSON lines in a `.txt` file  
- Loaded into the notebook to extract:
  - `favorite_count`
  - `retweet_count`
  - `tweet_id`

Together, these datasets form the basis of the data wrangling workflow.

---

## **Data Assessment**

Assessment was done both **visually** (displaying the dataframes) and **programmatically** using Pandas.  
The following **quality** and **tidiness** issues were identified across the three datasets:

### **Quality Issues**
- Retweet rows present in `df1_archive_enhanced`
- Missing values represented as `None` instead of `NaN` in `name`, `doggo`, `floofer`, `pupper`, `puppo`
- Dog names in `p1`, `p2`, and `p3` starting with lowercase letters
- Incorrect datatypes:
  - `timestamp` not in datetime format  
  - `tweet_id` not stored as string
- Invalid dog names such as `"a"` in the `name` column
- The `source` column contains HTML tags
- Duplicate `tweet_id` values in certain datasets

### **Tidiness Issues**
- Dog stages (`doggo`, `floofer`, `pupper`, `puppo`) should be combined into a single column: **`stage_of_dog`**
- The `name` column should be renamed to **`name_dog`** for clarity
- Redundant columns need to be dropped
- All three datasets (`df_tweet_json`, `df_image_predictions`, `df1_archive_enhanced`) should be merged into **one master dataset**

---

## 📌 **Data Cleaning**

Before cleaning, copies of all datasets were created to preserve raw data.  
Cleaning steps included:

- Removing retweet rows from `df1_archive_enhanced`
- Replacing `None` with `NaN` in categorical dog-stage columns
- Capitalizing dog names in the image predictions dataset
- Converting:
  - `timestamp` → datetime format  
  - `tweet_id` → string format  
- Replacing incorrect dog names (e.g., `"a"` → `"Alfie"`)
- Renaming `name` to `name_dog`
- Cleaning HTML text from the `source` column
- Dropping columns with excessive missing values
- Combining dog-stage columns into one (`stage_of_dog`)
- Merging the three datasets into one master dataframe
- Exporting the final cleaned dataset to a CSV file

---

## **Python Libraries Used**

- **pandas**  
- **requests**  
- **numpy**  
- **tweepy**  
- **json**  
- **matplotlib.pyplot**

---

