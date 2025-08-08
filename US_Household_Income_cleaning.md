```sql


# US Household Income Data Cleaning

SELECT * 
FROM us_project.us_household_income;

-- The query returns a column with a corrupted name, which needs to be fixed
SELECT * 
FROM us_project.us_household_income_statistics;

-- Updated the column alias
ALTER TABLE us_project.us_household_income_statistics RENAME column `锘縤d` TO `id`;

SELECT COUNT(id)
FROM us_project.us_household_income;

SELECT COUNT(id)
FROM us_project.us_household_income_statistics;


-- Identify duplicate records based on the 'id' column
SELECT id, count(id)
FROM us_project.us_household_income
GROUP BY id
HAVING COUNT(id) > 1;


-- Identify duplicate records based on the 'id' column
SELECT id, count(id)
FROM us_project.us_household_income_statistics
GROUP BY id
HAVING COUNT(id) > 1;

-- Check for any unusual or duplicate values in the 'State_Name' column
-- Ordered alphabetically for easier inspection
SELECT DISTINCT State_Name
FROM us_project.us_household_income
ORDER BY 1;

UPDATE us_project.us_household_income
SET State_Name = 'Georgia'
WHERE State_Name = 'georia';

UPDATE us_project.us_household_income
SET State_Name = 'Alabama'
WHERE State_Name = 'alabama';

-- Check for any unusual or duplicate values in the 'State_ab' column
-- Ordered alphabetically for easier inspection
SELECT DISTINCT State_ab
FROM us_project.us_household_income
ORDER BY 1;

-- Check for any unusual or duplicate values in the 'Place' column
-- Ordered alphabetically for easier inspection
SELECT DISTINCT Place
FROM us_project.us_household_income
ORDER BY 1;

SELECT *
FROM us_project.us_household_income
WHERE County = 'Autauga County'
ORDER BY 1;

UPDATE us_project.us_household_income
SET Place = 'Autaugaville'
WHERE Place = '';

-- Count the number of occurrences for each distinct value in the 'Type' column
-- Helps to understand the distribution and identify any anomalies or unexpected values
SELECT Type, COUNT(Type)
FROM us_project.us_household_income
GROUP BY Type;

UPDATE us_project.us_household_income
SET Type = 'Borough'
WHERE Type = 'Boroughs';

-- Check distinct values in the 'AWater' column where the value is 0, empty string, or NULL
-- This helps identify any missing or potentially problematic entries in the 'AWater' field
SELECT DISTINCT(AWater)
FROM us_project.us_household_income
WHERE AWater = 0 OR Awater = '' OR AWater IS NULL;

```