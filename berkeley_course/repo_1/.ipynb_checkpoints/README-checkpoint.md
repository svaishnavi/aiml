# Assignment: Will the Customer Accept the Coupon?

Assignment notebook link: https://github.com/svaishnavi/aiml/blob/main/berkeley_course/repo_1/prompt.ipynb

## What is the problem?

The problem is to identify the factors influencing whether a driver accepts a coupon delivered to their phone while driving. The coupons vary by type (e.g., restaurant, bar, coffee house), and acceptance depends on multiple variables like the driver’s demographics, the presence of passengers, weather, time of day, and the destination. The challenge is to analyze these factors to predict or understand coupon acceptance behavior.

---

## What is the data?

- **Source:** UCI Machine Learning repository, survey data from Amazon Mechanical Turk.
- **Size:** 12,684 rows, 26 columns.
- **Data type:** Mostly categorical data covering user demographics (age, gender, marital status, education, income), behavior (frequency of visits to bars, coffee houses, restaurants), contextual attributes (driving destination, weather, temperature, passenger type), and coupon attributes (type of coupon, time before expiry).
- **Quality:** Mostly clean, but some columns have missing values (notably the car attribute, which is mostly missing), and some columns like age need data type conversion.
- **Outcome variable:** Coupon acceptance (Y=1 for accept immediately or later, Y=0 for decline).

---

## What are the findings?

@ Findings: The dataset contains 12,684 rows and 26 columns

@ Findings: The dataset contains 12,684 rows and 26 columns, with most columns fully populated. However, there are some columns with "object" as Dtype. These may need to be updated to int or string. For example, the age column is stored as an object type, likely due to inconsistent formatting, and should be converted to numeric or categorical. Overall, the dataset is mostly clean and well-structured, with only a few columns needing attention before analysis or modeling.

@ Findings: Rich in categorical data across demographics, behavior, and context. But missing values are mainly in car and some behavior columns (Bar, etc.).

@ Findings: The car column is almost entirely missing and may not be useful. The other food/venue-related columns (Bar, CoffeeHouse, etc.) have low to moderate missing values (1–2%), which can likely be handled with dropping the rows if needed. All other features are fully complete, providing a strong foundation for modeling or analysis. We need to clean the dataset especially the car column

@ Finding: Out of all the customers in the dataset, 56.9% accepted the coupon, indicating that more than half of the customers responded positively to the coupon offer.

@ Finding: The data suggests that casual and convenient dining options (e.g., coffee and takeout) are promoted more heavily or are more frequently accepted than higher-cost or social venue coupons like those for bars.

@ Finding: The histogram shows a trimodal distribution of temperature data with three distinct peaks around 30°F, 57°F, and 78°F. The highest frequency is at 78°F, suggesting warmer temperatures are most common.

@ Finding: The analysis shows that 788 bar coupons were accepted, which represents 41.2% of all bar coupon offers in the dataset. This indicates that less than half of the bar coupons were accepted by users.

@ Finding: The analysis shows that frequent bar visitors accepted 76.17% of the bar coupons offered to them. This indicates a high acceptance rate among those who go to bars more often

@ Finding: The analysis shows that less frequent bar visitors (those who go 3 or fewer times a month) accepted 37.27% of the bar coupons offered to them. This is significantly lower than the acceptance rate of frequent visitors, indicating that bar coupon effectiveness is much higher among frequent visitors.

@ Finding: The acceptance rate for bar coupons among frequent bar visitors over the age of 25 is 68.98%, while for less frequent visitors under 25, it's significantly lower at 33.77%. This suggests that age and visit frequency both influence coupon acceptance, with older, more frequent visitors being much more likely to redeem.

@ Finding: Among individuals who go to bars more than once a month, do not have kids as passengers, and are not in farming, fishing, or forestry occupations, the bar coupon acceptance rate is 70.94%, while the non-acceptance rate is 29.06%. This suggests a strong likelihood of coupon acceptance within this group.

@ Finding: Bar-goers without kids as passengers: Among people who go to bars more than once a month and do not have kids as passengers, the coupon acceptance rate is high at 70.94%. This suggests a strong interest in bar coupons among socially active individuals without child-related responsibilities.

@ Finding: Bar-goers under age 30: For individuals under 30 years old who go to bars frequently, the acceptance rate is slightly higher at 71.95%. Young adults appear particularly receptive to bar-related promotions.

@ Finding: Frequent cheap restaurant diners with income less than 50K: Among those who eat at cheap restaurants more than 4 times a month and have incomes below $50,000, the acceptance rate drops to 45.65%. Despite their frequent dining, this group is less responsive to coupons, possibly due to price sensitivity or lack of perceived value.

@ Finding: Based on the observations, I’d hypothesize that drivers who accepted the bar coupons tend to be: More socially active, frequently visiting bars (more than once a month). Younger (under 30 years old), likely more open to trying promotions and social outings. Less likely to have kids as passengers, suggesting fewer family responsibilities that might limit nightlife activities. Possibly not widowed, since the data filtered out widowed individuals who typically go less often.

In essence, these drivers are probably younger, socially engaged individuals who enjoy nightlife and are responsive to promotions related to bar visits. This demographic seems more receptive to coupons tied to social activities compared to others, like lower-income frequent cheap restaurant diners.

Finally independent investigation:

@ Finding: Drivers who frequently visit inexpensive or expensive restaurants show similarly high acceptance rates for carry out coupons regardless of the restaurant cost.
  
---

## What are some future recommendations?

1. **Feature engineering:** Create features combining demographics and behavior (e.g., social activity score), and contextual features like time of day, weather severity, and passenger type to improve prediction.
2. **Segmentation and targeting:**
   - Target coupons for bars mainly at younger, socially active, child-free individuals.
   - Customize offers for different income and dining habits, e.g., focus less on cheap restaurant coupons for low-income frequent diners.
3. **Modeling:** Build classification models using these features to predict coupon acceptance, employing techniques to handle categorical data and missingness.
4. **Expand data collection:** Incorporate real driving data (e.g., GPS movement patterns) and contextual info like traffic or real-time weather.
5. **User feedback:** Gather qualitative insights on why coupons are rejected to complement quantitative analysis.


