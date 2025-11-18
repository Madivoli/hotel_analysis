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

**Segment-Specific Insights**

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

The objective is to **lock in existing demand** and stabilise the booking forecast:

**Mandatory Non-Refundable Policy for Long Leads:** It is essential to focus on the months where the cancellation rate is worsening, and revenue growth is slowing (e.g., Q3 of 2017). Leadership should implement **a mandatory non-refundable deposit** (or full non-refundable rate) for any bookings made **more than 90 days** in advance. This approach will convert long-lead, high-risk "placeholder" bookings into actual revenue, directly addressing the core issues facing the City Hotel.

**Dynamic Pricing & Inventory Control:** During periods when year-over-year (YoY) cancellation rates are significantly positive (worsening, such as an increase of +4 percentage points in July), the hotel should **temporarily restrict inventory available** on high-flexibility, low-commitment channels (like certain Online Travel Agencies, or OTAs) for the same month in the following year.

**B. Strategic Focus: Resort Hotel (Sustainable Growth, Escalating Risk)**  
The goal is to **protect healthy revenue growth** by increasing customer commitment without discouraging new bookings:

**Value-Added Pre-Commitment:** Instead of simply requiring a cash deposit (which could deter leisure bookings), leadership should leverage the average long lead time (92.68 days) to sell **non-refundable, value-added ancillary services**. For example, a $50 non-refundable pre-payment could be required for a poolside cabana or spa treatment, which would secure a 10-15% discount on that service. This strategy utilizes the "Special Requests" metric to ensure cash commitment.

**Targeted Channel Review:** Leadership should promptly review the Resort Hotel's booking channels during months with the highest increases in cancellation rates (for instance, July’s +5.99 percentage points). If a specific third-party travel agent or OTA is contributing to low-commitment bookings, **stricter cancellation terms should be negotiated**, or their **inventory allotment should be reduced**.

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

**Key Insights**

**City Hotel Performance:**
- Higher ADR ($100.69 vs $92.45): 8.9% premium pricing power.
- Significantly higher total revenue ($25.27M vs $17.44M): 44.8% more revenue.
- Massive RevPAR advantage ($3,158 vs $2,199): 69.6% higher revenue efficiency.

**Resort Hotel Performance:**
- Lower ADR: Potential underpricing or different market positioning.
- Lower Total Revenue: Despite possibly similar room counts.
- Significantly Lower RevPAR: Major revenue optimisation opportunity.

**Implications and Opportunities**
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

**Resort Hotel: Pricing Strategy vs. Cancellation Risk**

The Resort Hotel's unstable pricing is directly related to its **cancellation challenges**:

- **Issue:** During the low-demand months (November to February), the hotel tends to **attract less profitable, low-commitment bookings at a lower ADR**. These low-ADR reservations are easily canceled when guests find better deals elsewhere, often characterized by the **"Book Now, Decide Later"** mentality.
- **Solution:** Increase the price floor during the low season (November to February). Rather than resorting to aggressive discounts on ADR, consider **bundling services** (such as offering free parking or a meal credit) that add perceived value and require a non-refundable deposit to secure. This approach allows the hotel to **use price resilience to filter out high-risk cancellations**.


**City Hotel: Capitalizing on Price Stability**

City Hotel's price stability provides a stronger foundation for managing cancellations:

- **Issue:** The hotel **heavily relies on Offline Travel Agents/Tour Operators (TA/TO)**, which means that **cancellations are often influenced by external contract terms** rather than dynamic pricing alone.
- **Solution:** Utilize the stable ADR to **implement non-refundable prepayments for all long-lead bookings** made through tour operators. Since the prices do not decrease significantly during the low season, guests have reduced incentives to cancel and rebook. Leverage the consistent ADR to **negotiate stricter cancellation terms in all new contracts**, focusing on the hotel’s top markets.

**ADR-Cancellation Correlation Analysis**

The hotels must **analyze the correlation between booking rates at high ADR and cancellation rates compared to those at low ADR**:
- If the data shows that **higher ADR correlates with lower cancellation rates, promote non-refundable rates aggressively** during the initial long-lead booking window, even for high-ADR bookings. This strategy will help lock in higher prices.
- If the data indicates that **ADR does not affect cancellation rates, then the issue may stem from lead time and flexibility**. In this case, an immediate shift to **mandatory deposit policies should be implemented** regardless of price.


---
**REVPAR Trends Over Time Segmented by Hotel Type**

The analysis of the **Revenue Per Available Room** (**RevPAR**) trend over time, segmented by hotel type, indicates that the City **Hotel serves as the primary driver of potential revenue**; however, **its volatility presents a significant financial risk**.

