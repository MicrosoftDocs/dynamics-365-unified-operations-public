--- 
title: Change depreciation conventions for multiple fixed assets
description: Learn about the depreciation convention for a specified fixed asset group, including a step-by-step process of a task guide that uses the USMF demo company. 
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysQueryForm, SrsReportViewerForm
ms.dyn365.ops.version: Version 7.0.0 
---

# Change depreciation conventions for multiple fixed assets

[!include [banner](../../includes/banner.md)]

This task updates the depreciation convention for a specified fixed asset group. This task guide uses the USMF demo company.

1. Go to **Fixed assets > Periodic tasks > Mass update**.
2. In the **Depreciation book** field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the **Placed in service start** field, enter a date.
5. In the **Placed in service end** field, enter a date.
    * Only assets that are a part of the select depreciation book and that have been placed in service between these dates will be updated.  
6. In the **Current depreciation convention** field, select an option.
    * Only assets that have the current depreciation convention will be updated.  
7. In the **New depreciation convention** field, select an option.
    * Verify the report will print to the desired destination.  
8. Expand the **Records to include** section.
9. Click **Filter**.
10. In the list, select the **Fixed asset group**.
11. In the **Criteria** field, click the drop-down button to open the lookup.
12. Select the desired **Fixed asset group**.
13. In the list, click the link in the selected row.
14. Click **OK**.
15. Click **OK**.
    *  Results of the process are shown on the **Mass update** report.     



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
