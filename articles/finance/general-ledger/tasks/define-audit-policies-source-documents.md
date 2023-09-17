--- 
# required metadata 
 
title: Define audit policies for source documents
description: This article explains how to set up and run audit policy rules. 
author: panolte
ms.date: 08/20/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysPolicySourceDocumentRuleType, SysFieldLookUp, SysPolicyListPage, SysPolicy, AuditPolicyRule, SysQueryForm, SysQueryFieldLookUp, AuditPolicyDateSelection, AuditPolicyAdditionalOption, BatchJob, CaseDetail   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Define audit policies for source documents

[!include [banner](../../includes/banner.md)]

This article explains how to set up and run audit policy rules. The example uses expense reports with the hotel expense type. This procedure uses the USMF demo company. The auditor role contains the correct permissions in order to perform these tasks.

1. In the navigation pane, go to **Modules > Audit workbench > Setup > Policy rule type**.
2. Select **New**.
3. In the **Rule name** field, type a value.
4. In the **Description** field, type a value.
5. In the **Query name** field, select **Expense report line**
6. In the **query type** field, select **Aggregate**
7. In the **Legal entity** field, select **Legal entity**
8. In the **Document date reference** field, select **Modified date and time**
9. Select **Save**.
10. In the navigation pane, go to **Modules > Audit workbench > Setup > Audit policies**.
11. Select **New**.
12. In the **Name** field, type a value.
13. Expand the **Policy organizations** section.
14. In the tree, select **Contoso Entertainment System USA**, then select **Add**.
15. In the tree, select **Contoso Consulting USA**, then select **Add**.
16. In the tree, select **Contoso Retail USA**, then select **Add**.
17. Collapse the **Policy organizations** section.
18. Expand the **Policy rules** section.
19. In the list, find and select the Policy Rule that was created previously.
20. Select **Create policy rule**.
21. In the **Effective date** field, enter a date and time.
22. Select **Filter**.
23. In the list, select the row for **Expense category**, and set the details to **Hotel**.
24. In the **Criteria** field, enter or select a value.
25. Select the **Aggregate** tab.
26. Select **Add**.
27. In the list, select a field value of **Transaction amount**.
28. In the **Field** field, enter or select a value.
29. In the **AggregateFunction** field, select **Sum**.
30. Select the **Group by** tab.
31. Select **Add**.
32. In the list, select a value of **Employee** .
33. Select **Add**.
34. In the list, select a value of **Expense category**.
35. In the **Field** field, enter or select a value.
36. Select the **Having** tab.
37. Select **Add**.
38. Select **Transaction amount**.
39. In the **Field** field, enter or select a value.
40. In the **AggregateFunction** field, select **Sum**.
41. In the **Criteria** field, type `>2000`.
42. Select **OK**.
43. Select **Test**.
44. In the **Document selection starting date** field, enter a date and time.
45. In the **Document selection ending date** field, enter a date and time.
46. Select **Run test**.
47. On the Action Pane, select **Audit policy**.
48. Select **Additional options**.
49. In the **Starting date** field, enter a date and time.
50. In the **Ending date** field, enter a date and time.
51. Select **Batch**.
52. Expand the **Run in the background** section.
53. Select **Yes** in the **Batch processing** field.
54. Select **OK**.
55. In the navigation pane, go to **Modules > Audit workbench > Audit cases**.
56. In the list, find and select the desired record.
57. Expand the **Associations** section.
58. In the list, find and select the desired record.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
