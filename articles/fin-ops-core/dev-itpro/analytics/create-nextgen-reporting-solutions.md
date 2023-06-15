---
title: Create reporting solutions
description: This tutorial shows how to create a report, expand predefined views, add navigation to charts, use the free-form report designer, and customize the parameters.
author: RichdiMSFT
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: richdi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 2e1c96f8-46c9-428e-bb3d-6791f2a954ef
---

# Create reporting solutions

[!include [banner](../includes/banner.md)]

This tutorial shows how to export data and create a report, expand predefined views and add navigation to charts, use the free-form report designer, and customize the parameter experience.

## Prerequisites

For this tutorial, you must access the application environment, and you must be provisioned as an administrator on the instance.

## Key concepts
- Describe the various ways reports can be created and consumed
- Add interactivity to embedded aggregate reports in forms and workspaces
- Use framework extensions to customize the parameter experience for SSRS based business documents
- Export List Page data to create reports with external tools including Microsoft Excel
- Author modern report designs using enhanced developer tooling in Visual Studio

## What's new in Reporting?
- Embedded report drill-through navigations to AX forms and reports
- Navigate between reports using embedded report drill-through links
- Several Document Routing Service enhancements including support for custom print settings
- Introduced Document Brand Management administrative tools
- Additional visualizations available through the Embedded Charting Control
- Dates and Amounts in the report body are formatted based on the "Date, time, and number format" user setting
- Network Print monitoring form
- Table extensions need to be supported through the VS Query picker

## What is a report in Dynamics 365 finance and operations apps?
Reports can be defined simply as any visualization of a structured data set. This may include transactional data presented in a tabular layout and advanced graphical views of aggregate information. To account for this broad definition, the application offers several tools to produce reports to satisfy complex business requirements. Some common applications of reports in an ERP include:

- Creating and archiving transactional documents as part of a posting process
- Producing packing slips for tracking orders from Manufacturing to Warehousing to Sales
- Monitoring key performance metrics and surfacing trends in data
- Navigating the client through filtered searches
- Distributing heavily branded documents to customers and employees
- Extracting data in such a way that it articulates the health of a business

The most difficult task for developers is selecting the *right* Business Intelligence visualization tool for the job, given a customer's requirements. To accomplish this, it's important to understand the capabilities offered through the tools that are available for creating reports. We offer tooling to support the following basic reporting requirements:

- **Excel Integration** – Allows data management and analysis using Microsoft Excel
- **Embedded Analytics** – Add aggregate data to a Workspaces using native controls like charts and grids
- **Reporting Services** – Create business documents that require precision using SSRS-based solutions
- **Power BI Integration** – Author and share reports that can be accessed anywhere
- **Management Reporter** – Designed to help users create financial reports

The following table can be used to compare the basic characteristics of these reporting tools:

| Tool                | Author     | Target     | Data                         | Consumption       | Designer  |
|---------------------|------------|------------|------------------------------|-------------------|-----------|
| Excel               | Power User | Power User | Transactional                | External          | Free form |
| Embedded BI         | Developer  | All users  | Aggregates                   | Internal          | Modeled   |
| SSRS Report         | Developer  | All users  | Transactional and Aggregates | Internal/External | Free form |
| Power BI            | Power User | All users  | Aggregates                   | Internal/External | Free form |
| Management Reporter | Power User | Power User | Transactional                | External          | Modeled   |

## Create a report using List Pages
In this section, we'll walk you through the process of exporting data displayed in an entity details form. Here we'll demonstrate how every form in can be viewed as a source of data for management and analysis using the power of Excel.

### Create an analysis report based on all rentals in Fleet Management that are marked as complete

1. Open Internet Explorer, and navigate to your instance base URL and sign in.

    1. On the cloud environment, the base URL is obtained from LCS
    2. On a local VM, the base URL is `https://usnconeboxax1aos.cloud.onebox.dynamics.com`.

2. On the Dashboard, scroll to the far right, and click the **Reservation management** tile.
3. Under the **Summary** section, click on the **All rentals** tile.
4. Expand the **Filters** pane by clicking on the Filters icon next to the main grid.
5. Click **Add a filter field**, and then select **Status** in the drop-down list.
6. Enter **Complete** in the Status filter field, and then click **Apply**.
7. Expand the page action bar, click **Open in Office**, and then select **Rentals**.

    [![FMRentals export.](./media/fmrentals-export.png)](./media/fmrentals-export.png) 

    After the data has been exported, you can use the power and flexibility of the Excel tools to create reports for presentation or additional analysis. The following is an example of a self-service report authored with Excel.

    [![FMRentals analysis.](./media/fmrentals-analysis-1024x775.png)](./media/fmrentals-analysis.png)

