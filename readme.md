<div align="center" id="top"> 
  <img src="./.github/app.gif" alt="Namaste_sql" />

&#xa0;

  <!-- <a href="https://namaste_sql.netlify.app">Demo</a> -->
</div>

<h1 align="center">Namaste_sql</h1>

<p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8">

  <img alt="Github language count" src="https://img.shields.io/github/languages/count/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8">

  <img alt="License" src="https://img.shields.io/github/license/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8">

  <!-- <img alt="Github issues" src="https://img.shields.io/github/issues/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8" /> -->

  <!-- <img alt="Github forks" src="https://img.shields.io/github/forks/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8" /> -->

  <!-- <img alt="Github stars" src="https://img.shields.io/github/stars/{{YOUR_GITHUB_USERNAME}}/namaste_sql?color=56BEB8" /> -->
</p>

<!-- Status -->

<!-- <h4 align="center">
	🚧  Namaste_sql 🚀 Under construction...  🚧
</h4>

<hr> -->

<p align="center">
  <a href="#dart-about">About</a> &#xa0; | &#xa0; 
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#rocket-technologies">Technologies</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requirements">Requirements</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-starting">Starting</a> &#xa0; | &#xa0;
  <a href="https://github.com/suneelkumarr" target="_blank">Author</a>
</p>

<br>

## :dart: About

Heare all video solutions avaiable for sql interviews

## :rocket: Technologies

The following tools were used in this project:

