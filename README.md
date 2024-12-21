README

1.)	Overview:
This project leverages a fictional dataset from a coffee shop, “Cosmic Café,” to analyze customer behavior and marketing effectiveness. The data includes marketing channels, reward offer types, customer demographics, and spending trends within the first 30 days of membership. The goal is to identify patterns and propose strategies to maximize profitability while showcasing analytical skills.
2.)	Data Sources and Structure
Data Tables:

Customers_dim
-	Columns: customer_num, income, age_group, day_name, start_of_week, start_of_month, start_of_year, month_name, start_of_quarter, year, customer_id, gender, age, became_member_on, month, week_of_year
  
Events_dim
-	Columns: event_id, event
  
Events_facts
-	Customer_num, event_id, time, offer_id, amount_spent, reward, day_of_month
  
Offers_dim
-	Columns: offer_num, offer_id, offer_type, reward, channels, web, email, mobile, social
Relationships:
-	Offers_dim: offer_num (Primary Key) // events_facts: offer_id (Foreign Key)
-	Customers_dim: customer_num (Primary Key) // events_facts: customer_num (Foreign Key)
-	Events_dim: event_id (Primary Key) // events_facts: event_id (Foreign Key)
  
3.)	Dashboard Pages and Features

Page 1: Home Page
-	KPIs: Number of Transactions, Total Sales Amount, Rewards Given
-	Figures: Sales Time Series, Sales, and Rewards For the Day of Month, Count of Transactions, and Rewards
-	Filters: 2013 – 2018, January – December
  
Page 2: Breakdown
-	KPIs: Ratio (Rewards/Reward Offers), Ratio (Rewards/Viewing Offers), Ratio (Viewing Reward Offer/Receiving Reward Offer), Ratio (Customer Purchase/Viewing Reward Offer), Ratio (Customer Purchase/Receiving Reward Offer)
-	Figure: Number of Rewards broken down by age

Page 3: Top 500 Customers
-	Figures: Customer Spending vs Income, Customer Purchase per Number of Reward Offers Viewed, Reward breakdown by age group. 
-	Filters: 2013 – 2018, January – December

4.)	Measures
Measures include ‘Total Customers’, ‘Total Offers’, Count of Email Offers’, Time to Complete Reward etc. 
Ex:
Total Income = SUM(customer_dim[income])

5.)	About the Data

The dataset provided by Kaggle is featured on the Maven Analytics platform.
Data Transformation and Calculations:
I created a relational database centered around 1 facts table displaying every customer event (e.g. transaction, received rewards, completed reward offer, etc.). Three dimensional tables linked to the event table (customers, events, and offers).
The “customers” table included – customer ID, gender, age, income, and member sign-up date.
The “events” table included the event ID (e.g. offer received, transaction, offer completed, etc.).
The “offers” table included the offer ID, the offer type, which marketing channel the offer came from, and the counts of the marketing channels responsible for an offer. (e.g. offer 1, a buy one get one free offer, was presented through three channels (email, mobile, and social media). The email, mobile, and social media columns display a “1”, while the web column is a “0”).
The initial difficulty came when the raw data contained a column with dictionaries as values. I needed to extract transaction amounts or offer IDs from the dictionary values. I enjoyed the learning opportunities as the data was not originally clean.
I utilized DAX to create measures for my analysis.
Notable measures include total sales, total rewards, total customers, percent of a particular marketing channel, count of each event (transaction, reward, etc.), and the ratios of events to one another (e.g. transactions per reward offer received).


6.) Key findings:

· Between 2014 and 2018, 4 distinct moments occurred where sales numbers changed. These moments were stagnant for a period ranging from a few months to a couple of years. The periods are referenced as plateaus due to the shape of a time series line chart.
o Plateau 1 “P1” (Jan 5, 2015 – April 26, 2015)
o Plateau 2 “P2” (Mar 6, 2017 – Jun 25, 2017)
o Plateau 3 “P3” (Aug 7, 2017 – Dec 3, 2017)
o Plateau 4 “P4” (Feb 5, 2018 – Jan 3, 2018)
________________________________________
· The number of transactions and offers followed the same shape throughout all 4 years in a 2:1 ratio. The shape also follows the total sales time series suggesting that the number of transactions is the primary predictor of total sales.
· On average, the second half of the thirty days following a member sign-up, shows more sales and customer rewards. This suggests that rewards are a predictor of how much a customer spends. This makes sense since customers must spend to complete some reward offers.
· Customers receive considerably more rewards when reward offers are marketed from email, mobile, and website channels than social media.
· A decrease in the ratio of transactions to offers negatively correlates with increased sales.
· Increasing the percentage of infographic offers to the 18-25 age group despite increasing offers 4x did not affect sales compared to offers that highlighted BOGO or discounts in other age groups.
· Transactions were halved between P3 and P4 despite a comparable number of rewards offered. This suggests the difficulty of obtaining these rewards increased as well.
· The top 500 spending customers make up 18% of sales, despite only being 3% of the customer population.
· There is little correlation between income and sales.
· There is little correlation between the number of rewards offers a customer receives, and sales.

Final Thoughts and Insights:
To boost sales and profitability, I would recommend prioritizing strategies from late 2017, where a high volume of rewards drove transactions, and simplify reward redemption processes. Focus marketing efforts on dominant channels like email, mobile, and websites while reducing reliance on social media. Additionally, limit rewards to 3-4 offers within the first 30 days and reinvest in a second reward cycle for long-term customer engagement. Lastly, avoid targeting based on income as it shows no correlation with sales. 
