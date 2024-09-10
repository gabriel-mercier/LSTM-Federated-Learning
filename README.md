# Agricultural Time Series Prediction using LSTM and Federated Learning

## Overview

This project focuses on developing an LSTM model for time series prediction of soil humidity, leveraging a Hierarchical Federated Learning (HFL) framework. The goal is to predict future soil conditions for more effective agricultural decision-making.

### Key Features:
- **LSTM Model**: Predicts 5-hour future values based on 10-minute interval data from sensor stations from the a partnership grant between university of Newcastle  and university  of Waikatoo.
- **Federated Learning Integration**: Improves prediction accuracy by 94.2% compared to isolated local models.
- **Data Augmentation**: Handles small datasets (2000-3000 samples) through augmentation techniques inspired by computer vision.
- **Sensor Data Handling**: Interpolates missing values, suppresses zero/peak values, and smooths noisy data using rolling averages.

## Data

![data](./images/data.png)

- **Source**: Real-world agricultural sensor data (soil humidity), collected across multiple clients.
- **Challenges**: Small datasets, missing values, and noise.
- **Preprocessing**: 
  - Suppression of peak and zero values.
  - Rolling average to reduce noise.
  - Interpolation for missing data.
  - Feature engineering to detect when crops are watered.

## Model Architecture

![structure](./images/structure.png)

The model architecture was fine-tuned to achieve the best results, with key hyperparameters being:

- **Batch Size**: 64
- **Learning Rate**: 0.005 (Adam optimizer)
- **Loss Function**: Mean Squared Error (MSE)
- **Variable Hyperparameters**: 
  - Number of layers
  - Units per layer
  - Number of input time steps (`n_step_in`)
 
![fine-tuning](./images/fine-tuning.png)

## Federated Learning (HFL) Implementation

This project integrates **Flower**, a federated learning framework, to facilitate training across multiple clients and servers:

- **Local Models**: Each client trains a model on their local data.
- **Local Servers**: Aggregate models from clients within the server’s scope.
- **Global Server**: Aggregates local server models to produce a global model.

### Results:

- **Local Model Performance**: Local models suffered from lack of data, but served as useful benchmarks.
- **Global Model**: Significant improvement in performance when aggregating across clients and servers.

![results](./images/results.png)

## References

- [Flower Federated Learning Framework](https://flower.dev/)
- LSTM architecture inspired by [TensorFlow Sunspots CNN-RNN-DNN Lab](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C4/W4/ungraded_labs/C4_W4_Lab_3_Sunspots_CNN_RNN_DNN.ipynb)

## Contact

For further details or inquiries, please feel free to reach out.