- [SQL](https://www.microsoft.com/en-gb/sql-server/sql-server-2022)

## :white_check_mark: Requirements

Before starting :checkered_flag:, you need to have [mssql](https://www.microsoft.com/en-gb/sql-server/sql-server-2022) installed.

## :checkered_flag: Starting

```bash
# Clone this project
$ git clone https://github.com/suneelkumarr/namaste_sql.git

# Access
$ cd namaste_sql
```

## Video_1 Derive Points table for ICC tournament S

Here is the table for icc tournament

<table> 
<tr> 
<th> Team_1</th>
<th> Team_2</th>
<th> Winner </th>
</tr>
<tr>
<td> IND</td>
<td> SL</td>
<td> IND</td>
</tr>
<tr>
<td> AUS</td>
<td> SL</td>
<td> AUS</td>
</tr>
<tr>
<td> AUS</td>
<td> SA</td>
<td> SA</td>
</tr>
<tr>
<td> IND</td>
<td> SA</td>
<td> IND</td>
</tr>
<table>

output table is looked like :

<table> 
<tr> 
<th>tram_name</th>
<th>no_of_matches_played</th>
<th> no_of_matches_won </th>
<th> no_of_matches_lossed </th>
</tr>
<tr>
<td> IND</td>
<td> 2</td>
<td> 2</td>
<td> 0</td>
</tr>
<tr>
<td> AUS</td>
<td> 2</td>
<td> 1</td>
<td> 1</td>
</tr>
<tr>
<td> SA</td>
<td> 2</td>
<td> 1</td>
<td> 1</td>
</tr>
<tr>
<td> SL</td>
<td> 2</td>
<td> 0</td>
<td> 2</td>
</tr>
<table>

```sql
--first create the table

create table icc_word_cup (
    team_1 Varchar(10),
    team_2 Varchar(10),
    winners Varchar(10),
)

-- then insert the records into the table

insert into icc_word_cup values ('IND', 'SL', 'IND')
insert into icc_word_cup values ('AUS', 'SL', 'AUS')
insert into icc_word_cup values ('AUS', 'SA', 'SA')
insert into icc_word_cup values ('IND', 'SA', 'IND')


-- fetch the record from table

select * from icc_word_cup

-- after that aggregate the final table

select team_name , count(1) as no_of_matches_played , sum(win_flag) as no_of_matches_won , count(1) - sum(win_flag) as no_of_matches_lossed
from (
select team_1 as team_name , case when team_1=Winner then 1 else 0 end as win_flag
from icc_world_cup
union all
select team_2 as team_name , case when team_2=Winner then 1 else 0 end as win_flag
from icc_world_cup ) A
group by team_name
order by no_of_matches_won desc
```

## Product Category

You are provided with a table named Products containing information about various products, including their names and prices. Write a SQL query to count number of products in each category based on its price into three categories below. Display the output in descending order of no of products.

1- "Low Price" for products with a price less than 100

2- "Medium Price" for products with a price between 100 and 500 (inclusive)

3- "High Price" for products with a price greater than 500.

Tables: Products

<table>
    <thead>
        <tr>
            <th>COLUMN_NAME</th>
            <th>DATA_TYPE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td>product_id</td>
        <td>int</td>
        </tr>
               <tr>
        <td>product_name</td>
        <td>varchar(20)</td>
        </tr>
               <tr>
        <td>price</td>
        <td>int</td>
        </tr>
    </tbody>
 </table>

INPUT:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Table</title>
    <style>
        table {
            width: 50%;
            border-collapse: collapse;
            margin: 25px 0;
            font-size: 18px;
            text-align: left;
        }
        th, td {
            padding: 12px;
            border: 1px solid #dddddd;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

<table>
    <thead>
        <tr>
            <th>product_id</th>
            <th>product_name</th>
            <th>price</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Laptop</td>
            <td>800</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Smartphone</td>
            <td>600</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Headphones</td>
            <td>50</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Tablet</td>
            <td>400</td>
        </tr>
        <tr>
            <td>5</td>
            <td>Keyboard</td>
            <td>30</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Mouse</td>
            <td>15</td>
        </tr>
        <tr>
            <td>7</td>
            <td>Monitor</td>
            <td>350</td>
        </tr>
        <tr>
            <td>8</td>
            <td>Printer</td>
            <td>120</td>
        </tr>
        <tr>
            <td>9</td>
            <td>USB Drive</td>
            <td>10</td>
        </tr>
        <tr>
            <td>10</td>
            <td>External Hard Drive</td>
            <td>150</td>
        </tr>
        <tr>
            <td>11</td>
            <td>Wireless Router</td>
            <td>80</td>
        </tr>
        <tr>
            <td>12</td>
            <td>Bluetooth Speaker</td>
            <td>70</td>
        </tr>
        <tr>
            <td>13</td>
            <td>Webcam</td>
            <td>45</td>
        </tr>
        <tr>
            <td>14</td>
            <td>Microphone</td>
            <td>25</td>
        </tr>
        <tr>
            <td>15</td>
            <td>Gaming Mouse</td>
            <td>50</td>
        </tr>
    </tbody>
</table>

</body>
</html>

OUTPUT:

<table>
    <thead>
        <tr>
            <th>category</th>
            <th>no_of_products</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td>Low Price</td>
        <td>9</td>
        </tr>
               <tr>
        <td>Medium Price</td>
        <td>4</td>
        </tr>
               <tr>
        <td>High Price</td>
        <td>2</td>
        </tr>
    </tbody>
 </table>

```sql
with cte as (
SELECT
    product_id,  product_name, price,
    CASE
        WHEN price < 100 THEN 'Low Price'
        WHEN price >= 100 AND price <= 500 THEN 'Medium Price'
        ELSE 'High Price'
    END AS category
FROM Products
)
select category , count(*) as no_of_products
from cte
group by category
ORDER BY no_of_products DESC;

```

## Airbnb Top Hosts

Suppose you are a data analyst working for a travel company that offers vacation rentals similar to Airbnb. Your company wants to identify the top hosts with the highest average ratings for their listings. This information will be used to recognize exceptional hosts and potentially offer them incentives to continue providing outstanding service.

Your task is to write an SQL query to find the top 2 hosts with the highest average ratings for their listings. However, you should only consider hosts who have at least 2 listings, as hosts with fewer listings may not be representative.

Display output in descending order of average ratings and round the average ratings to 2 decimal places.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Database Schema</title>
    <style>
        table {
            width: 50%;
            border-collapse: collapse;
            margin: 25px 0;
            font-size: 18px;
            text-align: left;
        }
        th, td {
            padding: 12px;
            border: 1px solid #dddddd;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

<h2>Table: listings</h2>
<table>
    <thead>
        <tr>
            <th>COLUMN_NAME</th>
            <th>DATA_TYPE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>host_id</td>
            <td>int</td>
        </tr>
        <tr>
            <td>listing_id</td>
            <td>int</td>
        </tr>
        <tr>
            <td>minimum_nights</td>
            <td>int</td>
        </tr>
        <tr>
            <td>neighborhood</td>
            <td>varchar(20)</td>
        </tr>
        <tr>
            <td>price</td>
            <td>decimal(10,2)</td>
        </tr>
        <tr>
            <td>room_type</td>
            <td>varchar(20)</td>
        </tr>
    </tbody>
</table>

<h2>Table: reviews</h2>
<table>
    <thead>
        <tr>
            <th>COLUMN_NAME</th>
            <th>DATA_TYPE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>listing_id</td>
            <td>int</td>
        </tr>
        <tr>
            <td>rating</td>
            <td>int</td>
        </tr>
        <tr>
            <td>review_date</td>
            <td>date</td>
        </tr>
        <tr>
            <td>review_id</td>
            <td>int</td>
        </tr>
    </tbody>
</table>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Listings and Reviews</title>
    <style>
        table {
            width: 70%;
            border-collapse: collapse;
            margin: 25px 0;
            font-size: 18px;
            text-align: left;
        }
        th, td {
            padding: 12px;
            border: 1px solid #dddddd;
        }
        th {
            background-color: #f2f2f2;
        }
        caption {
            font-size: 1.5em;
            margin: 10px 0;
        }
    </style>
</head>
<body>

<h2>Listings</h2>
<table>
    <caption>Listings Table</caption>
    <thead>
        <tr>
            <th>listing_id</th>
            <th>host_id</th>
            <th>neighborhood</th>
            <th>room_type</th>
            <th>price</th>
            <th>minimum_nights</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>101</td>
            <td>Downtown</td>
            <td>Entire home/apt</td>
            <td>150.00</td>
            <td>2</td>
        </tr>
        <tr>
            <td>2</td>
            <td>101</td>
            <td>Downtown</td>
            <td>Private room</td>
            <td>80.00</td>
            <td>1</td>
        </tr>
        <tr>
            <td>3</td>
            <td>101</td>
            <td>Downtown</td>
            <td>Entire home/apt</td>
            <td>200.00</td>
            <td>3</td>
        </tr>
        <tr>
            <td>4</td>
            <td>102</td>
            <td>Downtown</td>
            <td>Entire home/apt</td>
            <td>120.00</td>
            <td>2</td>
        </tr>
        <tr>
            <td>5</td>
            <td>102</td>
            <td>Downtown</td>
            <td>Private room</td>
            <td>100.00</td>
            <td>1</td>
        </tr>
        <tr>
            <td>6</td>
            <td>102</td>
            <td>Midtown</td>
            <td>Entire home/apt</td>
            <td>250.00</td>
            <td>2</td>
        </tr>
        <tr>
            <td>7</td>
            <td>103</td>
            <td>Midtown</td>
            <td>Private room</td>
            <td>70.00</td>
            <td>1</td>
        </tr>
        <tr>
            <td>8</td>
            <td>103</td>
            <td>Queens</td>
            <td>Private room</td>
            <td>90.00</td>
            <td>1</td>
        </tr>
        <tr>
            <td>9</td>
            <td>104</td>
            <td>Midtown</td>
            <td>Private room</td>
            <td>170.00</td>
            <td>1</td>
        </tr>
    </tbody>
</table>

<h2>Reviews</h2>
<table>
    <caption>Reviews Table</caption>
    <thead>
        <tr>
            <th>review_id</th>
            <th>listing_id</th>
            <th>review_date</th>
            <th>rating</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>1</td>
            <td>2023-01-05</td>
            <td>4</td>
        </tr>
        <tr>
            <td>2</td>
            <td>1</td>
            <td>2023-01-10</td>
            <td>5</td>
        </tr>
        <tr>
            <td>3</td>
            <td>2</td>
            <td>2023-01-15</td>
            <td>4</td>
        </tr>
        <tr>
            <td>4</td>
            <td>3</td>
            <td>2023-01-20</td>
            <td>5</td>
        </tr>
        <tr>
            <td>5</td>
            <td>3</td>
            <td>2023-01-25</td>
            <td>3</td>
        </tr>
        <tr>
            <td>6</td>
            <td>3</td>
            <td>2023-01-30</td>
            <td>4</td>
        </tr>
        <tr>
            <td>7</td>
            <td>4</td>
            <td>2023-02-05</td>
            <td>5</td>
        </tr>
        <tr>
            <td>8</td>
            <td>5</td>
            <td>2023-02-10</td>
            <td>4</td>
        </tr>
        <tr>
            <td>9</td>
            <td>6</td>
            <td>2023-02-15</td>
            <td>5</td>
        </tr>
        <tr>
            <td>10</td>
            <td>6</td>
            <td>2023-02-20</td>
            <td>4</td>
        </tr>
        <tr>
            <td>11</td>
            <td>7</td>
            <td>2023-02-25</td>
            <td>5</td>
        </tr>
        <tr>
            <td>12</td>
            <td>8</td>
            <td>2023-03-05</td>
            <td>5</td>
        </tr>
        <tr>
            <td>13</td>
            <td>9</td>
            <td>2023-03-05</td>
            <td>5</td>
        </tr>
    </tbody>
</table>

</body>
</html>

```sql
with cte as (
select host_id,listing_id
, count(*) over(partition by host_id) as cnt_listings
 from listings
)
select cte.host_id,cte.cnt_listings as no_of_listings,round(avg(r.rating),2) as avg_rating
from cte
inner join reviews r on cte.listing_id=r.listing_id
where cte.cnt_listings >= 2
group by cte.host_id,cte.cnt_listings
order by avg_rating desc
limit 2;
```

output

<table>
<thead>
<tr>
<th>host_id </th> 
<th>no_of_listings </th> 
<th>avg_rating </th> 
</tr>
</thead>
<tbody> 
<tr> 
<td>103</td>
<td>2</td>
<td>5.00</td>
</tr>
<tr> 
<td>102</td>
<td>3</td>
<td>4.50</td>
</tr>
</tbody>
</table>

<a href="#top">Back to top</a>
