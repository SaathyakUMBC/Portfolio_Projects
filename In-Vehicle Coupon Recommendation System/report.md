## 1. Title and Author

**Project Title:** In-Vehicle Coupon Recommendation System Using Machine Learning

Prepared for UMBC Data Science Master Degree Capstone by Dr Chaojie (Jay) Wang

**Author Name:** Saathyak Rao Kasuganti

**GitHub:** https://github.com/SaathyakUMBC/Portfolio_Projects

**LinkedIn:** https://www.linkedin.com/in/saathyak-rao-kasuganti-241440190/

**PowerPoint presentation file:** https://github.com/DATA-606-2023-FALL-MONDAY/Kasuganti_Saathyak/blob/main/docs/Project_power_point.pptx

**Link to your YouTube video:** https://youtu.be/LTwmpIrmWYU
    
## 2. Background

**What is the Project about?**

- With the rise of digitization in our era, most businesses heavily rely on personalized marketing strategies, including coupons and discounts, to attract and retain customers.  

- However, the effectiveness of coupon recommendations can vary significantly depending on the context.  

- This project aims to predict whether individuals will accept coupons in different driving scenarios.  

- By using machine learning techniques on UC Irvine in-vehicle coupon recommendation dataset, this project aims to aid businesses optimize their coupon marketing strategies for better customer engagement and successful conversion.  



**What are your research questions?**


Some of the critical research questions that the project seeks to answer are:

  - What are the major factors that influence an individual's decision to accept or reject a coupon in various driving scenarios?  

  
  -	How does general demographic criteria such as gender, age, marital status, presence of children, education, occupation, and income influence and relate to coupon acceptance in different driving scenarios?  
  
  -	What types of coupons (e.g., restaurant, coffee, carry-out, bar) are most likely to be accepted based on different driving scenarios?  


  -	How can businesses/ entrepreneurs customize their marketing strategies based on the identified factors influencing coupon acceptance?  
  

  The answers to these questions can inform marketing strategies, enhance customer engagement, and improve the effectiveness of successful coupon promotions.


## 3. **Where is the data sourced from? Description about the quality of data, credibility and attributes.**  

**Data sources:** - https://archive.ics.uci.edu/dataset/603/in+vehicle+coupon+recommendation

**Data size:** - 2213 Kb

