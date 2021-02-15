![Satelite](/images/satelite.jpg)

# Forecasting Customer Retention Using Classification Modeling Techniques

**Author**: [Matthew Lipman](mailto:matthewrlipman@gmail.com)

## Overview

###### "Do what you do so well that they want to see it again and bring their friends." -Walt Disney

Customer retention is a mainstay for profitability and success of businesses. With the telecommunications industry's ever-changing technologies and rapidly increasing user base, Internet and phone providers need to continually advance their products and services to meet their customers' growing expectations and needs. Using data provided by IBM Watson Analytics about Telco, a telecommunications company, I have analyzed key features driving a customer from leaving the service. With over seven thousand customers and over twenty different features and attributes provided about each customer, this dataset provides a strong basis to classify how and why a customer churns out of the service. By understanding, analyzing, and modeling the data, I am able to correctly classify 86.8% of customers who churned out and left the service based upon how the customers interact with specific features and parameters.

![Tenure](/images/tenurevschurn.png)


## Business Problem

Customer retention is key to driving a company's profitability. Customer retention allows for companies to reduce time and costs spent by the Sales department driving new business, and helps businesses maintain a stable, reliable flow of income. In addition, customers who are happy with their service and perceive that they are getting a strong value for their product, are less likely to leave the service, and more likely to recommend the products and services they are receiveing to their colleagues, family, and friends. As Tamulienea and Gabryteb have pointed out in a case study of Lithuanian mobile operators, customers who are satisfied end up being growth opportunities for future revenue of the business by a process called "relationship marketing." Thus, focusing on retention reduces loss of revenue and inadvertently cultivates future sales.

![Churn](/images/totalrevenue.png)

Currently, 36.2% of customers churned out of the business. Additionally, the base of customers who do not churn generate almost 13.2 million dollars while customers who have churned generated just under 2.9 million dollars in total revenue. If the 36.2% of customers who had churned had not churned--based upon the current average lifetime revenue generated per customers--Telco could have received an additional 1.9 million dollars in revenue, not including the additional customers and revenue that could have been achieved through relationship marketing. As a whole, maintaining a strong client base by retaining customers is a key component to the vitality of your business. Through this research and development, I will be answering/addressing the following questions:
<ol>
  <li> Can churn be explained and understood through a classification model?
  <li> If so, which features are associated with churn?
  <li> How can Telco reduce churn and other businesses learn how to reduce customer churn?
</ol>

The model I created aims to be able to classify whether or not a customer successfully churns.

(Citation: 19th International Scientific Conference; Economics and Management 2014, ICEM 2014, 23-25 April 2014, Riga, Latvia. Factors influencing customer retention: case study of Lithuanian mobile operators Vilma Tamulienea, Ingrida Gabryteb.)


## Data

The dataset used for this project can be found at https://www.kaggle.com/blastchar/telco-customer-churn. It contains 7,043 rows of 21 features representing 7,043 different individuals who were all Telco customers. The features describe some qualitative features about the customer, the quality and quantity of services used by the customer, and metrics involving how much money was spent by the customer and the length of time the customer remained using the service. The target feature--or feature we are trying to get a deeper understanding of as it relates to customer retention--is "churn." Churn is defined as whether or not the customer churned out of the service and left. This variable is categorical and binary (Yes/No). "Yes" represents that the customer has churned and thus left the service. "No" represents that the customer remained utilizing and paying for the service provided. A comprehensive exploratory data analysis was conducted and is available for viewing in the Jupyter Notebook, "EDA, Preprocessing, and Visualizing Relationships."


## Methods

This classification modeling project is in accordance with the CRISP-DM method. I began my work by importing, preprocessing, cleaning, and visualizing the relationships between the features and the target feature, "churn." First I used a relatively minimally pre-processed dataset to create a baseline model. Each subsequential model had an iterative approach using a number of techniques such as Synthetic Minority Oversampling Technique (SMOTE), feature engineering, attempting different classification modeling techniques, and grid searches to address a variety of modeling obstacles such as class imbalances, model complexity reduction, and overfitting. To streamline the modeling process, I created a number of pipelines to assess and compare the various models' metric performances. I identified the metric to best analyze my model, recall, because I was interested in reducing the number of times the model predicted that someone would not churn, but did in fact churn. By reducing the number of these instances, this model is able to minimize costly situations where we did not identify a potential churner and is able to notify the Sales team which products to try to sell to the existing customer. 


## Results

![Models](/images/modelcomparisons.png)

After conducting eight iterations of the baseline model, I was able to acheive a model recall of 86.8%, meaning 86.8% of customers who churned were correctly classified by the model.

