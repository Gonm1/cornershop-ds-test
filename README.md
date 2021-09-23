# Repo's description

Files:
1. `data_process.ipynb`: a notebook that processes the tables provided and combines them into a dataset. It joins the tables, re-structure columns, add extra features, remove outliers and outputs it all to a `data.csv` file. Also it outputs the `submission_data.csv` file, which have the rows not containing a `total_minutes` value for later prediction.
2. `random_search.ipynb`: setups pipelines and perform a randomized search of hyperparameters to find the best combination for the given task. Outputs a `results.txt` file with the mae and mse metrics over the test data and also outputs the best models. All output can be found in `rand_search_results` folder.
3. `grid_search.ipynb`: setups the pipelines and perform a grid search around the hyperparameters found in the randomized search with the objective of finding an even better combination. All output can be found in `grid_search_results` folder.
4. `predictions.ipynb`: loads the models, make the predictions over the `submission_data.csv` and writes it to `submission_file.csv`.

## Results on test data - summary table

| Metric | Model         | Random search | Grid search |
|--------|---------------|---------------|-------------|
| MAE    | SVM           | 17.696        | 17.694      |
| \|     | Random Forest | 18.375        | 18.376      |
| \|     | XGBoost       | 17.885        | 17.855      |
| \|     | Ensemble      | **17.658**    | 17.659      |
| MSE    | SVM           | 579.375       | 579.333     |
| \|     | Random Forest | 561.918       | 562.135     |
| \|     | XGBoost       | 573.365       | 567.926     |
| \|     | Ensemble      | 554.118       | **552.983** |
| RMSE   | SVM           | 24.070        | 24.069      |
| \|     | Random Forest | 23.704        | 23.709      |
| \|     | XGBoost       | 23.945        | 23.831      |
| \|     | Ensemble      | 23.539        | **23.515**  |
| R2     | SVM           | 0.440         | 0.440       |
| \|     | Random Forest | 0.457         | 0.456       |
| \|     | XGBoost       | 0.446         | 0.451       |
| \|     | Ensemble      | 0.464         | **0.465**   |

*Denoted in bold are the best results.

## Submission file
The predictions on the submission data were made with the grid search ensemble model and can be found on the `submission_file.csv`.

# Cornershop´s Data Science Test

Cornershop has operations in several cities and countries, delivering thousands of orders every day. In order to deliver these orders on time we depend on good estimations of how much time the shopper needs to complete the order.

In this technical test you will be creating a machine learning model to make these estimation. As we internally build our machine learning solutions using python, we ask you to do the same in this technical test. However you are free to use the libraries you are most comfortable with.

## Before you begin ##
You will need to create a new repository and invite @ThomasSve, @Camiloez and @fcid92 as collaborators.

## Data

In this repository, we have included data representing the order, shopper and the store branch. 

### File description and data fields
***order_products.csv:***
- order_id: ID of the order
- product_id: ID of the product
- quantity: The quantity ordered of this product
- buy_unit: The unit of the product (KG/UN)

***orders.csv:***
- order_id: ID of the order
- lat: The latitude of the delivery location
- lng: The longitude of the delivery location
- promised_time: The delivery time promised to the user
- on_demand: If true, the order was promised to be delivered in less than X minutes
- shopper_id: ID representing the shopper completed the order.
- store_branch_id: ID of the store branch
- total_minutes: The total minutes it took to complete the order (label)

***shopper.csv***
- shopper_id: ID of the shopper
- seniority: The experience level of the shopper.
- found_rate: Percentage of products found by shopper historical.
- picking_speed: Historical picking speed, products pr minutes.
- accepted_rate: Percentage of orders historically accepted by shopper
- rating: client rating of shopper

***storebranch.csv:***
- store_branch_id: ID of the store branch
- store: ID representing the store
- lat: Latitude of the branch location
- lng: Longitude of the branch location

*All the data has been anonymized*

### Objective

The objective is to predict the `total_minutes` an order takes to complete, where the rows not containing a `total_minutes` value should be set aside as a part of the submission file, containing the `order_id` with the predicted values. 

As we are interested in seeing how you attacked the problem, we also ask you to include your code together with the submission file. The code needs to be well documented, explaining the decisions made. With these explanations, we will be looking at everything from how the data was processed, features used to the completed model and predictions. 

Good luck!
