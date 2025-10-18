--- PROPERTY SALES DATA ---
<img width="1158" height="705" alt="propertySales data" src="https://github.com/user-attachments/assets/c325175b-4a3f-47cc-b8ab-62a1d7a75703" />


The Goal of this project is to analyze and visualize:

1. how many properties was sold in Europe. Need to choose all EU countries

2.what is an average property size?

3. which property type is most popular?

4. verage construction year

5. Average property price.

6. Average number of bedrooms.

7. Average loan amount.

--- ADDED TABLE CALCULATIONS in PowerBI

Average Property Size = AVERAGE('global_house_purchase_dataset'[property_size_sqft])
Average_construction_year = AVERAGE('global_house_purchase_dataset'[constructed_year])
Average_loan_amount = AVERAGE('global_house_purchase_dataset'[loan_amount])
Average_property_price = AVERAGE('global_house_purchase_dataset'[price])

Difference between loan and price
Difference = AVERAGE('global_house_purchase_dataset'[loan_amount]) / AVERAGE('global_house_purchase_dataset'[price]) * 100

EU property sold: 
EU Properties Sold = 
CALCULATE (
    COUNTROWS ( 'global_house_purchase_dataset' ),
    'global_house_purchase_dataset'[country] IN {
        "Austria","Belgium","Bulgaria","Croatia","Cyprus","Czechia",
        "Czech Republic","Denmark","Estonia","Finland","France","Germany",
        "Greece","Hungary","Ireland","Italy","Latvia","Lithuania","Luxembourg",
        "Malta","Netherlands","Poland","Portugal","Romania",
        "Slovakia","Slovenia","Spain","Sweden"
    }
)
    CONCLUSIONS:

    Maximum property size is 6000 square feet, doble times bigger than average, which is only 3200 sq.feet.
    Most popular sale property type is farmhouse, (33.5%), but all other are very close. The difference is les then 1%
    Difference between average loan and average price is 62,51%. Average loan is high, ($0.76 M).
    Most of all properties was built in mid nighty's. Average year 1991.
    Properties are quite expensive, Average is $3.2 M, Maximum price is $4 M.
    