![Matrix](/images/confusionmatrix.png)

The most effective model that classified churn with 86.8% recall used the following attributes:
<ol>
  <li> SMOTE to address class imbalance
  <li> Feature Engineering to reduce model complexity
  <li> A Decision Tree Classifier
  <li> Hyperparameter tuning to optimize the model's recall and reduce model overfitting
</ol>

This Decision Tree Classifier indicates that 86.8% of customers churning are able to be successfully predicted by the model.

![Tree](/images/decisiontree.png)

In addition, this Decision Tree illustrates:
<ol>
  <li> The contract type is very important to customer retention. Specifically, customers who are on a longer-term contract are strongly associated with not churning. Customers that are on atleast a 1-year contract are less likely to churn and customers that are on atleast a 2-year contract are much less likely to churn.
  <li> The amount of money spent by a customer for their services is a strong indicator of classifying whether or not they are going to churn. Customers that spend more than 59.65 dollars per month on their biill are likely to churn and customers that spend 89.85 dollars per month on their bill are highly likely to churn.
       
![AdvanceImage1](/images/monthlycharges_contract.png)
    
  <li> There is a conditionality to these two features. For example, those are are on an atleast 2-year contract and paying less than 59.65 dollars per month on their monthly rate are of the subgroup of individuals who are least likely to churn.
  
![AdvanceImage2](/images/monthlycharges_paymentmethod.png)
  
  <li> Customers who are on a month-to-month contract, pay more than $89.85 per month, are extremely likely to churn if they pay by automatic payments via a credit card.
</ol>

By honing in on recall, the model ensures that we capture all instances where a customer churns, which makes this the most important metric for the problem at hand because it is the instance where a customer leaves the service and the company loses the most revenue. By focusing on recall, this model avoids false negatives or Type II errors, where we do not predict and identify a customer who will churn.


## Conclusions

This analysis leads to three recommendations for reducing customer churn:

- **Get customers on long term contracts.** In order to reduce churn, I advise Telco to reach out to their population of customers that are on a month-to-month contract and attempt to convert them into a longer term contract. Currently 55.1 percent of customers are not on a long term contract. By increasing the number of customers on a minimum of a 1-year contract, the model forecasts that less customers will churn.
- **Reduce the monthly bills of customers who pay more than $59.65 per month.** By reaching out to customers who pay more than the threshold for what the model predicts are customers more likely to churn, Telco's retention team can try helping the customer save on their monthly bill. This will increase customer relations by building trust between the customer and service provider, further aiding in relationship marketing.
- **For customers on month-to-month contracts and pay more than 89.85 dollars per month, have the retention team reach out to the customer and change their payment method from automatic credit card.** If all three of these conditionals are satisfied, customers are extremely likely to churn. With that said, by changing their payment method they become substantially less likely to churn.

### Future Work

Further analyses could yield additional insights to substantiate behavior leading to customer retention.

- **Model Implementation:** Conduct a short term study on the financial effects of converting customers onto longer term contracts, reducing monthly payments, and changing payment methods.
- **Finer-tune understanding of the service add-ons:** To keep the complexity of the model more straightforward, this model has feature engineered the add-ons and treated them equally when classifying churn. With more time and understanding, it would benefit the company to see which specific add-ons affect the causality of churn.
- **Continue to improve model overfitting:** The training data has a higher recall percentage of 5.9 as compared to the testing data. With more time, I would increase the number of cross validations to conduct the hyperparameter tuning, with the hope of finding a better-tuned model and reduce overfitting.

## For More Information

See the full analysis in my <a href="https://github.com/mattielips/customer-retention-modeling/blob/main/Customer%20Retention%20Classification.ipynb>Jupyter Notebook</a> or review my <a href="https://github.com/mattielips/customer-retention-modeling/Presentation.pdf">Presentation</a>.

For additional info, contact me here: [ Matthew Lipman,](mailto:matthewrlipman@gmail.com)


## Repository Structure

```
├── Customer Retention Classification.ipynb
├── data
    ├── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── EDA, Preprocessing, Visualizing Relationships.ipynb
├── images
    ├── categoricalfeatures.png
    ├── confusionmatrices.png
    ├── confusionmatrix.png
    ├── decisiontree.png
    ├── modelcomparisons.png
    ├── monthlycharges_contract.png
    ├── monthlycharges_paymentmethod.png
    ├── satelite.jpg
    ├── tenurevschurn.png
    └── totalrevenue.png
├── Modeling.ipynb
├── Notebook_Playground.ipynb
├── Presentation.pdf
└── README.md
