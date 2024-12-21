# interview-questions
Sql interview Questions 



Sql interview Questions Data Analyst interview questions for Experience candidate

Find out delivery partner wise delayed orders count (delay means - the order which tookmore than predicted time to deliver the order). 
wrire a sql query to calculate the number of delayed orders for each delivery partner. 
an order is considered delayed if the actual delivery time exceeds the predicted delivery time.

NOTE -- if a partner has no delayed orders then display as 0

CREATE TABLE swiggy_orders ( orderid INT PRIMARY KEY, custid INT, city VARCHAR(50), del_partner VARCHAR(50), order_time DATETIME, deliver_time DATETIME, predicted_time INT 
-- Predicted delivery time in minutes );

DDL 
INSERT INTO swiggy_orders (orderid, custid, city, del_partner, order_time, deliver_time, predicted_time) VALUES

DML

(1, 101, 'Mumbai', 'Partner A', '2024-12-18 10:00:00', '2024-12-18 11:30:00', 60), (2, 102, 'Delhi', 'Partner A', '2024-12-18 09:00:00', '2024-12-18 10:00:00', 45), (3, 103, 'Pune', 'Partner A', '2024-12-18 15:00:00', '2024-12-18 15:30:00', 30), (4, 104, 'Mumbai', 'Partner A', '2024-12-18 14:00:00', '2024-12-18 14:50:00', 45), (5, 105, 'Bangalore', 'Partner B', '2024-12-18 08:00:00', '2024-12-18 08:29:00', 30), (6, 106, 'Hyderabad', 'Partner B', '2024-12-18 13:00:00', '2024-12-18 14:00:00', 70), (7, 107, 'Kolkata', 'Partner B', '2024-12-18 10:00:00', '2024-12-18 10:40:00', 45), (8, 108, 'Delhi', 'Partner B', '2024-12-18 18:00:00', '2024-12-18 18:30:00', 40), (9, 109, 'Chennai', 'Partner C', '2024-12-18 07:00:00', '2024-12-18 07:40:00', 30), (10, 110, 'Mumbai', 'Partner C', '2024-12-18 12:00:00', '2024-12-18 13:00:00', 50), (11, 111, 'Delhi', 'Partner C', '2024-12-18 09:00:00', '2024-12-18 09:35:00', 30), (12, 112, 'Hyderabad', 'Partner C', '2024-12-18 16:00:00', '2024-12-18 16:45:00', 30);

query solutions

select del_partner, sum( case when datediff(MINUTE,order_time,deliver_time) > predicted_time then 1 else 0 end )as flag from swiggy_orders group by del_partner

2 )

On which date did the 3rd highest sale of product 4 take place in terms of value

DDL
CREATE TABLE sales_data ( order_date DATE, customer_id INT, store_id INT, product_id INT, sale INT, order_value INT );
DML
INSERT INTO sales_data (order_date, customer_id, store_id, product_id, sale, order_value) VALUES ('2024-12-01', 109, 1, 3, 2, 700), ('2024-12-02', 110, 2, 2, 1, 300), ('2024-12-03', 111, 1, 5, 3, 900), ('2024-12-04', 112, 3, 1, 2, 500), ('2024-12-05', 113, 3, 4, 4, 1200), ('2024-12-05', 114, 3, 4, 2, 400), ('2024-12-05', 115, 3, 4, 1, 300), ('2024-12-01', 101, 1, 4, 2, 500), ('2024-12-01', 102, 1, 4, 1, 300), ('2024-12-02', 103, 2, 4, 3, 900), ('2024-12-02', 104, 2, 4, 1, 400), ('2024-12-03', 105, 1, 4, 2, 600), ('2024-12-03', 106, 1, 4, 3, 800), ('2024-12-04', 107, 3, 4, 1, 200), ('2024-12-04', 108, 3, 4, 2, 500);

query with cte as ( select order_date,sum(order_value) as total_sales, DENSE_RANK() over(order by sum(order_value) desc) as rnk from swiggy_sales12 where product_id = 4 group by order_date ) select order_date,total_sales from cte where rnk = 3

Editing interview-
