Data Dictionary – Bank Marketing Dataset
Dataset Overview
Item	Description
Dataset name	bank
Description	Contains information about marketing calls made by the bank and whether the customer subscribed to a deposit product
Grain	One row per contact attempt
Primary KPI	Conversion Rate (Deposit Subscription)
📂 Table: bank
Column Name	Data Type	Description
balance	Numeric	Average yearly balance of customer
duration	Numeric (seconds)	Duration of last contact call
deposit	Text (yes / no)	Indicates whether the customer subscribed to deposit
contact	Text	Contact communication type (e.g., cellular, telephone)
📊 Measures
1. Avg Balance
Field	Value
Measure Name	Avg Balance
Formula	AVERAGE('bank'[balance])
Description	Average account balance across all contacted customers
Business Use	Used to understand financial profile of contacted audience
2. Avg Call Duration
Field	Value
Measure Name	Avg Call Duration
Formula	AVERAGE('bank'[duration])
Description	Average duration of marketing calls in seconds
Business Use	Helps analyse call engagement quality
3. Total Contacts
Field	Value
Measure Name	Total Contacts
Formula	COUNTROWS('bank')
Description	Total number of marketing calls made
Business Use	Overall campaign volume metric
4. Total Subscriptions
Field	Value
Measure Name	Total Subscriptions
Formula	
CALCULATE(
    COUNTROWS('bank'),
    'bank'[deposit] = "yes"
)
``` |
| Description | Total number of successful deposit subscriptions |
| Business Use | Core success metric of campaign |

---

### 5. Responses

| Field | Value |
|------|------|
| Measure Name | `Responses` |
| Formula |  
```DAX
CALCULATE( COUNTROWS('bank'), 'bank'[deposit] = "yes" )
``` |
| Description | Number of customers who subscribed |
| Business Use | Used as numerator for response and conversion KPIs |

---

### 6. Conversion Rate – Current Context

| Field | Value |
|------|------|
| Measure Name | `Conversion Rate Current Context` |
| Formula |  
```DAX
DIVIDE(
    CALCULATE( COUNTROWS('bank'), 'bank'[deposit] = "yes" ),
    CALCULATE( COUNTROWS('bank') ),
    0
)
``` |
| Description | Percentage of contacts that resulted in a subscription within the current filter context |
| Business Use | Main campaign effectiveness KPI |

---

### 7. Response Rate

| Field | Value |
|------|------|
| Measure Name | `Response Rate` |
| Formula | `[Conversion Rate Current Context]` |
| Description | Alias for Conversion Rate |
| Business Use | Alternative naming for reporting |

---

### 8. Subscriptions by Contact

| Field | Value |
|------|------|
| Measure Name | `Subscriptions by Contact` |
| Formula |  
```DAX
CALCULATE(
    [Total Subscriptions],
    ALLEXCEPT('bank', 'bank'[contact])
)
``` |
| Description | Number of subscriptions grouped only by contact type |
| Business Use | Compare effectiveness of contact channels |

---

### 9. Success Rate – Long Calls

| Field | Value |
|------|------|
| Measure Name | `Success Rate LongCalls` |
| Formula |  
```DAX
VAR Longs =
    FILTER( ALL('bank'), 'bank'[duration] > 300 )

RETURN
DIVIDE(
    CALCULATE( COUNTROWS(Longs), Longs[deposit] = "yes" ),
    CALCULATE( COUNTROWS(Longs) ),
    0
)
``` |
| Description | Conversion rate for calls longer than 300 seconds |
| Business Use | Measures impact of long engagement calls |

---

## 🧠 KPI Summary

| KPI | Measure |
|-----|--------|
| Campaign Reach | Total Contacts |
| Campaign Success | Total Subscriptions |
| Conversion Efficiency | Conversion Rate Current Context |
| Channel Effectiveness | Subscriptions by Contact |
| Engagement Impact | Success Rate LongCalls |

---
