---
# required metadata

title: Create a Power BI report by using Dynamics 365 for Operations data
description: This tutorial outlines the process for creating an end user–friendly data model, reports, and dashboards in the version of Power BI that is currently available from http - //app.powerbi.com.
author: sericks007
manager: AnnBe
ms.date: 2015-12-12 19 - 09 - 37
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 24531
ms.assetid: f944f045-8dd1-4b38-be17-7ce958124eeb
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Create a Power BI report by using Dynamics 365 for Operations data

This tutorial outlines the process for creating an end user–friendly data model, reports, and dashboards in the version of Power BI that is currently available from http - //app.powerbi.com.

Key concepts
------------

-   **Power BI** refers to the cloud-based analytics visualization platform that is used to extract, transform, and present data from Microsoft Dynamics 365 for Operations (together with other systems), so that users can interact with it and share it.
-   **Power Query** refers to the Microsoft Excel–based tool set for extracting and transforming data through OData feeds into an Excel-based data model that is used in Power BI reporting.
-   **Self-service BI** refers to enabling users to tweak existing analytic content and create new analytic content, such as reports, key performance indicators (KPIs), and dashboards.

## Supported platforms and environments
-   It’s a good idea to use your local desktop version of Excel to connect to the cloud instance, not Excel within the virtual machines (VMs). There is a known limitation in PowerPivot on Windows Data Center VMs.
-   PowerQuery authentication is supported completely. Earlier versions aren't registered for Microsoft Azure Active Directory authentication. Registration of the instance with Azure AD is a required step and is automated as part of the deployment process.

Microsoft Excel 2013 is required, together with PowerQuery (a post–February 2015 update of PowerQuery is required). Both 32-bit and 64-bit versions of Microsoft Office are supported, but the 64-bit version is recommended for optimal performance.

## Before you start
### Download and install PowerQuery

1.  Download PowerQuery from the following location: <http://www.microsoft.com/en-us/download/details.aspx?id=39379> **Note:** PowerQuery comes in two versions that correspond to the two versions of Excel (32-bit and 64-bit). You must find out which version of Excel you have. You must then choose and install either the 64-bit or the 32-bit versions of PowerQuery. **The 64-bit version of Excel 2013 is already installed in the developer environment.**
2.  Start Excel 2013, and verify that the **PowerQuery** tab is available.
3.  Enable the PowerPivot and PowerView add-ins.

## Verify that the data entities are available
1.  Start Internet Explorer in **InPrivate** mode, and enter the URL that is used to access your deployment. This URL will end with ".cloud.dynamics.com*." * Throughout this document, this URL will be referred to as \[baseurl\]. You will be asked to sign in on a page that resembles the following screen shot. [![PowerBI1](./media/powerbi1-1024x718.png)](./media/powerbi1.png)
2.  Enter your user credentials for access to your environment. After your credentials are authenticated, you will see the client. [![PowerBI2](./media/powerbi2-1024x553.png)](./media/powerbi2.png)
3.  To validate that data entities are exposed by using the ODatav4 endpoint, enter the following URL in the browser window: \[baseurl\]/data You will be asked whether you want to display the data in JSON format, as shown in the following screenshot. [![PowerBI3](./media/powerbi3-1024x554.png)](./media/powerbi3.png)
4.  Click **Open**. You will see the available entities in the JSON file downloaded, as shown in the following screen shot. This feed shows all the entities that have been made public from your deployment. As you develop new public entities, they will appear in this list. [![PowerBI4](./media/powerbi4-1024x616.png)](./media/powerbi4.png)

**Note:** To enable the browser to display JSON content, run the file at C:\\FMLab\\ison-ie.reg, and click **Yes** to change the registry.

