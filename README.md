# Power-BI-Portfolio_HR-Analytics-Project

![](Human_Resource.jpg)

## Introduction & Project Overview ##

**SH Group**, founded in 1982, is a multinational retail organization operating across multiple regions with a large and diverse workforce. Over the years, the company has accumulated a significant volume of data across its core business functions, including Sales, Marketing, Finance, and Human Resource Management.

As the organization continued to grow, HR leadership identified the need for a data-driven approach to workforce management. Traditional reporting methods were no longer sufficient to provide timely and actionable insights into employee demographics, performance trends, satisfaction levels, and workforce stability.

To address this challenge, an HR Analytics initiative was launched to consolidate and analyze employee-related data. The objective of this project was to transform raw HR data into meaningful insights that support strategic decision-making in areas such as employee retention, performance management, and workforce planning.

Using Power BI, this project analyzes key HR datasets covering employee profiles, performance reviews, satisfaction levels, and education background. The resulting dashboards enable HR managers and senior leadership to:

The resulting dashboards enable HR managers and senior leadership to:

📈 Understand workforce composition and demographics

🔍 Identify performance and satisfaction patterns

🎯 Support proactive planning and retention strategies

This project demonstrates how business intelligence (BI) tools can be applied to HR data to improve organizational effectiveness and align people strategies with business goals.

## 🛠️ Skills Demonstrated ##

This project demonstrates the end-to-end Power BI workflow, covering data preparation, modeling, analysis, and dashboarding.

### 🔄 Data Preparation / ETL Process (Power Query) ###

- 📥 Extracted raw HR data from the web and created Fact and Dimension tables.

- 🧹 Cleaned and transformed data: removed unnecessary columns, handled blanks/errors, replace abbreviations, created custom columns, ensured correct data types etc.

- 🔑 Created duplicate dimension table to build proper data model (explained in the model overview Section). Removed duplicates from dimension tables to maintain integrity.


![Data Transformation – Employee Table](Images/Power_Query_Data_Cleaning_Employee_Table.jpg)
  

### 🗂️ Data Modeling ###

- 📅 Built separate Date Tables (Dim_Date) for accurate time-series analysis (Year-over-Year, Qtr-Over-Qtr, Month-over-Month). we

- ⭐ Designed a Star-Oriented Fact Constellation Schema with multiple fact tables (Fact_Employee & Fact_Performance Rating) and dimension tables (Dim_Date Table, Dim_Manager_Rating Table, Dim_Self_Rating Table, etc. ).

- 🔗 Established 1-to-many and one-way filter propagation relationships for consistent and correct insights.


### 📊 Data Analysis (DAX) ###

- ➕ Created calculated columns and measures: By applying DAX Formulas and Functions, we have calculated core metrics like Total Employees, Reviewed Employees, Attrition Count, Attrition Rate (Population), Attrition Rate (Sample), Attrition Risk, Overall Employee Satisfaction, Overall Employee Performance, Average Salary, Average Tenure etc.

- 🧮 Applied functions like CALCULATE, AVERAGE, AVERAGEX, DIVIDE, DISTINCTCOUNT, SELECTEDVALUE, SWITCH, MINX, MAXX, UNION, SELECTCOLUMNS, ADDCOLUMNS etc.
  We have also used variables to store the temporary results of a calculation so that we can reduce the no. of measure. 

- ⏳ Enabled time intelligence with CALENDAR, YEAR, MONTH, DAY, FORMAT etc.

  ![DAX Measure - Overall Employee Satisfaction](Images/DAX_Measure_Overall_Employee_Satisfaction.jpg)

### 📈 Data Visualization ###

- 📉 Line Charts → To show Attrition, Performance, and Satisfaction Trends over time (Year-over-Year, Month-over-Month, Quater-over-Quater).

- 🗂️ Cards → To demonstrate Key KPIs (Total Employee's, Reviewed Employee's, Attrition Count, Attrition Rate, Overall Employee Satisfaction, Overall Employee Performance etc.).

- 📊 Bar/Column/Cluster Column/Stacked Bar Charts → To compare Attrition, Performance, Satisfaction by Department, Job Role, Gender, Age Group etc.

- 🥧 Pie Chart → To exhibit part-to-whole composition. For Example, Employee by Gender, Age Group, Ethnicity etc.

  We have also demonstrated other important visuals like Map Chart, Treemap, Matrix, Table etc. However, we try to use common charts most so that different   stakeholders or non-technical people can easily understand the essence. 

