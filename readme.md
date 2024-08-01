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
  <a href="#memo-license">License</a> &#xa0; | &#xa0;
  <a href="https://github.com/{{YOUR_GITHUB_USERNAME}}" target="_blank">Author</a>
</p>

<br>

## :dart: About ##

Heare all video solutions avaiable for sql interviews

## :rocket: Technologies ##

The following tools were used in this project:

- [SQL](https://www.microsoft.com/en-gb/sql-server/sql-server-2022)

## :white_check_mark: Requirements ##

Before starting :checkered_flag:, you need to have [mssql](https://www.microsoft.com/en-gb/sql-server/sql-server-2022) installed.

## :checkered_flag: Starting ##

```bash
# Clone this project
$ git clone https://github.com/{{YOUR_GITHUB_USERNAME}}/namaste_sql

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

## :memo: License ##

This project is under license from MIT. For more details, see the [LICENSE](LICENSE.md) file.


Made with :heart: by <a href="https://github.com/{{YOUR_GITHUB_USERNAME}}" target="_blank">{{YOUR_NAME}}</a>

&#xa0;

<a href="#top">Back to top</a>
