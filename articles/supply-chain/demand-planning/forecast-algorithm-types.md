## <a name="forecasting-algorithms"></a>Demand forecasting algorithms

Demand planning includes three popular demand forecasting algorithms: *auto-ARIMA*, *ETS*, and *Prophet*. The demand forecasting algorithm that you use depends on the specific characteristics of your historical data.

- Auto-ARIMA is suited for stationary data, which is data with constant mean, constant standard deviation and no seasonality.

- Error, trend, and seasonality (ETS) shines if your business case is simple and the data has various patterns like linear or exponential trends **or** you would like the forecast to give more weight to most recent data. 

- Prophet works best with complex, real-world data.

Demand planning also provides both a *best fit* model (which automatically selects the best of the available algorithms for each product and dimension combination) and the ability to develop and use your own custom models.

By understanding these algorithms and their strengths, you can make informed decisions to optimize your supply chain and meet customer demand.

This section describes how each algorithm works and its suitability for different types of historical demand data.

### Best fit model

The best fit model automatically finds which of the other available algorithms (auto-ARIMA, ETS, or Prophet) best fits your data for each product and dimension combination. In this way, different models can be used for different products. In most cases, we recommend using the best fit model because it combines the strengths of all of the other standard models. The following example shows how.

Suppose you have the historical demand time-series data that includes the dimension combinations listed in the following table.

| Product | Store |
|---|---|
| A | 1 |
| A | 2 |
| B | 1 |
| B | 2 |

When you run a forecast calculation using the Prophet model, you get the following results. In this example, the system always uses the Prophet model, regardless of the calculated mean absolute percentage error (MAPE) for each product and dimension combination.

| Product | Store | forecast model | MAPE |
|---|---|---|---|
| A | 1 | Prophet | 0.12 |
| A | 2 | Prophet | 0.56 |
| B | 1 | Prophet | 0.65 |
| B | 2 | Prophet | 0.09 |

When you run a forecast calculation using the ETS model, you get the following results. In this example, the system always uses the ETS model, regardless of the calculated MAPE for each product and dimension combination.

| Product | Store | forecast model | MAPE |
|---|---|---|---|
| A | 1 | ETS | 0.18 |
| A | 2 | ETS | 0.15 |
| B | 1 | ETS | 0.21 |
| B | 2 | ETS | 0.31 |

When you run a forecast calculation using the best fit model, the system optimizes the model selection for each product and dimension combination. The selection changes based on patterns found in the historical sales data.

| Product | Store | Prophet MAPE | Auto-ARIMA MAPE | ETS MAPE | Best fit forecast model | Best fit MAPE |
|---|---|---|---|---|---|---|
| A | 1  | 0.12 | 0.34 | 0.18 | Prophet | 0.12 |
| A | 2  | 0.56 | 0.23 | 0.15 | ETS | 0.15 |
| B | 1  | 0.65 | 0.09 | 0.21 | Auto-ARIMA | 0.09 |
| B | 2  | 0.10 | 0.27 | 0.31 | Prophet | 0.10 |

The following graph shows the overall sales forecast across all dimensions (all products in all stores) over the next nine months, found using three different forecast models. The green line represents the best fit model. Because best fit chooses the best forecast model for each product and dimension combination, it avoids the outliers that could occur from forcing a single model on all dimension combinations. As a result, the overall best-fit forecast resembles an average of the single-model forecasts.

:::image type="content" source="media/forecast-model-compare-graph.png" alt-text="Forecast results from three different forecast models based on the same historical data":::

Legend:

- Red = Only Prophet
- Blue = Only ETS
- Green = Best fit

### Auto-ARIMA: The time traveler's delight

The ARIMA algorithm is like a time machine: it takes you on a journey through past demand patterns so that you can make informed predictions about the future. Auto-ARIMA uses a technique that's known as autoregressive integrated moving average (ARIMA). This technique combines three key components: autoregression, differencing, and moving averages. The auto-ARIMA algorithm automatically identifies the best combination of these components to create a forecast model that suits your data.

