---
title: Import configurations to generate documents that have application data
description: To complete the steps in this procedure, you must first complete the procedure, ""ER Create a configuration provider and mark it as active"".
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Import configurations to generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, "ER Create a configuration provider and mark it as active".

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document. In this procedure, you import the required ER configurations that are created for the sample company, Litware, Inc., and use them to generate electronic documents. This procedure is created for users with the assigned role of system administrator or electronic reporting developer. You can complete these steps by using the DEMF dataset. Before you begin, download and save the files listed in the Help article, "Generate electronic documents and update application data with ER tool" (generate-electronic-documents-update-application-data/). The files are Intrastat (model).xml, Intrastat (mapping).xml, and Intrastat (format).xml.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure, Create a configuration provider and mark it as active.  
    * The steps in this procedure show how to use ER capabilities to complete an application data update and how to generate an Intrastat report. The details of the reporting process are archived in the application tables. Currently, when you activate the Intrastat reporting process from the Intrastat form, archiving is done based on the logic programmed in the existing source code. In this procedure, you configure a similar yet simplified logic of application data by using only the ER framework. You make no changes to the source code.

## Import ER configurations

1. Select **Reporting configurations**.
1. Select **Exchange**.
1. Select **Load from XML file**.
    * Import the ER model configuration that contains the data model designed to be used as the data source for generating the Intrastat report. Later, you can extend this data model definition to use it for an application data update to archive details of the Intrastat reporting process.
    * Select **Browse** and select the Intrastat (model).xml file.  
1. Select **OK**.
1. In the tree, select **Intrastat (model)**.
1. Select **Designer**.
1. In the tree, expand **For outgoing document**.
1. In the tree, expand **For outgoing document\Transactions**.
    * Review the structure of the imported data model. The root item **For outgoing document** specifies the data flow for getting data from the application and using it as the data source to generate the Intrastat report. The **Transactions (Record list)** represents the list of Intrastat transactions that you must report. Because you archive reported commodity codes, the unique identifier of a single commodity code **Commodity rec id (Int64)** is needed in this data flow.
1. Close the page.
1. Select **Exchange**.
1. Select **Load from XML file**.
    * Import the ER mapping configuration that specifies the data flow for getting data from the application and then using it to generate the Intrastat report. Later, you can extend this model mapping definition to get data from the Intrastat report and use it for the application data update to archive details of Intrastat reporting process.
    * Select **Browse** and select the Intrastat (mapping).xml file.  
1. Select **OK**.
1. In the tree, expand **Intrastat (model)**.
1. In the tree, select **Intrastat (model)\Intrastat (mapping)**.
1. Select **Designer**.
    * The current model mapping contains the value **To model** in the Direction field. This value means that this model mapping is designed for getting data from the application and storing it in the data model.  
1. Select **Designer**.
1. In the tree, expand **List**.
1. In the tree, expand **Transactions= List**.
    * Review the structure of the model mapping that uses the data model filtered based on the root item, **For outgoing document**. The added data source, **List** provides access to the required application data, which is the list of records from the Intrastat table.  
1. Close the page.
1. Close the page.
1. Select **Exchange**.
1. Select **Load from XML file**.
    * Import the ER format configuration that specifies the layout of the Intrastat report and the process of populating data to the report. Later, you can extend this format definition to put data from the Intrastat report into the data model and then use it to update application data to archive the details of Intrastat reporting process.
    * Click Browse and select the Intrastat (format).xml file.  
1. Select **OK**.
1. In the tree, select 'Intrastat (model)\Intrastat (format)'.
1. Select **Designer**.
1. Click Expand/collapse.
1. In the tree, select 'File\Declaration'.
1. Click the Mapping tab.
1. In the tree, select 'File'.
    * Review the structure of the format used to generate the Intrastat report. Note that it is designed to generate an XML file by populating data from the data model, which is based on the root item 'For outgoing document'. Verify that the name for generated file is defined on the user dialog form ('fn' data source is used for that).
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
