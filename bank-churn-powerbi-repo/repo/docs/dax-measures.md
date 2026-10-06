# DAX: columns and measures
Table name: `Churn` (columns: CustomerId, CreditScore, Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, EstimatedSalary, Exited)

## Calculated columns
```dax
Churn Status = IF(Churn[Exited] = 1, "CHURNED", "STAYED")
Activity Status = IF(Churn[IsActiveMember] = 1, "ACTIVE", "INACTIVE")
Card Status = IF(Churn[HasCrCard] = 1, "OWNED", "NOT OWNED")
Age Group =
SWITCH(TRUE(),
  Churn[Age] <= 20, "18-20", Churn[Age] <= 30, "21-30", Churn[Age] <= 40, "31-40",
  Churn[Age] <= 50, "41-50", Churn[Age] <= 60, "51-60", ">60")
Credit Bucket =
SWITCH(TRUE(),
  Churn[CreditScore] <= 400, "<=400", Churn[CreditScore] <= 500, "401-500",
  Churn[CreditScore] <= 600, "501-600", Churn[CreditScore] <= 700, "601-700",
  Churn[CreditScore] <= 800, "701-800", ">800")
Balance Bucket =
SWITCH(TRUE(),
  Churn[Balance] = 0, "0", Churn[Balance] <= 10000, "1-10K", Churn[Balance] <= 100000, "10K-100K",
  Churn[Balance] <= 200000, "100K-200K", ">200K")
```

## Measures
```dax
Total Customers = COUNTROWS(Churn)
Churned Customers = CALCULATE([Total Customers], Churn[Exited] = 1)
Churn Rate = DIVIDE([Churned Customers], [Total Customers])
Retention Rate = 1 - [Churn Rate]
Avg Balance (Churned) = CALCULATE(AVERAGE(Churn[Balance]), Churn[Exited] = 1)
Avg Credit Score = AVERAGE(Churn[CreditScore])
Churn Rate vs Overall = [Churn Rate] - CALCULATE([Churn Rate], ALL(Churn))
```
Sort bucket columns with a helper sort column (1..6) via Column tools -> Sort by column.
