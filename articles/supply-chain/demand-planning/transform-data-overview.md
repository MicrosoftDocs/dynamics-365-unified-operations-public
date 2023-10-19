# Transform data overview

Transformations allow you to change the input data so it can be used as a time series, basis for creating a forecast or as data to be compared to the forecast.

For example, you may want to time shift the historical demand time from last year by 12 months so it can be used as the base for the forecast for next year. Or you may want to combine the historical demand data that is daily into monthly buckets as your planning will happen on a monthly basis.

Note that the output of a transformation is a Time series, that follows the aggregation and data rules based on the selections followed.

The Demand planning app lets you build a collection of *transformation profiles*, each of which transforms data from a specific data table already set up in the app into a time series that you can analyze using the app.

Each transformation profile takes a selected [main table](#_Set_up_tables) as its input, and that main table could have other tables related to it.

-   The main table typically represents historical demand, such as sales orders.

-   The main table must include a *timestamp* column, which will become the X-axis of the output time series. This will typically be the order date or delivery date.

-   The main table must include a *measure* column, which will become the Y-axis of the output time series. This will typically represent units sold.

-   Either the main table or one of its related tables must include at least one dimension column. Often you'll select more than one dimension because that will let you analyze the data in several ways. For example, if you are looking at T-shirts, you might include dimensions for color dimension, size, style, and warehouse. These dimensions would allow you to view the output time series to see, for example, the historical demand for red, extra-large T-shirts sold from the Chicago warehouse and compare that with the overall sales of all T-shirts from all warehouses.

Typically, a manager or system administrator will create the initial collection required profiles and, after that, forecasters and other users will be able to run the profiles to update the time series as needed.

