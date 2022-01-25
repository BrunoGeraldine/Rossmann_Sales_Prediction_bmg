
<p align="center">
  <img width="1000" height="200" src="https://user-images.githubusercontent.com/87772120/141830775-ca0b346c-9936-4e12-bcde-7032c9be1616.png"
</p> 


**Warning:**This is an unrealistic project, the business problem, the context, the CEO's questions don't exist in real life. Just to study and carry out this experience project.

Rossmann is one of the largest drugstore chains in Europe, operating in more than 3000 units in 7 European countries. With the success of its brand, Rossmann plans a general renovation in all its stores, but currently the sales forecast is made through an excel spreadsheet considering the average sales, finding this methodology to be faulty and old, the company's management seeks new solutions.

A meeting was held with Rossmann's managers, directors and CEO to plan the renovations at the Rossmann stores in order to renew the aesthetics and standardize the stores. For this renovation to be possible, the Rossmann business team would need to have sales forecasts from all stores for the next 6 weeks, however, as currently sales forecasts were only made by means of an average spreadsheet, it is impossible to have a notion of the magnitude of individual sales and sales fluctuations between each store. Therefore, the company decided to hire a data scientist, to be aware of the best solution to the problem.

During the meeting the data scientist explained the details of a sales forecast as well as the methods that could be used. At the end of the meeting, the data scientist was responsible for creating a sales forecast model based on machine learning to answer the company's business question.
  
  
The main problem of this project is to answer: **"How much will each store sell in the next six weeks?"**


     
<p align="left">
	<img width="90" height="30" src="https://user-images.githubusercontent.com/87772120/141834545-f9186e6f-b2e6-4cd8-ae45-60df39a57d8e.png"
</p>  
     
<p align="left">
<img width="90" height="30" src="https://user-images.githubusercontent.com/87772120/148815386-40bfef66-6fda-44f5-99fb-2c3675176acf.png"
</p>

<p align="left">
<img width="90" height="30" src="https://user-images.githubusercontent.com/87772120/148815830-d8ed34a3-0272-4d1f-b4dc-6eb11848deaf.png"
</p>


# Business Assumptions
The following assumptions were made about the business problem:
- As it was assumed that there is a competitor even if very far away, if there is no date the competitor opened or data regarding promotional periods, work with the store date considering the premise that some time-derived variables are extremely important to represent a behavior.
- Customers' data being difficult to predict was discarded and could be scoped for another project to complement this one.
- The days when the stores were closed were discarded.
- Only entries in which the **Sales** values were greater than 0 were considered.

## **Attribute List:**

| Attributes                       | Explanation                                                    |
| -------------------------------- | ------------------------------------------------------------ |
| Id                               | An Id that represents a pair (Store, Date) within the test suite |
| Store                            | A unique id for each store                                   |
| Sales                            | The sales volume for any day                       |
| Customers                        | The number of customers on a given day                     |
| Open                             | An indicator to know if the store was open: 0 = closed, 1 = open |
| StateHoliday                     | Indicates a state holiday. Typically all stores, with few exceptions, close on state holidays. Please note that all schools are closed on holidays and weekends. a = holidays, b = Easter holiday, c = Christmas, 0 = None |
| SchoolHoliday                    | Indicates if (Store, Date) was affected by the closing of public schools |
| StoreType                        | Difference between 4 different store models: a, b, c, d  |
| Assortment                       | Describes an inventory level: a = basic, b = extra, c = extended |
| CompetitionDistance              | Distance in meters from the closest competitor          |
| CompetitionOpenSince[Month/Year] | Gives the approximate year and month in which the closest competitor was opened |
| Promo                            | Indicates if a store is running a promotion that day        |
| Promo2                           | Promo2 is a continuous and consecutive promotion for some stores: 0 = the store is not participating, 1 = the store is participating |
| Promo2Since[Year/Week]           | Describes the year and week the store started participating in Promo2 |
| PromoInterval                    | Describes the consecutive start intervals for promotion 2, naming the months when the promotion starts again. For example. "Feb, May, August, November" means each round starts in February, May, August, November of any year for that store |

# Solution Strategy:

Solution planning:

**Step 01. Data description:** My goal is to use statistical metrics to identify data outside the scope of the business.

**Step 02. Feature Engineering:** Derive new attributes based on the original variables to better describe the phenomenon to be modeled.

**Step 03. Data Filtering:** Filter rows and select columns that do not contain information for modeling or that do not correspond to the business scope.

**Step 04. Exploratory Data Analysis:** Explore the data to find insights and better understand the impact of variables on model learning.

**Step 05. Data Preparation:** Prepare the data so that machine learning models can learn specific behavior.

**Step 06. Selection of resources:** Selection of the most significant attributes to train the model.

**Step 07. Machine Learning Modeling:** machine learning model training

**Step 08. Hyperparameter Fine Tunning:** Choose the best values ​​for each of the parameters of the model selected in the previous step.

**Step 09. Convert model performance to business values:** Convert model performance to a business result.

**Step 10. Deploy Model to Production:** Publish the model to a cloud environment so that other people or services can use the results to improve the business decision.

  
  
# Top 5 Data Insights

**Hypothesis 1** - Stores with larger assortments should sell more.
**FALSE**: Stores with a larger assortment sell less.
	
<p align="left">
  <img width="1000" height="400" src="https://user-images.githubusercontent.com/87772120/148779512-f3bfdfd9-b82d-49b7-ad80-177ec7a8a821.png"
</p>
	 
