# View and run existing forecast profiles

To generate a new forecast by running an existing forecast profile, follow these steps:

1.  On the navigation pane, select **Forecasts &gt; Forecast Profiles**.

2.  Find the profile for the type of forecast you want to run and select the link in its **Name** column.

3.  The detail page opens for your selected profile. It provides the following tabs:

    - **Summary** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with.

    - **Horizon and time buckets** – Shows the granularity (bucket size) at which the forecast will be made (daily, weekly, or monthly) and the number of buckets that will be included in the forecast. You can modify the selections as needed. See the next section for details about how to work with these settings.

    - **Input data** – Shows the full list of available time series and indicates which of these are used by the selected profile. You can modify the selections as needed. See the next section for details about how to work with these settings.

    - **Forecast model** – Shows the forecast calculation made by the profile using a flowchart with interconnected tiles. Each tile does a specific type of operation and has settings that let you define how that operation works. See the next section for details about how to work with these settings.

    - **Jobs** – Shows a history of each time the profile was run, include date information, job status, and the times series that was generated. Select a link in the **Time Series** column to open that time series.

4.  To run the profile, select **Run** on the Action Pane.

5.  A dialog opens. Set **Output option** to one of the following values:

    -   *Create a new time series*: The job will create a new time series. Enter a name for the new series in the**Time series name** field.

    -   *Use an existing time series*: The job will overwrite or create a new version of an existing series. Use the settings provided to choose the target series, whether to overwrite or create a new version, and what thew new version should be called (if you choose to create one).

6.  Select **Save and close**.

7.  The new job is added to the grid on the **Jobs** tab, where you can follow the status of the new calculation. Select **Refresh** in the grid toolbar to refresh the status information.

