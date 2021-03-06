# SQL
## Programstruktur
### Enkelt program
```
SELECT
  <parameter1, parameter2, ...>
FROM
  <tabell>
```
**Exempel**
```
SELECT
  AppointmentDateTime
FROM
  variandw.DWH.DimActivityTransaction
```
### Lägg till villkor
```
SELECT
  <parameter1, parameter2, ...>
FROM
  <tabell>
WHERE <villkor>
```
**Exempel**
```
SELECT
  AppointmentDateTime
FROM
  variandw.DWH.DimActivityTransaction
WHERE AppointmentDateTime >= '20210101'
```
### Koppla ihop tabeller
```
SELECT
  <tab1.parameter1, tab1.parameter2, tab2.parameter1, ...>
FROM
  <tabell tab1>
  INNER JOIN <tabell2 tab2> ON <sammankopplingsvillkor>
WHERE <villkor>
```
**Exempel 1 (obs parenteser)**
```
SELECT 
  dat.AppointmentDateTime,
  da.ActivityCategoryENU 
FROM 
  variandw.DWH.DimActivityTransaction dat
  INNER JOIN variandw.DWH.DimActivity da ON dat.DimActivityID = da.DimActivityID 
WHERE dat.AppointmentDateTime >= '20210101' 
AND (da.AppointmentStatus = 'Completed' OR da.AppointmentStatus = 'Manually Completed')
```
**Exempel 2**
```
SELECT 
  dat.AppointmentDateTime,
  da.ActivityCategoryENU 
FROM 
  variandw.DWH.DimActivityTransaction dat
  INNER JOIN variandw.DWH.DimActivity da ON dat.DimActivityID = da.DimActivityID 
WHERE dat.AppointmentDateTime >= '20210101' AND da.AppointmentStatus LIKE '%Completed'
```
### Sortera på parameter
```
ORDER BY <parameter>
```
**Exempel**
```
SELECT
  dat.AppointmentDateTime
FROM
  variandw.DWH.DimActivityTransaction dat
ORDER BY dat.AppointmentDateTime
```
### Välj max N värden
```
SELECT TOP N
```
**Exempel**
```
SELECT TOP 5
  dat.AppointmentDateTime
FROM
  variandw.DWH.DimActivityTransaction dat
```
### Välj bara unika värden
```
SELECT DISTINCT
```
**Exempel**
```
SELECT DISTINCT
  dat.AppointmentDateTime,
  dat.ActivityCategoryENU
FROM
  variandw.DWH.DimActivityTransaction dat
```
## Jämförelse
|Symbol|Betyder|Exempel|Exempel2||
|-|-|-|-|-|
|=|Lika med|AppointmentStatus = 'Completed'|Age = 37||
|<>|Inte lika med|AppointmentStatus <> 'Deleted'|Age <> 37||
|>|Större än||Age > 37||
|>=|Större än eller lika med||Age >= 37||
|<|Mindre än||Age < 37||
|<=|Mindre än eller lika med||Age <= 37||
|LIKE|Jämförelse för text|ActivityCategory LIKE '%Completed'||& fungerar som wildcard|
## Mer tricks
### Byt namn på variabler
```
<parameter> [nytt_parameter_namn]
```
**Exempel**
```
SELECT DISTINCT
  dat.AppointmentDateTime [StartTime],
  dat.ActivityCategoryENU [Activity]
FROM
  variandw.DWH.DimActivityTransaction dat
```
### Nesting
**Exempel**
```
```
### Cross apply
**Exempel**
```
```

