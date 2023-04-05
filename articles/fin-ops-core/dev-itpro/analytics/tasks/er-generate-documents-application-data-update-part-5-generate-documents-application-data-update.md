---
title: Generate documents that have application data
description: To complete the steps in this procedure, you must first complete the procedure, ""ER Generate documents with application data update (Part 4 - Modify format)"".
author: kfend
ms.date: 06/19/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, "ER Generate documents with application data update (Part 4: Modify format)".



The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document and update application data. In this procedure, you execute the ER format configuration to generate the Intrastat report and update application data for archiving details of the reporting process.



This procedure is created for users with the assigned role of system administrator or electronic reporting developer. These steps can be completed using the DEMF dataset. Before you begin, make sure that the country context for the DEMF company is BEL (Belgium).


## Set up foreign trade parameters
1. Go to Tax > Setup > Foreign trade > Foreign trade parameters.
2. Click the Number sequences tab.

    Archiving details of Intrastat reporting process, we need to identify records of each archive we created. A special number sequence must be configured for that.  

3. Select the 'Intrastat archive ID' reference.
4. In the Number sequence code field, type a value.

    In the 'Number sequence code' field, enter or select the value 'Fore_2'.  

5. ResolveChanges the Number sequence code.
6. Click Save.
7. Close the page.

## Run modified ER format
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Intrastat (model)'.
3. In the tree, select 'Intrastat (model)\Intrastat (format)'.
4. Click Run.
5. In the Enter file name field, type 'intrastat2.xml'.
6. Click OK.

## Review ER format execution's results
Review the generated XML file.  
1. Close the page.
2. Go to Tax > Declarations > Foreign trade > Intrastat.

    Open this form containing Intrastat transactions that have been included to the generated electronic document.  

3. Click Intrastat archive.

    Since the executed ER format contains now settings for application data update, the details of the completed Intrastat reporting have been archived. In this form, you can see the header record of the created archive.  

4. Click Details.

    In this form, you can see the details for the created archive.  

5. Close the page.
6. Close the page.
7. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
