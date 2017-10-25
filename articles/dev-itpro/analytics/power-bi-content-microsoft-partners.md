---
# required metadata

title: Power BI content in LCS from Microsoft and your partners
description: This topic explains how to find and install Power BI content that is distributed by the Finance and Operations team and your partners via Lifecycle Services (LCS). 
author: MilindaV2
manager: AnnBe
ms.date: 09/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 265674
ms.assetid: 246a113f-fbc0-4fee-b07e-793938a4a22a
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Power BI content in LCS from Microsoft and your partners

[!include[banner](../includes/banner.md)]


This topic explains how to find and install Power BI content that is distributed by the Finance and Operations team and your partners via Lifecycle Services (LCS). 

Access Power BI content
-----------------------

If you've read the [Authoring and distributing Power BI reports](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/) blog post, you know that Microsoft Power BI content from the Microsoft Dynamics 365 for Finance and Operations team is available in Microsoft Dynamics Lifecycle Services (LCS). Power BI content is released as global implementation assets. Open LCS at [https://lcs.dynamics.com](https://lcs.dynamics.com/), and go to the Shared asset library. In the Shared asset library, you will see a list of assets that are available to all LCS projects. Select **Power BI report model** as the asset type to see a list of Power BI content. The files in this list are the Power BI content that is published by Microsoft and that has a scope of **Global**.

