# 🚗 Used Cars Sales Analysis — Exploratory Data Analysis (EDA)

---

## 📌 Project Overview

This project performs a complete **Exploratory Data Analysis (EDA)** on used car listings scraped from **Cars24** — one of India's largest used car platforms.

The goal is to understand **pricing patterns, depreciation trends, and brand performance** in the Indian second-hand car market using real-world data collected from 15 cities and 11 car brands.

---

## 🎯 Objective

> To analyze used car resale data and identify key factors that influence pricing — including brand, car age, kilometers driven, fuel type, and transmission type.

**Key Questions Answered:**
- Which brands retain resale value the best?
- How does car age affect the resale price?
- What is the impact of kilometers driven on price?
- Do automatic cars command a price premium?
- How are brands distributed across price segments?

---

## 🗂️ Repository Structure

```
used-cars-sales-eda/
│
├── EDA_Project_Cars24_Final.ipynb       ← Main notebook (scraping + cleaning + EDA)
├── Cars24_Used_Cars_Raw_Data.xls        ← Raw scraped dataset (before cleaning)
├── Cars24_Used_Cars_Clean_Data.xls      ← Cleaned dataset (ready for analysis)
└── README.md                            ← Project documentation
```

---

## 📊 Dataset Details

| Feature | Description |
|---|---|
| **Source** | Cars24 (scraped using BeautifulSoup) |
| **Cities Covered** | 15 cities across India |
| **Brands Covered** | 11 brands (Maruti, Hyundai, Tata, Honda, Ford, Mahindra, BMW, Toyota, Renault, KIA, Volkswagen) |
| **Raw Records** | 3,000+ listings |
| **Clean Records** | 3,073 rows × 13 columns |

### Columns in the Dataset

| Column | Type | Description |
|---|---|---|
| Brand | Categorical | Car manufacturer |
| Variant | Categorical | Specific model/variant |
| Model Year | Numerical | Year of manufacture |
| City | Categorical | City where the car is listed |
| Kilometer | Numerical | Total distance driven (km) |
| Fuel_Type | Categorical | Petrol / Diesel / CNG / Electric |
| Drive_Mode | Categorical | Manual / Automatic |
| EMI | Numerical | Estimated monthly installment (₹) |
| Final_Price | Numerical | Resale price — target variable (₹) |
| Car_Age | Numerical | Current Year − Model Year |
| KM_per_Year | Numerical | Kilometer / Car_Age |
| Price_Segment | Categorical | Budget / Mid / Upper-Mid / Premium |
| Age_Bucket | Categorical | 0–3 / 4–6 / 7–10 / 10+ years |

---

## 🔧 Tools & Libraries Used

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Requests + BeautifulSoup | Web scraping from Cars24 |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualizations |
| Jupyter Notebook | Development environment |

---

## 🪜 Project Workflow

### Step 1 — Web Scraping
- Targeted 15 Indian cities and 11 car brands
- Dynamically constructed URLs for each city–brand combination
- Extracted 9 key features using `BeautifulSoup` and `regex`
- Collected 3,000+ listings and exported to CSV

### Step 2 — Data Understanding
- Checked data types, missing values, duplicates
- Examined value counts for all categorical columns
- Reviewed statistical summary using `df.describe()`

### Step 3 — Data Cleaning
- Dropped rows with missing `Fuel_Type` (0.41% of data — all Toyota listings)
- Cleaned `Kilometer` column — removed text, converted to integer
- Applied domain threshold of 600,000 km to remove extreme outliers
- Extracted numeric `Final_Price` from raw text (used last/discounted price)
- Cleaned `EMI` column using regex extraction

### Step 4 — Feature Engineering
- `Car_Age` = 2026 − Model Year
- `KM_per_Year` = Kilometer / Car_Age
- `Price_Segment` = Budget (0–5L) / Mid (5–10L) / Upper-Mid (10–20L) / Premium (20L+)
- `Age_Bucket` = 0–3 / 4–6 / 7–10 / 10+ years

### Step 5 — Exploratory Data Analysis
- **Univariate Analysis** — distributions of price, km, age, fuel type, transmission, price segment
- **Bivariate Analysis** — brand vs price, car age vs price, km vs price, fuel vs price, transmission vs price
- **Multivariate Analysis** — brand × price box plots, fuel × transmission, correlation heatmap, price segment by brand, city-wise analysis

---

## 💡 Key Insights

### 💰 Pricing & Market
- **57% of listings are Budget segment** (below ₹5 Lakhs) — India's used car market is heavily budget-driven
- **Median resale price is ₹4.5 Lakhs** — lower than mean (₹5.85L) due to premium outliers

### 🏷️ Brand Performance
- **BMW** has the highest average resale price — ₹15.7 Lakhs
- **Renault and Ford** have the lowest resale values — fastest depreciation
- **Toyota** retains value best among mass-market brands

### 📉 Depreciation Factors
- Cars aged **0–3 years** have the highest average price
- Cars driven **less than 30,000 km** fetch nearly **2× the price** of 100K+ km cars
- **Automatic cars** cost **92% more** on average than manual cars

### ⛽ Fuel Insights
- **Petrol dominates** at 68% of listings — preferred for city driving
- **Diesel cars** are priced higher due to better fuel economy for long distances

### 🏙️ City Insights
- **New Delhi and Noida** together account for the largest share of listings (~25%)
- Southern cities like **Kochi and Coimbatore** show relatively higher average prices

---

## ▶️ How to Run This Project

### 1. Clone the Repository
```bash
git clone https://github.com/GSKReddy-01468/used-cars-sales-eda.git
cd used-cars-sales-eda
```

### 2. Install Required Libraries
```bash
pip install pandas numpy matplotlib seaborn requests beautifulsoup4 openpyxl
```

### 3. Open the Notebook
```bash
jupyter notebook EDA_Project_Cars24_Final.ipynb
```

> **Note:** The raw data and clean data files are already included in the repository.  
> You do not need to run the web scraping section again — directly load `Cars24_Used_Cars_Clean_Data.xls` for the EDA part.

---

## 📁 File Details

| File | Description |
|---|---|
| `EDA_Project_Cars24_Final.ipynb` | Complete notebook — scraping, cleaning, and EDA with observations |
| `Cars24_Used_Cars_Raw_Data.xls` | Raw data as scraped from Cars24 (before any cleaning) |
| `Cars24_Used_Cars_Clean_Data.xls` | Final cleaned and feature-engineered dataset used for analysis |

---

## 👤 Author

**Sivamanikumar Reddy Gogireddy**    
📧 gsivamanikumarreddy2003@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/sivamani-kumar-reddy-gogireddy-346665259)  
🐙 [GitHub](https://github.com/GSKReddy-01468)

---

## 📄 License

This project is for educational purposes as part of Data Analytics training at Innomatics Research Labs.