**Hypothesis 2**. Stores with closer competitors should sell less.
**FALSE**: stores with closest competitors sell more!
<p align="left">
  <img width="1000" height="400" src="https://user-images.githubusercontent.com/87772120/148780086-b0a56917-efec-4ff8-a994-d4db7e883613.png"
</p>
	
**Hypothesis 3**. Stores with longer-term competitors should sell more.
**FALSE**: stores with competitors open longer, sell less!

<p align="left">
  <img width="1000" height="400" src="https://user-images.githubusercontent.com/87772120/148773814-70b3a362-3b5a-47fe-9b68-3fb2ed5e5112.png"
</p>
  
**Hypothesis 6**. Stores with more consecutive promotions should sell more.
**FALSE**: Stores with more consecutive promotions sell less.
	
<p align="left">
  <img width="1000" height="400" src="https://user-images.githubusercontent.com/87772120/148778946-22395915-d45b-4bbb-a771-53f2d7dab072.png"
</p>
  
**Hypothesis 10.** - Stores should sell more after the 10th of each month.
**TRUE**: Stores sell more after the 10th of each month.
	
<p align="left">
  <img width="1000" height="400" src="https://user-images.githubusercontent.com/87772120/148776316-9dce4761-bca6-4632-92e6-2548a2de6b7f.png"
</p>

  
# Machine Learning Models Applied
Testing were performed using the following algorithms:

**Average Model**

**Linear Regression Model**

**Linear Regression Regularized Model - Lasso**

**Random Forest Regressor**

**XGBoost Regressor**

# 6. Machine Learning Model Performance

**Single Performance**

| Model Name	| MAE	| MAPE	| RMSE |
|-----------|---------|-----------|---------|
| Random Forest Regressor	| 684.564904	| 0.100777	| 1019.742124 |
| XGBoost Regressor	| 843.112293	| 0.122609	| 1250.952637 |
| Average Model	| 1354.800353	| 0.206400	| 1835.135542 |
| Linear Regression	| 1867.089774	| 0.292694	| 2671.049215 |
| Linear Regression - Lasso	| 1891.704881	| 0.289106	| 2744.451737 |
 
**Real Performance - Cross Validation**

| Model Name | MAE CV   | MAPE CV      | RMSE CV |
|-----------|---------|-----------|---------|
|  Random Forest Regressor	| 847.78 +/- 224.47	| 0.12 +/- 0.02 | 1271.62 +/- 328.74 |
|  XGBoost Regressor	| 1030.28 +/- 167.19	| 0.14 +/- 0.02	| 1478.26 +/- 229.79 |
|  Linear Regression	  |	2081.73 +/- 295.63	| 0.3 +/- 0.02	| 2952.52 +/- 468.37 |
|  Linear Regression - Lasso  |2116.38 +/- 341.5	| 0.29 +/- 0.01	| 3057.75 +/- 504.26 |
 

Although the Random Forest model has proven to be superior to the others, in some cases this model ends up requiring a lot of space to be published, resulting in an extra cost for the company to keep it running. Therefore, the chosen algorithm was the **XGBoost Regressor** which in sequence passed to the Hyperparameter Fine Tunning step.


**Final Performance - Hyperparameter Fine Tunning Cross Validation**

Após encontrar os melhores parâmetros para o modelo através do metódo Random Search as métricas finais para o modelo foram as seguintes:

| Model Name | MAE CV   | MAPE CV      | RMSE CV |
|-----------|---------|-----------|---------|
|  XGBoost Regressor	  | 1030.28 +/- 167.19 | 0.14 +/- 0.02 | 1478.26 +/- 229.79 |
	

**Model with XGBoost Regressor**

| Scenario | Values  |                              
|-----------|---------|
| Predictions	| €286,066,344.23 |
| Worst Scenario | €285,305,077.05 |
| Best Scenario	| €286,827,611.42 | 

#  Next steps

Start a second cycle to analyze the problem, seeking different approaches, especially considering stores with behavior that is difficult to predict.

Possible points to be addressed in the second cycle:

-**Work with NA data differently**

-**Rescaling and Encoding of data with different methodologies**

-**Work with new features for forecasting**

-**Work with a more robust method to find the best Hyper parameters for the model**
	
-**Analyzing sales equal to zero has some relationship with days when stores were closed or if there are stores operating without sales on those days.


Ref.: 
  - Imagem disponible on [Google Imagens](https://www.google.com/imgres?imgurl=https%3A%2F%2Fd1hbpr09pwz0sk.cloudfront.net%2Flogo_url%2Frossmann-czech-republic-e86d67e6&imgrefurl=https%3A%2F%2Frocketreach.co%2Frossmann-czech-republic-profile_b55ebaf6f68b0522&tbnid=DgzEqnZWCD-1zM&vet=12ahUKEwji6_XZ9pr0AhWWK7kGHb5PDqYQMyg5egQIARBF..i&docid=ZLc7upQS0jcYKM&w=200&h=200&itg=1&q=Rossmann%20Marketing&ved=2ahUKEwji6_XZ9pr0AhWWK7kGHb5PDqYQMyg5egQIARBF#imgrc=HCCKxz-5W3rzJM&imgdii=RysZEEX_uQ6jyM)




BG Rosmann Slaes Predict by Geraldine, Bruno.

[Kaggle](https://www.kaggle.com/c/rossmann-store-sales)


Ps.: Correcting erro install requeriments.txt:
Inside this file there are two versions of sklearn, delete both and reinstall scikit-learn==0.24.2
