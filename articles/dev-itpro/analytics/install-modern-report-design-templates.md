---
# required metadata

title: Install report design templates
description: This topic describes how to install the modern report design templates in the application suite. You can use these samples to create graphically rich business documents that have flexible header and footer branding.
author: tjvass
manager: AnnBe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 82783
ms.assetid: 96676acf-a86b-4296-81db-b6ad6b4a46fb
ms.search.region: Global

# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Install report design templates

[!include[banner](../includes/banner.md)]


This topic describes how to install the modern report design templates in the application suite. You can use these samples to create graphically rich business documents that have flexible header and footer branding.

Introduction
------------

This topic introduces a new set of developer tools that take the form of report designs for several core business documents in the application suite. These report designs have been re-imagined so that flexible branding in the header and footer is rendered for publicly facing documents when transactions are generated in Microsoft Dynamics 365 for Finance and Operations. The following illustration shows how a legacy design for a sales invoice differs from a modern sales invoice. [![Examples of a legacy design for a sales invoice and a modern sales invoice](./media/design-comparison-1024x653.png)](./media/design-comparison.png)

After completing this installation, you'll be able to use the built-in Brand Management tools **[Organization administration > Setup > Document branding > Branding details]** to define brand settings that can applied to the modern designs for application business documents. 

## Why aren't these designs the default designs for the application suite reports?
There are two primary reasons why we are maintaining the legacy solutions for Finance and Operations:

-   **Modern designs don't include code.** Although the legacy solutions use embedded Microsoft Visual Basic (VB) code to recognize configuration keys and honor regulatory requirements that vary by region, the modern designs offer much less flexibility. The benefit of a simple design that has minimal code behind it comes at the expense of reusability across regions.
-   **Modern designs aren't available for all business documents.** There is a gap between supported business documents and the availability of a modern design. Although the legacy designs aren't as aesthetically pleasing, they provide a sense of consistency.

**Important:** These simple modern designs are **not** recommended for all types of deployments. They are intended for cases where the customer doesn't require run-time control over the layout of the document through existing application configuration settings.

## Apply the modern designs
The report designs have been bundled into a model file and posted to Microsoft Dynamics Lifecycle Services (LCS), so that you can easily access them from your existing subscription. Use the following procedure to obtain the report design solutions and install them in your local development environment. After you've installed them, you must apply some customizations to incorporate the new report designs for the appropriate scenarios. Follow these steps to install the modern report designs for the application suite.

1.  Download the ApplicationSuiteModernDesigns model file from the **Shared asset library** page on LCS. Sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/) to access the deployment dashboard, and then save the model file to a location that is accessible from the development environment. [![ApplicationSuiteModernDesigns model file](./media/lcs-shared-asset-library-1024x489.png)](./media/lcs-shared-asset-library.png)
**Note:** be sure to select the Model file appropriate for the version of the Application you're using.

2.  Import the model file into your local development environment. To install a model file in a Finance and Operations development environment, use the ModelUtil.exe tool and the **-import** directive. Here is an example.

        ModelUtil.exe -import -metadatastorepath=[path of the metadata store] -file=[full path of the file to import]

3.  Navigate to the **J:\AOSService\PackagesLocalDirectory\bin** folder.
4.  Run the following command.

        ModelUtil.exe -import -metadatastorepath=J:\AOSService\PackagesLocalDirectory -file="E:\Test\AppSuiteModernDesigns.axmodel"

    For more information about how to import model files, see [Distribution of models: How to export and import a model](..\dev-tools\models-export-import.md). After you've imported the model file, start Microsoft Visual Studio 2015 to verify that the new collection appears under the **AOT** node in Application Explorer. [![New collection under the AOT node](./media/imported-model-file-1024x488.png)](./media/imported-model-file.png)

Now that you have successfully imported the Application Suite Modern Designs model, you'll need to rebuild the Application Suite to refresh the meta data elements.

## Build the Application Suite 
The Application Suite Modern Designs model is an extension of the Application Suite model.  To ensure that all application references are updated to target the model extensions, you'll need to build the Application Suite model using Visual Studio.

1.  Open Visual Studio 2015 or use the existing instance
2.  Open the **Dynamics 365** menu and select **Build models…**
3.  Select the **ApplicationSuite** package from the list
[![Model Build dialog provided in Visual Studio 2015](./media/BuildAppSuite.png)](./media/BuildAppSuite.png)
    **Note:**  you'll notice that the Application Suite Modern Designs is included in the package definition
4.  Click on the **Build** button to perform a Full build of the Application Suite

This process may take up to 20 minutes depending on the size of your machine.  Consider grabbing a cup of coffee and some air before returning to complete the process.

## Deploy the modern designs (1Box Environments)
Once you have successfully compiled the Application Suite that includes the Modern Design templates you'll want to verify the changes locally.  To do this, you'll need to deploy the new Modern report design solutions to the SQL Report Services (SSRS) instance running locally.

Follow these steps to incorporate the modern report design into an existing application suite report: 
1. Create a project that contains the application suite report.  Expand the **Reports/Reports** collection in the Application Explorer under the **Application Suite Modern Designs** model, **select the items** in the folder, **right + click**, and select **Add to new project**.  Here's a screen shot of the project creation gesture in Visual Studio 2015
[![User gesture for creating Visual Studio Project](./media/DeployModernDesigns.png)](./media/DeployModernDesigns.png)
2. Complete the **New Project** wizard accepting all default values
3. Select the project in the **Solution Explorer**, **right + click**, and select **Deploy reports** to deploy the build and deploy the reports locally
	
By adding the modern report design to the existing report, you can reuse both the parameter handling and the data provider that the out-of-box solution uses.

## Update Print Management settings
At this point, you should be able to access the modern report designs from the application. Be sure to perform thorough test validations on these design templates before you deploy to production environments.  To do this, you'll need to **Activate the Modern Designs for the Application Business Process**.  

Use the following steps to update the Print Management settings for **Customer Sales Orders** by selecting the Modern solution as the default report design.  
 
1.  Access the Form setup form for the module **[AR > Setup > Forms > Form Setup]**
2.  Click on **Print management** button to access the Print Management Settings form 
3.  Expand the tree and locate the settings for the **Sales order confirmation** document
4.  Select **Original <Default>** to begin modifying the default document routing 
5.  Expand the drop-down under the **Report format**
6.  Select **SalesConfirmModern.Report** to enable the modern solution
[![Print Management settings form used to select the modern design](./media/UpdatePrintMgtSettings.png)](./media/UpdatePrintMgtSettings.png)
7.  Navigate to another form (this forces a “save” operation)
8.  Now, go and post a **Sales Order** to view the modern design in the application