8. Close the browser session and the exported Excel file.

### Advantages of List Pages

- Flexible source for accessing transactional business data using external reporting and analytical tools like Excel
- Allows end-users to model the data sets they need without requiring a developer
- Direct access to real-time business information

## Expand predefined views and add navigation to charts
Business Intelligence can be useful at every level of an organization. Use embedded controls to elevate the most relevant information based on the target persona. Native controls offer users an intuitive and convenient way of interacting with aggregate data allowing for informed decision making.

### Create development project

1. On the Desktop, right-click the **Visual Studio** shortcut, and select **Run as administrator** to open the development environment.
2. On the toolbar, click **View**, and then select **Application Explorer**
3. Use the **Application Explorer** to search for the **FMReservationsReport** form in the **Fleet Management** module.
4. In the **Application Explorer's** search results, right-click **FMReservationsReport** form, and then select **Add to new project**.
5. Select the **finance and operations Project** template, and then click **OK** to create the project.
6. In **Solution Explorer**, right-click **FMReservationsReport** menu item, and then select **Set as startup object.**
7. Press Ctrl+Shift+B to save and build the project.
8. Press Ctrl+F5 to load the form containing the report.

    [![FMCustomer activity.](./media/fmcustomer-activity-300x224.png)](./media/fmcustomer-activity.png) 

At this point, you have a collection of pre-defined chart visualizations of Aggregate data. The controls offer basic interactive features like hover text, series filtering, and touch expansion. However, it is often appropriate that a greater degree of user interactivity is required.

### Change the default chart type for the visualization

1. Close the browser session and return to the Visual Studio project.
2. Open the **Application Explorer**, locate the **FMReservationsByCustPart** form, right-click, and then select **Add to project**.
3. Open the **FMReservationsByCustPart** form designer.
4. Access the **Series** collection in the **ReservationsByCust** chart definition.
5. Select the **SysBuildChatMeasure1** series definition
6. Locate the **Appearance** section in the **Properties** window.
7. Update the **Chart type** value and select **Pie**
8. Press Ctrl+Shift+B to save and rebuild the project.
9. Press Ctrl+F5 to run the report.

The **Reservations by customer** view now visualizes the aggregate data set using a Pie chart to simplify the task of comparing rental activity across customers. 

[![FMCustomer activity 2.](./media/fmcustomer-activity-2-1024x733.png)](./media/fmcustomer-activity-2.png) 

Additional functions include:

- Define contextual drill-through navigations using modeled properties
- Manage drill-through links using X++ form logic

### Advantages of embedded aggregate visualizations

- Designed to be simple and intuitive to promote informed decisions at every level of the organization
- Pre-defined views tailored to meet the needs of the consumer
- Augments the user's ability to recognize key performance trends in the data

## Using the freeform report designer
SSRS continues to be the platform for producing advanced Business Document solutions for your ERP application. The hosted service is designed for high volume and heavily transactional reports with an integrated parameter experience. Backed by the Document Printing & Distribution Services, these solutions are ideal for producing precision documents which are intended for email, printing, archive, and bulk distribution.

### Open the Precision Designer

1. Close the browser session and return to the Visual Studio project.
2. Click **File** &gt; **Close Solution**, to close the active project.
3. Use the **Application Explorer** to search for objects with **FMRentalsByCust** in the name
4. In the **Application Explorer's** search results, select all **Classes**, the **Output Menu Item**, and the **FMRentalsByCustomer** report
5. Right-click and then select **Add to new project**.
6. Select the **Dynamics 365** template, and then click **OK** to create the project.
7. In **Solution Explorer**, double-click on the **FMRentalsByCustomer** report to open the designer.
8. Expand the **Designs** collection in the designer to view the list of design definitions
9. Double-click on the **Report** design to view the report definition using the Precision Designer

[![Report designer.](./media/report-designer-1024x665.png)](./media/report-designer.png) 

The above is a screen-shot of the FMRentalsByCustomer report design definition as viewed using the Visual Studio Precision Designer. The Precision Designer offers a free-form design surface with built-in tools that allow you to customize the content and layout of the report. You can also take advantage of embedded VB code to create run-time design manipulations and support user interactions. As an integrated tool, developers are able to reference AX labels and public APIs to format data in the report body based on AX EDTs. MSDN offers a rich collection of developer documentation related to SSRS formatting capabilities. See the article [Reporting Services Reports (SSRS)](/sql/reporting-services/reports/reporting-services-reports-ssrs) on for a good primer on designing effective SSRS reports.

