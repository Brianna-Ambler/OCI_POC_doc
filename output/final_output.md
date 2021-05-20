# Run Business queries Graph Schema in 19C
## Before You Begin

Objectives:  
We will be running queries from SQL Developer, this query will connect to OLAP customer details and graph table to get top 10 customers based on highest purchase, and then fetch the list of friends of those customers who are staying in 50 miles radius from primary customer’s address.


Prerequisites:  
This lab assumes you have completed all the other Labs




## **Step 1** Connect to Oracle database  
Connect to Oracle database instance as shown in Lab 1 Connect to DB instance  


## **Step 2:** Run Business queries
1. Execute below query which will give list of of top 10 customers
~~~~sql
select customer_dwh.social_media_id from cust_transaction_dwh
left outer join customer_dwh  on cust_transaction_dwh.customer_id = customer_dwh.customer_id
group by customer_dwh.social_media_id,cust_transaction_dwh.customer_id,cust_transaction_dwh.year_y,cust_transaction_dwh.month_m,cust_transaction_dwh.date_d order by sum(price) DESC FETCH FIRST 10 ROWS ONLY;

~~~~

2. Execute below query which will give list of customers which lives within 50 km of top customer. You can replace       social\_media\_id with any customer from above query.

~~~~sql
define social_media_id = '4121746429'

select social_media_id,customer_email from customer_dwh where sdo_within_distance(sch_name_to_geom(social_media_id), sch_name_to_geom(&&social_media_id), 'distance=50 unit=miles')='TRUE' and social_media_id <> &&social_media_id
and social_media_id IN (
SELECT
T0$4.V AS "CUST_F_SM_ID$V"
FROM "POC".oci_poc_graphGT$ T0$0,
( SELECT L.VID, L.VL, R.K, R.T, R.V, R.VN, R.VT
  FROM "POC".oci_poc_graphVD$ L,
       (SELECT * FROM "POC".oci_poc_graphVT$ WHERE K=n'SOCIAL_MEDIA_ID' ) R
  WHERE L.VID = R.VID(+)
) T0$1,
( SELECT L.VID, L.VL, R.K, R.T, R.V, R.VN, R.VT
  FROM "POC".oci_poc_graphVD$ L,
       (SELECT * FROM "POC".oci_poc_graphVT$ WHERE K=n'CUSTOMER_NAME' ) R
  WHERE L.VID = R.VID(+)
) T0$2,
( SELECT L.VID, L.VL, R.K, R.T, R.V, R.VN, R.VT
  FROM "POC".oci_poc_graphVD$ L,
       (SELECT * FROM "POC".oci_poc_graphVT$ WHERE K=n'LONGITUDE' ) R
  WHERE L.VID = R.VID(+)
) T0$3,
( SELECT L.VID, L.VL, R.K, R.T, R.V, R.VN, R.VT
  FROM "POC".oci_poc_graphVD$ L,
       (SELECT * FROM "POC".oci_poc_graphVT$ WHERE K=n'SOCIAL_MEDIA_ID' ) R
  WHERE L.VID = R.VID(+)
) T0$4,
( SELECT L.VID, L.VL, R.K, R.T, R.V, R.VN, R.VT
  FROM "POC".oci_poc_graphVD$ L,
       (SELECT * FROM "POC".oci_poc_graphVT$ WHERE K=n'LATITUDE' ) R
  WHERE L.VID = R.VID(+)
) T0$5
WHERE T0$0.SVID=T0$1.VID AND
T0$0.DVID=T0$2.VID AND
T0$0.DVID=T0$3.VID AND
T0$0.DVID=T0$4.VID AND
T0$0.DVID=T0$5.VID AND
(T0$1.VL = n'PERSON' AND T0$1.VL IS NOT NULL) AND
(T0$2.VL = n'PERSON' AND T0$2.VL IS NOT NULL) AND
(T0$0.EL = n'KNOWS' AND T0$0.EL IS NOT NULL) AND
(T0$1.T = 1 AND T0$1.V = n'&&social_media_id'))

~~~~
