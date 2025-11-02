## Hotel Revenue Optimization & Booking Pattern Analysis

![donald-teel-CFyJZMDyJJY-unsplash](https://github.com/user-attachments/assets/81947078-394e-4e5f-abe3-68d099c41a83)

**Project Overview**

As a hotel manager, have you ever wondered about the average daily rate (ADR) and revenue per available room (RevPAR) of your hotel or resort? Are you curious about which market segments and distribution channels attract the highest-value customers based on ADR and length of stay? Do you want to know which countries are the top sources of guests, and how their booking lead times and cancellation rates differ? Additionally, would you like to establish the typical lead time for guest bookings and determine if a longer lead time correlates with a higher likelihood of cancellations? 

This data analysis helps answer such questions!

The dataset includes 119,334 booking records from both a city hotel and a resort hotel. It contains various information such as when the booking was made, the length of stay, the number of adults, children, and babies, as well as the number of available parking spaces, among other details. This rich resource is valuable for various stakeholders in the hospitality industry. Here are the key stakeholders, the business questions they may have, and the project struture and tools used for analysing the data.


---

**Stakeholders and Business Questions**

**Hotel General Manager / Strategic Leadership**

- What is the year-over-year growth in bookings and revenue, and how does the cancellation rate trend compare between the city hotel and the resort hotel?

- Using clustering, can we identify distinct customer profiles (e.g., "last-minute business travelers," "long-stay families") to inform targeted service packages and investments?

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

This section explores the **year-over-year (YoY) growth** in both bookings and revenue for the two types of hotels. It also examines the **performance metrics** and **trends in cancellation rates**, comparing city hotels and resort hotels. Finally, by utilizing cluster analysis, it aims to **identify distinct customer profiles** — such as "leisure travellers" and "family vacationers" — to guide our development of targeted service packages and investments.

**Performance Metrics by Hotel Type**

<img width="1200" height="488" alt="image" src="https://github.com/user-attachments/assets/e07efc53-e2f1-499c-9cf2-e246f287bffc" />

**SEGMENT-SPECIFIC INSIGHTS**

A. **The City Hotel (The Core Problem)**

- **Higher Risk, Higher Price:** The City Hotel has the highest ADR ($105.35) but is experiencing a higher 41.73% cancellation rate.
- **Placeholder Bookings:** The City Hotel's lead time is the longest (109.76 days), and its guest engagement is the lowest (0.55 special requests). This confirms that a high volume of long-lead, non-committed "placeholder" bookings are inflating the forecast and causing massive revenue leakage.
- **Guest Profile:** This profile strongly suggests a high volume of business travellers or deal-seekers who book early on flexible rates across multiple properties, with the intention of cancelling all but one later on.
  
B. **The Resort Hotel**
- **Better Commitment:** The Resort Hotel has a lower, though still high, cancellation rate (27.76%), shorter lead time (92.68 days), and slightly higher engagement (0.62 special requests).
- **Guest Profile:** This profile is typical of leisure travellers who plan a bit closer to the date and are slightly more invested in their booking (higher special requests). The long lead time remains a risk factor, but their higher engagement suggests a need for less drastic policy measures than those implemented by the City Hotel.

**Recommendations**

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

The company should implement **segmented revenue strategies** that address the distinct growth and cancellation dynamics of the two types of hotels.

**A. Strategic Focus: City Hotel (High Volatility, Maturing Market)**  

The objective is to **lock in existing demand** and stabilise the booking forecast.

1. **Mandatory Non-Refundable Policy for Long Leads:** It is essential to focus on the months where the cancellation rate is worsening, and revenue growth is slowing (e.g., Q3 of 2017). Leadership should implement **a mandatory non-refundable deposit** (or full non-refundable rate) for any bookings made **more than 90 days** in advance. This approach will convert long-lead, high-risk "placeholder" bookings into actual revenue, directly addressing the core issues facing the City Hotel.

2. **Dynamic Pricing & Inventory Control:** During periods when year-over-year (YoY) cancellation rates are significantly positive (worsening, such as an increase of +4 percentage points in July), the hotel should **temporarily restrict inventory available** on high-flexibility, low-commitment channels (like certain Online Travel Agencies, or OTAs) for the same month in the following year.

**B. Strategic Focus: Resort Hotel (Sustainable Growth, Escalating Risk)**  
The goal is to **protect healthy revenue growth** by increasing customer commitment without discouraging new bookings.

1. **Value-Added Pre-Commitment:** Instead of simply requiring a cash deposit (which could deter leisure bookings), leadership should leverage the average long lead time (92.68 days) to sell **non-refundable, value-added ancillary services**. For example, a $50 non-refundable pre-payment could be required for a poolside cabana or spa treatment, which would secure a 10-15% discount on that service. This strategy utilizes the "Special Requests" metric to ensure cash commitment.

2. **Targeted Channel Review:** Leadership should promptly review the Resort Hotel's booking channels during months with the highest increases in cancellation rates (for instance, July’s +5.99 percentage points). If a specific third-party travel agent or OTA is contributing to low-commitment bookings, **stricter cancellation terms should be negotiated**, or their **inventory allotment should be reduced**.

---
**Cluster Analysis**

The primary objective is to **identify distinct customer segments** within the data to facilitate **personalized marketing**, **targeted service offerings**, and **strategic resource allocation**. Customers were segmented into five clusters, as outlined below.

<img width="1200" height="389" alt="image" src="https://github.com/user-attachments/assets/94423ae4-fc18-41e2-9834-7e0d20411158" />


The analysis highlights a **significant business risk**: 64.8% of customers fall into the category of **"High-Risk Advance Planners,"** who exhibit considerable cancellation rate (40%). This situation requires immediate attention and action.


<img width="1200" height="663" alt="image" src="https://github.com/user-attachments/assets/ff2ce7f7-a56c-43cb-b662-da238fb099f8" />

<img width="1200" height="588" alt="image" src="https://github.com/user-attachments/assets/1f091a3e-0dc3-4174-b09c-c778c6f045b0" />


**Recommendations**

**A. Cluster 1 (High-Risk - 64%):**

**Implement Tiered Deposit System:**
- 30% deposit for bookings >90 days advance
- 50% deposit for bookings >180 days advance
- Full prepayment for peak season >120 days advance
  
**Create Non-Refundable Rate Options:**
- 15-20% discount for non-refundable bookings
- Clear communication of cancellation penalties

**B. Cluster 0, 2, 4 (Standard Leisure - 34.4%):**

**Further segmentation needed (segment optimisation)**
- Analyze differences between these clusters
- Develop targeted approaches for each sub-segment
- Focus on converting to lower-risk booking patterns

**C. Cluster 3 (Family Vacationers - 0.8%):**

**Growth Strategy (Aggressive Expansion):**

**Family Package Development:**
- "Kids Stay Free" promotions
- Family suite packages with activity bundles
- Multi-generational travel offers

**Targeted Marketing:**
- Family travel websites and influencers
- School vacation period campaigns
- Family-focused social media content

**Service Enhancements:**
- Childcare services
- Family activity coordinators
- Child-friendly dining options

**D. Business Model Restructuring:**

**Revenue Mix Rebalancing:**

- **Target:** Reduce Cluster 1 to 40%, grow Cluster 3 to 15%
- **Timeline:** 12-month transformation
  
**Pricing Strategy Overhaul:**

- Dynamic pricing based on cancellation risk
- Advance purchase discounts with restrictions
- Last-minute booking incentives
  
**Channel Optimisation:**

- Reduce dependency on high-cancellation channels
- Develop direct booking incentives
- Partner with family-focused travel agencies

---
---
**REVENUE MANAGEMENT & PRICING TEAM**

The objective is to determine the **average daily rate (ADR)**, **revenue per available room (RevPAR)**, **total bookings**, as well as the metrics for **cancelled and non-cancelled bookings**, **cancellation rate**, **total revenue** (including both actual revenue and revenue lost due to cancellations), **average lead time**, and the **average number of special requests received**. These key metrics will be categorized by month and by hotel type to identify any performance variations between city hotels and resort hotels. Ultimately, significant insights will be highlighted, accompanied by relevant recommendations.

**Key Performance Metrics and Insights**
<img width="1200" height="1488" alt="image" src="https://github.com/user-attachments/assets/50f72504-b1bc-41b4-9309-316e8d8b30d5" />


**Recommendations**

**Revenue and Policy Optimisation:**
   
a)	**Implement Stricter Cancellation Policies:** 
- **Introduce or strengthen policies**, especially for non-refundable or semi-flexible rates.
- For instance, **offer a tiered pricing structure**: _Non-Refundable_ (Lowest Price), _Partially-Refundable/Semi-Flexible_ (Mid Price), and _Fully-Flexible_ (Highest Price).

