# Create and manage calculation profiles

Each time your organization requires a new type of calculation, a manager or admin must create a new calculation profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a calculation profile, follow these steps:

1.  On the navigation pane, select **Data Creation &gt; Calculations**.

2.  On the Action Pane, select **New**.

3.  A setup wizard launches, open to the **Get started** page. Make the following settings:

    - **Name** – Enter a name for the new profile.

    - **Description** – Enter a short description of the profile.

    - **Owner** – Select the user account that owns the profile.

4.  Select **Next**.

5.  The **Select input data source** page opens. Use this page to choose which time series to use as input for your calculation.

    -   The **Available** tab shows the full list of available time series. To add a times series to the calculation, select its name in the grid and then select **Include data source** from the toolbar. By default, the most recent version of each time series will be used, but you can select older versions by going to the **Included** tab.

    -   The **Included** tab shows the time series that are included for this calculation in the order you added them. For time series that have more than one version available, select the version you want to use from the **Output version** drop-down list. To remove a time series, select it and then select **Remove** from the toolbar.

You can add several time series. The selection order is important because time series are assigned an index ID (shown in the **\#** column on the **Included** tab), which is referenced in the name of each input tile you add to the calculation model.

6.  When you're done selecting the input time series, select **Next.**

7.  The **Select and configure calculation model** page opens. Here, you can select a calculation model preset to use with your current profile. Browse the various presets listed under the **Available model presets** heading to see a preview of the calculation made by that preset. You'll be able to make settings and customize the calculation model however needed after you save the profile, so just pick the preset that's closest to what you're looking for and then select **Next**. For details about how to make settings and customize the calculation model used by a profile, and how to create new presets, see [Desing calculation models](designing-calculation-models.md).

8.  The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

9.  Your profile is now saved, but it hasn't run yet. If you're ready to run the calculation now, then select **Run** on the Action Pane.

