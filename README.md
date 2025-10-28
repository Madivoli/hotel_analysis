## Hotel Revenue Optimization & Booking Pattern Analysis

![donald-teel-CFyJZMDyJJY-unsplash](https://github.com/user-attachments/assets/81947078-394e-4e5f-abe3-68d099c41a83)

**Project Overview**

As a hotel manager, have you ever wondered about the average daily rate (ADR) and revenue per available room (RevPAR) of your hotel or resort? Are you curious about which market segments and distribution channels attract the highest-value customers based on ADR and length of stay? Do you want to know which countries are the top sources of guests, and how their booking lead times and cancellation rates differ? Additionally, would you like to establish the typical lead time for guest bookings and determine if a longer lead time correlates with a higher likelihood of cancellations? 

This data analysis helps answer such questions!

The dataset includes 119,334 booking records from both a city hotel and a resort hotel. It contains various information such as when the booking was made, the length of stay, the number of adults, children, and babies, as well as the number of available parking spaces, among other details. This rich resource is valuable for various stakeholders in the hospitality industry. Here are the key stakeholders, the business questions they may have, and the project struture and tools used for analysing the data.


---

**Stakeholders and Business Questions**

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


---
**Project Structure and Tools**

- **Data Processing and Manipulation:** The analysis begins with a thorough examination of the data to identify issues such as missing values, duplicate records, inconsistencies in data types, standardizing data, finding and replacing country codes with country names, and creating new columns, utilizing Excel Power Query, MySQL and Pandas for data cleaning and transformation.

- **Data Summary and Trend Analysis:** Subsequently, the booking data will be summarized to identify trends, including total revenue, average daily rate (ADR) and revenue per available room (RevPAR). This analysis will be performed using MySQL, Pandas and Tableau, leveraging tools such as Power Query, Key Performance Indicators (KPIs), Calculated Fields and Parameters.

- **Data Visualization:** Finally, the cleaned and summarized data will be visualized utilizing Matplotlib, Tableau and Excel to enhance understanding and facilitate informed decision-making.

---
---
**HOTEL GENERAL MANAGER / STRATEGIC LEADERSHIP**

**Performance Metrics by Hotel Type**

<img width="1200" height="488" alt="image" src="https://github.com/user-attachments/assets/e07efc53-e2f1-499c-9cf2-e246f287bffc" />

**Segment-Specific Insights:**

A. **The City Hotel (The Core Problem)**

- **Higher Risk, Higher Price:** The City Hotel has the highest ADR ($105.35) but is experiencing a higher 41.73% cancellation rate.
- **Placeholder Bookings:** The City Hotel's lead time is the longest (109.76 days), and its guest engagement is the lowest (0.55 special requests). This confirms that a high volume of long-lead, non-committed "placeholder" bookings are inflating the forecast and causing massive revenue leakage.
- **Guest Profile:** This profile strongly suggests a high volume of business travellers or deal-seekers who book early on flexible rates across multiple properties, with the intention of cancelling all but one later on.
  
B. **The Resort Hotel**
- **Better Commitment:** The Resort Hotel has a lower, though still high, cancellation rate (27.76%), shorter lead time (92.68 days), and slightly higher engagement (0.62 special requests).
- **Guest Profile:** This profile is typical of leisure travellers who plan a bit closer to the date and are slightly more invested in their booking (higher special requests). The long lead time remains a risk factor, but their higher engagement suggests a need for less drastic policy measures than those implemented by the City Hotel.

**Recommendations:**

The hotels must implement different commitment strategies for each segment to combat the $4.5 million in lost revenue.

**Immediate Action: Secure City Hotel Revenue**

The City Hotel's priority is to convert non-committed bookings into secure revenue.
- **Policy Change:** Implement a **Tiered Non-Refundable Deposit Policy** for all City Hotel bookings made more than 60 days out.
- **Mandatory:** Require a non-refundable deposit equal to 1-2 nights' ADR ($105.35 to $210.70) to confirm any booking with a lead time of 60+ days. This aligns the financial commitment with the long time window.
- **Drive Engagement:** Introduce a highly visible "_Personalise Your Stay_" pop-up during the City Hotel booking flow that requires the guest to choose at least one item (e.g., preferred bed size, floor level, early check-in preference). This artificially increases the Special Requests figure (engagement) and guest psychological commitment.
  
**Targeted Action: Optimize Resort Hotel Revenue**
   
The Resort Hotel's policy should be softer to maintain the slightly better booking behaviour.
- **Incentivise Commitment:** For all Resort bookings with a lead time >90$ days, send a "Commitment Offer" at the 60-day mark: "_Confirm your stay is non-refundable now for an extra $10 off, or receive a complimentary spa voucher/resort credit._" This encourages the guest to commit financially for a perk.
- **Utilise Engagement:** Focus on **upselling** via special requests (e.g., pre-ordering cabana rentals, dinner reservations, or package upgrades) to secure additional ancillary revenue and further cement the bookings.

---
**YoY Revenue Growth Percentage by Month and Hotel Type**

This analysis examines the rate at which each hotel's actual revenue is growing compared to the same month in the previous year. The City Hotel demonstrates **a volatile growth**, while the Resort Hotel shows more **consistent and stable growth**.

<img width="1202" height="755" alt="image" src="https://github.com/user-attachments/assets/3eeab9a9-1280-4694-bf13-d5a1fbc96193" />

The analysis reveals a distinct pattern characterized by pronounced peaks followed by troughs, indicative of **a strong cyclical trend**. This pattern is typical of seasonal businesses where demand peaks during specific months, such as summer and the holiday season, while experiencing declines during other periods. For example, the City Hotel experienced **a revenue peak in  November**, followed by **a dip from December to February**. Conversely, the Resort experienced **a surge in revenue from December to January**, with a subsequent **decline from February to March (notably negative revenue)**. Further investigation is required to **ascertain the underlying cause of the negative revenue observed in March**.

<img width="1200" height="559" alt="image" src="https://github.com/user-attachments/assets/c6116190-bd06-4975-b5c3-eeae28a1ca77" />

---
**YoY Cancellation Rate Change by Month and Hotel Type**

This analysis highlights the changes in the cancellation rate expressed in percentage points compared to the previous year. A positive value indicates that the cancellation problem is worsening, whereas a negative value suggests improvement. The Resort Hotel shows a concerning trend of consistently rising cancellation rates during the comparative period. For example, the **cancellation rate increased by 5.99 percentage points and 4.3 percentage points in July and August 2017**, down from 31.64% and 34.2% in 2026, respectively.

<img width="1502" height="692" alt="image" src="https://github.com/user-attachments/assets/493d72f7-34c6-486c-a6b2-b2063974cc37" />

**Recommendations**

The company must adopt **segmented revenue strategies** that target the different growth and cancellation dynamics of the two hotel types.




---
**--Guest demographics between the City Hotel and the Resort Hotel**

--1. Geographic distribution (Top 10 source countries)

 
<img width="1515" height="600" alt="image" src="https://github.com/user-attachments/assets/012d3552-a97d-4e9c-b4ef-49ad05f17120" />

<img width="1202" height="917" alt="image" src="https://github.com/user-attachments/assets/db48291a-c256-4823-abad-fe89b8e32c55" />



---
--2. Repeat guest distribution

 

<img width="1200" height="167" alt="image" src="https://github.com/user-attachments/assets/15fcabe3-1819-4da1-8088-7c4505bd4faf" />

---
**Cancellation Rate**
    
    total_bookings = len(hb)
    cancelled_bookings = hb['is_canceled'].sum()
    cancellation_rate = (cancelled_bookings / total_bookings) * 100
    print(f" Cancellation Rate: {cancellation_rate:.2f}%")

_Cancellation Rate: 37.04%_

##
**Cancellation rate patterns**

--1. Lead time analysis by cancellation status

    lead_time_by_cancel = hb.groupby('is_canceled')['lead_time'].agg(['mean', 'median'])
    print(f"\nLead Time Analysis (in days):")
    print(f"  Not Cancelled - Mean: {lead_time_by_cancel.iloc[0, 0]:.1f}, Median: {lead_time_by_cancel.iloc[0, 1]:.1f}")
    print(f"  Cancelled - Mean: {lead_time_by_cancel.iloc[1, 0]:.1f}, Median: {lead_time_by_cancel.iloc[1, 1]:.1f}")

<img width="1200" height="73" alt="image" src="https://github.com/user-attachments/assets/503a4491-ed6e-4bb1-a7f8-4c8df32a0510" />

##
--2. Cancellation rates by deposit type

    plt.figure(figsize=(10, 6))
    deposit_cancel = hb.groupby('deposit_type')['is_canceled'].mean().sort_values(ascending=False)
    deposit_cancel.plot(kind='bar', title='Cancellation Rate by Deposit Type')
    plt.ylabel('Cancellation Rate')
    plt.show()

    print("Cancellation rates by deposit type:")
    for deposit_type, rate in deposit_cancel.items():
        count = hb[hb['deposit_type'] == deposit_type].shape[0]
        print(f"{deposit_type}: {rate:.2%} ({count} bookings)")

  <img width="1500" height="119" alt="image" src="https://github.com/user-attachments/assets/adecf53d-76d1-4285-a6ec-e8183bfb2cae" />

---
**REVENUE MANAGEMENT & PRICING TEAM**

**PERFORMANCE METRICS** 
<img width="1200" height="1488" alt="image" src="https://github.com/user-attachments/assets/50f72504-b1bc-41b4-9309-316e8d8b30d5" />


**Recommendations:**

**Revenue and Policy Optimisation:**
   
a)	**Implement Stricter Cancellation Policies:** Introduce or strengthen policies, especially for non-refundable or semi-flexible rates. For instance, **offer a tiered pricing structure**: _Non-Refundable_ (Lowest Price), _Partially-Refundable/Semi-Flexible_ (Mid Price), and _Fully-Flexible_ (Highest Price).