b)	**Deposit and Pre-payment Requirements:** 
- For bookings far out or during peak demand periods, **require a non-refundable deposit** (e.g., 1 night's stay) or **full pre-payment** to secure the reservation, shifting the risk to the guest.

c)	**Dynamic Rate Adjustments:** 
- Analyse if cancellations are concentrated around specific channels or lead times.
- Use data to adjust rates or restrictions to deter low-commitment bookings dynamically.

**Lock Down Long-Lead Revenue:**
   
The hotels must implement **Lead-Time-Based Cancellation Policies** to secure the $4.5 million in lost revenue due to cancellations.

a)	**Introduce a Stricter, Time-Sensitive Deposit Policy:**
- **Bookings > 90 Days Out (The 104-Day Problem)**: Mandate a non-refundable deposit equal to at least one night's stay to secure the reservation.
- This immediately converts placeholder bookings into revenue-secured commitments.
- **Bookings < 30 Days Out:** Maintain the current policy (or a slightly tightened 48-hour free cancellation), as these guests are typically more committed.
  
b)	**Refine the Non-Refundable Rate:** 
- Ensure the non-refundable rate is the lowest published price and is heavily promoted for bookings made >60 days out.

c)	**Implement a "Rate Lock" Option:** 
- Allow a guest to pay a small, non-refundable fee (e.g., $10-$20) to hold a flexible rate for 48 hours, mimicking the successful tactics used by airlines, to reduce unnecessary free inventory blocks.

