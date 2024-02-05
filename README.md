Q1 Find the distinct country ISO codes and their corresponding subcontinent ISO codes:
```sql
SELECT
  c.country_iso_3166_1,
  scm.subcontinent_iso_un_m49
FROM
  `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping` c
JOIN
  `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_subcontinent_mapping` scm
ON
  c.target_subcontinent = scm.target_subcontinent;
```
![image](https://github.com/M2337036/M2337036/assets/154054595/b24488b8-ae54-48de-8d87-389298cae1e7)

 Q2. Which continent is having highest number of countries
 SELECT target_continent, count(country_iso_3166_1) as country_count 
FROM `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping`
group by target_continent order by country_count DESC LIMIT 
![image](https://github.com/M2337036/M2337036/assets/154054595/21af6879-7302-49e7-acfe-4a942938432f)
Q3. To find average number of entries per sub-continent.
SELECT  
    target_subcontinent,
    COUNT(*) AS total_entries,
    AVG(COUNT(*)) OVER () AS avg_entries_per_subcontinent
    FROM `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_subcontinent_mapping` 
    group by target_subcontinent
    ![image](https://github.com/M2337036/M2337036/assets/154054595/2bc8a5be-d949-425b-a193-8fbf56d3c4f6)
   
    Q4 To find maximum and minimum number of entries per Sub-continent
    
SELECT  
target_subcontinent,
    MAX(region_iso_3166_2) AS max_entries,
    MIN(region_iso_3166_2) AS min_entries
FROM `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_region_mapping` 
group by target_subcontinent
![image](https://github.com/M2337036/M2337036/assets/154054595/5993660f-f143-41b5-92a7-6fe0c9278b96)

Q5 To find the countiries involved in geotargeted advertizing in Central Asia
SELECT 
country_iso_3166_1,
    target_country_region
FROM  `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping` 
    
WHERE
    target_subcontinent = 'Central Asia';
    ![image](https://github.com/M2337036/M2337036/assets/154054595/34111d8b-c01b-4f9c-8b09-ceadfdfc6d11)
    Q6. To find number of geotargeted advertizing regions in China
    
    SELECT 
    COUNT(DISTINCT target_region) AS num_target_regions
FROM  `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_region_mapping` 
    
WHERE
    target_country_region = 'China';
    
![image](https://github.com/M2337036/M2337036/assets/154054595/1a40a990-d843-4046-9ad4-e3330cf5fc6e)

Q7 To find top five target country region for geotargeted advertizing in various continents which also mentions sub-contienient.
SELECT target_continent,target_country_region,target_subcontinent
FROM `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping` 
order by target_country_region
DESC LIMIT 5
![image](https://github.com/M2337036/M2337036/assets/154054595/21d83145-d707-475b-b81b-17ced8f1586b)
Q8. To find target country regions for geotargeted google advertizing in Asia
SELECT 
  target_country_region, target_continent 
  
FROM `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping` 
WHERE target_continent = 'Asia'
![image](https://github.com/M2337036/M2337036/assets/154054595/1b7e413a-47fa-4113-87c3-ae992222b58b)
Q9 To find the target Country region and corresponding target city.
Select 
* from `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping`  ACM 
left join `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_criteria_mapping`  ACR on 
ACM.target_country_region = ACR.target_city   
  ![image](https://github.com/M2337036/M2337036/assets/154054595/718cd5e6-02ad-49c8-bd6b-4349309f505f)
  Q10. What are the cities along with their country information
  SELECT
    agcm.target_city,
    agcm.target_country_region,
    agcm.target_subcontinent,
    agcm.target_continent,
    agccm.country_iso_3166_1
FROM
    `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_criteria_mapping` AS agcm
INNER JOIN
    `bigquery-public-data.google_ads_geo_mapping_me_west1.ads_geo_country_mapping` 
     AS agccm ON agcm.target_country_region = at_country_region;gccm.target
  

     ![image](https://github.com/M2337036/M2337036/assets/154054595/bd26fdd3-f6f6-4d9e-b650-5f8d4cb7f777)




    


