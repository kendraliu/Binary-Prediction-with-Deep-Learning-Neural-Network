# Deep-learning-challenge-binary-classification




### The final neual network model
| Model Architecture |
|-------|
| ![Model](/images/nn.svg) |

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
Despite various changes made, there was virtually no improvement at all.

The accurracies of all the trials made were around 0.73.

In the end, the hyperparameters of the first trial was used, for it has the less amount of neurons and layers but still have the same accruacy as every other trial.

For detailed changed made, see below table.

| #Trial | modify | modified (add/remove etc.) code |
|--------|--------|---------|
| 1 | first trial | `hidden_nodes_layer1 = 8`<br>`hidden_nodes_layer2 = 5`<br><br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer1, activation="relu", input_dim = X_train_scaled.shape[1]))`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="relu"))`<br>`nn.add(tf.keras.layers.Dense(units=1, activation="sigmoid"))` |
| 2 | added neurons in each layer | `hidden_nodes_layer1 =  50`<br>`hidden_nodes_layer2 = 20` |
| 3 | added another hidden layer | `hidden_nodes_layer3 = 10`<br><br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer3, activation="sigmoid"))` |
| 4 | added more neurons to first two layers | `hidden_nodes_layer1 =  80`<br>`hidden_nodes_layer2 = 40 `|
| 5 | removed the third layer, changed the activation of the second layer to "tanh" | `#hidden_nodes_layer3 = 10`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="tanh"))` |
| 6 | decreased neurons in second layer, changed the activation of the second layer back to "relu" | `hidden_nodes_layer2 = 30`<br>`nn.add(tf.keras.layers.Dense(units=hidden_nodes_layer2, activation="relu"))` |