The **I** in Arima stands for integrated and sometimes is called differencing which is a step that the model takes if the time series is non-stationary and then in morphs it to stationary data. 


Auto-ARIMA works especially well with time series data that shows a stable pattern over time, such as seasonal fluctuations or trends. If your historical demand follows a reasonably consistent path, auto-ARIMA might be your preferred forecasting method.

The steps of ARIMA algorithm is that it:
1. Executes differencing on the data if it is not stationary
1. Finds correlation between lagged data points
1. Calculates moving average error.

The AR or AutoRegressive and MA or Moving average serve distinct but complementary roles in modeling the time series data. 
* AR (AutoRegressive) Component: The AR part of the model regresses the time series on its own previous values. It Captures the influence of past values on the current value.
* MA (Moving Average) Component: Accounts for past forecast errors and improves the model's accuracy by smoothing out the noise.
* ARIMA basically combines AR and MA after differencing the data.
* The final prediction is a combination of the influence of past values and the adjustments from past errors.

#### Equations

#### (AR) yt = c+ɸ1yt - 1 + ɸ2yt - 2 + … ɸpyt - p + ϵt

Where

- _Yt_ : Value at time t

- _c_: constant

- _ɸ1,ɸ2,  .. ɸp_: Coefficients of the model

- _ϵt_: white noise error term

---

#### (MA)  yt = c + ϵt + ϴ1ϵt - 1 + ϴ2ϵt - 2 + … + ϴqϵt-q

- _Yt_: Value at time t

- _c_: constant

- _ϵt, ϵt - 1  .. ϵt-q_: Error terms at time t, t-1, … ,t - q

- _ϴ1, ϴ2, .. ϴq_: Coefficients of the model

---

#### (ARIMA) =  (AR) + (MA) _After differencing the time series_


### ETS: The shape shifter

Error, trend, and seasonality (ETS) is a versatile demand forecasting algorithm that adapts to the shape of your data. It can change its approach based on the characteristics of your historical demand. Therefore, it's suitable for a wide range of scenarios.

The name ETS is an abbreviation for the three essential components that the algorithm decomposes the time series data into: error, trend, and seasonality. By understanding and modeling these components, ETS generates forecasts that capture the underlying patterns in your data.

The core idea of ETS is Forecasting future data points by applying varying weights to different observations where recent data points carry more weight than older ones.
As for more advanced ETS, it decomposes the time series into Trend, Seasonal and Error components, error here is the noise and fluctuations in the time series.

It uses the seasonal period parameter set by the user as seasonal index.
Estimates the trend in the upcoming horizon and tries multiple values to see what fits.
Finally, the model forecasts the error and then combine it again with the estimated trend and seasonality components.

The app figures out which flavor of ETS is most suitable for the time series and applies it accordingly.


Here's a step-by-step explanation of the algorithm:


1. **Decomposition of Components**:
   - The time series is broken down into three components:
     - **Error (E)**: Captures the random noise or irregular fluctuations.
     - **Trend (T)**: Represents the overall direction (increasing, decreasing, or constant) of the data over time.
     - **Seasonality (S)**: Reflects repetitive patterns or cycles in the data (e.g., yearly, monthly).

2. **Selection of Models for Components**:
   - Each component follows an **Additive** model:     
     - **ETS(A,A,A)**: Additive Error, Additive Trend, Additive Seasonality.

3. **Specification of the Initial States**:
   - Initial values for the **Level**, **Trend**, and **Seasonality** are calculated to start the recursive updating process.

4. **Updating the States**:
   - As new data points arrive, the states of the model (level, trend, seasonality) are updated using weighted smoothing equations.
   - General equations:
     - **Level (ℓ):** Represents the current smoothed value of the series.
     - **Trend (b):** Represents the rate of change in the series.
     - **Seasonality (s):** Adjusts for periodic patterns.
     - **Error (e):** Difference between the actual and predicted values.

5. **Forecasting**:
   - Future values are predicted by combining the most recent estimates of the **Level**, **Trend**, and **Seasonality** components.


