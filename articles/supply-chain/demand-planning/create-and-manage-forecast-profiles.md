# Create and manage forecast profiles

Each time your organization requires a new type of forecast, a manager or admin must create a new forecast profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a forecast profile, follow these steps:

1.  On the navigation pane, select **Forecasts &gt; Forecast Profiles**.

2.  On the Action Pane, select **New**.

3.  A setup wizard launches, open to the **Get started** page. Make the following settings:

    - **Name** – Enter a name for the new profile.

    - **Description** – Enter a short description of the profile.

    - **Owner** – Select the user account that owns the profile.

4.  Select **Next**.

5.  The **Set horizon and time buckets** page opens. Make the following settings:

    - **Time bucket** – Select the granularity (bucket size) at which the forecast should be made (daily, weekly, or monthly).

    - **Horizon in time buckets** – Enter the number of buckets to include in the forecast.

6.  Select **Next**.

7.  The **Select input data source** page opens. Use this page to choose which time series to use as input for your forecast. You must selected exactly one time series.

    -   The **Available** tab shows the full list of available time series. To add a times series to the forecast, select its name in the grid and then select **Include data source** from the toolbar. By default, the most recent version of the time series will be used, but you can select older versions by going to the **Included** tab.

    -   The **Included** tab shows the time series selected for use with this forecast. If more than one version is available, select the version you want to use from the **Output version** drop-down list.

8.  When you're done selecting the input time series, select **Next.**

9.  The **Select a forecasting model preset** page opens. Here, you can select a forecast model preset to use with your current profile. Browse the various presets listed under the **Available model presets** heading to see a preview of the forecast made by that preset. You'll be able to make settings and customize the forecast model as needed after you save the profile, so just pick the preset that's closest to what you're looking for and then select **Next**. For details about how to make settings and customize the forecast model used by a profile, and how to create new presets, see [Designing forecast models](designing-forecast-models.md).

10. The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

11. Your profile is now saved, but it hasn't run yet. If you're ready to run the forecast now, then select **Run** on the Action Pane.

