# Project: Internship at Y.Afisha

*After managing to show brilliant performance during the Tripleten course. You were offered the opportunity to undergo an intership program in the **Y.Afisha's Analytics Departement**. On your first day, the **marketing department** give you a task to help them **optimize the marketing cost budget**.*

*In front of you are available data from January 2017 to December 2018 which consist of 3 files containing:*
- **Servers logs**/record of Y.Afisha site visit;
- **Order** data;
- Marketing **cost statistics**.

*By completing this task, they expect you to learn:*
- Y.Afisha user behaviour;
- Cohort analysis;
- Revenue generated;
- When all marketing costs pay off.

**Project Instructions**
1. ***Download data and prepare it for analysis***
    - Store visit, order, and expense data in variables.
    - Optimize the data you have for analysis purposes.
    - Make sure each of its columns is presented in the correct data type.
    - File path:
        - /datasets/visits_log_us.csv
        - /datasets/orders_log_us.csv
        - /datasets/costs_us.csv

2. ***Compile reports and calculate metrics:***
    
    - **Product**
        - How many people **use** the product **every day**, **week**, and **month**?
        - What is the number of **sessions per day**? (One user may have more than one session).
        - What is the **duration** for **each session**?
        - How often do **users return** to using the product?

    - **Sales**
        - **When** do people **start** making purchases?
            - **Additional Note**: In **KPI analysis**, we are usually interested in knowing the time that **elapses from** the time the **registration** is made until the **conversion** occurs or when an authorized user switches to a customer. For example, if the first registration and purchase occurred on the same day, that user could be included in the h0 Conversion category. If the first purchase occurs the next day, the category will also be h1 Conversions. You are welcome to use any approach that allows you to compare conversions from different cohorts, so you can determine which cohort or marketing channel is most effective.
        - How many **orders** do they make **over a period of time**?
        - What is the **average purchase size**?
        - How much money do they contribute? (**LTV**)

    - **Marketing**
        - How much **money is spent**? Overall/per source/over time
        - How much does **customer acquisition cost** (CAC) from each source?
        - How profitable is the investment? (**ROI**)

     *Create a **graph** that shows **how these metrics differ** for **different devices** and **ad sources**, as well as how they have **changed over time**.*

3. ***Writing down the conclusion:*** *tell marketing specialists how much money to invest and **where it should be invested**.*
   - What **sources/platforms** would you **recommend**?
   - Give reasons to support your choice:
       - What **metrics** do you focus on?
       - **Why**?
       - What **conclusions** do you make after finding the values of those metrics?

**Data dictionary**
**The visits table (server logs with data on website access):**
- `Uid` — Unique user identifier
- `Device` — User's device
- `Start Ts` — Session start date and time
- `End Ts` — Session end date and time
- `Source Id` — The ID of the advertising source, the source with which the user comes to the website

**The orders table (order data):**
- `Uid` — Unique identifier of the user placing an order
- `Buy Ts` — Order date and time
- `Revenue` — Y.Afisha's revenue with order

**The costs table (data on marketing expenses):**
- `source_id` — Ad source identifier
- `dt` — Date
- `costs` — Expenses for this ad source on this day

**Conclusion**
**Overview do dataframe df_visits:**
- *The dataframe contains five columns `device`, `end_ts`, `source_id`, `start_ts` and `user_id` with 50415 rows each and each of type object, int64, object, or uint64. A few of the column names have been changed, and the data type of the `end_ts` and `start_ts` columns has been changed from object to datetime. The dataframe shows no significant difference between mean and median, and no duplicate or missing data.*

**Overview do dataframe df_orders:**
- *The dataframe contains three columns, `user_id`, `revenue`, and `orders_ts`, with 50415 rows each. The columns have been changed from `buy ts` to `orders_ts`, and the data type of `orders_ts` was changed from object to datetime. And no duplicate or missing data.*

**Overview do dataframe df_costs:**
- *The dataframe contains three columns, `source_id`, `dt`, and `costs`, with 2542 rows each. The columns have been changed from `dt` to `date`, the data type of `date` changed from object to datetime, and there are no duplicate or missing data.*

*On **product analysis**, we answer the question asked by calculating these following metrics.*
- **Active User**
    - Daily: 907 users
    - Weekly: 5,825 users
    - Monthly: 23,228 users
- **Session per Day**: 987 sessions
- **Session Length**:
    - Average: 10 minutes
    - Mode: 60 seconds
- **Sticky Factor**:
    - Weekly: 15.59%
    - Monthly: 3.91%

On **sales analysis**, we answer the question asked by calculating these following metrics.

- **Lead time** - Time taken from the first session start to a final decision to purchase product
    - Average: 4 hours and 44 minutes
    - Median: 20 minutes
    - Max: 24 hours
- **Cohort Analysis**
    - Order count: The significant drop after the first month for each cohort show a majority of users are not making repeat purchases.
    - Average revenue per user: This analysis shows that the buyer who decided to make a repeat purchase, order in higher volume then their first order.
    - Lifetime Value: Each cohort starts with almost similar LTV, experience drop in average revenue per buyer the following month and cumulatively continues to increase in value.

***After conducting product, sales, and marketing analysis. We recommend marketing department to:***
- *Invest **more** money on **ad source** that have **low customer aqcuisition cost** such as ad source 2, 3, and 4*;
- *Start investing on **high visitor ad source** that have not been invested (ad source 9, and 10)*;
- *Invest **less** on ad source with **high customer acquisition cost** such as ad source 6*.