#### Equation:

#### Ft+1 = αAt + (1 – α) Ft 

- _Ft+1_: Forecasted value

- _Ft_: Previous forecasted value

- _At_: Actual historical value

- _α_: Smoothing constant 0 ≤ α ≤ 1




### Prophet: The visionary forecasting guru

Prophet was developed by Facebook's research team. It's a modern and flexible forecasting algorithm that can handle the challenges of real-world data. It's especially effective at handling missing values, outliers, and complex patterns.It performs best with seasonal data and accounts for holidays during forecasting and doesn’t need much preprocessing.


Prophet works by decomposing the time series data into several components, such as trend, seasonality, and holidays, and then fitting a model to each component. This approach enables Prophet to accurately capture the nuances in your data and produce reliable forecasts. Prophet is ideal for businesses that have irregular demand patterns or frequent outliers, or businesses that are affected by special events such as holidays or promotions.

Here is step by step how the algorithm works:

1. Decomposes the time series into Trend, Seasonality, and Holiday components.
1. Detects and handle changepoints for trend shifts.
1. Uses Fourier series for seasonal patterns.
1. Adds holiday regressors for irregular events.
1. Fit the model parameters using Bayesian optimization.
1. Generate predictions and uncertainty intervals.


#### Equation

#### y(t)=g(t)+s(t)+h(t)+ϵ(t)

- g(t): Captures the non-periodic trend changes over time and is calculated using Piecewise Linear Trend equation

- s(t): recurring seasonality patterns (e.g., daily, weekly, yearly) and is modeled using fourier series.

- h(t): Accounts for known, irregular effects caused by holidays or special events and they are treated as additional regressors that allow for flexibility in modeling special events.

- ϵ(t): Random noise or unexplained variability

### When to use what algorithm

We realized that your business case will vary and when having big data, it contains literally thousands of Timeseries inside of it, each is embedded with different trait and characteristics so we hope this color coded table aids you.

<table style="border-collapse: collapse; width: 100%; text-align: center;">
  <tr>
    <th style="border: 1px solid black; padding: 10px;">Scenario</th>
    <th style="border: 1px solid black; padding: 10px;">ARIMA</th>
    <th style="border: 1px solid black; padding: 10px;">ETS</th>
    <th style="border: 1px solid black; padding: 10px;">Prophet</th>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Simple business case</td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Time series has different (linear/exponential) trend and several seasonality types</td>
    <td style="background-color: red; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Time series exhibits a clear linear trend</td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Data is stationary</td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: red; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Data is non-stationary</td>
    <td style="background-color: red; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Require quick forecasting</td>
    <td style="background-color: red; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
  </tr>
  <tr>
    <td style="border: 1px solid black; padding: 10px;">Forecasting with focus on recent period</td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
    <td style="background-color: lightgreen; border: 1px solid black;"></td>
    <td style="background-color: yellow; border: 1px solid black;"></td>
  </tr>
</table>


### XGBoost

The XGBoost algorithm is able to generate a forecast based on two multiple inputs. It is currently the only algorithm that you can use with the *Forecast with signals* step and is only supported by that type of step. You can learn more about setting up forecast models that use XGBoost and signals input in [Forecast with signals](forecasts-with-signals.md).

XGBoost (Extreme Gradient Boosting) is a highly efficient and scalable implementation of gradient boosting. It builds an ensemble of decision trees to make predictions, let's break down each of these componenets:

#### Decision trees
A decision tree is a machine learning model that splits data into subsets based on signals values (also known as dimensions or features), forming a tree-like structure, below is an example of sales based on wether data:

                             [Is Temp > 25°C?]
                              /       \
                         Yes            No
                        /                 \
           [Is Temp > 30°C?]       [Is Temp > 15°C?]
              /       \                  /       \
        Leaf: 80 SKU  Leaf: 60 SKU        [Is Temp > 10°C?]  Leaf: 20 SKU
                                     /         \
                                Leaf: 40 SKU  Leaf: 10 SKU