### 🎛️ Interactive Dashboard ###

- 🎛️ Added slicers, drill-downs, drill-through, tooltips, and navigation buttons for interactivity.

- 🎨 Delivered a business-friendly, interactive dashboard that supports strategic decision-making.


## Data Structure / Model Overview ##


![Data Model](Images/Data_Model.jpg)

The data model for this HR Analytics project was designed using Power BI best practices, focusing on clarity, correctness, and maintainability. A star-schema–oriented structure was implemented to ensure predictable filter behavior, good performance, and minimal DAX complexity.

The model is centered around a FactPerformanceRating table containing employee performance review data, supported by several dimension tables, most notably Fact_Employee (act as _Dim Table also) and Dim_Date.

*Key modeling decisions and activities include:*

-A clear distinction was maintained between all employees and reviewed employees to avoid biased attrition calculations, as not all employees were considered for performance review. Employee-centric KPIs or Visual's (Total Employees, Active Employees, Attrition Count) were calculated from Fact_Employee, where Employee-Performance or Satisfaction related KPIs or Visual's (Reviewed Employee, Attrition  Rate [Reviewed]) were calculated from Fact_PerformanceRating Table.

-A single Date dimension was used to support both Hire Date and Performance Review Date, enabling consistent time-based analysis.

-Mixed regional date formats (EU and US) were standardized during Power Query (M) data preparation using locale-aware transformations.

-Relationships were designed as one-to-many and single-directional (dimension → fact) to preserve model stability and avoid ambiguous filter propagation.

- Role-playing dimension tables were intentionally implemented for satisfaction and rating attributes:

    -The original Satisfaction Level dimension was duplicated into separate dimension tables for Job
     Satisfaction, Work-Life Balance, Work Environment Satisfaction, and Relationship Satisfaction.

    -Similarly, the Rating Level dimension was duplicated to support Manager Rating and Self Rating
     independently.

This approach avoided reliance on inactive relationships and repeated use of USERELATIONSHIP() or other complex DAX patterns.

-Lookup dimensions (Satisfaction Level, Rating Level, Education Level) were used for semantic clarity and clean slicing, rather than forcing complex filtering logic in measures.

Overall, the model follows a “model-first, simple DAX” philosophy, reflecting real-world BI practices where strong data modeling significantly reduces the need for complex calculations while improving reliability and explainability.  


## Dashboard Overview: Executive Summary / Key Insights ##

### Sales Insights: ###

![Dashboard 01: Employee Demographics](Images/Dashboard_01_Employee_Demographics.jpg)

This is the overall sales insights dashboard. It highlights key KPIs like Total orders, Total Sales, Total Profit, and Profit Margin. This also compares year-over-year Total Sales and Profit Growth. The Dashboard shows following insights: 

1. Revenue shows a strong upward trend from 2015 to 2017, after remaining relatively flat between 2014 and 2015. The largest year-over-year growth occurred between 2015 and 2016, indicating a turning point in sales performance and possible improvements in market demand, pricing, or sales strategy.

2. Profit increased consistently year over year, with growth rates of 24%, 33%, and 14% respectively. However, despite rising profits, the overall profit margin remains low at 2.89%, suggesting that costs are growing almost proportionally with revenue. This indicates limited pricing power or high operational/discount costs.

3. A clear seasonal sales pattern is observed across all years, with Q4 consistently generating the highest revenue, followed by Q3, Q2, and Q1. This suggests strong year-end demand, likely driven by holiday seasons and promotional campaigns, and highlights the importance of inventory and marketing planning ahead of Q4.

### Product Insights: ###

![Overall Product Insights](/Images/Product%20Insights_Overall.jpg)

This is the overall product insights dashboard. It compares product categories and sub-categories as well as shows best and worst performing products in terms of total sales or revenue. The Dashboard shows following Insights: 

1. "Technology" is the highest revenue-generating product category, significantly outperforming "Furniture" and "Office Supplies". This indicates a strong customer demand for technology             products and suggests that this category is a key driver of overall sales performance.

2. At the sub-category level, Chairs generate the highest revenue, followed by Phones, Storage, Tables, and Accessories. This highlights that high-value, durable goods contribute more to           revenue than low-cost consumables, even if their sales volumes may be lower.
   
