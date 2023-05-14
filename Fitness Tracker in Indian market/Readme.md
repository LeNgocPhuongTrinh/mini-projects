# FITNESS TRACKER IN INDIAN MARKET

<img src="https://www.polar.com/en/img/cms/538586fede80a63faa57726b2ba8c1127a559c64-3480x1130-2560.webp"/>

## Author
Le Ngoc Phuong Trinh

### About this challenge
- #DataDNA dataset challenge
- Owned by: Pomerol
- Dataset source: https://www.kaggle.com/datasets/arnabchaki/fitness-trackers-products-ecommerce
- Dataset: Fitness Tracker 
- About dataset background: This is a fitness tracker product dataset consisting of different products from various brands with their specifications, 
ratings and reviews for the Indian market. The data has been collected from e-commerce websites namely Flipkart and Amazon using web scraping technique.

## Key output

- User preferences:
  + Most of fitness trackers in Indian market are equipped with Touchscreen and Bluetooth
  + Preferred product features: 22-day battery life, Rectangle dial shape, 1.7-inch display size, Silicon Black strap, medium weight (35-50g)
- Price Segmentation and Brand
  + <b>Apple</b> focuses on premium-quality product segment with the highest rating and value contribution <i>despite low consumption</i>.
  + <b>Noise</b> is mostly preferred in the Indian market due to its <i>inexpensive price (under 18,000)</i>.
- Factor Correlations:
  + In terms of price difference, some features are found to be more important than others. The impact is more obvious if we examine price variation by each product features BY BRAND.
  + The drawback is that, data is not fulfilled with Product feature and Price. Only 31% data is valid to analyze the correlation.

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