<img width="1202" height="587" alt="image" src="https://github.com/user-attachments/assets/3e1c7f09-d563-46ca-a4e3-4e1084147d76" />

**RevPAR Trends Over Time**

**City Hotel**  

The RevPAR trend for the City Hotel is marked by **sharp peaks** (in June and September) and **deep troughs** (in July and November), highlighting **its extreme dependence on seasonal demand**.

- **Dominant Performance:** The City Hotel consistently **generates a higher RevPAR** than the Resort Hotel throughout most of the year, solidifying its status as **the most profitable segment in terms of revenue per room**.
- **Peak Season:** The RevPAR experiences **significant spikes during the summer months**, reaching levels well above those of the Resort Hotel.
- **Volatile Trough:** The RevPAR sees **a steep decline during low-demand months**, dropping close to or sometimes below the RevPAR of the Resort Hotel. This **volatility is concerning due to a high cancellation rate of 41.73% for bookings made well in advance of these low-demand months**, leading to substantial potential losses that are challenging to offset.

**Resort Hotel**  

The RevPAR trend for the Resort Hotel is **more stable and follows a predictable leisure cycle**.

- **Consistent Lower Value:** The Resort Hotel **consistently maintains a lower RevPAR** compared to the City Hotel.
- **Muted Volatility:** Although the Resort Hotel follows a similar cyclical pattern, **the difference between its peak and trough is less extreme** than that of the City Hotel. This stability might be **attributed to its more measured Average Daily Rate (ADR) strategy and its reliance on package bookings from tour operators**.


**Recommendation: Connecting RevPAR to Cancellations**

The analysis of RevPAR (Revenue Per Available Room) highlights the need for the City Hotel to implement strict policies due to its significant potential revenue currently being lost to cancellations.

- **Risk-Adjusted RevPAR (RAR):** Hotels should calculate **Risk-Adjusted RevPAR** by multiplying RevPAR by the Realization Rate (1 - Cancellation Rate).
- **City Hotel RAR:** This metric needs close monitoring. With a cancellation rate of 41.73% (resulting in a realization rate of 58.27%), **the City Hotel is realizing just over half of its potential RevPAR**. This means that for every 100 rooms booked at the City Hotel, only about 58 are expected to generate revenue. The remaining 42 rooms inflate the forecast, creating considerable operational and financial uncertainty.

- **Resort Hotel RAR:** The Resort Hotel, with a 27.76% cancellation rate (therefore a 72.24% realization rate), is closer to achieving its potential RevPAR. Its lower volume is thus more reliable.
**Targeting Peaks for Protection:** The months with the highest RevPAR at the City Hotel are where **strict enforcement of non-refundable policies** for the Transient segment is most crucial. **Securing these peak-price bookings helps prevent significant financial losses**.
- **Cross-Segment Pricing Opportunity:** During low-demand months when the City Hotel's RevPAR approaches that of the Resort Hotel, it should **consider raising its price floor** and **prioritize attracting higher-value**, **lower-risk Contract** or **managed Group business** instead of offering discounts to the volatile Transient segment. 

These trends underscore the necessity for **non-negotiable policies focused on the high-RevPAR**, **high-volatility City Hotel** and **its primary booking sources**, including Online Travel Agencies (OTAs) and Transient customers.

---
**Customer Value Analysis (CVA)** 

This analysis aims to identify the countries, market segments, and distribution channels that yield **the highest-value customers** based on **Average Daily Rate** (ADR) and **Average Length of Stay** (ALOS).

**By country**

The findings reveal that **the most valuable guests typically come from smaller**, **niche international markets rather than the largest source countries**. For example, the UK ranks as the top source country for guests, with a total of $24,568 in bookings compared to France's $21,579. However, France has more valuable guests when measuring Revenue per Guest (RPG), with an average of $64,503.41 compared to the UK's $55,569.76.

<img width="1200" height="442" alt="image" src="https://github.com/user-attachments/assets/b133eddf-4a89-498c-bae6-6afa70988be7" />

<img width="1187" height="1508" alt="image" src="https://github.com/user-attachments/assets/2bef08aa-b236-40ff-b5af-fadc9c56b340" />


---
**By market segment**

