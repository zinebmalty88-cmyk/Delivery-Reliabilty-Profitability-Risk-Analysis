# Delivery-Reliabilty-Profitability-Risk-Analysis
Delivery performance analysis exploring late deliveries, shipping efficiency, and profitability risk using SQL and Tableau.

## Project Overview

This project is part of the Google Data Analytics Capstone and focuses on analyzing key delivery-related metrics using a real world supply chain dataset.

The objective is to examine patterns of late deliveries, identify the worst-performing regions, shipping modes, and product categories, and explore the relationship between delivery reliability and profitability.

The analysis highlights the top 5 worst-performing segments to support targeted insights and decision-making.

It covers three years (2015–2017) and includes an interactive dashboard with a year filter for time based trend analysis.
Data from 2018 was excluded as it only contains one month of records.

## Ask Phase

### Business Problem

The company is experiencing a high rate of late deliveries, affecting delivery reliability across different regions, shipping modes, and product categories.

Despite this, profitability shows a slight increase, raising questions about the alignment between operational performance and business outcomes.

### Business Objective

The objective of this analysis is to:
	•	Identify patterns of late deliveries
	•	Detect the worst-performing regions, shipping modes, and product categories
	•	Compare planned vs actual delivery performance
	•	Evaluate the relationship between delivery reliability and profitability


### Key Questions

	•	Which regions have the highest late delivery rates?
	•	Which shipping modes are most associated with delays?
	•	Which product categories show the highest delivery risk relative to order volume?
	•	How has late delivery performance evolved over time (2015–2017)?
	•	What is the gap between scheduled and actual shipping duration?
	•	How does profitability relate to delivery risk across categories?

### Stakeholders

	•	Operations Manager
	•	Logistics Team
	•	Inventory Manager

### Target Audience

	•	Business decision-makers
	•	Supply chain and operations teams

## Prepare Phase

### Data Source

The dataset used in this project is the DataCo Global Supply Chain Dataset, obtained from Kaggle.

It contains real world supply chain operations data across multiple business areas, including:
	•	Provisioning
	•	Production
	•	Sales
	•	Distribution

### Data Structure
	
  •	Format: CSV
	•	Records: 180,000+ rows
	•	Columns: 50+ variables

A new working table was created using SQL by selecting and transforming only the relevant columns required for the analysis.

The final dataset includes key variables such as:
	•	Order_Id
	•	Days_for_shipping_real
	•	Days_for_shipment_scheduled
	•	Late_delivery_risk
	•	Delivery_Status
	•	Shipping_Mode
	•	Category_Name
	•	Order_Region
	•	Order_Country / Customer_Country
	•	Order_date_DateOrders
	•	Shipping_date_DateOrders

### Data Scope

	•	Time period analyzed: 2015–2017

The dataset includes data for 2018 but it only contains one month of records therefore, the analysis focuses on the years 2015–2017 to ensure consistent and comparable yearly insights.



### Data Credibility (ROCCC)

	•	Reliable: Large dataset suitable for analysis
	•	Original: Sourced from a recognized data repository (Kaggle / Mendeley)
	•	Comprehensive: Covers multiple aspects of supply chain operations
	•	Current: Contains sufficient historical data for trend analysis
	•	Cited: Widely used in supply chain research


### Data Limitations

	•	The dataset represents a single company (DataCo Global)
	•	Some variables may not fully capture operational complexity
	•	The dataset is historical and may not reflect current conditions

## Process Phase

Data cleaning and transformation were performed using SQL (BigQuery) to prepare the dataset for analysis.

### Data Preparation Steps

	•	Created a new working table by selecting and retaining only the relevant columns
	•	Checked for missing values in key fields and confirmed data completeness
	•	Standardized categorical fields using TRIM() and UPPER() to ensure formatting consistency
	•	Verified that date and numeric fields were correctly formatted using the schema
	•	Reviewed shipping duration fields (real vs scheduled) to ensure logical values
	•	Verified that there are no duplicate records in the dataset,Several records were identified with the same order_id,upon investigation, these records represent multiple items within a single order rather than duplicate errors.  

→ The final dataset is clean, structured, and ready for analysis.
→ SQL queries used for data cleaning and analysis are available in the /sql folder.

## Analyze Phase

The analysis focuses on key delivery-related metrics to identify patterns of late deliveries and evaluate performance across regions, shipping modes, and product categories over the period 2015–2017.

### Key Insights

- Out of approximately 178K orders, 54.81% are delivered late, while only 17.84% are delivered on time and 23.05% arrive early (advanced).
The cancellation rate remains very low, indicating strong customer retention despite service delays.
→  This highlights a significant imbalance in delivery performance, where late deliveries dominate the system.

- Late delivery rates remain relatively stable across 2015–2017, showing no significant improvement over time.

- Central Africa records one of the highest delay rates (~57.96%), consistently across the three-year period, highlighting persistent regional inefficiencies.

- First Class shipping shows the highest exposure to delays across all three years, indicating underperformance of premium shipping services.

- Significant gaps exist between scheduled and actual delivery times across shipping modes:
	• Second Class: Scheduled for 2 days, but actual delivery averages ~3.99 days, resulting in a high late rate (~85.56%)
	• Same Day: Scheduled for 0 days, with an actual average of ~0.48 days, but the target is missed 72.57% of the time
	• Standard Class: The only mode where scheduled (4 days) aligns with actual delivery time, resulting in the lowest delay rate
