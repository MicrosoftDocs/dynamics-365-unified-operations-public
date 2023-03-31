---
title: Design configurations to generate documents that have application data
description: This article describes how to design Electronic reporting (ER) configurations to generate an electronic document. (Part 1 - Import configurations).
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
# Design configurations to generate documents that have application data

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, ER Generate documents with application data update (Part 1: Import configurations).



The steps in this procedure explain how to design Electronic reporting (ER) configurations to generate an electronic document. In this procedure, you run the ER imported format configuration that has been created for the sample company, Litware, Inc. to generate electronic documents.



This procedure is created for users with the assigned role of system administrator or electronic reporting developer. These steps can be completed using the DEMF dataset. 



Before you begin, change the country context for the DEMF company from DEU (Germany) to BEL (Belgium). Click Organization administration > Organizations > Legal entities to update the country code in the primary address of the legal entity DEMF. Restart your application.


## Run imported ER format
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Intrastat (model)'.
3. In the tree, select 'Intrastat (model)\Intrastat (format)'.
4. Click Run.
    * Run the draft version of the ER format configuration to generate the Intrastat report.  
5. In the Enter file name field, type 'intrastat.xml'.
    * Specify the name of the file.  
6. Click OK.
    * Review the generated XML file.  
7. Close the page.
8. Go to Tax > Declarations > Foreign trade > Intrastat.
    * Open this form to view the Intrastat transactions that are included in the generated electronic document.  
9. Click Intrastat archive.
    * Because the executed ER format does not contain any settings for application data update, the details of the completed Intrastat report have not been archived.  
10. Close the page.
11. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
