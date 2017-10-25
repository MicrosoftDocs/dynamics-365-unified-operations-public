--- 
# required metadata 
 
title: Import configurations to generate documents with application data update for electronic reporting (ER)
description: To complete the steps in this procedure, you must first complete the procedure, “ER Create a configuration provider and mark it as active”. 
author: NickSelin
manager: AnnBe 
ms.date: 06/19/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Import configurations to generate documents with application data update for electronic reporting (ER)

[!include[task guide banner](../../includes/task-guide-banner.md)]

To complete the steps in this procedure, you must first complete the procedure, “ER Create a configuration provider and mark it as active”.

The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document. In this procedure, you will import the required ER configurations that have been created for the sample company, Litware, Inc. and use them to generate electronic documents. This procedure is created for users with the assigned role of system administrator or electronic reporting developer. These steps can be completed using the DEMF dataset. Before you begin, download and save the files listed in the Help topic, “Generate electronic documents and update application data with ER tool” (generate-electronic-documents-update-application-data/). The files are Intrastat (model).xml, Intrastat (mapping).xml, and Intrastat (format).xml.

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don’t see this configuration provider, complete the steps in the procedure, Create a configuration provider and mark it as active.  
    * The steps in this procedure show how to use ER capabilities to complete an application data update and how to generate a Intrastat report. The details of the reporting process are archived in the application tables. Currently, when the Intrastat reporting process is activated from the Intrastat form, archiving is done based on the logic programmed in the existing source code. In this procedure, you will configure a similar yet simplified logic of application data using only the ER framework. No changes will be made to the source code.   

## Import ER configurations
1. Click Reporting configurations.
2. Click Exchange.
3. Click Load from XML file.
    * Import the ER model configuration that contains the data model that is designed to be used as the data source for generating the Intrastat report. Later, you will extend this data model definition to use it for an application data update to archive details of the Intrastat reporting process.   
    * Click Browse and select the Intrastat (model).xml file.  
4. Click OK.
5. In the tree, select 'Intrastat (model)'.
6. Click Designer.
7. In the tree, expand 'For outgoing document'.
8. In the tree, expand 'For outgoing document\Transactions'.
    * Review the structure of the imported data model. Note that the root item ‘For outgoing document’ is defined to specify the data flow for getting data from the application and using it as data source to generate the Intrastat report. The ‘Transactions (Record list)’ is used to represent the list of Intrastat transactions that must be reported. Because you will archive reported commodity codes, the unique identifier of a single commodity code ‘Commodity rec id (Int64)’ is needed in this data flow.   
9. Close the page.
10. Click Exchange.
11. Click Load from XML file.
    * Import the ER mapping configuration that specifies the data flow for getting data from the application and then using it to generate the Intrastat report. Later, you will extend this model mapping definition to get data from the Intrastat report and use it for the application data update to archive details of Intrastat reporting process.   
    * Click Browse and select the Intrastat (mapping).xml file.  
12. Click OK.
13. In the tree, expand 'Intrastat (model)'.
14. In the tree, select 'Intrastat (model)\Intrastat (mapping)'.
15. Click Designer.
    * Note that the current model mapping contains the value ‘To model’ in the Direction field. This means that this model mapping has been designed for getting data from the application and storing it in the data model.  
16. Click Designer.
17. In the tree, expand 'List'.
18. In the tree, expand 'Transactions= List'.
    * Review the structure of the model mapping that uses the data model that is filtered based on the root item, ‘For outgoing document.’ Note that the added data source, ‘List’ provides access to the required application data, which is the list of records from the Intrastat table.  
19. Close the page.
20. Close the page.
21. Click Exchange.
22. Click Load from XML file.
    * Import the ER format configuration that specifies the layout of the Intrastat report and the process of populating data to the report. Later, you will extend this format definition to put data from the Intrastat report in to the data model and then use it to update application data to archive the details of Intrastat reporting process.   
    * Click Browse and select the Intrastat (format).xml file.  
23. Click OK.
24. In the tree, select 'Intrastat (model)\Intrastat (format)'.
25. Click Designer.
26. Click Expand/collapse.
27. In the tree, select 'File\Declaration'.
28. Click the Mapping tab.
29. In the tree, select 'File'.
    * Review the structure of the format used to generate the Intrastat report. Note that it is designed to generate an XML file by populating data from the data model, which is based on the root item ‘For outgoing document’. Verify that the name for generated file is defined on the user dialog form (‘fn’ data source is used for that).   
30. Close the page.

