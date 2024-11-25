# **Predicting Used Car Prices in Saudi Arabia**

-----
# 1. Project Overview

## 1.1 Company Overview: Syarah.com

**Syarah.com** is one of Saudi Arabia's leading online platforms for buying and selling cars. Launched in 2015, it connects customers to both new and used car dealerships across the Kingdom. What sets Syarah apart is its focus on offering a smooth and reliable car-buying experience, including detailed listings of cars with specifications, prices, and dealership contact information.

Syarah also offers more than just a marketplace—its services extend to financing, home delivery, and insurance, all designed to make the buying process as easy as possible. One of its key selling points for used cars is the assurance of quality, as all vehicles undergo thorough inspections before being listed. Additionally, Syarah provides a 10-day test drive and a one-year warranty, which adds to the peace of mind for customers.

The platform’s accessibility through both web and mobile apps makes it easy for buyers to browse cars at their convenience. Whether you’re a first-time buyer or looking for a specific model, Syarah.com aims to offer a trustworthy and user-friendly service for car enthusiasts across Saudi Arabia.

Source: [syarah.com](https://syarah.com/en/about-us)

### 1.2 Problem Statement

As a **Data Scientist** at **Syarah.com**, I aim to develop a **machine learning model** that assists the **Operational Division**, particularly the **Car Assessment & Negotiation Team**. The goal is to provide **data-driven price suggestions** prior to finalizing the price with sellers. By leveraging historical data and car features (such as **make**, **model**, **engine size**, **year**, **condition**, etc.), the model will predict the **ideal price range** for a used car based on its attributes.

This tool will help make the **pricing process** more **consistent**, **transparent**, and **accurate**. It will also empower the operational teams to make informed decisions during inspections and negotiations, reducing **human biases** and enhancing efficiency. The main challenge is developing a **robust**, **scalable model** that can accommodate the **diversity of cars** listed on the platform, while providing recommendations that align with **real-time market conditions**.

### 1.3 Goals

The main goals of this project are:

1. **Develop a Predictive Model**: Build a **machine learning model** capable of predicting an **ideal price range** for a used car based on its features, such as **make**, **model**, **engine size**, **year**, **condition**, etc.

2. **Assist Pricing and Negotiation**: Create a tool that assists the **Car Assessment & Negotiation Team** by providing **data-driven price suggestions** to help finalize prices with sellers, improving the decision-making process.

3. **Enhance Operational Efficiency**: Optimize the pricing workflow by automating and streamlining the **inspection** and **price negotiation** processes, reducing human biases, and enhancing the accuracy of decisions.

4. **Improve Consistency and Transparency**: Make the pricing process more **consistent**, **transparent**, and **fair**.

### 1.4 Dataset Description

This dataset contains a list of used cars for sale in Saudi Arabia through the Syarah.com application or website.

| **Column**       | **Description**                                                   |
|------------------|-------------------------------------------------------------------|
| **Type**         | Type of used car.                                                |
| **Region**       | The region where the used car is being offered for sale.         |
| **Make**         | The brand name of the car.                                        |
| **Gear_Type**    | The gear type of the used car.                                    |
| **Origin**       | The origin of the used car.                                       |
| **Options**      | Options available in the used car.                                |
| **Year**         | Manufacturing year of the car.                                    |
| **Engine_Size**  | The engine size of the used car.                                  |
| **Mileage**      | The mileage of the used car.                                      |
| **Negotiable**   | Indicates whether the price is negotiable (True if the price is 0, meaning negotiable). |
| **Price**        | The price of the used car.                                        |

### 1.5 Assumptions and Limitations

#### Assumptions:
- The analysis is based on data from **2023**.
- The data used is the most recent, obtained as of **December 20, 2022**.
- The reference data for market prices and trends comes from three leading used car sale platforms in Saudi Arabia: **Syarah**, **CarSemsar**, and **Hatla2ee**.

#### Limitations:
- The model is based solely on the available data and may not capture **future market changes**.
- The dataset may not cover all **car features** or accurately represent all **regions in Saudi Arabia**.
- Some features, such as **car condition** and **negotiation details**, might be **subjective** and harder to quantify.
- The dataset only contains information up to the **car make, type and engine size** and does not provide deeper insights such as the car' s**car condition**, **color**, **other specific features** and  **listing dates** on **Syarah.com**.
- **Randomstate** is determine by 1001 for all process

### 1.6 Analytical Approach

The objective of this analysis is to develop a **machine learning model** to predict the **price** of used cars listed on **Syarah.com**, based on various features such as **year**, **engine size**, **mileage**, and other relevant attributes. This approach can be broken down into the following key stages:

1. **Data Understanding**:
   - The first step is to get a comprehensive understanding of the dataset. This includes analyzing the structure, identifying the features available, and understanding their potential influence on the **target variable** (car price). Also look for potential **missing values** or **outliers** that might affect model performance.

2. **Data Exploration**:
   - Perform exploratory data analysis (EDA) to examine the dataset's **structure**, focusing on the **uniqueness** and **distribution** of each feature.
   - Identify and explore **missing values**, **duplicate entries**, and **outliers**.
   - Investigate the distribution of key features and the relationships with the **target variable** (price).
   - Understand the variety of values within each feature and examine if any **features** have a limited number of unique values or are highly skd.

3. **Data Cleaning**:
   - In this stage, handle data issues such as:
     - **Duplicate values**: Identifying and removing any duplicated rows.
     - **Missing values**: Using techniques such as **imputation** or removing rows/columns with insufficient data.
     - **Outliers**: Analyzing extreme values and deciding whether to keep or remove them.
     - **Encoding**: Applying **one-hot encoding** or **binary encoding** for categorical features.
     - **Feature selection**: Selecting the most relevant features for the model to improve predictive performance.

4. **Modeling**:
   - Once the data is prepared, apply different **machine learning algorithms** to predict the **price**. The algorithms include **XGBoost**, **Random Forest**, **Linear Regression**, **K-Nearest Neighbors (KNN)** etc.
   - Will optimize the models using techniques like **cross-validation** and **hyperparameter tuning** (via **RandomizedSearchCV**) to improve performance.

5. **Model Performance Evaluation**:
   - Will perform **residual analysis** to detect any patterns that the model might not be capturing.

6. **Interpretability & Insights**:
   - To interpret the model's predictions, we will use **SHAP (SHapley Additive exPlanations)** to explain which features are driving the predicted prices.

7. **Conclusion & Recommendations**:
   - It will summarize the **strengths** and **limitations** of the model, including any **challenges identified during the analysis**, such as **data quality issues**, **skewed distributions**, or the model's **ability to generalize to unseen data**.
   - The conclusions will aim to **contextualize the results** within the dataset's **limitations**, providing **insights into the relationships** between **car attributes** and their **prices**, while outlining **areas for further exploration**.
   - Based on the findings, **actionable recommendations** will be presented to improve future analyses, including potential **data enhancements**, **advanced feature engineering**, and **alternative modeling approaches**.

-----
# **Overall Model Review**

**Data Details:**
- The **cleaned data** used for modeling contains **2,613 rows** and **9 columns**.
- The **training data** consists of **2,090 rows** and **7 columns**.
- The **test data** contains **523 rows**.

**Model Reability:**
Based on the analysis of 100 predictions, the model shows mixed results:

- **8 predictions** are **significantly off**, indicating **major errors**.
- **42 predictions** are **outside the expected range**, but not extreme, showing difficulty with boundary cases.
- **50 predictions** are within the **acceptable range**, indicating moderate success.

# **Conclusion**

The machine learning model developed to predict used car prices on **Syarah.com** has shown some promising results but also highlights areas for improvement. 

**Key Insights:**
- **Accuracy**: The model's predictions are generally **within an acceptable range**, with **50% of predictions** being accurate. However, there are **8% predictions** that are **significantly off**, and **42% predictions** fall **outside the expected range**.
- **Feature Impact**: The model is strongly influenced by **engine size** and **year**, which have a **positive correlation** with car prices. This makes sense as larger engines and newer vehicles tend to be priced higher.
- **Training Data**: The small dataset of **2,090 training rows** limits the model’s ability to generalize well across the full range of potential car listings. The **data imbalance** and absence of detailed information (such as car condition and color) also affect the model's reliability.
- **Challenges**: The model struggles to handle **extreme values** and **edge cases**, likely due to a lack of sufficient data to cover all possible variations in car listings.

**Key Attention Points**: Engine Size Inconsistencies
- **Engine Size Below 2000cc**: Premium brands like **BMW**, **Mercedes**, and **Lexus** rarely have models with engine sizes below **2000cc**.
- **Engine Size Above 7000cc**: Engine sizes above **7000cc** are typically found in **supercars**, not regular luxury vehicles from these brands.
- **Impact on Price Predictions**: These inconsistencies can lead to unrealistic price estimates—either inflated for large engines or underestimated for smaller ones.
- **Possible Data Errors**: There may be issues such as data entry mistakes or modifications/variants not properly recorded.

- # **Recommendations**

To further improve the model, consider the following suggestions:

- **Increase the Training Dataset**: Expand the dataset to include a broader range of car attributes, especially **different conditions** and **price ranges**, to improve the model's ability to generalize better and handle outliers and edge cases.

- **Improve Feature Engineering**: Enhance the model by adding more relevant features such as **car condition**, **modifications**, or even **vehicle history** to better capture the relationships between features and target variable, while ensuring consistency in engine size data.

- **Address Engine Size Inconsistencies**: Focus on cleaning and validating the **engine size** data, especially for premium brands like **BMW**, **Mercedes**, and **Lexus**. Ensure that extreme values (both below 2000cc and above 7000cc) are handled correctly to avoid unrealistic predictions.

- **Monitor Model Performance**: Continuously evaluate the model's performance, especially in predicting edge cases or extreme values, to ensure that the model can adapt to any inconsistencies or errors in the data.
