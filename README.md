## Hotel Revenue Optimization & Booking Pattern Analysis

Have you ever wondered when the best time of year is to book a hotel room? Or what is the optimal length of stay to secure the best daily rate? What if you want to predict whether a hotel is likely to receive an unusually high number of special requests? 
This hotel booking data analysis can help answer such questions!
The dataset includes 119,334 booking records from both a city hotel and a resort hotel. It contains various information such as when the booking was made, the length of stay, the number of adults, children, and babies, as well as the number of available parking spaces, among other details. 
This rich resource can be valuable for various stakeholders in the hospitality industry. Here are the key stakeholders, the business questions they may have, and the tools used for analyzing this data.

##
**Stakeholders**

**Hotel General Manager / Strategic Leadership**

**_Focus:** Overall business performance and long-term strategic planning._

- What are the key differences in performance and guest demographics between the City Hotel and the Resort Hotel?
- What is the overall cancellation rate, and can we identify any patterns (e.g., by deposit type, lead time, or repeat guest status) that predict cancellations?

**Revenue Management & Pricing Team**

_**Focus:** Maximizing revenue and optimizing pricing strategies._

- What is the average daily rate (ADR) and revenue per available room (RevPAR) by month and hotel type?
- Which market segments and distribution channels bring in the highest-value customers (based on ADR and length of stay)?

**Marketing Team**

_**Focus:** Optimizing marketing spend and understanding customer acquisition._

- What are the most effective market segments and channels for securing bookings that do not get canceled?
- Which countries are the top sources of guests, and how does their booking lead time and cancellation rate vary?

**Operations & Reservations Team**

_**Focus** Ensuring smooth hotel operations and efficient room allocation._

- How far in advance (lead time) do guests typically book, and does a longer lead time correlate with a higher chance of cancellation?
- What is the most common room type booked, and how often do guests get upgraded/downgraded from their reserved room type?

##
**Project Structure and Tools**

Data Processing and Manipulation: The analysis began with a thorough examination of the data to identify issues such as missing values, duplicate records, inconsistencies in data types, standardizing data, finding and replacing country codes with country names, and creating new columns, utilizing Excel Power Query, MySQL and Pandas for data cleaning and transformation.

Data Summary and Trend Analysis: Subsequently, the booking data were summarized to identify trends, including total revenue, average pricing, and correlations. This analysis was performed using MySQL, Pandas and Tableau, leveraging tools such as DAX, key performance indicators (KPIs), and Power Query.

Data Visualization: Finally, the cleaned and summarized data was visualized utilizing Matplotlib, Tableau and Excel to enhance understanding and facilitate informed decision-making.


##
**Revenue Management & Pricing Team**

--Calculating the average daily rate (ADR), total revenue (TR) and revenue per available room (RevPAR) by month and hotel type.

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
