# SQL
## Programstruktur
### Enkelt program
```
SELECT
  <parameter>
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
  <parameter>
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
  <parameter>
FROM
  <tabell>
  INNER JOIN <tabell2> ON <villkor>
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
WHERE AppointmentDateTime >= '20210101' AND (AppointmentStatus = 'Completed' OR AppointmentStatus = 'Manually Completed')
```
**Exempel 2**
```
SELECT 
  dat.AppointmentDateTime,
  da.ActivityCategoryENU 
FROM 
  variandw.DWH.DimActivityTransaction dat
  INNER JOIN variandw.DWH.DimActivity da ON dat.DimActivityID = da.DimActivityID 
WHERE AppointmentDateTime >= '20210101' AND **AppointmentStatus LIKE '%Completed'**
```
