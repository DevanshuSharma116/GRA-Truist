# GRA-Truist


#FINDING BLOCKS WITH THEIR RELATIONSHIPS WHERE THE MEDIAN HOUSING AGE IS MORE THAN 10, THE MEDIAN HOUSING VALUE RANGE IS IN THE RANGE OF 14999-119400

MATCH (n:BlockID)-[r:AGE]->(m:HOUSING_AGE_RANGE),
(n)-[c:LOCATION]->(p:CITY),
(n)-[d:EARNS] -> (q:INCOME_RANGE),
(n)-[e:VALUE] -> (s:HOUSEVALUE_RANGE)
WHERE r.Age < 10 and s.Housevalue_Range='14999.0 < House_Value <= 119400.0 '
RETURN n, r,c, d,e,m,q,s,p;


#FINDING BLOCKS WITH THEIR RELATIONSHIPS WHERE THE MEDIAN HOUSING AGE IS MORE THAN 10, THE MEDIAN HOUSING VALUE RANGE IS IN THE RANGE OF 14999-119400, AND 
BELONGING TO THE CITY OF GROVER BEACH 

MATCH (n:BlockID)-[r:AGE]->(m:HOUSING_AGE_RANGE),
(n)-[c:LOCATION]->(p:CITY),
(n)-[d:EARNS] -> (q:INCOME_RANGE),
(n)-[e:VALUE] -> (s:HOUSEVALUE_RANGE)
WHERE r.Age < 10 and s.Housevalue_Range='14999.0 < House_Value <= 119400.0 ' and p.City="Grover Beach"
RETURN n, r,c, d,e,m,q,s,p;

#FINDING THE CITIES WITH THE LOWEST MEDIAN HOUSING VALUE 

MATCH (n:BlockID)-[e:VALUE]->(s:HOUSEVALUE_RANGE),(n)-[c:LOCATION]->(p:CITY) RETURN p,
ROUND(AVG(e.Value)) as medianAverageValue ORDER BY medianAverageValue ASC LIMIT 100


#FINDING THE CITIES WITH THE HIGHEST MEDIAN HOUSING VALUE 

MATCH (n:BlockID)-[e:VALUE]->(s:HOUSEVALUE_RANGE),(n)-[c:LOCATION]->(p:CITY) RETURN p,
ROUND(AVG(e.Value)) as medianAverageValue ORDER BY medianAverageValue DESC LIMIT 100