This analysis of the most valuable market segments synthesizes key performance metrics: Average Daily Rate (ADR), Average Length of Stay (ALOS), Revenue per Available Room (RevPAR), and Total Revenue. From the analysis, **Online Travel Agents (OTAs) represent the most significant and valuable market segment**, with over 1,000 guests, 1,761 nights booked, an ADR of $61,123, a RevPAR of $244,778, and total revenue of $23,270,565 during the analyzed period. This segment is undoubtedly **the primary driver of the hotel’s revenue**. In contrast, **the segment with the least value is Aviation**, which recorded only 17 guests, an ALOS of 87 nights, an ADR of $1,717, a RevPAR of $9,563, and total revenue of $79,520.

<img width="1200" height="312" alt="image" src="https://github.com/user-attachments/assets/36f2bb90-1d3b-4ceb-ac85-ea58b2d9f03e" />

**Market Share and Volume:**

**Online TA** dominates with:
- 46% of total guests or confirmed bookings.
- 41% of total room nights.
- Highest revenue at $23.27M.

**Offline TA/TO** show strong performance:
- 371 confirmed bookings. 
- Over 7M in total revenue.
- Revenue per guest (RPG) of $19,108.22.
  
**Direct Channel** maintains significance presence:
- 24% of guests who have confirmed their reservation.
- 13% of total revenue.
- 878 nights that generated revenue of $4.7M.

**Strategic Opportunities:**

**Groups – high value in terms of ALOS:**
- Potential for expansion.
- Premium pricing justified by extended stays.

**Direct Channel Growth**
- Healthy ADR and RevPAR but lower total revenue.
- Opportunity to improve occupancy/revenue per room

**Offline TA/TO Optimization**
- Second largest volume but moderate RevPAR and lower ADR.
- Focus on increasing length of stay, ADR, or confirmed bookings/guests

**Revenue Concentration:**

- Top 3 Segments (Online TA, Offline TA/TO, Direct) generate over 98% of total revenue.
- Aviation, while small, shows premium pricing potential.

---
**By distribution channels**

The most significant revenue source is the Travel Agency/Tour Operator (TA/TO) channel, which served 1,548 guests across 2,757 stays, generating a total revenue of $31 million. This indicates that **the TA/TO channel is the primary and most valuable channel** for both the city hotel and the resort. The **second most valuable channel is the Direct channel**, which served 618 guests with 984 stays and generated a total revenue of $5 million. The **least valuable channel is the undefined segment**, which generated a total revenue of $1,099, resulting in a revenue per guest (RPG) of $219.

<img width="1200" height="234" alt="image" src="https://github.com/user-attachments/assets/8320dd9a-d50c-4fe2-9672-406d5ab9670e" />

**Key Implications**

1. Channel Dependency Risk
- TA/TO channels dominate with 65% of guests and 86% of revenue
- High vulnerability to commission costs and third-party dependency. 
- Direct channel underperforming relative to its potential. 26% of guests and 14% of revenue

2. Pricing Power Insights
- TA/TO demonstrates strong pricing power ($81,734 ADR)
- Direct accepting premium rates ($35,206 ADR) with good length of stay (984 nights).
- Corporate show willingness to pay for extended stays

3. Revenue Concentration
- Top 3 channels generate 98.8% of total revenue
- High reliance on TA/TO partnerships

**Strategic Recommendations**

1. Revenue Diversification

- Increase direct channel from 14% to 25% of revenue
- Invest in CRM and direct marketing
- Develop corporate portal for direct bookings

2.	Portfolio Optimization
- Reduce dependency on high-commission channels
- Develop proprietary technology for direct bookings
- Build segment-specific value propositions

3.	Dynamic Pricing Strategy
•	Channel-based pricing: Differentiate rates by channel value
•	Length-of-stay optimization: Incentivize longer bookings in high-ADR segments
•	Corporate rate restructuring: Move from flat to dynamic corporate pricing

---
---
**MARKETING TEAM**

•	Question 1: What are the most effective market segments and channels for securing bookings that do not get canceled?

•	Question 2: Which countries are the top sources of guests, and how does their booking lead time and cancellation rate vary?

**Top 10 Sources of Guests by Hotel Type**

<img width="1502" height="962" alt="image" src="https://github.com/user-attachments/assets/935c0a9f-6684-4265-b667-6c2fe4216cc9" />


<img width="975" height="644" alt="image" src="https://github.com/user-attachments/assets/8324b42f-1988-44f0-8c44-35cdd910f970" />

---
---
**OPERATIONS & RESERVATIONS TEAM**

•	Question 1: How far in advance (lead time) do guests typically book, and does a longer lead time correlate with a higher chance of cancellation?

•	Question 2: What is the most common room type (assigned_room_type) booked, and how often do guests get upgraded/downgraded from their reserved_room_type?
