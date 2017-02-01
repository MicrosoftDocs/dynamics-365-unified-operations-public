---
# required metadata

title: Author and distribute Power BI reports with Entity store | Microsoft Docs
description: This topic walks you through the process of authoring and publishing Power BI reports with Entity store. 
author: sericks007
manager: AnnBe
ms.date: 2017-01-05 15:20:29
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 71
ms.suite: Released- Dynamics AX platform update 1
# ms.tgt_pltfrm: 
ms.custom: 265864
ms.assetid: 2e77a3c5-1d71-4193-bd9f-031330e5e4d2
ms.region: Global
# ms.industry: 
ms.author: milindav

---

# Author and distribute Power BI reports with Entity store

This topic walks you through the process of authoring and publishing Power BI reports with Entity store. 

Create reports on the Power BI desktop
--------------------------------------

If you are a power user or a business analyst, you probably create many reports for your users. Perhaps you create them in Microsoft Excel: exporting data to an Excel file, formatting and relating data, and then creating a report or a chart before you email it to users. Your users probably come back to you if they need to make a modification to the report (and yes, you may be very busy with a queue of requests waiting in your inbox; so let’s get to the point quickly). We want to help you by providing an easy way to author rich, interactive reports. As a report writer, you could use Power BI desktop as the reporting tool and the reports you create can be published to PowerBI.com. You can read more about Power BI desktop in [Create stunning reports and visualizations with Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop). In the Dynamics AX 7.0  release (February 2016), you could author Power BI reports by using OData end points that are exposed via data entities (both aggregate data entities as well as “detailed” or “regular” data entities). Although this approach is still supported, with Entity store, power users or business analysts can create reports using the DirectQuery option enabled for SQL server databases. This approach yields several benefits:

-   You can leverage Power BI DirectQuery capabilities and author reports that execute directly on the Entity store database. DirectQuery-based Power BI reports reflect live data in the Entity store.
-   You have the ability to author Power BI reports over larger data volumes than what was possible with OData.

