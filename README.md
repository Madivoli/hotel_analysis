## Hotel Revenue Optimization & Booking Pattern Analysis

![donald-teel-CFyJZMDyJJY-unsplash](https://github.com/user-attachments/assets/81947078-394e-4e5f-abe3-68d099c41a83)

As a hotel manager, have you ever wondered about the average daily rate (ADR) and revenue per available room (RevPAR) of your hotel or resort? Are you curious about which market segments and distribution channels attract the highest-value customers based on ADR and length of stay? Do you want to know which countries are the top sources of guests, and how their booking lead times and cancellation rates differ? Additionally, would you like to establish the typical lead time for guest bookings and determine if a longer lead time correlates with a higher likelihood of cancellations? 

This data analysis can help answer such questions! 

The dataset includes 119,334 booking records from both a city hotel and a resort hotel. It contains various information such as when the booking was made, the length of stay, the number of adults, children, and babies, as well as the number of available parking spaces, among other details. 

This rich resource can be valuable for various stakeholders in the hospitality industry. Here are the key stakeholders, the business questions they may have, and the tools used for analyzing the data.

##
**Stakeholders**

**Hotel General Manager / Strategic Leadership**

- What are the key differences in performance and guest demographics between the City Hotel and the Resort Hotel?
- What is the overall cancellation rate, and can we identify any patterns (e.g., by deposit type, lead time, or repeat guest status) that predict cancellations?

**Revenue Management & Pricing Team**

- What is the average daily rate (ADR) and revenue per available room (RevPAR) by month and hotel type?
- Which market segments and distribution channels bring in the highest-value customers (based on ADR and length of stay)?

**Marketing Team**

- What are the most effective market segments and channels for securing bookings that do not get canceled?
- Which countries are the top sources of guests, and how does their booking lead time and cancellation rate vary?

**Operations & Reservations Team**

- How far in advance (lead time) do guests typically book, and does a longer lead time correlate with a higher chance of cancellation?
- What is the most common room type booked, and how often do guests get upgraded/downgraded from their reserved room type?

##
**Project Structure and Tools**

- **Data Processing and Manipulation:** The analysis begins with a thorough examination of the data to identify issues such as missing values, duplicate records, inconsistencies in data types, standardizing data, finding and replacing country codes with country names, and creating new columns, utilizing Excel Power Query, MySQL and Pandas for data cleaning and transformation.

- **Data Summary and Trend Analysis:** Subsequently, the booking data will be summarized to identify trends, including total revenue, average daily rate (ADR) and revenue per available room (RevPAR). This analysis will be performed using MySQL, Pandas and Tableau, leveraging tools such as Power Query, Key Performance Indicators (KPIs), Calculated Fields and Parameters.

- **Data Visualization:** Finally, the cleaned and summarized data will be visualized utilizing Matplotlib, Tableau and Excel to enhance understanding and facilitate informed decision-making.

##
**Revenue Management & Pricing Team**

**Question 1:** What is the average daily rate (ADR) and revenue per available room (RevPAR) by month and hotel type?

--Calculating the **average daily rate** (**ADR**), **total revenue** (**TR**) and **revenue per available room** (**RevPAR**)

    WITH hotel_capacity AS (
        SELECT 
          hotel,
          COUNT(DISTINCT assigned_room_type) AS total_rooms
        FROM hb_staging 
        GROUP BY hotel
    ),
    daily_revenue AS (
        SELECT 
          hotel,
          arrival_date,
          ROUND(AVG(adr), 2) AS average_daily_rate,
          ROUND(SUM(adr * (stays_in_weekend_nights + stays_in_week_nights)), 2) AS total_revenue
        FROM hb_staging
        GROUP BY hotel, arrival_date
    )
    SELECT 
      dr.hotel,
      dr.arrival_date,
      dr.average_daily_rate,
      dr.total_revenue,
      dr.total_revenue / hc.total_rooms AS revenue_per_available_room
    FROM daily_revenue AS dr
    JOIN hotel_capacity AS hc ON dr.hotel = hc.hotel;

<img width="1202" height="719" alt="image" src="https://github.com/user-attachments/assets/57e7cb89-f1ed-4183-9891-61a4df942a9d" />

📊 **Key Findings**

-- City Hotel Performance:
- Higher ADR ($100.69 vs $92.45): 8.9% premium pricing power.
- Significantly higher total revenue ($25.27M vs $17.44M): 44.8% more revenue.
- Massive RevPAR advantage ($3.16M vs $1.74M): 81.2% higher revenue efficiency.

-- Resort Hotel Performance:
- Lower ADR: Potential underpricing or different market positioning.
- Lower Total Revenue: Despite possibly similar room counts.
- Significantly Lower RevPAR: Major revenue optimisation opportunity.

🎯 **Implications and opportunities**
- City Hotel has a stronger market position and pricing power.
- Resort Hotel has significant room for rate optimisation.

🚀 **Recommendations**

-- For Resort:
- Increase ADR by 10-15% through value-added packages.
- Introduce premium pricing for high-demand periods.
- Review competitor pricing in the resort category.

-- For City Hotel: 
- Develop tiered pricing for different room categories.
- Optimize distribution channel mix for net revenue.

**ADR by month and hotel type**

![adr](https://github.com/user-attachments/assets/419c6215-3b2c-477b-9704-648956e705ee)




**TR by month and hotel type**

<img width="1172" height="480" alt="image" src="https://github.com/user-attachments/assets/05def408-f3df-4f55-808d-b7160b956188" />



**RevPAR by month and hotel type:**

<img width="1174" height="487" alt="image" src="https://github.com/user-attachments/assets/71a0dcaf-cfb8-4de3-8d1d-04b066160680" />

##
**Question 2:** Which market segments and distribution channels bring in the highest-value customers (based on ADR and length of stay)?

-- Customer Value Analysis (CVA)

    SELECT 
        country,
        market_segment,
        distribution_channel,
        total_guests,
        ROUND(AVG(adr), 2) AS avg_adr,
        ROUND(AVG(stays_total_nights)) as avg_length_of_stay,
        ROUND(AVG(adr * (stays_total_nights)), 2) AS avg_total_revenue_per_stay,
        ROUND(SUM(adr * (stays_total_nights)), 2) AS total_revenue
    FROM hb_staging
    WHERE is_canceled = 0  -- Only confirmed bookings
    GROUP BY country, market_segment, distribution_channel, total_guests
    ORDER BY avg_total_revenue_per_stay DESC;

**CVA by country**

<img width="1200" height="400" alt="image" src="https://github.com/user-attachments/assets/18133f6d-d5f4-43aa-8373-75795af59c52" />




**CVA by market segment**

<img width="1200" height="267" alt="image" src="https://github.com/user-attachments/assets/e20a1997-376b-4864-9ea3-b01ecd5b15e5" />



**CVA by distribution channels**

<img width="1200" height="234" alt="image" src="https://github.com/user-attachments/assets/8320dd9a-d50c-4fe2-9672-406d5ab9670e" />


-- Further Analysis: Customer lifetime value (CLV/LTV) 

    WITH customer_metrics AS (
    SELECT 
        country,
        market_segment,
        distribution_channel,
        ROUND(AVG(adr), 2)as customer_avg_adr,
        ROUND(AVG(stays_total_nights)) as customer_avg_stay,
        COUNT(*) as total_stays,
        SUM(adr * stays_total_nights) as lifetime_value
    FROM hb_staging
    WHERE is_canceled = 0
    GROUP BY country, market_segment, distribution_channel
    )
    SELECT 
        market_segment,
        distribution_channel,
        COUNT(*) as high_value_customers,
        ROUND(AVG(customer_avg_adr), 2) as segment_avg_adr,
        ROUND(AVG(customer_avg_stay)) as segment_avg_stay,
        ROUND(AVG(lifetime_value), 2) as avg_lifetime_value,
        ROUND(SUM(lifetime_value), 2) as total_segment_value
    FROM customer_metrics
    WHERE customer_avg_adr > (SELECT AVG(adr) FROM hb_staging WHERE is_canceled = 0)
       OR customer_avg_stay > (SELECT AVG(stays_total_nights) FROM hb_staging WHERE is_canceled = 0)
    GROUP BY market_segment, distribution_channel
    ORDER BY avg_lifetime_value DESC;


**CLV/LTV by market segment**

<img width="1200" height="286" alt="image" src="https://github.com/user-attachments/assets/44cada11-87d0-44c5-a048-d192756ca45d" />


<img width="1174" height="485" alt="image" src="https://github.com/user-attachments/assets/53824b89-52de-4eb1-aaab-e1613e2f9e91" />


<img width="1170" height="485" alt="image" src="https://github.com/user-attachments/assets/c8c9f073-977d-4012-8e58-d9e56309b206" />

