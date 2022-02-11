# Time-Series-Anomaly-Detection
Anomaly detection on office temperature: Numenta Anomaly Benchmark (NAB) data.
## 1.	Explore and Feature Engineering:
- The dataset contains two columns: timestamp and the temperature values. 
-	The timestamps are at an interval of an hour from the start date 2013-07-04 to 2014-05-28. 
-	There were no Null values in the dataset but few hours missing, so the hours were added into the dataset and empty values forward filled. (261 rows)   

    ![Missing Data](https://github.com/Anshumank399/Time-Series-Anomaly-Detection/blob/main/images/Missing%20Values.png)

- Understanding the distribution of the temperature values.

    ![Distribution](https://github.com/Anshumank399/Time-Series-Anomaly-Detection/blob/main/images/eda1.png)    ![Box Plot](https://github.com/Anshumank399/Time-Series-Anomaly-Detection/blob/main/images/eda2.png)

-   New features extracted from the datetime and temperature value column:  
    a. Hour, day, month, weekday, quarter.  
    b. Weekend column if the day of week is Sunday or Saturday.  
    c. Working Hours (assuming working hours from 8am to 8pm).   
    d. Temperature lag (24-hours lag variable).   
    e. Change in lag (difference between current and 24-hour lag temperature).  
    
-   Examining weekend temperature trends.   
    a.	On most weekends there is a continuous drop in temperature as shown in the graph below.  
    b.	Possible inference: the office is in a cold region where the temperature drops continuously if heating is not on.

    ![Weekend](https://github.com/Anshumank399/Time-Series-Anomaly-Detection/blob/main/images/weekend.png)
    
-   Examining working hours temperature trends.  
    a. On most working hours the temperature keeps on rising as shown in the graph below.     
    b. Possible inference: the office is in a cold region where the temperature is maintained by heating during working hours.   

    ![](https://github.com/Anshumank399/Time-Series-Anomaly-Detection/blob/main/images/working%20hours.png)

## 2.   Anomaly Detection using Statistical Method (z-score).   