## Customizing the parameter experience
The Reporting Framework offers flexibility through service extensions to facilitate advanced solutions with requirements that cannot be addressed using a modeled solution. Use the VS designer to add basic parameter formatting, grouping, and input validation. X++ based data contract validation is available for more advanced scenarios. Consider adding User Interface (UI) Builder Classes to customize the parameter pane used to prompt for session inputs before running a report. These custom extensions are effective for addressing the following functions:

- Overriding dialog field events
- Validating report parameters inline
- Adding customized lookups to dialog fields
- Changing the layout of the dialog controls
- Adding custom controls including images

### Defining parameters defaulting using code

1. In **Solution Explorer**, double-click on the **FMRentalsByCustUIBuilder** class to open the designer.
2. Locate the class **build** method and update the initialization code as follows

    ```xpp
    public void build()
    {
        Dialog dialogLocal = this.dialog();
        contract = this.dataContractObject() as FMRentalsByCustContract;// associate dialog field with data contract method
        this.addDialogField(methodStr(FMRentalsByCustContract, parmCustGroupId), contract);dialogLocal.addGroup("@SYS41297");
        fromDateField = this.addDialogField(methodStr(FMRentalsByCustContract, parmFromDate), contract);
        toDateField = this.addDialogField(methodStr(FMRentalsByCustContract, parmToDate), contract);// set the default date range values
        fromDateField.value(today() - 365);
        toDateField.value(today());
    }
    ```

3. Press Ctrl+Shift+B to save and rebuild the project.
4. Press Ctrl+F5 to run the report.

[![FMRentalsByCust controls.](./media/fmrentalsbycust-controls-1024x691.png)](./media/fmrentalsbycust-controls.png) 

The parameter initialization code above sets the default values of the report execution relative to today's date. Use the classes UIBuilder to override the framework's default handling of report parameters. Additional extension scenarios supported:

- Automatically set query ranges based on session context using Controller classes
- Select report designs at runtime using a shared menu item
- Modify report data contract values using business logic

> [!NOTE]
> This example demonstrates a UIBuilder extension with an RDP-based based report. For a Query based example that includes a UIBuilder extension, view the **FMCustomerList** report.

## Using VB code to manage running balances
The Reporting Framework offers flexibility through service extensions to facilitate advanced solutions with requirements that cannot be addressed using a modeled solution. Use the VS designer to add basic parameter formatting, grouping, and input validation. X++ based data contract validation is available for more advanced scenarios. Consider adding User Interface (UI) Builder Classes to customize the parameter pane used to prompt for session inputs before running a report. These custom extensions are effective for addressing the following functions:

- Overriding dialog field events
- Validating report parameters inline
- Adding customized lookups to dialog fields
- Changing the layout of the dialog controls
- Adding custom controls including images

### Import the section resources

1. Close the browser session and return to the Visual Studio project.
2. On the toolbar, click **DYNAMICS AX**, and then select **Import Project…**
3. In the File name window, browse to C:\\FmLab\\Lab10-3, select **FMRentalDetailsReport.axpp**, and then click **Open**.
4. In the Project file location text box, enter C:\\FmLab\\Lab10-3.
5. Select the **Current solution** radio button.
6. Click **OK** to close. Wait for the project to be imported and opened.
7. In the **Solution Explorer**, select the new project, right-click, and then select **Set as startup project.**
8. In the **Solution Explorer**, right-click **FMRentalDetails** menu item, and then select **Set as startup object.**
9. Select the Project in Solution Explorer, right-click, and then select **Deploy Reports**
10. Press Ctrl+F5 to view the report.

[![FMRentalDetails report.](./media/fmrentaldetails-report.png)](./media/fmrentaldetails-report.png) 

This report uses embedded VB script to keep track of running totals so that the balances from the previous page can be referenced on the active page. To inspect report's VB code, load the report design in the Precision Designer, access the **Report Properties**, and then select the **Code** section. Here you'll see several functions referenced by the report designs to surface running balances within the report headers and footers.

### Advantages of SSRS reports

- Built-in back office document management capabilities including email support, scheduled executions via Batch, and Print Archive
- Parameterized views with drill-through navigations to forms and other reports
- Used to produce precision documents for compliance with local regulatory business practices


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