## Access the OData endpoints in PowerQuery
1.  Start Excel 2013.
2.  On the **PowerQuery** tab, click **From other data sources** &gt; **From OData feed**. [![PowerBI5](./media/powerbi5-1024x457.png)](./media/powerbi5.png)
3.  Enter the URL of the OData endpoint, as shown in the following screen shot. Note that you must append **/data** to the \[baseurl\]. (You can copy \[basurl\] from your browser window and add **/data**.) [![PowerBI6](./media/powerbi6.png)](./media/powerbi6.png)
4.  When PowerQuery requests that you authenticate the OData feed, select **Organization ID** as the authentication method, and enter the user name and password that you entered earlier. **Note:** Dynamics 365 for Operations uses Azure AD to authenticate users. When you select **Organization ID** and enter your credentials, you're authenticated against Microsoft Dynamics 365 for Operations. Therefore, you will see only data that you have access to through the security model. PowerQuery displays a list of available entities, as shown in the following screen shot. [![PowerBI7](./media/powerbi7.png)](./media/powerbi7.png)
5.  Use the **Navigator** pane to select the following entities, and then click **Load**:
    -   GeneralLedgerActivities
    -   FiscalCalendars
    -   MainAccounts

    [![PowerBI8](./media/powerbi8.png)](./media/powerbi8.png) PowerQuery will load the data into the Excel data model. Depending on the size of the data set, this step mtake some time. [![PowerBI9](./media/powerbi9.png)](./media/powerbi9.png)
6.  Double-click **MainAccounts** to load the query. [![PowerBI10](./media/powerbi10.png)](./media/powerbi10.png)
7.  You can now use PowerQuery to transform your data set. For example, you can rename columns and transform values within the data set.
    1.  On the **Home** tab, click **Choose Columns**, select the following fields, and then click **OK**:
        -   AccountCategoryDescription
        -   MainAccountCategory
        -   MainAccountID
        -   MainAccountRecID
        -   Type
        -   Name

    2.  To rename columns to make them more readable (for example, by adding spaces), double-click the column header.
        -   AccountCategoryDescription &gt; Account Category Description
        -   MainAccountCategory &gt; Main Account Category
        -   MainAccountID &gt; Main Account ID

    3.  Click **Close & Load**.

8.  Optional: You can now repeat this process for the other queries to guarantee that there is a clean data set within the data model.

## Data model optimization
In this section, we will review the Excel data model to optimize our data for reports and PowerBI Q&A.

1.  On the **PowerPivot** tab, click **Manage Data Model**.
2.  On the **Design** tab, click **Manage Relationships** to create the relationships between the three entities.
    1.  Click **Create**, and select **GeneralLedgerActivites** as Table 1 and **MainAccounts** as Table2.
    2.  Select **MainAccountRecID** as the field for both tables.
    3.  Click **OK**.
    4.  Repeat steps 1 through 3, selecting **GeneralLedgerActivities** as Table 1, **FiscalCalendars** as Table 2, and **LedgerGregorianDateID** as the field for both tables.

    You should now have two relationships that join your three entities. [![PowerBI11](./media/powerbi11.png)](./media/powerbi11.png)**Note:** Depending on your version of Office, this form might appear slightly different.
3.  Close the **Manage Relationships** form.
4.  You can now hide fields that are used only for calculations or relationships from the end user.
    1.  On the **GeneralLedgerActivities** tab, right-click the **MainAccountRecID** column, and then select **Hide from Client Tools**.
    2.  Repeat step 1 across all entities for fields that should not be shown to the end user.

5.  To make sure that values are presented correctly, set the data type and format for all fields.
    1.  Select the **Expenses** column, and set the data type and format to **Decimal Number**.
    2.  Repeat step 1 across all fields to improve the presentation in visualizations and Power Q&A. [![PowerBI12](./media/powerbi12.png)](./media/powerbi12.png)

6.  You can now add a calculated measure that can be used in your reports.
    1.  Click in a cell in the **Measure** pane at the bottom of the PowerPivot window, enter the following formula, and then press Return.

        > Total Expenses this year: =calculate(sum(\[Expenses\]),'FiscalCalendars'\[YearOffset\]=0)

    2.  Click in the cell below the previous cell, and enter the following formula.

        > Total Expenses last year: =calculate(sum(\[Expenses\]),'FiscalCalendars'\[YearOffset\]=-1)

        **Note:** These formulas use the DAX language. They will sum the **Expenses** column but apply a filter to your fiscal calendars on the year offset. A year offset of 0 indicates the current financial year, whereas a year offset of -1 indicates the last financial year. Year offsets let users take advantage of their custom Microsoft Dynamics 365 for Operations fiscal calendars in Power BI. [![PowerBI13](./media/powerbi13.png)](./media/powerbi13.png)

    3.  Click each of the new measures, and set the format to **Decimal Number**.

