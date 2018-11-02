**For Challenge 4, after following the directions in the challenge 4 quention,I created new tables using the following lines of code;**

```
sql_query = '''CREATE TABLE test1 AS
                SELECT  player1 AS name,
      'M' AS gender,
      'US' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    us_men_2013

UNION ALL

SELECT  player2 AS name,
      'M' AS gender,
      'US' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    us_men_2013

UNION ALL

SELECT  player1 AS name,
      'M' AS gender,
      'AUS' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    aus_men_2013

UNION ALL

SELECT  player2 AS name,
      'M' AS gender,
      'AUS' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    aus_men_2013

UNION ALL

SELECT  player1 AS name,
      'M' AS gender,
      'French' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    french_men_2013

UNION ALL

SELECT  player2 AS name,
      'M' AS gender,
      'French' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    french_men_2013

UNION ALL

SELECT  player1 AS name,
      'M' AS gender,
      'wimbledon' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    wimbledon_men_2013

UNION ALL

SELECT  player2 AS name,
      'M' AS gender,
      'wimbledon' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    wimbledon_men_2013

UNION ALL

SELECT  player1 AS name,
      'F' AS gender,
      'wimbledon' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    wimbledon_women_2013

UNION ALL

SELECT  player2 AS name,
      'F' AS gender,
      'wimbledon' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    wimbledon_women_2013

UNION ALL

SELECT  player1 AS name,
      'F' AS gender,
      'French' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    french_women_2013

UNION ALL

SELECT  player2 AS name,
      'F' AS gender,
      'French' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    french_women_2013

UNION ALL

SELECT  player1 AS name,
      'F' AS gender,
      'AUS' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    aus_ladies_2013

UNION ALL

SELECT  player2 AS name,
      'F' AS gender,
      'AUS' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    aus_ladies_2013

UNION ALL

SELECT  player1 AS name,
      'F' AS gender,
      'US' AS tournament,
      result AS win,
      FSP_1 AS fsp,
      DBF_1 AS dbf,
      UFE_1 AS ufe
FROM    us_women_2013

UNION ALL

SELECT  player2 AS name,
      'F' AS gender,
      'US' AS tournament,
      1-result AS win,
      FSP_2 AS fsp,
      DBF_2 AS dbf,
      UFE_2 AS ufe
FROM    us_women_2013;'''

```
          
          
**q1.Find the number of matches played by each player in each tournament. (Remember that a player can be present as both player1 or player2).**

```
 sql_query='''SELECT COUNT(name) AS count_matches, name,tournament
              FROM test1
              GROUP BY  name,tournament
              ORDER BY name
              LIMIT 15;'''
              
 pd.read_sql_query(sql_query, cnx)           
 ```
      
q2.Who has played the most matches total in all of US Open, AUST Open, French Open? Answer this both for men and women.

```
sql_query='''SELECT COUNT(name) AS count_matches, name ,gender
             FROM test1
             GROUP BY  name,gender
             ORDER BY count_matches DESC
             LIMIT 15;'''  
             
 pd.read_sql_query(sql_query, cnx)
 ```
     
**q3.Who has the highest first serve percentage? (Just the maximum value in a single match.)**

```
sql_query='''SELECT MAX(fsp) AS max_fsp, name
             FROM test1
             GROUP BY name
             ORDER BY max_fsp DESC
             LIMIT 10;'''
  pd.read_sql_query(sql_query, cnx)
  
  ```
 
