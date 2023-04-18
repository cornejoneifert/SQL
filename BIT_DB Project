/*In this SQL, I'm querying a database with multiple tables to quantify
    statistics about customer and order data*/

/*How many orders were placed in January?*/
SELECT COUNT(orderID) FROM BIT_DB.JanSales;

/*How many of those orders were for an iPhone?*/
SELECT COUNT(orderID) FROM BIT_DB.JanSales
    WHERE product='iPhone';
    
/*Select the customer account numbers for all the orders that were placed in February.*/
SELECT distinct acctnum
    FROM BIT_DB.customers customer
    INNER JOIN BIT_DB.FebSales feb
    ON feb.orderID=customer.order_id
    WHERE length(order_id) = 6
    AND order_id <> 'Order ID';
    
/*Which product was the cheapest one sold in January, and what was the price?*/
SELECT product, MIN(price) FROM BIT_DB.JanSales
    GROUP BY product, price
    ORDER BY price ASC LIMIT 1;

/*What is the total revenue for each product sold in January?
    (Revenue can be calculated using the number of products sold and the price of the products).*/
SELECT SUM(quantity)*price AS revenue, product
    FROM BIT_DB.JanSales
    GROUP BY product;
    
/*Which products were sold in February at 548 Lincoln St, Seattle, WA 98101,
    how many of each were sold, and what was the total revenue?*/
SELECT product, SUM(quantity) AS "units sold", SUM(quantity)*price AS "revenue"
    FROM BIT_DB.FebSales
    WHERE location='548 Lincoln St, Seattle, WA 98101'
    GROUP BY product;

/*How many customers ordered more than 2 products at a time in February,
    and what was the average amount spent for those customers?*/
SELECT COUNT(distinct cust.acctnum), AVG(quantity*price)
    FROM BIT_DB.FebSales feb
    LEFT JOIN BIT_DB.customers cust
    ON cust.order_id=feb.orderID
    WHERE feb.quantity>2
    AND length(orderid) = 6
    AND orderid <> 'Order ID';





