# Customer Segmentation with RFM Analysis and K-Means Clustering

## Project Overview
In this project, I analyzed retail transaction data to better understand customer behavior and group customers into meaningful segments. I used **RFM analysis** and **K-Means clustering** to identify patterns in how recently customers purchased, how often they bought, and how much they spent.

The goal was to turn raw transaction data into useful customer groups that a business could use for more personalized marketing, stronger retention efforts, and better decision-making.

## Why I Did This Project
Not all customers behave the same way. Some are loyal and highly valuable, some are new and still growing, and some have become inactive over time. Treating all customers the same can lead to missed opportunities.

This project was built to answer questions like:
- Who are the most valuable customers?
- Which customers are becoming inactive?
- Which groups have the most revenue potential?
- How can different customer segments be targeted in different ways?

## Dataset
- **File used:** `online_retail_II.xlsx`
- **Source:** [Add Kaggle dataset link here](PASTE_KAGGLE_LINK_HERE)
- **Note:** The raw dataset is not included in this repository.

## Tools Used
- Python
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- Jupyter Notebook

## What I Did
Here’s the overall workflow I followed in this project:

1. Loaded the retail transaction dataset  
2. Checked the data structure and missing values  
3. Removed rows with missing customer IDs  
4. Removed invalid transactions such as negative quantities and prices  
5. Removed cancelled invoices  
6. Created a total spending column  
7. Converted invoice dates into datetime format  
8. Built an RFM table for each customer  
9. Standardized the RFM values using `StandardScaler`  
10. Used the Elbow Method to decide on the number of clusters  
11. Applied K-Means clustering with 5 segments  
12. Assigned business-friendly names to the customer groups  
13. Visualized the customer segments  
14. Created RFM scores  
15. Measured revenue contribution by segment  
16. Added strategy ideas for each customer group  

## Data Cleaning
To make sure the analysis reflected real purchase behavior, I cleaned the dataset by:
- removing missing `Customer ID` values
- keeping only rows where `Quantity > 0`
- keeping only rows where `Price > 0`
- removing cancelled invoices that start with `C`

## Dataset Snapshot
A few useful details from the notebook:

- **Original dataset size:** 525,461 rows × 8 columns  
- **Missing customer IDs:** 107,927  
- **Rows after cleaning invalid purchases:** 407,664  
- **Final RFM table:** 4,312 customers × 3 features  

## Feature Engineering

### Total Amount
I created a new column to calculate how much each transaction was worth:

`TotalAmount = Quantity × Price`

This was later used to calculate each customer’s total spending.

### RFM Features
For each customer, I calculated:

- **Recency:** how many days since their last purchase  
- **Frequency:** how many unique invoices they had  
- **Monetary:** how much they spent in total  

These three values became the foundation of the segmentation.

## Clustering Approach

### Why RFM?
RFM is a simple but powerful way to understand customer value. It helps answer:
- who bought recently
- who buys often
- who spends more

### Why K-Means?
I used K-Means because it is a popular clustering algorithm for grouping similar customers based on behavior.

Since K-Means is distance-based, I standardized the RFM values first so one feature would not dominate the others.

### Elbow Method
To choose the number of clusters, I tested values from **2 to 10** and plotted the inertia values. Based on the elbow curve, I selected **5 clusters**.

### Final Model Settings
- `n_clusters = 5`
- `random_state = 42`
- `n_init = 10`

## Customer Segments
After clustering, I mapped the clusters into more business-friendly segment names:

- **Champions**
- **Loyal Members**
- **Potential Loyalists**
- **New Enthusiasts**
- **Hibernating**

### Segment Counts
Based on the notebook results:

- **New Enthusiasts:** 3,053  
- **Hibernating:** 1,038  
- **Potential Loyalists:** 208  
- **Champions:** 10  
- **Loyal Members:** 3  

## Visualizations
This project includes:
- a **scatter plot** showing `Frequency` vs `Monetary` by customer segment
- a **bar chart** showing revenue contribution by customer segment

These visuals help make the segment behavior easier to understand.

## RFM Scoring
In addition to clustering, I also created an **RFM scoring system** using quantiles.

The notebook builds:
- `R_score`
- `F_score`
- `M_score`

These are combined into:
- `RFM_Score`

This gives another way to compare customer value across groups.

### Average RFM Score by Segment
- **Champions:** 15.00  
- **Loyal Members:** 15.00  
- **Potential Loyalists:** 14.53  
- **New Enthusiasts:** 9.92  
- **Hibernating:** 5.22  

## Revenue Contribution by Segment
I also calculated how much each segment contributed to total revenue.

### Revenue Contribution
- **New Enthusiasts:** 47.60%  
- **Potential Loyalists:** 28.84%  
- **Loyal Members:** 8.99%  
- **Champions:** 7.51%  
- **Hibernating:** 7.05%  

This helps show which customer groups matter most from a revenue perspective.

## Business Recommendations
One useful part of this project was turning the segments into practical business actions.

Some examples:
- **Champions** → VIP rewards, referral incentives, early access offers  
- **Loyal Members** → loyalty programs, premium offers, retention campaigns  
- **Potential Loyalists** → personalized recommendations, bundle offers  
- **New Enthusiasts** → onboarding campaigns, welcome offers  
- **Hibernating** → re-engagement campaigns, win-back discounts  

## What This Project Shows
This project shows how customer transaction data can be turned into actionable business insight. Instead of looking at customers as one big group, it becomes possible to understand different types of customers and make smarter marketing decisions for each one.

## Limitations
The segmentation was useful from a business perspective, but the cluster sizes were somewhat imbalanced. That means the results were helpful, but there is still room to improve the model.

In a future version, I would explore:
- additional feature transformations
- more cluster validation methods
- other clustering algorithms besides K-Means

## Files in This Repository
- `customer_segmentation.ipynb` — full notebook with data cleaning, RFM analysis, clustering, scoring, and visualizations
- `README.md` — project documentation

## How to Run
1. Open the notebook in Jupyter Notebook or JupyterLab  
2. Install the required Python libraries  
3. Place `online_retail_II.xlsx` in the same folder as the notebook  
4. Run the notebook cells step by step  

## Future Improvements
- Add screenshots of the visualizations to the repository  
- Test additional clustering methods  
- Add more validation metrics  
- Build a simple interactive dashboard  
