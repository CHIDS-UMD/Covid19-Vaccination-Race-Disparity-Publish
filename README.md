# Socioeconomic Privilege and Political Ideology are Associated with Racial Disparity in COVID-19 Vaccination: Methods and Materials

This public repository contains the materials for reproducing the results described in Agarwal et al. (2021) _Socioeconomic Privilege and Political Ideology Are Associated with Racial Disparity in COVID-19 Vaccination_ and additional supplementary analyses. 


## Table of Contents

- [Content Description](#materials)

- [Main Regression](#main-reg)

 
- [Robustness Checks](#robustness-checks)

    * [Age Group Controls](#age-control)
    
    * [Different Disparity Operationalizations](#disparity-measure)
    
    * [Different Dates and Full Vaccination Rate](#date-ratetype)
    
    * [Residential Mobility](#exodus-test)
    
    * [Recent Positive Rate per COVID-19 Test](#positivity)
    
    * [Avoid Collinearity by Droping `Hesitancy` Variable](#drop-hesitancy)

    * [Subsample Analysis (6 States and 10 States)](#610states)
   
   * [Vaccination Rate on Whole White Population](#rate-on-white)

  

   


<a name="materials"/>

## Content Description
Materials for reproducibility include:

1. [COVID-19 vaccination rate data](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/tree/main/CountyVaccine) and Python code to reproduce the data collection, including:<br>

    a) The notebook [1.CountyVaccine_Automation](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/1.CountyVaccine_Automation.ipynb) includes the code to collect the county-level vaccination information by race from the States whose vaccination data is oragnized in a downlable table. In this notebook, the Python code can automatically scrape the data. The States include： Illinois, Texas, Pennsylvania, Indiana, and Virginia. <br>
    
    b) The notebook [1.CountyVaccine_Tableau](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/1.CountyVaccine_Tableau.ipynb) is designed to collect the county-level vaccination information by race from the States whose vaccination information is present in a Tableau Dashboard format. In this notebook, the Python code can also automatically scrape the data. The States include：New York, Wisconsin, Ohio, South Carolina, and Oregon.<br>
    
    c) The notebook [1.CountyVaccine_Manual](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/1.CountyVaccine_Manual.ipynb) is developed to collect the county-level racial vaccination information from the States whose vaccination information needs to be collected manually before running the code. These States include: California, Tennessee, North Carolina, West Virginia, Maine, and New Jersey. The instructions on manual collections are documented [here](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/tree/main/CountyVaccine/Documents/Part1).<br> 
    
2. [Data](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/tree/main/DataMerge) and [Python code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/2.DataMerge.ipynb) to merge information from the various sources cited in our Supplementary Information (SI) Appendix.

3. Python code for [cleaning the data](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/2.DataClean.ipynb). 

4. [Clean data](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/tree/main/StataReg) and [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity/blob/main/3.StataCode.ipynb) to reproduce our main regression analyses (reported in main text) and robustness checks (reported in SI Appendix) as well as  additional supplementary analyses reported here. 

Below, we also provide additional summary statistics, exploratory data analysis, and full results for the robustness checks described in the SI appendix. 



<a name="main-reg"/>

## Main Regression

Below, we provide the source code for regression table presented in Agarwal et al. (2021).
   
You can get the stata code to do this regression by:
   ```shell
   python statacode.py --task main_regression 
   python statacode.py --task main_regression_originalX
   ```
   or directly check the data and stata code in the folder `StataCode/main_regression` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/main_regression) and `StataCode/main_regression_originalX` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/main_regression_originalX).

  

<a name="robustness-checks"/>

## Detailed Regression Results and Robustness Checks

    
    
 
<a name="age-control"/>
    
 ### Different Age Group Controls
  
Below, we provide the source codes to produce regression tables by controlling for proportion of population above age 75 and disparities in the proportion of population above age 75 for the White and Black population. We add this variable as a control to account for the fact that older adults were prioritized early on in the vaccine rollout. In addition, we add additional control variables to account for the population that was eligible for the vaccines. Based on available demographic data, we approximate the vaccine eligible population by controlling for the proportion of population ages 15-74 in one set of analyses and the proportion of population ages 20-74 in a second set of analyses.
 
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task check_age_all 
   python statacode.py --task check_age_above15 
   python statacode.py --task check_age_above20 
   ```
   or directly check the data and stata code in the folder `StataCode/check_age_all` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/check_age_all), `StataCode/check_age_above15` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/check_age_above15), and `StataCode/check_age_above20` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/check_age_above20).

<a name="disparity-measure"/>
    
 ### Different Disparity Operationalizations
 
  As additional robustness checks, we also model alternative operationlizations of disparity. Specifically, we model a ratio-based definition (White Vaccination Rate/Black Vaccination Rate), the log of that ratio, and an outcome that scales the absolute disparity by the overall vaccination rate of the White and Black populations in a given county.
 
    
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task check_disparity_types 
   ```
   or directly check the data and stata code in the folder `StataCode/check_disparity_types` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/check_disparity_types).
   

<a name="date-ratetype"/>
    
### Different Dates and Full Vaccination Rate Types
   
    We compiled data from multiple time points (March 27, April 07, and May 20, 2021) to compare against our main findings based on data from April 19, 2021. In addition, we checked the same model using full vaccination data from May 20, 2021 to explore whether our pattern of findings still hold.

   
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task diff_dates 
   ```
   or directly check the data and stata code in the folder `StataCode/diff_dates` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/diff_dates).
   
   

<a name="exodus-test"/>

   
   
### Residential Mobility
Some regions saw large rates of residential mobility (people moving in or out) during the course of the pandemic. To account for this, we collected data on areas that saw the greatest movement during the pandemic based on data from 75,000 moves (HireAHelper Migration Report, 2021). The list includes 10 cities with the greatest net increase in movement and the 10 cities with the greatest net decrease in movement, some of which are not represented in the counties included in our analysis. We exclude the 12 relevant counties represented in our data。
   
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task residential_mobility 
   ```
   or directly check the data and stata code in the folder `StataCode/residential_mobility` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/residential_mobility).
   
  
 
<a name="positivity"/>
   
### Recent Positive Rate per COVID-19 Test
 We include a variable measuring recent positivity rate (April 12-April 19). 
   
   
   
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task recent_positive_rate 
   ```
   or directly check the data and stata code in the folder `StataCode/recent_positive_rate` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/recent_positive_rate).
   
   
   
   
   
<a name="drop-hesitancy"/>

### Avoid Collinearity by Droping `Hesitancy` Variable

   We reviewed the Variable Inflation Rate (VIF) for our main regression model, finding that vaccine hesitancy had a VIF that exceeds the suggested cut-off value of 10. To assess how much the multicollinearity may have an impact on our findings, we try models excluding vaccine hesitancy. 
   
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task avoid_collinearity 
   ```
   or directly check the data and stata code in the folder `StataCode/avoid_collinearity` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/avoid_collinearity).
   
   
   

<a name="610states"/>

### Subsample Analysis (6 States and 10 States)

   We split our sample into two subgroups, those that provide estimates for non-Hispanic White vaccination rates specifically (six states) and those that do not (ten states).
   
   
   You can get the stata code to do this regression by:
   ```shell
   python statacode.py --task subsample_analysis_6_and_10_states 
   ```
   or directly check the data and stata code in the folder `StataCode/subsample_analysis_6_and_10_states` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/subsample_analysis_6_and_10_states).
   

   
<a name="rate-on-white"/>
   
 ### Vaccination Rate on Whole White Population
  
 In this robustness check, we treat all the State in the same way in terms of calculate the COVID-19 White Vaccination Rate: Reported-CvdVax-White / Total-White-Population. Then we ran the models with different covariates. 
   
   You can get the stata code to do this robustness check by:
   ```shell
   python statacode.py --task vax_rate_on_all_white 
   ```
   or directly check the data and stata code in the folder `StataCode/vax_rate_on_all_white` [code](https://github.com/CHIDS-UMD/Covid19-Vaccination-Race-Disparity-Publish/blob/main/StataCode/vax_rate_on_all_white).
   
   
   