[![Power BI report model files in the Shared asset library](https://msdnshared.blob.core.windows.net/media/2016/12/LCS-asset-library-List-of-PowerBI-reports-1024x598.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/LCS-asset-library-List-of-PowerBI-reports.jpg) 

Select a file in the library by clicking it. You can then immediately download the file that contains the reports. The file that you download is a PBIX file. This file type is the same type that you create by using Microsoft Power BI desktop, if you create files yourself as explained in the [Authoring and distributing Power BI reports](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/) blog post. 

Click **Save**. You can find the reports in the Downloads folder on your computer. If you're a report author who has access to a demo or developer instance of Finance and Operations, you can open these reports by using the Power BI Desktop tool.

## Power BI content that is developed by your partner
Power BI content that is released by Microsoft is shared as global assets in the Shared asset library in LCS. In addition, your partner or independent software vendor (ISV) may ship Power BI content in an LCS project and share that project with you. 

You can access reports that have been shared with you at a project level. In LCS, open your LCS project. (Ideally, you should open the project that you provisioned your developer environment of Finance and Operations with. Otherwise, create a new LCS project.) Click the **Asset library** tile, and then select **Power BI report model** as the asset type. You will see the Power BI content that your partner has shared with your project. 

[![Power BI content that your partner has shared with your project](https://msdnshared.blob.core.windows.net/media/2016/12/Project-scoped-PowerBI-assets-1024x573.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/Project-scoped-PowerBI-assets.jpg) 

You can save a copy of the shared assets into your project by clicking **Save to my library**. In addition, you can import global implementation assets (that is, Power BI content that is released by Microsoft) into your asset library. This step is important if you want to extend the reports yourself before you deploy these files to your sandbox or production environment. Click **Import**, select the file to import, and then click **Pick**. The system imports the file into your project. You should now see that the report has been copied to your project. 

[![Imported report](https://msdnshared.blob.core.windows.net/media/2016/12/Library-with-copied-reports-1024x576.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/Library-with-copied-reports.jpg)

## Download and extend readymade reports that are distributed via LCS
Next, we will examine how you can deploy the report to your demo or developer environment. You can also extend the reports that are provided by Microsoft. You can include your customizations, or you can create new pages in the same report. 

For this step, you must sign in to your demo environment as an administrator by using Remote Desktop. You must also download Power BI Desktop, which is the tool that is used to write and edit Power BI reports. 

You can download the PBIX files from the LCS project into your environment by selecting them. 

If you haven’t updated the Entity store with data, open the **Entity store** page in the Finance and Operations client. Select the aggregate measurement that contains the data that is related to the report. In a few minutes, you're ready to work with the report. (To find the aggregate measurement that was used to create the report, examine the table names. Each table name is prefixed with the name of the aggregate measurement. Alternatively, you can update all aggregate measurements.) 

The update of aggregate measurements uses the batch framework. If the update takes more than a few minutes, go to the **Batch jobs** page to view the status of bath jobs in your environment. 

You can open the PBIX files in your demo environment by double-clicking the report. If Power BI Desktop is installed on your computer, the report opens and is updated with data from your Entity store. 

If the report isn't updated, make sure that it points to the local Entity store. In Power BI Desktop, select the **Edit Queries** option on the menu, and then select the **Data Source connections** option. Select the **Data Sources in Current File** option, and provide the connection parameters to your local Entity store, as shown in the following illustration. 

[![Connection parameters](https://msdnshared.blob.core.windows.net/media/2016/12/Data-source-settings-in-PBI-desktop-1024x661.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/Data-source-settings-in-PBI-desktop.jpg) 

Click **OK**. The report should now reflect data from your local Entity store. Optionally, you can modify the report by using the capabilities of Power BI Desktop. Alternatively, you can just use this report with your Finance and Operations instance.

## Publish a report from your demo environment to your PowerBI.com account
As we discuss in the [Authoring and distributing Power BI reports](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/) blog post, if you modified the report that was released by Microsoft or your partner, you must migrate the report to your sandbox or production environment. 

However, if you want to pin this report, together with demo data, to the Finance and Operations demo environment, you must configure your demo environment by using your PowerBI.com account. In this case, the data that you see on the report will be sourced from your demo environment. However, if your intention is to try (and perhaps extend) the content that is distributed by Microsoft or your partner, this data may suffice. 

For this operation, you must open a Remote Desktop session and sign in to your demo environment. While you're signed in to your demo environment, start a web browser, and go to [http://app.powerbi.com](http://app.powerbi.com/). 

Next, you must download and configure the Data Gateway tool from the Power BI website. This report enables reports on the PowerBI.com site to access data from your demo environment. You must complete this step this only one time for your demo environment. After you complete the configuration, you can use the same gateway with all the Power BI reports that you download from LCS. 

[![Downloading the Data Gateway tool](https://msdnshared.blob.core.windows.net/media/2016/12/Download-Data-gateway-298x300.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/Download-Data-gateway.jpg) 

The process for downloading and configuring the Data Gateway tool is straightforward. For detailed instructions, see [Download and install the On-premises data gateway](https://powerbi.microsoft.com/en-us/documentation/powerbi-gateway-onprem/#download-and-install-the-on-premises-data-gateway). 

Here are some notes that you should be aware of as you configure the data gateway:

-   Select the **On premises Data gateway** option. Although you can use the **Personal gateway** option, the **On premises Data gateway** option lets you use this configuration for other products.
-   When you name the gateway, use the name of your demo environment. This approach prevents confusion, especially if you have more than one demo environment.
-   When installation is successful, you will be prompted to configure a dataset for the gateway. You will configure the Entity store, or AXDW database on your local computer, as the data source to configure for the gateway. Note the following points before you configure a data source:
    -   Name the data source **AXDW**. You can give this data source any name. However, by keeping the same name, you prevent confusion, and fewer changes are required when you publish the reports.
    -   User accounts to access AXDW: When your demo environment was provisioned, LCS assigned a set of default user accounts for the AXDW database. You can configure the data gateway with the pre-provisioned user account. Open the LCS project that was used to provision your demo environment, and find the password for the **axdwruntimeuser** user account.
    -   If other users will use the demo environment, you can assign them to the gateway. This step is a good idea, especially if the demo or developer computer is a shared computer.
-   When you've finished, you will see the gateway in Power BI administration panel. You can test the gateway to make sure that it's configured correctly.

After you've configured the gateway, you can publish the reports by using the integrated **Publish** button in Power BI Desktop. If you aren't signed in to you PowerBI.com account, you're prompted to sign in. After sign-in, the system publishes the report by using the gateway that you configured. 

[![Publishing to Power BI](https://msdnshared.blob.core.windows.net/media/2016/12/published-with-gateway-1024x736.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/published-with-gateway.jpg) 

At this point, you should see the report in your PowerBI.com account, together with other Power BI reports. You can now pin this report to the Finance and Operations client. However, you must remember that this report points to your demo data. If you want the report to reflect production data, you must migrate the PBIX artifact to sandbox and production environments, just as you migrate any other Finance and Operations artifact.

## Licensing requirements
As a report author, you can create reports by using the Entity store in Power BI Desktop. A Power BI license isn't required. In addition, report authors who have a pro or free license can publish their reports to PowerBI.com. 

To view reports that were built by using the Entity store, users must have a Power BI pro license. If you don't have a Power BI pro license, you can choose a Power BI pro trial license. All the functionality will be available to you.

## Deploy reports to a sandbox or production environment
So far, we have explained how to view Power BI reports in the demo environment. If you're in a sandbox or production environment, you can immediately deploy these Power BI reports to the environment by using functionality in Finance and Operations. (You don’t have to configure the data gateway for sandbox or production environments. In fact, you *can’t* configure the data gateway for those environments.) You must be a system administrator to perform this operation. 

The [Authoring and distributing Power BI reports](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/) blog post describes this process from the perspective of an author. We will now describe this process from the perspective of a system administrator. (The processes don't differ, but some of the pages have been updated since we wrote the blog post.) 

In Finance and Operations, go to the **Deploy Power BI files** page. 

If you haven’t previously deployed Power BI files to this environment, you receive the following message: “You must provide the LCS project ID with PowerBI assets in Life cycle services help configuration field in the System Administration &gt; System Parameters &gt; Help form.” This message indicates that you must configure your LCS project in Finance and Operations. In other words, your system isn't connected to the LCS project where you've accumulated your Power BI files. Therefore, your system can't detect any of the Power BI files in your project. 

Go to the **System parameters** page. Click the **Help** tab. If you've connected an LCS project, you will see a project ID next to the **Lifecycle Services help configuration** field. However, because your system isn't connected to an LCS project, you're prompted to connect to LCS. You must complete this operation. Otherwise, Finance and Operations can't use your user credentials to establish a trusted connection to LCS. Click the **Click here to connect to Lifecycle Services** link. If you mistakenly clicked **OK** before you clicked the link, you must reopen the page. When the connection is successful, you can select a set of LCS projects in the **Lifecycle Services help configuration** field. Select the LCS project that you used earlier. Now, go back to the **Deploy Power BI report files** page. You will now see that the Power BI files are ready for deployment to your Finance and Operations environment. 

[![Power BI files ready for deployment to your Finance and Operations environment](https://msdnshared.blob.core.windows.net/media/2016/12/Deploy-PowerBI-files-form-with-all-reports-1024x573.jpg)](https://msdnshared.blob.core.windows.net/media/2016/12/Deploy-PowerBI-files-form-with-all-reports.jpg) 

Select a file to deploy, and then click **Deploy Power BI files**. The file that you selected is deployed to your PowerBI.com account.