---
**Average Daily Rate, Total Revenue and Revenue per Available Room by Hotel Type**

<img width="1202" height="617" alt="image" src="https://github.com/user-attachments/assets/972074ff-e07f-43e6-8ba2-48951a75d8b4" />

**KEY INSIGHTS**

**City Hotel Performance:**
- Higher ADR ($100.69 vs $92.45): 8.9% premium pricing power.
- Significantly higher total revenue ($25.27M vs $17.44M): 44.8% more revenue.
- Massive RevPAR advantage ($3,158 vs $2,199): 69.6% higher revenue efficiency.

**Resort Hotel Performance:**
- Lower ADR: Potential underpricing or different market positioning.
- Lower Total Revenue: Despite possibly similar room counts.
- Significantly Lower RevPAR: Major revenue optimisation opportunity.

**IMPLICATIONS AND OPPORTUNITIES**
- City Hotel has a stronger market position and pricing power.
- Resort Hotel has significant room for rate optimisation.

**Recommendations**

**For Resort:**
- Increase ADR by 10-15% through value-added packages.
- Introduce premium pricing for high-demand periods.
- Review competitor pricing in the resort category.

**For City Hotel:**
- Develop tiered pricing for different room categories.
- Optimize distribution channel mix for net revenue.

---
**ADR Trends Over Time Segmented by Hotel Type**

The line graph shows the Average Daily Rate (ADR) trend by hotel type, revealing critical differences in pricing strategy, market resilience, and seasonal dependence between the City Hotel and the Resort Hotel.
<img width="1202" height="617" alt="image" src="https://github.com/user-attachments/assets/d1cc329a-c7fd-4e23-ab12-8bdd2b35116a" />

**Interpretation by Hotel Type**

**Resort Hotel ADR Trend**  
The Average Daily Rate (ADR) for Resort Hotels displays **a highly volatile and aggressive pricing strategy**.  
- **Peak Season Pricing Power:** The ADR **surges significantly during the summer months** (June to August), often exceeding the **$180** mark. This indicates strong demand in the summer, enabling substantial price increases.  
- **Deep Low Season Discounts:** Conversely, the ADR **drops sharply during the low season** (late fall and winter, from September to February), falling to around **$53**. This suggests that Resort Hotel **relies on aggressive discounting to maintain occupancy during off-peak periods**, likely aimed at attracting local and regional customers.  
- **Overall Average:** The average ADR for Resort Hotels is $92.45, with **frequent fluctuations that result in prices dipping below this average**.

**City Hotel ADR Trend**  
The ADR for City Hotels, on the other hand, showcases **a less volatile and more stable pricing strategy**.  
- **Higher Overall Price Point:** The average ADR for City Hotels is higher at $100.69, generally remaining above that of Resort Hotels throughout the year.  
- **Extended Peak Season:** While summer (June) remains the peak period, the City Hotel's pricing **maintains higher levels for a longer duration**, suggesting an **extended shoulder season** and **a stronger demand for short-term business or transit stays**.  
- **Price Floor Resilience:** Importantly, the City Hotel does not resort to the extreme **low-season discounting** typical of the Resort Hotel. Instead, it maintains a higher price floor (above $80), indicating less pressure to reduce room rates in the low season dramatically.

**Recommendations**

The pricing trends must be closely **linked to the cancellation crisis**, which has resulted in a loss of $4.5 million in revenue, and the issues within the City Hotel’s **Transient segment**, which has a 40.75% cancellation rate. 


---
**REVPAR Trends Over Time Segmented by Hotel Type**

<img width="1202" height="587" alt="image" src="https://github.com/user-attachments/assets/3e1c7f09-d563-46ca-a4e3-4e1084147d76" />


---
- Which market segments and distribution channels bring in the highest-value customers (based on ADR and length of stay)?










