
**1.Which team scored the most points when playing at home? (ANS:Real Madrid)**


```
   sql_query='''SELECT Team.team_api_id,Team_long_name,SUM(Match.home_team_goal) AS total_goals
                FROM Team
                JOIN Match ON Team.team_api_id=Match.home_team_api_id
                GROUP BY Team.team_api_id,Team.team_long_name
                ORDER BY total_goals DESC;'''
                
    pd.read_sql_query(sql_query,conn)
 ```
            
            
**2.Did this team also score the most points when playing away?( ANS:No,Kilmarnock scored the highest goals)**

```
   sql_query= '''SELECT Team.team_api_id,Team_long_name,SUM(Match.away_team_goal) AS total_goals
                 FROM Team
                 JOIN Match ON Team.team_api_id=Match.home_team_api_id
                 GROUP BY Team.team_api_id,Team.team_long_name
                 ORDER BY total_goals DESC;'''
                 
    pd.read_sql_query(sql_query1,conn)
 ```
    
   
   
**3.How many matches resulted in a tie? (ANS:6596)**

```
    sql_query= '''SELECT COUNT (match_api_id) AS number_of_ties
                   FROM Match
                   WHERE Match.home_team_goal=Match.away_team_goal;'''
   pd.read_sql_query(sql_query1,conn)
 ```
   
**4.a)How many players have Smith for their last name?(ANS:15)**

```
    sql_query='''SELECT COUNT(player_name)
                 FROM Player
                 WHERE player_name LIKE '% smith'
                 LIMIT 10;'''
 ```


**b) How many have 'smith' anywhere in their name? (ANS:18)**
 
 
 ``` 
      sql_query='''SELECT COUNT(player_name)
                   FROM Player
                   WHERE player_name LIKE '%smith%'
                    LIMIT 10;'''
       pd.read_sql_query(sql_query1,conn)
  ```
                
    
    
**6.What percentage of players prefer their left or right foot? (ANS:75 %)**
 
 ```sql_query1= '''SELECT COUNT (id)
                FROM Player_Attributes;'''
             
 
 sql_query2=SELECT COUNT (preferred_foot)
            FROM Player_Attributes
            WHERE preferred_foot='right';
              
              
 %=sql_query2/sql_query1
 ```
