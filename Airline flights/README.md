<img width="1166" height="756" alt="dashboard" src="https://github.com/user-attachments/assets/ed2bbb32-7809-4dca-90b0-e4438706f319" />

-- CREATED MODEL


<img width="1846" height="902" alt="model" src="https://github.com/user-attachments/assets/1bfbb056-78ec-45cc-9488-7f1e474c95cc" />

-- DAX MESURES

% Cancelled = DIVIDE([Cancelled Flights], [Total flights],"-")
% Delayed = DIVIDE([Delayed Flights], [Total flights],"-")
% On-Time = DIVIDE([On-Time Flights], [Total flights],"-")
Cancelled Flights = CALCULATE([Total flights], flights[Status]="Cancelled")
Delayed Flights = CALCULATE([Total flights], flights[Status]="Dellay")
On-Time Flights = CALCULATE([Total flights], flights[Status]="On-Time")
Total flights = COUNTROWS(flights)


