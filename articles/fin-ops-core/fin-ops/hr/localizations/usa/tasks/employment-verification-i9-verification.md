--- 
title: Employment verification i9 verification
description: Learn about the Immigration Reform and Control Act, which requires US employers to verify the employment eligibility status of newly hired employees. 
author: ShielaSogge
ms.author: shielas
ms.topic: how-to
ms.date: 01/10/2022
ms.custom:
ms.reviewer: twheeloc  
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: HcmWorker, HcmPersonIdentificationNumber, Hcmi9Document  
ms.dyn365.ops.version: Version 7.0.0
---

# Employment verification i9 verification

[!include [banner](../../../../includes/banner.md)]

The Immigration Reform and Control Act requires US employers to verify the employment eligibility status of newly hired employees. This procedure will walk you through the steps of recording the necessary documents for I-9 verification. Use the USMF company for this procedure.

1. Go to **Human resources \> Workers \> Employees**.
2. Use the Quick Filter to find records. For example, filter on a value of **Vince** for the **Name** field.
3. Select the employee. For example, select **Vince Prado**.
4. Select the **Personal information** FastTab.
5. Select **Identification numbers**.
6. Select **New**.
7. Select the identification type that you're recording. For example, select **Passport**.
8. In the **Number** field, enter a value.
9. In the **Primary** field, select **Yes**.
10. In the **Description** field, enter a brief description of the identification record.
11. In the **Issuing agency** field, select the agency that issued the form of identification to the worker. For example, select **Government**.
12. Enter the date when the issuing agency issued the form of identification to the worker. For example, enter **02/15/2011** (February 15, 2011).
13. Enter the date when the form of identification expires. For example, enter **2/15/2021** (February 15, 2021).
14. Select **Save**.
15. Close the page.
16. Select the **Employment** tab.
17. Select **I-9**.
18. Select **New**.
19. In the **Work eligibility** field, select an option.

    If the employee isn't a citizen or national of the United States, you must enter the worker's resident alien or admission number.

20. Select the **GroupListA** option.

    The list that you select depends on the form of identification that the worker provided. A worker must provide either one document from List A or one document from both List B and List C. For example, if the worker provided a passport, you can select List A. However, if the worker provided only a driver's license and Social Security card, you must select List B and List C.

21. In the **I-9 document type** field, select the type of document that the worker provided.
22. In the **Document number** field, enter or select a value.
23. Select **Save**.

[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
