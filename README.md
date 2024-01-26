# Next Day Precipitation Prediction

## Problem Statement
Predict Lake Effect precipitation reliably 3 days (or less) in advance by combining satellite data with weather station data. Generate predictive labels for precipitation: "no," "low," "medium," "high."

## Processing Steps

### Step 1: Data Preprocessing
#### Satellite Image Data:
- Focus on Lake Michigan's precise geographical coordinates.
- Convert images to PNG format, resize to 64x64 pixels.

#### Meteorological Data:
- KNN imputation for NaN values.
- Remove NaN values from the precipitation column.
- Discard first four columns.

### Step 2: First Model - Rain or No Rain
- Binary classification for rain or no rain.
- Input layer combines satellite imagery and meteorological data.
- Apply Convolutional Long Short-Term Memory (convLSTM) to satellite image input.
- Flatten layer processes flattened outputs of convLSTM and meteorological data input.
- Concatenate flattened outputs.
- Dense layer processes concatenated features.
- Output layer yields binary classification.
- Achieve Class-1 accuracy of 88%.

### Step 3: Second Model - Precipitation Intensity
- Further classify Class-1 into low, medium, and high precipitation intensity.
- Filter values related to precipitation for intensity discernment.
- Use Long Short-Term Memory (LSTM) and Convolutional Long Short-Term Memory (convLSTM) for meteorological and cloud data, respectively.
- Filtered precipitation labels serve as targets.
- Same layered approach as the first model, resulting in a multi-class classification output.

This project enhances precipitation prediction accuracy, providing valuable insights into the intensity and occurrence of Lake Effect precipitation.


**List of libraries used:**

[![Python](https://img.shields.io/badge/Python-%233776AB.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-%23150458.svg?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-%23013243.svg?logo=numpy&logoColor=white)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-%2300599C.svg?logo=matplotlib&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-%237DB5A5.svg?logo=seaborn&logoColor=white)](https://seaborn.pydata.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-%23F7931E.svg?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

[![KNNImputer](https://img.shields.io/badge/KNNImputer-%23F7931E.svg?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/stable/modules/generated/sklearn.impute.KNNImputer.html)
[![Pickling](https://img.shields.io/badge/Pickle-%237B5EAF.svg)](https://docs.python.org/3/library/pickle.html)
[![Ast](https://img.shields.io/badge/Ast-%2343853D.svg)](https://docs.python.org/3/library/ast.html)
[![TQDM](https://img.shields.io/badge/TQDM-%238BBE3C.svg?logo=tqdm&logoColor=white)](https://tqdm.github.io/)

[![Jupyter](https://img.shields.io/badge/Jupyter-%23F37626.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![TensorFlow Keras](https://img.shields.io/badge/TensorFlow_Keras-%23FF6F00.svg?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/guide/keras)
[![EarlyStopping](https://img.shields.io/badge/EarlyStopping-%23FF6F00.svg?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/EarlyStopping)