**Data shape (# of rows and # columns) :** - (12684, 24) i.e. 12684 rows and 24 columns

**Credibility of Source:** The UCI Machine Learning Repository has a longstanding reputation for providing high-quality datasets, making it a credible source for our research. The repository is maintained by the University of California, Irvine, anddata quality standards.

**Size of Data:** The dataset offers a substantial number of instances, totalling 12,684 records. This size provides sufficient data to conduct statistically meaningful analyses and train predictive models effectively.

**Attributes of Data:** The dataset has 23 distinct features. These attributes depict a wide range of information, including demographic details, driving scenario specifics, coupon-related variables, and behavioural characteristics, contributing to a comprehensive analysis.


**Feature Dictionary**

| Feature                  | Data Type     | Description                                         | Possible Data Entries                               |
|--------------------------|---------------|-----------------------------------------------------|------------------------------------------------------|
| destination              | Categorical   | The intended destination of the driver.            | "No Urgent Place", "Home", "Work"                   |
| passenger                | Categorical   | The type of passengers present in the car.         | "Alone", "Friend(s)", "Kid(s)", "Partner"          |
| weather                  | Categorical   | The weather conditions at the time of driving.     | "Sunny", "Rainy", "Snowy"                           |
| temperature              | Continuous    | The temperature in degrees Fahrenheit.             | 55, 80, 30 (numerical values)                       |
| time                     | Categorical   | The time of day when the driving scenario takes place. | "2PM", "10AM", "6PM", "7AM", "10PM"            |
| coupon                   | Categorical   | The type of coupon offered.                        | "Restaurant(<$20)", "Coffee House", "Carry out & Take away", "Bar", "Restaurant($20-$50)" |
| expiration               | Categorical   | The expiration period of the coupon.               | "1d" (1 day), "2h" (2 hours)                       |
| gender                   | Categorical   | Gender of the driver.                              | "Female", "Male"                                   |
| age                      | Categorical   | Age group of the driver.                           | "21", "46", "26", "31", "41", "50plus", "36", "below21" |
| maritalStatus            | Categorical   | Marital status of the driver.                      | "Unmarried partner", "Single", "Married partner", "Divorced", "Widowed" |
| has_Children             | Categorical   | Whether the driver has children (binary).          | 1 (Yes), 0 (No)                                    |
| education                | Categorical   | Educational level of the driver.                   | "Some college - no degree", "Bachelors degree", "Associates degree", "High School Graduate", "Graduate degree (Masters or Doctorate)", "Some High School" |
| occupation               | Categorical   | Occupation of the driver.                          | [List of various occupation types]                 |
| income                   | Categorical   | Annual income range of the driver.                 | ["$37500 - $49999", "$62500 - $74999", "$12500 - $24999", "$75000 - $87499", "$50000 - $62499", "$25000 - $37499", "$100000 or More", "$87500 - $99999", "Less than $12500"] |
| Bar                      | Categorical   | Frequency of visiting bars every month.            | "never", "less1", "13", "gt8", "nan48"             |
| CoffeeHouse              | Categorical   | Frequency of visiting coffee houses every month.   | "never", "less1", "48", "13", "gt8", "nan"         |
| CarryAway                | Categorical   | Frequency of getting take-away food every month.   | "n48", "13", "gt8", "less1", "never"               |
| RestaurantLessThan20     | Categorical   | Frequency of going to restaurants with an average expense per person of less than $20 every month. | "48", "13", "less1", "gt8", "never" |
| Restaurant20To50         | Categorical   | Frequency of going to restaurants with an average expense per person of $20 - $50 every month. | "13", "less1", "never", "gt8", "48", "nan" |
| toCoupon_GEQ15min        | Categorical   | Whether the driving distance to the restaurant/bar for using the coupon is greater than 15 minutes (binary). | 0 (No), 1 (Yes) |
| toCoupon_GEQ25min        | Categorical   | Whether the driving distance to the restaurant/bar for using the coupon is greater than 25 minutes (binary). | 0 (No), 1 (Yes) |
| direction_same           | Categorical   | Whether the restaurant/bar is in the same direction as the current destination (binary). | 0 (No), 1 (Yes) |
| direction_opp            | Categorical   | Whether the restaurant/bar is in the opposite direction of the current destination (binary). | 1 (Yes), 0 (No) |
| Y                        | Categorical   | Whether the coupon is accepted (binary).           | 1 (Yes), 0 (No)                                    |


## 4. Exploratory Data Analysis - A pointwise summary:

1. Out of the 24 columns of the dataset, 6 of them have missing values.

2. The columns with missing values, 'CoffeeHouse', 'CarryAway', 'RestaurantLessThan20', and 'Restaurant20To50' seem to be important features that improve the performance of the Machine learning model. We can consider deleting the rows with missing values as the number of missing values ranges between 107 and 217 only.

3. The column 'car' has missing values for most entries; therefore, it is best to drop the column to end up with cleaner data.

4. Next, we check the Data-types of the columns and the number of Non-Null Values:
   - About half of the columns have an object datatype, while the remaining are integers. Most columns have no null values.
   - As most of the numerical columns are essentially categorical values, there is not much insight to gain from the statistical summary generated above.
   - Occupation column has the highest possibilities of values with 25 types of entries, followed by income classified into 9 different classes.

5. All of the features (including temperature) are essentially categorical in nature; a correlation matrix would not be of any benefit. Therefore, to understand the distribution of various features into categories, I have used the ProfileReport class from the pandas_profiling module.
   - There are 74 duplicated rows, which is 0.6% of total rows and needs to be dropped to achieve clean data.
   - 'toCoupon_GEQ5min' neither has duplicates nor missing values, but it has only the value '1' for all rows; therefore, it can be dropped.
   - Occupation has a very high number of distinct entries, which greatly increases the dimensionality of the data when using techniques like one-hot-encoding.
   - Therefore, as we are using one-hot encoding that converts the existing categorical features to binary features, we can consider dropping the column 'occupation'.

6. Drop any last remaining rows with NaN values, and cross-check for missing values to verify. Now we end up with a data frame that still has 12k+ rows and no null values.

7. Finally, before starting the pre-processing for the ML models, we use OneHotEncoder for converting the categorical data to be able to use for various machine learning models.

## 5. Feature Engineering: Encoding features and feature selection:
### Categorical Data Encoding and Feature Selection Analysis

- **Encoding Categorical Data:**
  - Utilized OneHotEncoder to transform categorical data, resulting in 80 individual features instead of the original 25 columns.

- **Feature Selection Techniques:**
  - To select relevant features for categorical data, considered techniques such as Chi2 or Recursive Feature Elimination (RFE).

- **RFE Technique Application:**
  - Applied RFE to choose the 20 most important features for the analysis.

- **Effect on Random Forests Accuracy:**
  - Despite selecting the top 20 features using RFE, the accuracy of the Random Forests algorithm decreased compared to using all 80 encoded features.

- **Accuracy Variation with Feature Count:**
  - Experimented with different feature counts (5, 10, 20, 25, 40, 50, 65), but the accuracy only approached the original accuracy of 74% and did not surpass it.

- **Limited Performance Improvement:**
  - Concluded that feature selection did not significantly enhance performance, particularly in the context of a dataset composed entirely of categorical variables.

- **Model Complexity and Performance:**
  - Observed a direct proportional relationship between the complexity of the models and their performance. Reducing the number of features may result in a loss of crucial information for the Random Forests algorithm, affecting predictive accuracy.


## 6.  Machine Learning Models Performance Evaluation:

- **Primary Metric for Comparison of Model Performance:** F1 Scores of Individual Binary Classes.
- **Secondary Metric for Comparison of Model Performance:** Overall Model Accuracy.

### Model Performance Summary

| Model                   | F1 Score (Class 0) | F1 Score (Class 1) | Accuracy |
|-------------------------|---------------------|---------------------|----------|
| Gradient Boosting Model | 0.71                | 0.79                | 0.757    |
| SVM Model (Poly Kernel)  | 0.70                | 0.79                | 0.750    |
| Random Forests          | 0.68                | 0.78                | 0.743    |
| SVM Model (RBF Kernel)   | 0.68                | 0.78                | 0.735    |
| Decision Tree Model     | 0.64                | 0.74                | 0.700    |
| Ada Boost               | 0.62                | 0.74                | 0.690    |

### Why Gradient Boosting Model is Chosen:

1. **High Accuracy:**
   - The Gradient Boosting Model demonstrated the highest accuracy of 75.7% among all models tested, making it the most reliable choice for making coupon recommendations.

2. **Balanced F1 Scores:**
   - With competitive F1 scores for both Class 0 and Class 1 (0.71 and 0.79, respectively), the model shows an ability to effectively identify both successful and unsuccessful recommendations.

3. **Interpretability:**
   - The model is relatively interpretable, allowing you to understand how it makes predictions. This transparency is essential for trust and compliance in recommendation systems.

4. **Ensemble Learning:**
   - By combining the strength of multiple weak learners through boosting, the model reduces overfitting, effectively captures complex patterns in the data, and enhances prediction performance.

### How Gradient Boosting Model Outperforms Others:

1. **Ensemble Learning:**
   - The ensemble nature of the Gradient Boosting Model allows it to harness the collective wisdom of many weaker models, reducing variance and improving model performance.

2. **Reduced Overfitting:**
   - Gradient Boosting's ability to handle overfitting effectively results in a more reliable model when compared to other models that might suffer from high variance.

3. **Generalization Capability:**
   - The model demonstrates excellent generalization, indicating that it's better at making accurate recommendations on unseen data or new users.


## 7. Project Findings and Conclusion

1. **Feature Significance**
   - Connecting with research question 1, it is observed that all features play a crucial role in coupon acceptance. Feature selection experiments, including iterations with varying feature counts, showed that excluding features decreased model performance.

2. **Weather Influence on Coupon Acceptance**
   - Connecting with research question 1, weather conditions significantly impact coupon acceptance. Coupons have a higher chance of acceptance during sunny weather, with a slightly higher chance of rejection during snowy or rainy weather.

3. **Gender and Coupon Acceptance**
   - Addressing research question 2, both men and women generally have a higher chance of accepting coupons. However, a deeper analysis reveals that, when comparing acceptance and rejection cases (y=1 and y=0), men tend to accept slightly more often than women.

4. **Age and Coupon Acceptance**
   - Addressing research question 2, age plays a crucial role in coupon acceptance. Customers aged 21-31 show a very high chance of acceptance, gradually fading as age approaches 50. Customers above 50 have an equal chance of accepting or rejecting coupons. This insight suggests that food coupons should primarily target customers in their 20s for higher success rates.

5. **Major take-aways:**
- These insights collectively aid in devising targeted marketing strategies, personalized campaigns, sales initiatives, and advertisements.
- The predictive model, with an accuracy of 75.7%, offers valuable real-time insights for business owners. 
- It serves as a practical accuracy for marketing purposes, considering the inherent unpredictability associated with human decision-making.
- Acknowledging the limitations, such as the influence of human 'free will' and 'mental state,' this level of accuracy is deemed highly effective for a marketing-focused use-case.

## This level of accuracy is particularly significant in a marketing context, where precision in targeting specific demographics and scenarios is crucial for campaign success.


