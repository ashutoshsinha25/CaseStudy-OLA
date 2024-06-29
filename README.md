### Problem Statement

Recruiting and retaining drivers is seen by industry watchers as a tough battle for Ola. Churn among drivers is high and it’s very easy for drivers to stop working for the service on the fly or jump to Uber depending on the rates.

As the companies get bigger, the high churn could become a bigger problem. To find new drivers, Ola is casting a wide net, including people who don’t have cars for jobs. But this acquisition is really costly. Losing drivers frequently impacts the morale of the organization and acquiring new drivers is more expensive than retaining existing ones.

You are working as a data scientist with the Analytics Department of Ola, focused on driver team attrition. You are provided with the monthly information for a segment of drivers for 2019 and 2020 and tasked to predict whether a driver will be leaving the company or not based on their attributes like

Demographics (city, age, gender etc.)
Tenure information (joining date, Last Date)
Historical data regarding the performance of the driver (Quarterly rating, Monthly business acquired, grade, Income)



### Column Profiling:

- MMMM-YY : Reporting Date (Monthly)
- Driver_ID : Unique id for drivers
- Age : Age of the driver
- Gender : Gender of the driver – Male : 0, Female: 1
- City : City Code of the driver
- Education_Level : Education level – 0 for 10+ ,1 for 12+ ,2 for graduate
- Income : Monthly average Income of the driver
- Date Of Joining : Joining date for the driver
- LastWorkingDate : Last date of working for the driver
- Joining Designation : Designation of the driver at the time of joining
- Grade : Grade of the driver at the time of reporting
- Total Business Value : The total business value acquired by the driver in a month (negative business indicates cancellation/refund or car EMI adjustments)
- Quarterly Rating : Quarterly rating of the driver: 1,2,3,4,5 (higher is better)








### Model Performance Metrics

| Model       | Precision (Class 0) | Recall (Class 0) | F1-score (Class 0) | Precision (Class 1) | Recall (Class 1) | F1-score (Class 1) | Accuracy | Macro avg Precision | Macro avg Recall | Macro avg F1-score | Weighted avg Precision | Weighted avg Recall | Weighted avg F1-score |
|-------------|----------------------|------------------|---------------------|----------------------|------------------|---------------------|----------|---------------------|------------------|--------------------|------------------------|---------------------|------------------------|
| Decision Tree | 0.856              | 0.935            | 0.894               | 0.968                | 0.926            | 0.946               | 0.929    | 0.912               | 0.930            | 0.920              | 0.932                  | 0.929               | 0.929                  |
| Random Forest 1 | 0.910              | 0.928            | 0.919               | 0.966                | 0.957            | 0.961               | 0.948    | 0.938               | 0.942            | 0.940              | 0.948                  | 0.948               | 0.948                  |
| Random Forest 2 | 0.902              | 0.902            | 0.902               | 0.954                | 0.954            | 0.954               | 0.937    | 0.928               | 0.928            | 0.928              | 0.937                  | 0.937               | 0.937                  |
| XGBoost     | 0.875              | 0.915            | 0.895               | 0.959                | 0.938            | 0.949               | 0.931    | 0.917               | 0.927            | 0.921              | 0.932                  | 0.931               | 0.931                  |
| LightGBM    | 0.887              | 0.916            | 0.901               | 0.962                | 0.944            | 0.953               | 0.937    | 0.925               | 0.930            | 0.927              | 0.938                  | 0.937               | 0.937                  |



### Model Selection

For a ride-sharing platform focused on driver churn, the key metric depends on the business objectives:

1. High Recall (Class 1): If the goal is to catch as many potential churners as possible, recall is crucial. Random Forest 1 has the highest recall for Class 1 (0.956790).
2. Balanced Performance (F1-score): The F1-score provides a balance between precision and recall. Random Forest 1 has the highest F1-score for Class 1 (0.961240).
3. Accuracy: Overall performance across all classes can be reflected by accuracy. Random Forest 1 has the highest accuracy (0.947589).
4. Weighted Metrics: Considering the weighted averages of precision, recall, and F1-score gives an overview of the model's performance across all classes. Random Forest 1 performs best with weighted avg F1-score (0.947817).



### Actionable Insights and Recommendation
- based on the data we saw that ~68% of the drivers have left the company.
- after training the model, best features to represent our data are `months worked in the company`, `total business value generated` , `increase of quarterly rating`, `uareterly ratings` and `monthly average income`.
- comapny needs to employ more insentive or the drivers based on their worked monthsm business value they generate.
- also company can look at doing more frrquent rating of drivers instead of quarterly rating to see how drivers are performing and provide insentives/bonus to top performers.
- Company can also employ a feedback system where drivers can express their intent for leaving, that way company can promptly see what they can do from their based for that particular driver to make him.her stay

