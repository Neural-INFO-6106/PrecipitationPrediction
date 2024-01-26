# PrecipitationPrediction

**Problem Statement**

Pick any city and combine the satellite data with weather station data,can we reliably predict Lake Effect precipitation 3 days (or less?) in advance? Instead of predicting the exact value, you can create predictive labels for precipitation "no", "low", "medium", "high".

**Processing Steps**

**Step-1 Data Preprocessing** :
Firstly we are preprocessing our satellite image data : Specifically, we focus on Lake Michigan by narrowing our scope to its precise geographical coordinates, discarding the extra surroundings captured in the original satellite image. This process involves converting the images into PNG format from a 1-dimensional array and subsequently resizing them to a more manageable 64x64 pixel resolution.

For our meteorogical data : Here instead of using 0 imputation approah, we have performed KNN imputation. The advantage lies in capturing the local patterns and relationships within the dataset, resulting in a more contextually relevant imputation compared to the simplistic 0 imputation strategy. Additionally, our preprocessing involves the removal of NaN values from the precipitation column, enhancing the dataset's integrity and also removing the first four columns.

**Step-2 First Model - To find whether it's going to rain or not** :
In our initial modeling step, we perfom a binary classification task differentiating between rain and no rain, assigning labels 0 for no rain and 1 for rain. The model's first layer, the INPUT LAYER, encompasses inputs from both satellite imagery and meteorological data. Subsequently, we apply Convolutional Long Short-Term Memory (convLSTM) to the satellite_image_input in the following layer. Moving forward, the FLATTEN LAYER processes the flattened outputs of convlstm_satellite and meteo_data_input, which are then concatenated. The subsequent DENSE LAYER processes the concatenated features, leading to the final step in the OUTPUT LAYER. This architecture yields a binary classification, achieving a Class-1 accuracy of 88%.

**Step-3 Second Model - To find the amount of precipitaion** :
In our second modeling phase, we delve deeper into the classification by categorizing Class-1 into low, medium, and high precipitation intensity. This involves filtering values related to precipitation to discern its intensity. The filtered meteorological and cloud data serve as inputs for Long Short-Term Memory (LSTM) and Convolutional Long Short-Term Memory (convLSTM), respectively, with the filtered precipitation labels as the target. Following the same layered approach as described in the first model, this process results in a multi-class classification output."
