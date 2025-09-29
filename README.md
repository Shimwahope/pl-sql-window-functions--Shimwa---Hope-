[Database with PL.docx](https://github.com/user-attachments/files/22603185/Database.with.PL.docx)
# pl-sql-window-functions--Shimwa---Hope-
PL/SQL assignment answer


Step 1:
A. IWAWE Properties Rwanda  
Real estate industry 
Sales department

B.
IWAWE Properties Rwanda want to analyze the company’s performance. They want to know the regions with the most sales, the best agents of company and the bestselling houses.

C.
The expected outcome is to be able to show and analyze the performance of the company. To show agents that are doing good and the ones that are performing poorly.


Step  2:
1. Running total sales smoothly
2. Agent of the month
3. Region with the most sales
4. The houses people want
5. Best modes of payment


Step 3:
Table	Purpose	Column
1. Agent :sales agent	:Id,name,no,salary,status
2. Sales	:Each sale	:Id,agent_id,property_id,price,date,region_id
3. properties:Houses or unit being sold:Id,region_id,address,model_id,listed_price
4. Region	:Districts where properties are located	:id,name
5. Model	:Types of properties sold	:id,.name



Step 4:
1. ranking:
Row_ number: ranks without douplicating rank for similar values.
select id,listed_price, row_number() over(order by listed_price)as Row_numbers from properties. 

Rank : rank while douplicating ranks for similar values and continue numbering without skipping a digit.
select id,listed_price, rank() over(order by listed_price)as Rank from properties;

Dense_rank: rank while douplicating ranks for similar values but skip diggits that were ranked the same. 
select id,listed_price, dense_rank() over(order by listed_price)as Dense_rank from properties;

2. Aggregates:
Avg calculates the average of numbers,
select avg(price) as Average_price from sale;

min display the minimum value
select min(price) as minimum_price from sale;

max display the maximum value.
select max(price) as maximum_price from sale;

3. Navigation:
lead() show the next value 
select price,date,lead(price) over (order by date asc) as next_price from sale;

lag() shows previous value
select price,date,lag(price) over (order by date asc) as previous_price from sale;

4. Distribution:
cume_dist(): calculate cumulative distribution and give answer between 1 and 0
select agent_id,price,cume_dist() over (order by price desc) as cume_distribution from sale;

Ntile(n): creates segments according to the number in the brackets.
select agent_id,price,ntile(3) over (order by price desc) as sale_segment from sale;


Step 6:
1. Descriptive: The queries show that in 21 properties,13 have been sold by all the agent with agent 1,5 (David,Isheja)the best agents and Gikondo the best selling region.

2. Diagnosis: People have been needing properties in Gikondo as it is in the city and we have many properties there.

3. Prescription:We have to increase our agents and properties so that the sales the next month  may increase even in other regions.


Step 7:
Reference:
YouTube tutorial on ranks: https://www.youtube.com/watch?v=rIcB4zMYMas

Tutorial on ranks and navigation: https://www.youtube.com/watch?v=Ww71knvhQ-s&t=196s

https://www.youtube.com/watch?v=nHEEyX_yDvo
SCreenshoot and ER diagram
[Database with PL.odt](https://github.com/user-attachments/files/22603215/Database.with.PL.odt)