Here's the revised ASCII art for a regression decision tree predicting sales **only based on temperature**:

```
                             [Is Temp > 25°C?]
                              /       \
                         Yes            No
                        /                 \
           [Is Temp > 30°C?]       [Is Temp > 15°C?]
              /      \                  /       \
        Leaf: 80  Leaf: 60        [Is Temp > 10°C?]  Leaf: 20
                                     /       \
                                Leaf: 40  Leaf: 10
```

**Explanation**:

1. **Root Node**:
   - Splits on whether the temperature is greater than 25°C.
     - **Yes** → Go to the left subtree.
     - **No** → Go to the right subtree.

2. **Left Subtree (Temp > 25°C)**:
   - Further splits on whether the temperature exceeds 30°C:
     - **Yes** → Predict **80** sales.
     - **No** → Predict **60** sales.

3. **Right Subtree (Temp ≤ 25°C)**:
   - Splits on whether the temperature is greater than 15°C:
     - **Yes** → Further splits on whether the temperature is greater than 10°C:
       - **Yes** → Predict **40** sales.
       - **No** → Predict **10** sales.
     - **No** → Predict **20** sales.


#### Ensemble Learning
A machine learning approach that combines multiple models (often called "weak learners") to make predictions. The idea is that the combined output of many models is often more accurate and robust than any single model.
One type of ensemble learning is called *Boosting* where models are built sequentially, with each one correcting the errors of the previous one.

#### Gradient Boosting
Gradient Boosting is a powerful machine learning technique used for both regression (which is our case) and classification problems. It builds an ensemble of weak models (typically decision trees) in a sequential manner, where each model focuses on reducing the errors (residuals) made by the previous models.
It is effective at capturing complex relationships between signals (also known as exegenous variable) and the input data (also known as target variable), it also provides better predictive performance than other methods.

#### How XGBoost algorithm works

XGBoost (Extreme Gradient Boosting) is a highly efficient and scalable implementation of gradient boosting. It builds an ensemble of decision trees to make predictions. Here's a step-by-step explanation of how it works:


1. **Initialize Predictions**
   - **Task**: Start by predicting a base value for all instances. 
   - **Why**: The base value is typically the mean of the target variable for regression or the log-odds for classification. 

1. **Calculate Residuals (Gradients)**
   - **Task**: Compute the residuals or gradients, which represent the difference between the predicted and actual values.
   - **Why**: These residuals serve as the error signal that the model will try to minimize.

1. **Fit a Decision Tree**
   - **Task**: Train a new decision tree using the residuals (gradients) as the target values.
   - **Why**: The tree predicts adjustments to the previous model's predictions.
   - **Key Details**:
     - XGBoost uses a greedy algorithm to split the data.
     - Splits are selected based on the gain in the objective function, which is regularized to avoid overfitting.


1. **Regularize Tree Growth**
   - **Task**: Apply constraints to prevent overfitting.
   - **Why**: Regularization helps generalize the model and maintain performance on unseen data.
   - **Techniques**:
     - **Tree depth**: Limit maximum depth of trees.
     - **Leaf weights**: Penalize overly complex trees by adding regularization terms.
     - **Minimum split gain**: Require a minimum improvement in the loss function to allow a split.


1. **Update Predictions**
   - **Task**: Adjust predictions by adding the outputs of the new tree.
   - **Why**: This step reduces the error progressively.


1. **Repeat the Process**
   - **Task**: Repeat steps 2-5 to sequentially add more trees.
   - **Why**: Each tree reduces the residuals, gradually improving the model.
   - **Stopping Criteria**:
     - A fixed number of trees implemented in the Demand Planning app algorithm.
     - Convergence: No significant improvement in the loss function.


1. **Combine Trees for Final Prediction**
   - **Task**: Aggregate the outputs of all trees to produce the final prediction.
   - **Why**: Each tree contributes to the final result, creating an ensemble effect.

---


### Custom Azure Machine Learning algorithm

If you have a custom Microsoft Azure Machine Learning algorithm that you want to use with your forecasting models, you can use it in Demand planning.
