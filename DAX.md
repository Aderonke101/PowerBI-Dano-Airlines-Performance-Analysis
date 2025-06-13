# Dano Airlines Power BI DAX Measures

This file documents the key **DAX calculations** used to power the insights and visualizations in the **Dano Airlines Performance Overview** dashboard.

---

## 📌 Core Metrics


```DAX

1. Total Passengers = DISTINCTCOUNT(Dano_Airline_Data[ID])

2. Service Rank = 
RANKX(
    ALL('Dano_Airline_Data'[Service Name]),
    CALCULATE([Average Rating]),
    ,
    DESC
)

3. Satisfaction Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(Dano_Airline_Data), Dano_Airline_Data[Satisfaction] = "Satisfied"),
    COUNTROWS('Dano_Airline_Data')
)

4. Satisfaction by Travel Type = AVERAGE(Dano_Airline_Data[Satisfaction])

5. Satisfaction by Class = AVERAGE(Dano_Airline_Data[Satisfaction]) 

6. Satisfaction by Age Group = AVERAGE(Dano_Airline_Data[Satisfaction])

7. Dissatisfaction Rate = 
DIVIDE(
    CALCULATE(COUNTROWS('Dano_Airline_Data'), 'Dano_Airline_Data'[Satisfaction] = "Dissatisfied"),
    COUNTROWS('Dano_Airline_Data')
)

8. Avg Online Rating = 
CALCULATE(
    AVERAGE(Dano_Airline_Data[Rating]),
    'Dano_Airline_Data'[Service Category] = "Online Services"
)

9. Avg Inflight Rating = 
CALCULATE(
     AVERAGE(Dano_Airline_Data[Rating]),
     'Dano_Airline_Data'[Service Category] = "In-flight Services"
)

10. Avg Boarding Rating = 
CALCULATE(
    AVERAGE(Dano_Airline_Data[Rating]),
    'Dano_Airline_Data'[Service Category] = "Boarding Services"
)

11. Average Rating = 
AVERAGE(Dano_Airline_Data[Rating])

12. Average Flight Distance = AVERAGE(Dano_Airline_Data[Flight Distance])

13. % Returning Customers = 
DIVIDE(
    CALCULATE(COUNTROWS('Dano_Airline_Data'), 'Dano_Airline_Data'[Customer Type] = "Returning"),
    COUNTROWS('Dano_Airline_Data') * 100)

14. % First-time Customers = 
DIVIDE(
    CALCULATE(COUNTROWS('Dano_Airline_Data'), 'Dano_Airline_Data'[Customer Type] = "First-time"),
    COUNTROWS('Dano_Airline_Data') * 100)

15. % Customer Type = 
DIVIDE(
    COUNTROWS(Dano_Airline_Data),
    CALCULATE(COUNTROWS(Dano_Airline_Data), ALL(Dano_Airline_Data[Customer Type]))
)