→ This indicates inefficiencies in delivery planning and execution
→ The logistics system is optimized for high volume, low-speed delivery, while faster shipping options are not reliably supported

- Category level analysis reveals critical delivery risks:
	• Golf Bags & Carts (68.85% late, low volume) suggests issues related to bulky or non standard items
	• High volume categories such as Cameras (58% late) indicate internal processing limitations

- Categories with higher average benefit per order tend to fall within the high-profit / high-risk zone.
  → This creates a risk to both customer satisfaction and long-term business performance .
The overall late delivery rate reaches 54.81%, and most categories perform close to this level.
  →  This indicates that delays are not limited to specific categories but are widespread across the system.

- Profitability shows a slight increase, while delivery performance remains unchanged, indicating misalignment between business growth and operational efficiency

### Overall Conclusion

The consistently high delay rates across regions, shipping modes, and product categories indicate that the issue is systemic rather than localized.

## Share Phase

An interactive dashboard was developed using Tableau to present delivery performance insights and highlight operational risks across regions, shipping modes, and product categories for the period 2015–2017.
The dashboard is structured to guide decision makers from high-level KPIs to detailed performance breakdowns

### Dashboard Overview 

![Dashboard](https://github.com/user-attachments/assets/b0b2a013-6550-4f3b-a14b-ad601bd3dcd7)

At the top level, key performance indicators provide a quick summary

	•	Total Orders: 178K
	•	Average Benefit per Order: 22.05 
	•	Average Actual Shipping Time: 3.50 days
	•	Overall Late Delivery Rate: 54.81%

→ These KPIs highlight a high delay rate despite stable profitability, while the average actual shipping time (3.5 days) does not meet expected delivery timelines.
  
###  Delivery Performance Breakdown

The Overall Delivery Status chart shows that late deliveries represent the largest share, exceeding both on time and early deliveries, while cancellations remain minimal
The Late Delivery Rate by Region visualization highlights the top 5 worst performing regions, with Central Africa (57.96%) leading
→ This enables quick identification of geographically concentrated inefficiencie. 

- Shipping Mode Analysis
  
	 •	The Late Delivery Rate by Shipping Mode chart shows that:
	  •	First Class has the highest delay rate
	  •	Followed by Second Class and Same Day
	  •	Standard Class performs relatively better
→ This reveals that faster shipping options underperform compared to expectations

 - Category Performance
   
	•	The Late Delivery Rate by Category vs Orders Volume chart highlights:
	•	High delay rates even in low volume categories ( Golf Bags & Carts)
	•	High delay rates in high-volume categories (Cameras)
→ This indicates both specialized handling issues and capacity limitations

- Time Trend Analysis
  
   • The Late Delivery Trend by Year shows that delay rates remain stable across 2015–2017, with no significant improvement
→ This confirms that the issue is persistent rather than temporary

- Delivery Time Efficiency
	•	The Scheduled vs Actual Shipping Duration chart shows clear gaps:
	•	Second Class significantly exceeds planned delivery time
	•	Same Day frequently misses its target
	•	Standard Class aligns closely with planned delivery
→ This highlights inefficiencies in delivery planning and execution

 - Profitability vs Delivery Risk
	• The Category Profitability vs Delivery Risk chart shows that most categories fall within the high-risk zone, including the most profitable ones.
	•	A visual threshold (20%) is used to distinguish between acceptable and high-risk performance
→ This demonstrates that high profitability is associated with higher delivery risk

- Design & Interaction Choices
	• A Top 5 filtering approach was applied to focus on the most critical performance issues
	• Interactive filters were integrated into key visuals, including:
	• Late delivery rate by region
	• Late delivery rate by category vs order volume

- These filters allow users to explore specific segments dynamically
	•  Color encoding:
	• Red → Critical delay levels
	• Orange → Warning levels
	• Bubble size represents average benefit per order, enabling comparison between profitability and risk
	• An interactive year filter allows analysis across 2015–2017

### Key Takeaway

The dashboard highlights that delays are consistently high across regions, shipping modes, and categories, while profitability remains stable. 

## Act Phase

Based on the analysis, several recommendations can be made to improve delivery performance and reduce operational risk.

- Optimize Handling of High-Risk Categories
	•	Implement specialized handling processes for bulky or non-standard items (eg Golf Bags & Carts)
	•	Improve internal processing for high-volume categories (eg Cameras)
→ This reduces delays caused by packaging and capacity limitations

- Improve Planning and Scheduling Accuracy
  •	Review the execution of First Class, Second Class, and Same Day shipping
  •	Align promised delivery times with actual operational capacity
	-	Improve demand forecasting and resource allocation
→ This enhances delivery time accuracy and operational efficiency

- Balance Profitability and Delivery Risk
  • Monitor high profit categories that also show high delivery risk
  • Ensure that revenue growth is not achieved at the expense of service reliability
 → This protects long term customer satisfaction and business sustainability

- Implement Performance Monitoring
  •Track key KPIs such as:
  • Late delivery rate
  •	Shipping duration gap
  •	Performance by region and category
  •	Use dashboards to monitor performance continuously and support decision-making
→ This enables proactive management of delivery performance

##  Conclusion

This analysis revealed that delivery delays are widespread across all area of the business.
Despite stable profitability, delivery performance remains poor, with more than half of orders delivered late and no significant improvement over time.
The findings highlight a clear misalignment between operational efficiency and business performance, emphasizing the need for improvements in planning, execution, and service reliability and addressing these issues is essential to enhance customer satisfaction and ensure sustainable business growth.