b)	**Deposit and Pre-payment Requirements:** For bookings far out or during peak demand periods, **require a non-refundable deposit** (e.g., 1 night's stay) or **full pre-payment** to secure the reservation, shifting the risk to the guest.

c)	**Dynamic Rate Adjustments:** Analyse if cancellations are concentrated around specific channels or lead times. Use data to adjust rates or restrictions to deter low-commitment bookings dynamically.

**Lock Down Long-Lead Revenue:**
   
The hotels must implement **Lead-Time-Based Cancellation Policies** to secure the $4.5 million in lost revenue due to cancellations.

a)	**Introduce a Stricter, Time-Sensitive Deposit Policy:**
- **Bookings > 90 Days Out (The 104-Day Problem)**: Mandate a non-refundable deposit equal to at least one night's stay to secure the reservation. This immediately converts placeholder bookings into revenue-secured commitments.
- **Bookings < 30 Days Out:** Maintain the current policy (or a slightly tightened 48-hour free cancellation), as these guests are typically more committed.
  
b)	**Refine the Non-Refundable Rate:** Ensure the non-refundable rate is the lowest published price and is heavily promoted for bookings made >60 days out.

c)	**Implement a "Rate Lock" Option:** Allow a guest to pay a small, non-refundable fee (e.g., $10-$20) to hold a flexible rate for 48 hours, mimicking the successful tactics used by airlines, to reduce unnecessary free inventory blocks.


