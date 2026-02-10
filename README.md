# Data-Generation-using-Modelling-and-Simulation-for-Machine-Learning

## 1. Introduction
This project focuses on generating synthetic data using a simulation-based approach and applying machine learning models to analyze the generated data. The objective is to demonstrate how simulation tools can be used to create datasets for machine learning when real-world data is limited or expensive.

## 2. Simulation Tool Used
SimPy (Discrete-Event Simulation Framework)

SimPy is an open-source, process-based discrete-event simulation library in Python. It is widely used to model real-world systems such as queues, networks, and service systems.

This project uses SimPy to simulate a single-server queue (M/M/1 system).

## 3. Simulation Model Description
The simulated system represents a single-server queue where:

Customers arrive according to a random process
A single server processes customers one at a time
Waiting time and system performance metrics are recorded

## 4. Input Parameters and Bounds

| Parameter | Description | Lower Bound | Upper Bound |
|----------|-------------|-------------|-------------|
| Arrival Rate (λ) | Average number of customers arriving per unit time | 0.5 | 5 (exclusive) |
| Service Rate (μ) | Average number of customers served per unit time | 1.0 | 6.0 (exclusive) |
| Simulation Time | Total duration of the simulation | 50 | 200 (inclusive) |

**Notes:**
- Arrival rate (λ) and service rate (μ) are sampled from continuous uniform distributions.
- Simulation time is sampled as an integer value.
- Bounds marked as *exclusive* indicate the upper limit is not included in sampling.
  
## 5. Output Parameters

| Output Metric | Description |
|--------------|-------------|
| Average Waiting Time | Mean time customers spend waiting in the queue |
| Server Utilization | Ratio of arrival rate to service rate |
| Average Queue Length | Average number of customers present in the queue |

## 6. Data Generation Methodology
The data was generated using a Discrete-Event Simulation (DES) model, implemented with the SimPy library:

- **Random Input Parameters**: Input parameters (arrival_rate, service_rate, sim_time) are randomly sampled within their predefined bounds.
- **Simulation Execution**: Each unique set of these parameters is passed to the SimPy simulator.
- **Performance Metrics Recorded**: The simulator then records key performance metrics, including Average Waiting Time, Server Utilization, and Average Queue Length.
- **Repetitive Process**: This entire simulation and recording process is repeated 1000 times to create a diverse dataset.
- **Data Storage**: The generated dataset is then saved as a CSV file (synthetic_data.csv).

## 7. Machine Learning Models Used
The following regression models were trained and evaluated:
| S. No. | Model |
|------:|---------------------------|
| 1 | Linear Regression |
| 2 | Decision Tree |
| 3 | Random Forest |
| 4 | Gradient Boosting |
| 5 | K-Neighbors Regressor |
| 6 | Support Vector Regressor |
| 7 | Ridge Regression |
| 8 | Lasso Regression |
| 9 | Elastic Net |
| 10 | MLP Regressor |
| 11 | XGBoost |
| 12 | LightGBM |

## 8. Evaluation Metrics
Models were evaluated using:

- Mean Squared Error (MSE)
- MAE
- R² Score

## 9. Results

| Model                    |     MAE |      MSE |        R2 |
|:-------------------------|--------:|---------:|----------:|
| Linear Regression        | 6.95873 |  80.2698 |  0.59826  |
| Decision Tree            | 2.79585 |  28.8368 |  0.855676 |
| Random Forest            | 1.75602 |  12.8562 |  0.935657 |
| Gradient Boosting        | 2.05704 |  13.6537 |  0.931665 |
| K-Neighbors              | 4.64899 |  68.8727 |  0.655301 |
| Support Vector Regressor | 7.75074 | 250.816  | -0.255301 |
| Ridge                    | 6.95778 |  80.2728 |  0.598245 |
| Lasso                    | 6.85293 |  81.9378 |  0.589912 |
| ElasticNet               | 6.7328  |  87.6382 |  0.561382 |
| MLPRegressor             | 1.92695 |  10.9917 |  0.944988 |
| XGBoost                  | 1.93198 |  15.7427 |  0.92121  |
| LightGBM                 | 1.89735 |  12.4376 |  0.937752 |

Best Performing Model: Random Forest Regressor

## 10. Result Graphs

1. R2:
   <img width="1389" height="690" alt="image" src="https://github.com/user-attachments/assets/70dc85ec-2cb2-4f4d-811c-7365e15c7a10" />

2. MAE:
   <img width="1389" height="690" alt="image" src="https://github.com/user-attachments/assets/683804dd-5a44-4d70-b289-e1b85aab489d" />

3. MSE:
    <img width="1389" height="690" alt="image" src="https://github.com/user-attachments/assets/d32512c7-164a-4e62-a20c-b5fc844b99b0" />

## 11. Conclusion
The most suitable model depends on the specific objective: if minimizing absolute prediction error is paramount, Random Forest Regressor is the best choice. If maximizing the explained variance of the target variable is the priority, MLPRegressor is slightly superior. Both, along with LightGBM, XGBoost, and Gradient Boosting, represent strong candidates for further optimization and deployment.
