# Create and manage transformation profiles

Each time your organization requires a new type of data transformation, a manager or admin must create a new transformation profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a transformation profile, follow these steps:

1.  On the navigation pane, select **Data Creation &gt; Transformation**.

2.  On the Action Pane, select **New**.

3.  A setup wizard launches, open to the **Get started** page. Make the following settings:

    - **Name** – Enter a name for the new profile.

    - **Description** – Enter a short description of the profile.

    - **Owner** – Select the user account that owns the profile.

    - **Time Bucket** – Specify the time span by which data should summed in the time series output by this profile (*Daily*, *Weekly*, or*Monthly*). A shorter time bucket results in more data points along the X-axis. Choose the level of granularity that meets your needs.

4.  Select **Next**.

5.  The **Configure transformation** page opens. This is where you will select a table and then map the columns of that table, and its related tables, to transform the data into a timeline.

    -   The grid shows a row for each column output by the transformation.

    -   Buttons on the toolbar let you add new columns, remove a column selected in the grid, or reset the grid entirely.

    -   You can only select a single main table at a time. If you need to change the main table, then you must reset the grid.

6.  To select the main table and/or add or remove columns for the main table and related tables Select **Add column** from the toolbar. The **Add columns to your transformation dialog** opens.

7.  If no main table has been selected yet, then select one from the **Tables** drop-down list. (If you need to change the main table, you must first reset the entire transform by selecting **Reset**.)

8.  To add a data column to the transformation, select a table in the left column of the dialog, then in the middle column, select the name of the data column from that table that you want to add. For more information about how these various types of columns are used, see the introduction to this article.

    -   You must have exactly one column selected under the **Timestamp** heading. This will become the X-axis of the output time series and will typically come from the main table.

    -   You must have exactly one column selected under the **Measure** heading. This will become the Y-axis of the output time series and will typically come from the main table.

    -   You must have at least one dimension column selected under the **Dimension** heading. Dimensions provide interactive parameters that let you choose which values to view in the output time series. These columns might come from the main table and/or any of the related tables.

**Note**: The order in which you add the dimension columns defines how the output time series aggregates the data.

Each time you add a data column, it's added to the list in the right column of the dialog, which lets you see your previous selections even while you explore the various tables. The order in which you selected the dimensions is reflected under the **Dimension** heading here. Select **OK** when you are done selecting data columns.

9.  The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

10. Your profile is now saved, but it hasn't run yet. If you're ready to create a time series now, then select **Run** on the Action Pane.

