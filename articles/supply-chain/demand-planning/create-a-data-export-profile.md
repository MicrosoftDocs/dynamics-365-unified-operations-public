# Create a data export profile

Follow these steps to create a new data export profile:

   

1.  Navigate to **Data Providers &gt; Export** in the site map.

<!-- -->

2.  Click button **New**.

<!-- -->

3.  Provide a **Name**. 

<!-- -->

4.  Provide a **Description.** 

<!-- -->

5.  Click **Next**.

<!-- -->

6.  Select data provider **Microsoft finance and operations apps** 

<!-- -->

7.  Click **Next.** 

<!-- -->

8.  Provide **Connection** **URL** of the Supply Chain Management instance.  

<!-- -->

9.  Click **Next.**

Note: System will validate the URL and authentication

10. Select correct **Time series.**  

<!-- -->

11. Click **Include data source**.

 

Note: You can select the specific version you want to export

You can only select one time series for export in each Export data profile.

You can create many Export data profiles that connect to the same Microsoft finance and operations app URL if needed.

  

12. Select **Time series**.

<!-- -->

13. Click **Filter data source**.

<!-- -->

14. Click **Next**.

Note: You can filter the data source on the data source. This means that you will only export a filtered portion of data from the selected time series

In addition, an export provider can only export to one legal entity. Therefore, If the time series has legal entity as a dimension, then a legal entity filter must be setup, and multiple providers need to be created – one per legal entity with appropriate filters.

This is a temporary limitation that will be overcome later with more advanced export rules (see step 6 below).

15. Map columns of Time series to Microsoft finance and operations apps data schema   

<!-- -->

16. Click  **Next** 

 

Note: Number of columns in time series are dynamic so users must perform the mapping.

The entity for Microsoft finance and operations apps data schema  is fixed. This will be changed so a custom entity can be selected. This will be required if you have customized Supply Chain Management.

17. Provide a **Company** 

<!-- -->

18. Provide a **Forecast Model ID**   

<!-- -->

19. Click  **Next** 

 

Note: Export rules determines where the exported data will be imported in Supply Chain Management. As of now this has to be Text provided by the user and match values of Supply Chain Management.

For now, a single rule can be created moving all data to designated Company and Forecast model ID can be made.

In a future release you will be able to export filtered portions of a time series to specific companies in Supply Chain Management.

Review the settings

20. Click **Review And Finish**  

A record in Export Data Profile has been created.

21. Click on button **Run** to trigger export job 

The data is exported and transformed based on the rule defined. The transformation will add Company **USMF** and Forecast model ID **CurrentF** to all the lines. Then these will be imported and inserted into Table **Demand Forecast** and visible in Form **Demand forecast lines**

 

Supply Chain Management

22. Navigate to **Master planning &gt; Forecasting &gt; Manual forecast entry &gt; Demand forecast lines** in site map 

<!-- -->

23. Click button **New** 
