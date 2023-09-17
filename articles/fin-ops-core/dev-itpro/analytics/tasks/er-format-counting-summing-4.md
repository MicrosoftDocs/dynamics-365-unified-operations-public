---
title: ER Configure format to do counting and summing (Part 4 - Run format)
description: This article describes how to configure an Electronic reporting format to do counting and summing based on data of the already generated text output. (Part 4)
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, IntrastatParameters, Intrastat, InventItemIdLookupSimple, IntrastatCommodityLookup, ERFormatMappingRunLogTable, DocuView
---
# ER Configure format to do counting and summing (Part 4 - Run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to do counting and summing based on data of the already generated text output. These steps can be performed in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Configure format to do counting and summing (Part 3: Use computations to make the output)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Test this configuration for generation of the Intrastat reports
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Intrastat model'.
4. In the tree, expand 'Intrastat model\Intrastat (DE)'.
5. In the tree, select 'Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing'.
6. On the Action Pane, click Configurations.
7. Click User parameters.
8. Select Yes in the Run settings field.
9. Click OK.
10. Click Edit.
11. Select Yes in the Run Draft field.
12. Click Save.
13. Go to Tax > Setup > Foreign trade > Foreign trade parameters.
14. Expand the Electronic reporting section.
15. Select the "Intrastat (DE) with counting & summing" configuration.
16. Select the "Intrastat (DE) with counting & summing" configuration.
17. Click Save.
18. Close the page.
19. Go to Tax > Declarations > Foreign trade > Intrastat.
20. Click Output.
21. Click Report.
    * Run the Intrastat report generation process.  
22. In the From date field, set the date to '2000-01-01'.
    * Define start and end dates for the reporting period that include the existing on the form transactions.  
23. In the To date field, set the date to '2022-12-31'.
    * Define start and end dates for the reporting period that include the existing on the form transactions.  
24. In the Direction field, select 'Arrivals'.
25. Select Yes in the Generate file field.
26. Click OK.
    * Review the created output with the summary lines in the end.  
27. Click New.
28. In the list, mark the selected row.
29. In the Direction field, select 'Dispatches'.
30. In the Item number field, enter or select a value.
31. In the Commodity field, enter or select a value.
32. Set Weight to '10'.
33. Set Invoice amount to '10000'.
34. Set Statistical amount to '10000'.
35. Click Output.
36. Click Report.
37. In the Direction field, select 'Dispatches'.
38. Click OK.
    * Review the created output with the summary lines in the end. Note that it has been changed in comparison to the first run.  

## Run this configuration in debug mode to review the collected counting & summing data
1. Go to Organization administration > Electronic reporting > Configurations.
2. In the tree, expand 'Intrastat model'.
3. In the tree, expand 'Intrastat model\Intrastat (DE)'.
4. In the tree, select 'Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing'.
5. On the Action Pane, click Configurations.
6. Click User parameters.
7. Select Yes in the Run in debug mode field.
8. Click OK.
9. Close the page.
10. Go to Tax > Declarations > Foreign trade > Intrastat.
11. Click Output.
12. Click Report.
13. Click OK.
14. Close the page.
15. Go to Organization administration > Electronic reporting > Configurations.
16. In the tree, expand 'Intrastat model'.
17. In the tree, expand 'Intrastat model\Intrastat (DE)'.
18. In the tree, select 'Intrastat model\Intrastat (DE)\Intrastat (DE) with counting & summing'.
19. Click Debug logs.
    * Note that a debug log record has been created for the execution process of the selected configuration.  
20. Click Attach.
21. Click Open.
    * Review the created XML file that contains counting and summing details that were collected during the execution of the selected configuration.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
