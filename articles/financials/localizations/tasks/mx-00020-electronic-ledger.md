--- 
# required metadata 
 
title: Produce Mexican electronic ledger accounting report version 1.1
description: This task walks through all necessary steps to configure the generation of electronic ledger accounting XML files by using the Electronic Reporting tool. 
author: sndray
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Produce Mexican electronic ledger accounting report version 1.1

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks through all necessary steps to configure the generation of electronic ledger accounting XML files by using the Electronic Reporting tool. You can import from the AX resource center the model and formats of XML files to generate the statements. 


## Import a configuration including XML formats
1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the Configuration providers list, click Set active on the Microsoft provider box.
    * If the Microsoft provider is already the active provider, you can skip this step.  
3. In the Configuration providers list, click the Repositories link on the Microsoft provider box.
4. Click Add to open the drop dialog.
5. Click Create a repository.
6. In the Name field, type a value.
7. In the Description field, type a value.
8. Click OK.
9. In the list, select the configuration that you just created.
10. On the action pane, click Open.
11. In the tree, select 'Electronic ledger accounting model MX'.
12. Click Import.
13. Click Yes.
14. In the tree, select 'Electronic ledger accounting model MX\Auxiliary Ledger XML MX'.
15. Click Import.
16. Click Yes.
17. In the tree, select 'Electronic ledger accounting model MX\Chart of Account XML MX'.
18. Click Import.
19. Click Yes.
20. In the tree, select 'Electronic ledger accounting model MX\Journals XML MX'.
21. Click Import.
22. Click Yes.
23. In the tree, select 'Electronic ledger accounting model MX\Trial Balance XML MX'.
24. Click Import.
25. Click Yes.
26. Close the page.
27. Close the page.
28. Click the Configurations box.
29. In the tree, select 'Electronic ledger accounting model MX'.
30. In the tree, expand 'In the treem expand 'Electronic ledger accoutning model MX''.
    * You will be able to see the four (4) XML formats that you previously imported.  

## Configure general ledger parameters for electronic reporting mapping
1. Go to General ledger > Ledger setup > General ledger parameters.
2. In the Trial balance field, click the drop-down button to open the lookup.
3. In the list, select the Trial Balance XML format
4. In the list, click the link in the selected row.
5. In the Auxiliary ledger field, click the drop-down button to open the lookup.
6. In the list, selecy the Auxiliary ledger XML format
7. In the Ledger entries field, click the drop-down button to open the lookup.
8. In the list, select the Journal XML format
9. In the list, click the link in the selected row.
10. In the Chart of accounts field, click the drop-down button to open the lookup.
11. In the list, select the Chart of Account XML format.
12. Click Save.

## Generate XML files
1. Go to General ledger > Inquiries and reports > Ledger reports > Electronic ledger accounting statement.
2. In the SAT consolidation account group field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Period field, enter a date.
6. Check or uncheck the Trial Balance opcion
    * This option generates the Chart of Account and Trial Balance XML files.  
7. Select or clear the Ledger entries check box.
8. Select or clear the Auxiliary ledger check box.
9. In the Request type field, select an option.
10. In the Order number field, type a value.
11. Click OK.

