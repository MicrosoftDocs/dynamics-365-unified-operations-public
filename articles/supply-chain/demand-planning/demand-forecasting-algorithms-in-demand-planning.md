# Demand forecasting algorithms in Demand planning

Demand planning includes three popular demand forecasting algorithms: *auto-ARIMA*, *ETS*, and*prophet*. Choosing the right demand forecasting algorithm depends on the specific characteristics of your historical data. auto-ARIMA shines when data follows stable patterns, ETS is a versatile choice for data with trends or seasonality, and Prophet excels with complex, real-world data. By understanding these algorithms and their strengths, you can make informed decisions to optimize your supply chain and meet customer demand.

This section describes how each of these algorithms works and their suitability for various types of historical demand data.

## Auto-ARIMA – The time traveler's delight

The auto-ARIMA algorithm is like a time traveler, taking you on a journey through past demand patterns to make informed predictions about the future. At its core, auto-ARIMA uses a technique called ARIMA (autoregressive integrated moving average), which combines three key components: autoregression, differencing, and moving averages.

Auto-ARIMA automatically identifies the best combination of these components to create a forecast model that fits your data like a glove. It works particularly well with time series data that exhibits a stable pattern over time, such as seasonal fluctuations or trends. If your historical demand follows a reasonably consistent path, auto-ARIMA might be your go-to forecasting method.

## ETS – The shape shifter

ETS (error, trend, seasonality) is a versatile demand forecasting algorithm that adapts to the shape of your data. Like a chameleon, it can change its approach based on the characteristics of your historical demand, making it suitable for a wide range of scenarios.

ETS decomposes the time series data into three essential components: error, trend, and seasonality. By understanding and modeling these components, ETS generates forecasts that capture the underlying patterns in your data. ETS works best with data that exhibits clear seasonal patterns, trends, or both, making it an excellent choice for businesses with seasonally affected products or services.

## Prophet – The visionary forecasting guru

Developed by Facebook's research team, Prophet is a modern and flexible forecasting algorithm that can handle the challenges of real-world data. It has a knack for dealing with missing values, outliers, and complex patterns, making it a visionary guru in the realm of demand forecasting.

Prophet works by decomposing the time series data into several components, such as trend, seasonality, and holidays, and fitting a model to each component. This approach allows Prophet to accurately capture the nuances in your data and produce reliable forecasts. Prophet is ideal for businesses with irregular demand patterns, frequent outliers, or those affected by special events like holidays or promotions.

## Best fit model

It uses machine learning to find out which is the model that fits best for your data, for each product and dimensions combination. This way, different products could have different models used.

## Use your custom Azure machine learning model

If you have already setup your Azure machine learning for Dynamics 365 Supply Chain Management

Explain how to create and manage these.

Define all fields.