7.  Close the PowerPivot data model.

## Optional: Additional data model optimization
At this point, you can use the Excel PowerPivot data model to optimize your data, so that it includes additional measures that can be used in your visualizations. Here are just some of these additional optimizations:

-   Additional calculated measures
    -   New calculations
    -   This year/last year measures
-   Synonyms for column names
-   Optimization for default field sets, and so on

## Create a report by using PowerView
In this section you will create a basic report by using PowerView.

1.  On the **Insert** tab, click **PowerView**. Excel will load a blank PowerView report. You will see your three entities in the **Power View Fields** pane on the right side.
2.  Expand **GeneralLedgerActivites**, and click **Total Expense this year**. PowerView adds the field to a table on the report.
3.  Click in the table, and then, on the **Design** tab, click **Column Chart** &gt; **Stacked Column Chart** to change the table to a column chart.
4.  You can now customize the column chart:
    1.  To resize the column chart, drag the corners. Expand the chart until it to take up two-thirds of your report. [![PowerBI14](./media/powerbi14-1024x645.png)](./media/powerbi14.png)
    2.  To add some more detail to the chart, select the following fields in the **Power View Fields** pane:
        -   FiscalCalendars - Quarters
        -   FiscalCalendars - PeriodName
        -   MainAccounts - Main Account Category

    3.  You will notice that the fields on the chart aren't presented the way that you expected. To fix this, drag the fields to the correct axis and legend areas.
        1.  Drag **PeriodName** to the **AXIS** area underneath **Quarter**.
        2.  Drag **Main Account Category** to the **Legend** area. **Note:** As you add fields from the three entities, you wil notice that all three are presented in a single visualization. This is possible because of the relationships that you set up in the PowerPivot data model earlier in this tutorial. [![PowerBI15](./media/powerbi15.png)](./media/powerbi15.png)

5.  You can now drill into the first quarter by double-clicking the **Q1** column. [![PowerBI16](./media/powerbi16.png)](./media/powerbi16.png)
6.  Specify a title for your report by clicking **Click here to add a title** and entering a name.
7.  Save your Excel workbook to your local machine or your Microsoft OneDrive library.

## Upload the Excel worksheet to PowerBI.com
In this section, you will create a dashboard by using the data model that you created in PowerQuery.

1.  In a browser, go to [http://app.PowerBI.com](http://app.powerbi.com/).
2.  Sign in by using the same credentials that you used to access Dynamics 365 for Operations.
3.  Create a new dashboard by click the plus sign (+) next to **Dashboards**. Enter a suitable name. A blank dashboard that resembles the following screen shot will appear.[![PowerBI17](./media/powerbi17.png)](./media/powerbi17.png)
4.  Click **Get data** to import data into the dashboard. A page that resembles the following screen shot will open. [![PowerBI18](./media/powerbi18-1024x448.png)](./media/powerbi18.png)
5.  In the left pane, click **Excel Workbook**, and then click **Connect**. In the **File picker** dialog box, click **Browse** to select the Excel model that you saved in previous section. Then click **Connect**. [![PowerBI19](./media/powerbi19-1024x490.png)](./media/powerbi19.png) A blank chart icon appears on the dashboard to indicate that the data is available. [![PowerBI20](./media/powerbi20-1024x451.png)](./media/powerbi20.png)
6.  Click the blank chart icon. The PowerView report that you authored earlier is displayed. You can author additional reports and pin them to the dashboard by using PowerBI.com functionality. [![PowerBI21](./media/powerbi21-1024x395.png)](./media/powerbi21.png)
7.  Click the chart, and then click the pushpin button in the upper-right corner to pin the report to your dashboard. [![PowerBI22](./media/powerbi22.png)](./media/powerbi22.png)
8.  In the navigation pane on the left side of the page, click the name of your dashboard. You are returned to your dashboard, which now displays your chart. [![PowerBI23](./media/powerbi23.png)](./media/powerbi23.png)