--**Calculating the **average daily rate** (**ADR**), **total revenue** (**TR**) and **revenue per available room** (**RevPAR**)**

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

##

**ADR by month and hotel type**

![adr](https://github.com/user-attachments/assets/419c6215-3b2c-477b-9704-648956e705ee)

##

**TR by month and hotel type**

<img width="1172" height="480" alt="image" src="https://github.com/user-attachments/assets/05def408-f3df-4f55-808d-b7160b956188" />

##

**RevPAR by month and hotel type:**

<img width="1174" height="487" alt="image" src="https://github.com/user-attachments/assets/71a0dcaf-cfb8-4de3-8d1d-04b066160680" />

##

-- **Calculating customer value [Customer Value Analysis (CVA)]**

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


##
**CVA by market segment**

<img width="1200" height="267" alt="image" src="https://github.com/user-attachments/assets/e20a1997-376b-4864-9ea3-b01ecd5b15e5" />


##
**CVA by distribution channels**

<img width="1200" height="234" alt="image" src="https://github.com/user-attachments/assets/8320dd9a-d50c-4fe2-9672-406d5ab9670e" />

##
-- Further Analysis: Customer lifetime value (CLV/LTV) 

    WITH customer_metrics AS (
    SELECT 
        country,
        market_segment,
        distribution_channel,
        ROUND(AVG(adr), 2) AS customer_avg_adr,
        ROUND(AVG(stays_total_nights)) AS customer_avg_stay,
        COUNT(*) as total_stays,
        SUM(adr * stays_total_nights) AS lifetime_value
    FROM hb_staging
    WHERE is_canceled = 0
    GROUP BY country, market_segment, distribution_channel
    )
    SELECT 
        market_segment,
        distribution_channel,
        COUNT(*) as high_value_customers,
        ROUND(AVG(customer_avg_adr), 2) AS segment_avg_adr,
        ROUND(AVG(customer_avg_stay)) AS segment_avg_stay,
        ROUND(AVG(lifetime_value), 2) AS avg_lifetime_value,
        ROUND(SUM(lifetime_value), 2) AS total_segment_value
    FROM customer_metrics
    WHERE customer_avg_adr > (SELECT AVG(adr) FROM hb_staging WHERE is_canceled = 0)
       OR customer_avg_stay > (SELECT AVG(stays_total_nights) FROM hb_staging WHERE is_canceled = 0)
    GROUP BY market_segment, distribution_channel
    ORDER BY avg_lifetime_value DESC;

**CLV/LTV by market segment**

<img width="1200" height="286" alt="image" src="https://github.com/user-attachments/assets/44cada11-87d0-44c5-a048-d192756ca45d" />




##
**CLV/LTV by distribution channels**

<img width="1515" height="357" alt="image" src="https://github.com/user-attachments/assets/3f4d782b-675d-49b1-876b-1fe87176a8a0" />


---
**Marketing Team**

--Calculating the most effective market segments  

<img width="1500" height="244" alt="image" src="https://github.com/user-attachments/assets/0c5eec87-eb32-4756-8a95-8a359eba4027" />

##
--Calculating the most effective market channels 

<img width="1500" height="170" alt="image" src="https://github.com/user-attachments/assets/bce5c72e-1be9-4b99-9b7c-eded6216cca3" />

##
--The top sources of guests by bookings

<img width="1500" height="269" alt="image" src="https://github.com/user-attachments/assets/8b361b5b-7e03-4a7b-a7b7-f69de7994a69" />

##
--Countries by lead time

<img width="1500" height="289" alt="image" src="https://github.com/user-attachments/assets/73cbbfac-63e3-4335-87dd-4bd215e0d2bb" />
