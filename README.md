# Deep-learning-challenge-binary-classification

### Overview
This neural network model aims to help the non-profit foundation Alphabet Soup determine funding applicants with the best chnance in success.

It does a binary classification of the applicants on whether they would be successful if funded by Alphabet Soup. 

The data contains the information from more than 34,000 organizations that have received their funding in the past.

Model was trained with labeled data and performed prediction on a group of testing data with the goal of achieving at least 75% accuracy. 

## The final neual network model
Sadly, all the attempts made yielded significantly similar results, with an accuracy around 73% over 100 epochs. More detailed record can be reviewed in the "Optimization attempts" section.

The final model that was decided on was in fact the one in the first trial, with the least amount of neurons and layers with an accuracy of 73%.

The hyperparameters of the model and its results are shown in the images below.

| Model Architecture | Activation Functions |
|-------|-------|
| ![Model](/images/nn.png) | First layer: ReLu,<br>Second layer: ReLu,<br>Output layer: Sigmoid |

| Model Accuracy | Model Loss |
|-------|-------|
| ![Model Accuracy](/images/accuracy.png) | ![Model Loss](/images/loss.png) |


### Variables used for the model
- target variable: `IS_SUCCESSFUL` — whether the money used effectively
- unused variables: `EIN` and `NAME` — identification columns, they are used for ID purposes for the dataset and not contributing factors
- feature variables: all other variables 
    - `APPLICATION_TYPE` — Alphabet Soup application type
    - `AFFILIATION` — Affiliated sector of industry
    - `CLASSIFICATION` — Government organization classification
    - `USE_CASE` — Use case for funding
    - `ORGANIZATION` — Organization type
    - `STATUS` — Active status
    - `INCOME_AMT` — Income classification
    - `SPECIAL_CONSIDERATIONS` — Special considerations for application
    - `ASK_AMT` — Funding amount requested


### Optimization attempts
Despite various changes made, there was virtually no improvement at all from the accuracy of 73% in first trial. The accuracies of all the trials made were all around 72%-73%. The actual accuracies were not recorded because of the little changes.

In the end, the hyperparameters of the first trial was used, for it has the less amount of neurons and layers but still have the same accruacy as every other trial.

For detailed changes made, see below table.

| #Trial | modify | modified (add/remove etc.) code |
|--------|--------|---------|
| 1 | first trial | `hidden_nodes_layer1 = 8`<br>`hidden_nodes_layer2 = 5`<br><br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer1, activation="relu", input_dim = X_train_scaled.shape[1]))`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="relu"))`<br>`nn.add(tf.keras.layers.Dense(units=1, activation="sigmoid"))` |
| 2 | added neurons in each layer | `hidden_nodes_layer1 =  50`<br>`hidden_nodes_layer2 = 20` |
| 3 | added another hidden layer | `hidden_nodes_layer3 = 10`<br><br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer3, activation="sigmoid"))` |
| 4 | added more neurons to first two layers | `hidden_nodes_layer1 =  80`<br>`hidden_nodes_layer2 = 40 `|
| 5 | removed the third layer, changed the activation of the second layer to "tanh" | `#hidden_nodes_layer3 = 10`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="tanh"))` |
| 6 | decreased neurons in second layer, changed the activation of the second layer back to "relu" | `hidden_nodes_layer2 = 30`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="relu"))` |