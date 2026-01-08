📖 Data Dictionary: Bank Marketing Analysis.
This document provides a detailed breakdown of the metrics and business logic used in the Power BI dashboard.
 Measures Summary TableMeasure NameDescription FormatTotal ContactsTotal number of leads/customers contacted.
Whole NumberTotal Subscriptions Total number of successful "Yes" deposits.
Whole NumberConversion RatePercentage of contacts that resulted in a subscription.
PercentageAvg BalanceThe average account balance of the customers.
CurrencySuccess Rate (Long Calls)
Conversion rate for calls exceeding 5 minutes (300s).
Percentage. 
Detailed Business Logic (DAX)<details><summary>Total Contacts & Subscriptions</summary>Total contactsCounts every row in the bank table to represent the total outreach.Фрагмент кодаTotal contacts = COUNTROWS('bank')
Total SubscriptionsCounts only the rows where the outcome (deposit) was "yes".Фрагмент кодаTotal Subscriptions = 
CALCULATE(
    COUNTROWS('bank'), 
    'bank'[deposit] = "yes"
)
ResponsesAn alias for the total count of successful deposits.Фрагмент кодаResponses = CALCULATE( COUNTROWS('bank'), 'bank'[deposit] = "yes" )
</details><details><summary>Averages & Performance</summary>Avg BalanceCalculates the arithmetic mean of the 'balance' column.Фрагмент кодаAvg Balance = AVERAGE('bank'[balance])
Avg Call DurationThe mean length of calls in seconds.Фрагмент кодаAvg Call Duration = AVERAGE('bank'[duration])
</details><details><summary>Conversion & Rates</summary>Conversion Rate Current ContextThe primary KPI for campaign success. Calculated as (Subscriptions / Total Contacts).Фрагмент кодаConversion Rate Current Context = 
DIVIDE(
    CALCULATE( COUNTROWS('bank'), 'bank'[deposit] = "yes" ),
    CALCULATE( COUNTROWS('bank') ), 
    0
)
Response RateDirectly references the Conversion Rate measure for consistency across visuals.Фрагмент кодаResponse Rate = [Conversion Rate Current Context]
</details><details><summary>Advanced Analytics</summary>Subscriptions by ContactCalculates total subscriptions while ignoring filters except for the contact type. Useful for benchmarking specific contact methods against the total.Фрагмент кодаSubscriptions by Contact = 
CALCULATE( 
    [Total Subscriptions], 
    ALLEXCEPT('bank', 'bank'[contact]) 
)
Success Rate LongCallsA specialized KPI to analyze if longer call durations ( > 300 seconds) correlate with higher success.Фрагмент кодаSuccess Rate LongCalls = 
VAR Longs = FILTER( ALL('bank'), 'bank'[duration] > 300 )
RETURN DIVIDE(
    CALCULATE( COUNTROWS(Longs), Longs[deposit] = "yes" ),
    CALCULATE( COUNTROWS(Longs) ), 
    0
)
</details>3. Data Source NotesSource Table: bankKey Column: deposit (Values: "yes", "no")Granularity: One row per customer contact.