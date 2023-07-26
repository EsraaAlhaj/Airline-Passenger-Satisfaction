# Airline-Passenger-Satisfaction
I conducted an analysis on Airlines Passenger Satsifaction using SQL

dataset : https://drive.google.com/file/d/1aPodQ_BUDRaKEX9qnSRozacfTy8M-T70/view 

Objectives :

1. Which percentage of airline passengers are satisfied? 

/*Count how many 'Satisfied' and 'Neutral or Dissatisfied' */
SELECT Satisfaction, COUNT(*) AS Count
FROM [Maven_Airplane].[dbo].[airline]
WHERE Satisfaction IN ('Satisfied', 'Neutral or Dissatisfied')
GROUP BY Satisfaction;

/*Use Case when */
SELECT *,
CASE
	WHEN Age > 40 THEN 'Old'
	WHEN Age BETWEEN 11 AND 39 THEN 'Young'
	ELSE 'Baby'
END
FROM [Maven_Airplane].[dbo].[airline]
ORDER BY Age;

/*Average Age */
SELECT AVG(Age) AS AvgAge
FROM [Maven_Airplane].[dbo].[airline];

/*Partition */
SELECT [ID], [Age], [Gender], [Customer Type], [Type of Travel], Satisfaction,
COUNT(Gender) OVER (PARTITION BY Gender) as Total_Gender
FROM [SQL_Airplane].[dbo].[airline]
ORDER BY [Age] DESC;


/*Create TABLE AS Satisfied*/
IF OBJECT_ID('Satisfied') IS NOT NULL
    DROP TABLE Satisfied;
GO
SELECT *
INTO Satisfied
FROM [SQL_Airplane].[dbo].[airline]
WHERE Satisfaction = 'Satisfied';

SELECT *
FROM Satisfied;

SELECT COUNT(*)
FROM Satisfied;






