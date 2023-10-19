# View and run existing transformation profiles

You only need to run a transformation profile as often as you import new data into the relevant tables. Some profiles will only need to be run occasionally, while others might be run nearly every time a user works with the app.

To refresh your time series by running an existing transformation profile, follow these steps:

1.  On the navigation pane, select **Data Creation &gt; Transformations**.

2.  Find the profile for the type of transformation you want to run and select the link in its **Name** column.

3.  The detail page opens for your selected profile. It provides the following tabs:

    - **Summary** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with. You can also change the **Owner** and adjust the **Time Bucket** but usually you shouldn't change these for existing profiles. See [Create a transformation profile](create-and-manage-transformation-profiles.md) for more information about these settings.

    - **Transformations** – Shows details about the transformation that the profile will process. See [Create a transformation profile](create-and-manage-transformation-profiles.md) for more information about these settings.

    - **Jobs** – Shows a list of each time the profile was run, include date information, job status, and the times series that was updated. Select the link in the **Time Series** column to open the time series.

4.  To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab, where you can follow the status of the new transformation. The page doesn't refresh automatically, so you must select **Refresh** in the grid toolbar to refresh the status information.