3. The "Cannon imageCLASS 2200 Advanced Copier" is the top-performing product, followed by the "GBC Ibimaster 500 Manual ProClick Binding System" and the "HON 5400 Series Task Chair for Big and    Tall". These products contribute disproportionately to revenue, indicating a reliance on high-ticket items.

   In contrast, "PNY Rapid USB Car Charger – Black", "Grip Seal Envelopes", and "Acco Economy Flexible Poly Round Ring Binder" are among the lowest-performing products, likely due to lower         price points, high competition, or limited differentiation.
  
4. A regional and year-specific analysis reveals significant variation in best- and worst-performing categories, sub-categories, and products compared to the overall dataset. This highlights the importance of localized and time-based analysis, as global averages can mask regional demand patterns and lead to sub-optimal business decisions.

   
### Consumer Insights: ###

![Overall Consumer Insights](/Images/Consumer%20Insights_Overall.jpg)

This is the overall consumer insights dashboard. It demonstrates which consumer segment, region, and states contributing most to our revenue. It also reveals product preferences by segment and geography. Key Insights are described below: 

1. The dataset consists of three customer segments: Consumer, Corporate, and Home Office. Among them, the Consumer segment contributes the highest share of total revenue, followed by Corporate     and Home Office.

   In terms of product preferences, the Consumer segment primarily purchases Furniture, followed by Technology and Office Supplies. In contrast, both Corporate and Home Office customers show a     stronger preference for Technology products, with Office Supplies and Furniture ranking second and third, respectively. This indicates distinct purchasing behaviors across customer segments,    emphasizing the importance of segment-specific product strategies.

2. From a geographic perspective, the West region is the highest revenue-contributing region, followed by East, Central, and South.

   At the state level, California leads sales in the West, followed by Washington and Arizona. In the East, New York is the top-performing state, followed by Pennsylvania and Ohio. Texas           dominates the Central region, with Illinois and Michigan as the next highest contributors, while North Carolina leads in the South, followed by Georgia and Virginia.

   Across all regions, each product category generates a reasonable share of revenue, although their relative performance varies slightly by region. This highlights the importance of regional-     level analysis rather than relying solely on global performance trends.

3. Analysis of shipping preferences shows that Standard Class is the most commonly used shipping mode, accounting for approximately 60% of all shipments. This is followed by Second Class (around 20%), First Class (around 15%), and Same Day Delivery (approximately 5%).

   The dominance of Standard Class suggests that most customers prioritize cost efficiency over delivery speed, while faster shipping options are used selectively for time-sensitive orders. 


## Dashboard Overview: One Level Details / Deeper Insights ##

Each Dashboard can also be drill-down by a specific year or region to see a particular year or geographic details. Results vary significantly compared to the overall dataset, allowing deeper exploration of temporal and regional analysis. 

To see the full details, we recommend to download the complete Dashboard (Power BI file). 

## Conclusion ##

The Superstore Sales Data Analytics project demonstrates how raw sales data can be transformed into actionable business insights using Power BI. Through structured data preparation, modeling, DAX calculations, and interactive visualization, the dashboard provides a 360° view of sales, products, and consumer behavior.

**Key Insights Delivered:**

- 📈 Identified overall and year-specific sales & profit growth trends.

- 🛍️ Highlighted best- and worst-performing products, product categories, and sub-categories across regions and time-frames.

- 👥 Analyzed customer segments and geographic markets contributing most to revenue.

- 🎛️ Delivered an interactive, user-friendly dashboard that supports data-driven decision-making for business development and sales strategy.

**Key Takeaways from this project**

- I understood the importance of proper data modeling (Star Schema) to ensure accurate and efficient analysis.

- I practiced writing DAX measures for KPIs such as profit margin, sales growth, and customer segmentation, which deepened my understanding of DAX functions.

- I learned how much value interactive features (slicers, drill-downs, tooltips, navigation) bring to a dashboard, making it easier for users to explore insights on their own.

- Most importantly, I realized that data visualization is not just about charts—it’s about telling a story that supports business planning.

Overall, this project improved both my technical Power BI skills and my ability to think from a business perspective. It reflects my ability to design, build, and deliver BI solutions that not only visualize data but also provide meaningful insights for strategic planning.
