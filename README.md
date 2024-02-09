# zoomcamp_hw3
Homework 3: Data Warehouse for Data Engineering Zoomcamp 2024


SELECT * FROM `terraform-demo-411110.green_taxi.green_taxi_2022` LIMIT 10;

SELECT count(*) FROM `terraform-demo-411110.green_taxi.green_taxi_2022` LIMIT 1000;

SELECT DISTINCT PULocationID FROM `terraform-demo-411110.green_taxi.green_taxi_2022`; 

SELECT DISTINCT PULocationID FROM `terraform-demo-411110.green_taxi.green_taxi_2022_mat`; 

SELECT count(*) FROM `terraform-demo-411110.green_taxi.green_taxi_2022_mat`
where fare_amount = 0;

CREATE OR REPLACE TABLE green_taxi.green_taxi_2022_part
PARTITION BY
  DATE(lpep_pickup_datetime) 
CLUSTER BY
  PULocationID AS
SELECT * FROM `terraform-demo-411110.green_taxi.green_taxi_2022`;

SELECT DISTINCT PULocationID FROM `terraform-demo-411110.green_taxi.green_taxi_2022_mat`
WHERE lpep_pickup_datetime >= '2022-06-01' AND lpep_pickup_datetime <= '2022-06-30';

SELECT DISTINCT PULocationID FROM `terraform-demo-411110.green_taxi.green_taxi_2022_part`
WHERE lpep_pickup_datetime >= '2022-06-01' AND lpep_pickup_datetime <= '2022-06-30';
