# Product Sales Analysis: Optimizing Sales Methods for New Stationery Line

## 📄 Project Background
**Pens and Printers**, a trusted provider of high-quality office products founded in 1984, recently launched a new line of stationery focused on creative brainstorming tools. 

In response to changing consumer behavior, the company tested three different sales strategies to identify the most effective approach for this new product line:
1. **Email**: Targeted emails at launch and 3 weeks later.
2. **Call**: Direct phone calls from the sales team (avg. 30 mins/customer).
3. **Email + Call**: An initial email followed by a shorter needs-assessment call (avg. 10 mins/customer).

## 🎯 Business Goals
The executive team requires a data-driven recommendation on which sales method to scale. The analysis focuses on:
* **Reach**: How many customers were acquired per method?
* **Revenue**: What is the spread of revenue for each method?
* **Trends**: How did revenue evolve over the 6-week post-launch period?
* **Efficiency**: Which method yields the best return on time invested?

## 🧹 Data Validation & Cleaning
The raw dataset (`product_sales.csv`) contained 15,000 records. The following steps were taken to ensure data integrity:
* **Standardization**: The `sales_method` column contained inconsistencies (e.g., "em + call", "email"). These were standardized to: `Email`, `Call`, and `Email + Call`.
* **Missing Values**: 1,074 entries had missing `revenue` data. These were imputed by calculating the median *price-per-unit* for the respective sales method and multiplying by `nb_sold`.
* **Outlier Removal**: Two records showed `years_as_customer` > 40 (impossible given the company's 39-year history). These were removed to prevent skewing tenure analysis.

**Final Dataset**: 14,998 clean records.

## 📊 Exploratory Data Analysis (EDA)

### 1. Customer Count by Approach
The **Email** strategy reached the largest audience (approx. 50% of customers), acting as a low-effort "wide net." The **Email + Call** strategy was the most targeted, reaching the fewest customers.

![Customer Count](images/barchart.png.png)

### 2. Revenue Spread
Revenue distribution is distinct for each method. 
* **Call**: Low variance, consistently generating lower revenue ($30-$70).
* **Email + Call**: High variance with a significantly higher median, indicating this method is effective at upselling larger baskets of goods ($120-$240).

![Revenue Boxplot](images/boxplot.pngboxplot.png)

*Overall Distribution showing the distinct tiers:*
![Overall Revenue](images/histogram.png.png)

### 3. Revenue Trends Over Time
* **Email**: "Front-loaded" success. Revenue peaked in Week 1 and declined steadily.
* **Email + Call**: "Momentum builder." Revenue started slow but **surged in Weeks 5 & 6**, eventually generating the highest weekly revenue of any method.

![Revenue Trends](images/lineplot.png.png)

## 📈 Metric Definition: Average Revenue Per Customer
To monitor future performance, I recommend tracking **Average Revenue Per Customer**. This metric normalizes results regardless of the volume of customers contacted.

| Method | Avg. Revenue | Time Spent (est.) | Revenue / Hour (est.) |
| :--- | :--- | :--- | :--- |
| **Call** | $47.65 | 30 mins | ~$95 |
| **Email** | $97.18 | ~0 mins | N/A (High) |
| **Email + Call** | **$184.28** | 10 mins | **~$1,100** |

## 💡 Final Recommendations

1.  **Adopt "Email + Call" as the Primary Strategy**: 
    * It generates nearly **4x the revenue** of calling alone.
    * It is significantly more time-efficient, requiring only 10 minutes of active sales time compared to 30 minutes for cold calling.
    
2.  **Discontinue the "Call Only" Method**: 
    * It is the least efficient use of resources, generating the lowest revenue per customer while consuming the most time.

3.  **Retain "Email Only" for Low-Priority Leads**: 
    * While it generates less revenue per customer than the hybrid approach, its near-zero marginal cost makes it perfect for covering the remaining customer base that the sales team cannot personally contact.

## 🛠️ Setup & Requirements
This analysis was performed using Python.

**Libraries used:**
* `pandas` (Data manipulation)
* `matplotlib` & `seaborn` (Visualization)

**To run the analysis:**
1.  Clone this repository.
2.  Ensure `product_sales.csv` is in the root directory.
3.  Run the Jupyter Notebook or Python script to reproduce the findings.