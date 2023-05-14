# OEE MANUFACTURING

<img src="https://altizon.com/wp-content/uploads/2018/01/how-real-time-accurate-calculation-of-oee-can-increase-your-factorys-throughput-by-at-least-20.jpg"/>

## Author
Le Ngoc Phuong Trinh

### About this challenge
- Enterprise DNA Data Challenge
- Owned by: Enterprise DNA
- More information about challenge: https://forum.enterprisedna.co/t/power-bi-builds-18-oee-manufacturing-report/22389
- Dataset: OEE Manufacturing
- About dataset background: ‘Grandma EDNA’s Biscuits’ is one of the biggest manufacturers of biscuits in New Zealand. The corporation has made significant investments in the machines and has installed a variety of sensors and smart IoT devices to measure and understand their operational effectiveness.
IT has now extracted and consolidated the data.
Factory management has charged "participants" with assisting them in comprehending the facts.

## View my result at:
<a href="xx">Data Processing</a>
<a href="https://www.novypro.com/project/oee-manufacturing-power-bi">Dashboard</a>

## Summary

### - <b>Objective</b>: Dig into the raw data, make sense of it and visualize to track OEE across the machines. So the key focus is machine.
- <b>Potential Analysis Aspects</b>:
  + OEE KPI and its relevant parameters (Availability, Performance, Quality). KPI Target is based on World-class OEE.
  + TEEP
  + Summarize machine performance
- <b>Data Exploration:</b> Some abnormal things in raw data are listed as below
  + Timing is continuous while this data aims to capture machine stops. It seems odd that the number of biscuits keeps increase even after continuous stoppages.
  + 50% data has Total Units Produced lower than Good Units Produced
  + Errors in the sensors or IoT Devices reset the counter to 0, therefore the accumulated biscuits in raw data are incorrect. The accumulated biscuits can be set to 0 or lower than the previous count.
  + Some stoppages can last up to 12 hours or even a day. 
  + Some machines have a small amount of biscuits compared with its Design Speed, something can be wrong in machine counting unit.
- <b>Assumption</b>
  + Total < Good then Total is set to be equal to Good count.
  + There are 10 machines and each of them is used for all products, implying that no multiple lines of the same machine type are running simultaneously.
- <b>Data Cleansing</b>
  + Accumulated Biscuits: Calculate the difference in Total Units Produced and Good Units Produced between consecutive rows by grouped Machine|Product. The peculiarity is that Row N+1 has fewer Accumulated Biscuits than Row N, as indicated by the <b>Negative Difference</b>. It is the result of errors in sensors which made the counter set to Zero. Assuming that if next value is lower than previous value, it is kept to add into the previous value. However, nearly 90% data in the "Negative Difference" case shown that Row N+1 has value less than 10% value of Row N, implying that it is a minor difference, and it appears mostly in Biscuits Filling Machine. Action on this 90% is set difference to 0. The consecutive difference is cleaned, recalculate the Accumulated Biscuits.
  + 

## Data Cleansing

- Detect Price Outliers: Z-Score method
- Define Price Bins: Jenks Natural Breaks
- Feature Engineering (encode Categorical Variables): LeaveOneOut
- Feature Selection: RobustScaler, RandomForest, XGB

Some data is missing. To examine the price variation by product features, it is required to have non-missing data but only 31% data is valid to proceed.


 ### Contact Information
 For more information, reach me at:
  [![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/kayleetrinh99/) 
  [![Gmail Badge](https://img.shields.io/badge/-GMail-red?style=flat&logo=Gmail&logoColor=white)](mailto:lengocphuongtrinh.ftu2@gmail.com)
 
 Visit my blog website [![Blog Badge](https://img.shields.io/badge/-Blog-blue?style=flat&logo=Twitter&logoColor=white)](https://lnptchinchin.wixsite.com/chinchin)  

##### Back to my Github main view 
<a href="https://github.com/LeNgocPhuongTrinh">
  <img src="https://github.com/devicons/devicon/blob/master/icons/github/github-original.svg" width="20" height="20"> 
</a>