Using Power BI desktop, you could create a report in your development or test environment by connecting directly to Entity store. When you are satisfied with the report you can migrate this report to your production environment with the help of your administrator. Let’s see how this is done. First, let’s stage the **RetailCube** aggregate measurement into the Entity store. Launch Microsoft Dynamics 365 for Operations client (Platform update 1 or later) and navigate to the **Entity store** form. Select **RetailCube** aggregate measurement, and then select the **Refresh** button on the menu. Provide a name for the job that will be run in the background. [![retail-cube-refresh](./media/retail-cube-refresh-1024x548.jpg)](./media/retail-cube-refresh.jpg) You can monitor the progress of the job used to stage the data using the batch job monitoring form (**System administration** &gt; **Database** &gt; **batch jobs**). After the data is populated into the Entity store (it should take a minute or so with demo data), you are ready to write reports. Launch Power BI desktop, if needed, you may need to download Power BI desktop and apply updates. You will notice a welcome page, as shown below. Select the **Get data** icon. [![POwerBI Desktop launch](https://msdnshared.blob.core.windows.net/media/2016/06/POwerBI-Desktop-launch-300x159.png)](https://msdnshared.blob.core.windows.net/media/2016/06/POwerBI-Desktop-launch.png) Alternatively, when Power BI desktop launches, you can select **Get Data** &gt; **SQL Server** from the menu. [![POwerBI desktop SQL connection](https://msdnshared.blob.core.windows.net/media/2016/06/POwerBI-desktop-SQL-connection-e1466658910508.png)](https://msdnshared.blob.core.windows.net/media/2016/06/POwerBI-desktop-SQL-connection-e1466658910508.png) In the **SQL Server Database** dialog box, enter the server name and the name of the Entity store database. If you deployed a developer environment and you're working on the same machine, you can enter “**.**” as server name and **AxDW** as the database name. If you are working on a test environment, you need to obtain these parameters from your system administrator. ![SQL database direct connection](https://msdnshared.blob.core.windows.net/media/2016/06/SQL-database-direct-connection1.png) Select the **DirectQuery** option. In this example, you will create Power BI reports that are executed directly on the Entity store. If you had used the **Import** option, Power BI would cache data from the Entity store and you would need to periodically refresh the Power BI model. We don’t support Import mode with Entity store at this point in time. Select the **OK** button. Next you will see the **Navigator** dialog box. Navigator enables you to select tables and views from the Entity store that you want to report on. Enter **Retail** in the Search box, as shown below. The system will filter entities that are related to the **RetailCube** aggregate measurement that you staged previously. Select the **RetailCube\_RetailTransDetailsView** table shown in the navigator, and then select the **Load** button. You are now ready to author a report. You can drag and drop measures and fields into the canvas and explore data and trends interactively. Power BI desktop also supports creating calculations and lets you combine data from multiple aggregate measurements. In a few minutes you should be able to create a report with the data available in development environment, as shown below. First, you need to save the report as a PBIX file. [![PBI Desktop report](https://msdnshared.blob.core.windows.net/media/2016/06/PBI-Desktop-report-1024x623.png)](https://msdnshared.blob.core.windows.net/media/2016/06/PBI-Desktop-report.png) After you review the report, you can migrate it to the production environment so that your users can use this report to interact with production data.

## Validate reports in a demo environment
You can validate the report using Power BI desktop as a first step. The report is shown with the demo or test data in your developer environment. You can continue to publish this report to your PowerBI.com account and pin it to the Dynamics 365 for Operations client if you want to integrate the report into a demo environment. If you want to preview this report with demo data, see the "Publish a report from your demo environment to your PowerBI.com account" section in [Power BI content in LCS from Microsoft and your partners](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/power-bi-content-microsoft-partners).

Publish reports into production
===============================

As you may have guessed, this step requires an administrator. You must send your PBIX file to the administrator, so the administrator can upload the report to Lifecycle Services (LCS) as an implementation asset. You can also upload the report to an LCS project and share it with an administrator for publishing to production. This is the same process adopted for migrating Dynamics 365 for Operations artifacts from developer environments into production – so you can follow the process that is used by your organization.

## Upload reports to Lifecycle Services
Dynamics Lifecycle Services (LCS) is the tool used to migrate development artifacts from developer to production environments. LCS supports migrating PBIX files (DirectQuery reports authored using Entity store) between environments. Launch LCS ([http://lcs.dynamics.com](http://lcs.dynamics.com/)) from the developer environment. If you haven’t created a project in the LCS environment, create a project. Scroll to the right and select the **Asset library** icon. [![LCS Asset Library screen](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-screen-1024x560.png)](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-screen.png) Notice that the Asset library lets you add **Power BI report models** (PBIX files) as implementation artifacts to a project. [![LCS Asset Library - assets page](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-assets-page-1024x528.png)](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-assets-page.png) Select the **+** icon to add a new asset. Provide a file name and description. Select the **Upload** button and locate the file that you saved in the earlier step. [![LCS Asset Library - upload new PBIX file](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-upload-new-PBIX-file1-1024x571.png)](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-upload-new-PBIX-file1.png) After successful upload, select **Confirm**. Notice that the selected file is uploaded into LCS as an implementation asset. LCS supports managing versions and releases for Power BI reports. You can maintain several versions and publish reports to other environments as you would in case of any other implementation artifact. Because you added the PBIX files as an asset within an LCS project, Dynamics 365 for Operations environments deployed using that project have access to this report. Optionally, you can publish this report so that all your projects can access the shared assets. If you are a Microsoft partner or an ISV, and want to share this report with your customers, you can share this asset to your global library and enable your customers to import the asset into their respective LCS projects. To do this, select the **Save to my library** option. [![LCS Asset Library - share the asset](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-share-the-asset-1024x568.png)](https://msdnshared.blob.core.windows.net/media/2016/06/LCS-Asset-Library-share-the-asset.png)

## Deploy the report into production
Your administrator should associate your environment with an LCS project so that Dynamics 365 for Operations is able to consume assets within the project. It’s very likely that this step has already been performed in your production environment. Launch the client from the environment that you want to deploy the Power BI reports. Typically this is the test or a production instance where you want to see your report with a different set of data than the ones you worked with as a business analyst. Go to the** System parameters** form. Select the **Help** tab. Using the **Lifecycle Services help configuration** list box, select the LCS project that you uploaded the PBIX file. Select the **Save** button. **Note:** This form will only show the LCS projects where the current user has access to. If this step is being performed by an administrator, either the administrator needs to have access to the project, or the PBIX artifacts need to be imported into a project that the administrator has access to. On the client, select **System Administration** &gt; **Setup** &gt; **Deploy Power BI**. You will see the file that you uploaded into LCS. [![deploy-powerbi-files-form-with-all-reports](./media/deploy-powerbi-files-form-with-all-reports-1024x573.jpg)](./media/deploy-powerbi-files-form-with-all-reports.jpg) Select the **Sales Report** file, and then select the **Deploy Power BI files** option on the menu. **Note:** You may be asked to consent publishing to PowerBI.com service. Click the link to provide consent. When consent is complete, you need to go back to the original browser window and select the **Close** button. After successful publishing, the Power BI report will appear in your own PowerBI.com subscription. You will notice that the report now points to the Entity store in the production environment.

## Partners and ISVs can distribute Power BI reports as LCS solution assets
In the previous section, you uploaded the PBIX file into LCS to migrate from the developer environment to the production environment. Because Power BI reports (PBIX files) are recognized as implementation assets within LCS, you can bundle Power BI reports with other solution assets. If you are working for a partner or an ISV, this provides you with the following opportunities:

-   You can ship Power BI reports with your ISV solution that includes models, demo data, etc. You can “wow” your users with rich, interactive reports that are shipped as part of your solution.
-   You can ship reports “out of band” with your solution. Because PBIX files are stand-alone implementation assets, you can continue to ship reports as regular updates to your customers – get feedback and continue to improve them. Developing reports is easy (as you have seen above), so you can iterate quickly
-   You can also build and share customized Power BI reports with specific customers – as you always have.


