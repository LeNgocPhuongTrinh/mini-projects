# OEE MANUFACTURING

<img src="https://media.licdn.com/dms/image/C4E12AQGyiQQHiiIaAw/article-cover_image-shrink_600_2000/0/1635916361437?e=2147483647&v=beta&t=GT5MWo0wrjSNf_UG55Dp9f1nq2tqNRc2O4eO3W7GBoE"/>

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
- <a href="https://github.com/LeNgocPhuongTrinh/mini-projects/tree/946248a1f1cede0ca95941b74f13852df956c8c0/OEE%20Manufacturing">Data Processing</a> <br>
- <a href="https://www.novypro.com/project/oee-manufacturing-power-bi">Dashboard</a>

## Summary

### - Objective
Dig into the raw data, make sense of it and visualize to track OEE across the machines. So the key focus is machine.

### - Potential Analysis Aspects
  + OEE KPI and its relevant parameters (Availability, Performance, Quality). KPI Target is based on World-class OEE.
  + TEEP
  + Summarize machine performance

### - Data Exploration 
Some abnormal things in raw data are listed as below
  + 50% data has Total Units Produced lower than Good Units Produced
  + Errors in the sensors or IoT Devices reset the counter to 0, therefore the accumulated biscuits in raw data are incorrect. The accumulated biscuits can be set to 0 or lower than the previous count.
  + Timing is continuous while this data aims to capture machine stops. It seems odd that the number of biscuits keeps increase even after continuous stoppages.
  + Some stoppages can last up to 12 hours or even a day. 
  + Some machines have a small amount of biscuits compared with its Design Speed, something can be wrong in machine counting unit.

### - Assumption
  + Total < Good then Total is set to be equal to Good count.
  + There are 10 machines and each of them is used for all products, implying that no multiple lines of the same machine type are running simultaneously.

### - Data Cleansing
  + <b>Total < Good:</b>
    If Total < Good then Total Count is set to be equal to Good Count.
  + <b>Accumulated Biscuits:</b>
    Calculate the difference in Total Units Produced and Good Units Produced between consecutive rows by grouped Machine|Product. <br>
    The peculiarity is that Row N+1 has fewer Accumulated Biscuits than Row N, as indicated by the <b>Negative Difference</b>. The counter was reset to zero as a result of sensor problems. <br>
    Assume that if next value is lower than previous value, it is retained to add to the prior value. <br>
    However, nearly 90% data in case "Negative Difference" reveal that Row N+1 has value less than 10% value of Row N, showing that it is a minor difference that usually appear in Biscuits Filling Machine. The action on this 90% is set the "difference" to 0. <br>
    The consecutive difference is cleaned, recalculate the Accumulated Biscuits.
  + <b>Start/End Stoppage Timing - Timing Continuous:</b>
    Problem is that Stoppage Timing is continuous, therefore producing extra biscuits during this time is unreasonable.
    Using Extra Biscuits as mentioned above, and using Design Speed to calculate the Run Time to produce these biscuits
    The difference between that time and original Duration is the Run Time. This new Duration is used to determine the new Stoppage End Time.
  + <b>Start/End Stoppage Timing - Timing Across the Day:</b>
    Split line across the day to ensure each row has start time and end time on the same day
    Some data lines depict the machine's stop duration over a two-day period, implying a planned shutdown.
  + <b>OEE Category - [NO ORDER, 0]:</b>
    If Duration >= 720 (12 hours), it is Schedule Loss. (Assume that if machine breaks down, it should be fixed within 12 hours)
    If Duration < 720 (12 hours), it is Availability Loss
  + <b>Counter Unit for each Machine</b>:
    If Machine = Boxing or Packaging Heat, assume Counter Unit is Case, then number of biscuits = Current Count * Product Spec.
 
 ### Output:
 - OEE is very low due to the low performance rate. 9/10 machines have Performance rate of less than 20%, 8 have rate under 10% and 6 have rate under 1%.
 - Quality rate seems to be good but it is because we had an assumption to clean the Total Units Produced in raw data.
 - The filling machine is the one that is operational the most of the time, with the highest performance rate and the most realistic quality rate.
 - While the counter sensor devices are being repaired, we can focus on Filling Machine to understand its root-cause of poor OEE.

--------------------------------------------------------------------------------
 ## Contact Information
 For more information, reach me at:
  [![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/kayleetrinh99/) 
  [![Gmail Badge](https://img.shields.io/badge/-GMail-red?style=flat&logo=Gmail&logoColor=white)](mailto:lengocphuongtrinh.ftu2@gmail.com)
 
 Visit my blog website [![Blog Badge](https://img.shields.io/badge/-Blog-blue?style=flat&logo=Twitter&logoColor=white)](https://lnptchinchin.wixsite.com/chinchin)  

##### Back to my Github main view 
<a href="https://github.com/LeNgocPhuongTrinh">
  <img src="https://github.com/devicons/devicon/blob/master/icons/github/github-original.svg" width="20" height="20"> 
</a>
