## Project
### Generate Insights to Solve a Supply Chain Issue in FMCG Domain

## Problem statement

GDS Mart is a growing FMCG manufacturer headquartered in Gujarat, India. It is currently operational in three cities Surat, Ahmedabad and Vadodara. They want to expand to other metro/tier1 cities in the next 2 years.

GDS Mart is currently facing a problem where a few key customers have not extended the annual contract due to service issues. It is speculated that some of the essential products were either not delivered on time or not delivered in full over a continued period, which could have resulted in bad customer service. Management wants to fix this issue before expanding to other cities and requested their supply chain analytics team to track the ’On time’ and ‘In Full’ delivery service level for all the customers on a daily basis so that they can respond swiftly to these issues.

The Supply Chain team decided to use a standard approach to measure the service level in which they will measure ‘on-time delivery (OT) %’, ‘In-full delivery (IF) %’ and OnTime in full (OTIF) % of the customer orders on a daily basis against the target service level set for each customer.



### Task 

Mr. Analyst is the data analyst in the supply chain team who joined GDS Mart recently. He has been briefed about the task in the stakeholder business review meeting. Now Imagine yourself as Mr. Analyst and play the role of the new data analyst who is excited to build this dashboard and perform the following task:

- Create the metrics according to the metrics list( Below)
- Create a dashboard according to the requirements provided by stakeholders in the business review meeting. You will be provided with the transcript of this business review meeting in the form of a comic.
- Create relevant insights that are not provided in the metric list/stakeholder meeting.



## Data Model 

<p align="center">
  
  <img src="https://github.com/ramtiwari96/Supply-Chain-Issue--Challenge-in-FMCG-Domain/blob/f1d6cb9a63c68465166db2b2ba55557a0f7ec97f/model_Image.png" height="400">
</p>


## Dashboard 


<p align="center">
  <img src="https://github.com/ramtiwari96/Supply-Chain-Issue--Challenge-in-FMCG-Domain/blob/7ccdebfe89b325d3b927419e590349c869b1a894/page1_powerbi_dashboard.png" width="300">
</p>

<p align="center">
  <img src="https://github.com/ramtiwari96/Supply-Chain-Issue--Challenge-in-FMCG-Domain/blob/7ccdebfe89b325d3b927419e590349c869b1a894/page2_powerbi_dashboard.png" width="300">
</p>


<p align="center">
  <img src="https://github.com/ramtiwari96/Supply-Chain-Issue--Challenge-in-FMCG-Domain/blob/7ccdebfe89b325d3b927419e590349c869b1a894/page3_powerbi_dashboard.png" width="300">
</p>

<p align="center">
  <img src="https://github.com/ramtiwari96/Supply-Chain-Issue--Challenge-in-FMCG-Domain/blob/7ccdebfe89b325d3b927419e590349c869b1a894/page4_powerbi_dashboard.png" width="300">
</p>

## Dashboard Overview:
- The dashboard displays key metrics provided by GDS from an FMCG company's supply chain team.
- Major key metrics tracked include OT%, IF%, OTIF%, LIFR (Line Fill Rate), and VOFR (Volume Fill Rate).
- DAX formulas are used for these metrics.
- The dashboard shows the percentage of all these metrics.
- Quantity matrices are also calculated.
- Data is presented with splits by cities, highlighting OT%, IF%, and OTIF%.
- Slicers are used for Month, Day, and Category filters.
- The Product Insight table presents LIFR and VOFR percentages based on product_name and months.
- Line charts display total orders by month and city, with slicers for city, category, and day columns.
- Pie charts depict city by orders, city by delivered orders, and city by undelivered orders.
- Slicers are used for category, product_name, and date columns.


## Tools

- Python - First of all, we imported the data through Python's pandas library, analyzed the data set, and checked that it did not contain any duplicate or missing values.
- Power Bi - After this, we used power bi for data visualization where we created many measures which is given below and prepared a good dashboard to extract useful insights.
  
## DAX MEASURES
### Measures of fact_order_lines
1.	Total Delivery Quantity = SUM(fact_order_lines[delivery_qty])
2.	Total Order Quantity = SUM(fact_order_lines[order_qty])
3.	Total Undeliverd Quantity = [Total Order Quantity]-[Total Delivery Quantity]
4.	total_order_line = COUNT(fact_order_lines[order_id])
5.	LIFR % = DIVIDE(CALCULATE(COUNTA(fact_order_lines[In Full]),fact_order_lines[In Full]=1),[total_order_line])
6.	VOFR % = DIVIDE(SUM(fact_order_lines[delivery_qty]),[Total Order Quantity])


### Measures of fact_order_aggregate
1.	inful_quantity=CALCULATE(COUNTA(fact_orders_aggregate[in_full]),
fact_orders_aggregate[in_full]=1)
2.	on_time_order=CALCULATE(COUNTA(fact_orders_aggregate[on_time]),
fact_orders_aggregate[on_time]=1)
3.	Total_Orders_agg = COUNT(fact_orders_aggregate[order_id])
4.	IF % = DIVIDE([inful_quantity],[Total_Orders_agg])
5.	OT % = DIVIDE([on_time_order],[Total_Orders_agg])
6.	OTIF%=DIVIDE(CALCULATE(COUNTA(fact_orders_aggregate[otif]),fact_orders_aggregate[otif]=1),[Total_Orders_agg])

### Measures of fact_targets_orders

1.	IF Traget% = AVERAGE(dim_targets_orders[infull_target%])
2.	OT Traget % = AVERAGE(dim_targets_orders[ontime_target%])
3.	OTIF Traget% = AVERAGE(dim_targets_orders[otif_target%])


## Some Major Insights 

- All the Key Metrics (OT%, IF%, OTIF%) are far behind the target
- Surat has fewer orders and delivered orders than other cities, but Vadodara has more undelivered Orders.
- On an average, orders are delayed 0.42 days from the agreed date of delivery
- Highest orders are coming in Vododara City
- Ghee, curd and butter products are most delayed to deliver. 
- There is no noticeable improvements in any of the key metrics in the last few months
- There is a huge gap in IF% for most of the customers. Is it because of less production?
