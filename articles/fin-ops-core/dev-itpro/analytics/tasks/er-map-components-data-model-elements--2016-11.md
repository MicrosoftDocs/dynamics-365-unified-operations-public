---
title: ER Map components of the created format to data model elements (November 2016)
description: This article describes how to map data model elements to components of the created Electronic reporting (ER) configuration.
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
ms.search.form: ERWorkspace, ERSolutionTable, EROperationDesigner
---
# ER Map components of the created format to data model elements (November 2016)

[!include [banner](../../includes/banner.md)]

The following procedure shows how a user in either the System administrator or Electronic reporting developer role can map data model elements to components of the created Electronic reporting (ER) configuration, which defines an electronic document format for the payments business domain. This format will be used later to generate electronic documents for processing payments. In this example, you will create a format configuration for the sample company, 'Litware, Inc.'. These steps can be performed in any company as ER configurations are shared for all companies. To complete these steps, you must first complete the steps in the "Create a format configuration" task guide.


## Select a format configuration
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Reporting configurations.
3. In the tree, expand 'Payments (simplified model)'.
4. In the tree, select 'Payments (simplified model)\BACS (UK fictitious)'.
5. Click Designer.

## Map format components to data model elements
1. Click Expand/collapse.
2. Click the Mapping tab.
3. In the tree, expand 'model'.
4. In the tree, select 'Xml\Message\ProcessingDate\DateTime'.
5. In the tree, select 'model\ProcessingDateTime'.
6. Click Bind.
7. In the tree, select 'Xml\Message\MessageId\String'.
8. In the tree, select 'model\MessageIdentification'.
9. Click Bind.
10. In the tree, expand 'model\Payments'.
11. In the tree, select 'Xml\Message\Payments\Item\Amount\String'.
12. In the tree, select 'model\Payments\InstructedAmount'.
13. Click Bind.
14. In the tree, select 'Xml\Message\Payments\Item\TransDate\DateTime'.
15. In the tree, select 'model\Payments\TransactionDate'.
16. Click Bind.
17. In the tree, select 'Xml\Message\Payments\Item\Description\String'.
18. In the tree, select 'model\Payments\Description'.
19. Click Bind.
20. In the tree, select 'Xml\Message\Payments\Item\Currency\String'.
21. In the tree, select 'model\Payments\Currency'.
22. Click Bind.
23. In the tree, select 'Xml\Message\Payments\Item\Id'.
24. In the tree, select 'model\Payments\End2EndID'.
25. Click Bind.
26. In the tree, expand 'model\Payments\Creditor'.
27. In the tree, expand 'model\Payments\Creditor\Account'.
28. In the tree, expand 'model\Payments\Creditor\Agent'.
29. In the tree, select 'Xml\Message\Payments\Item\Vendor\Name\String'.
30. In the tree, select 'model\Payments\Creditor\Name'.
31. Click Bind.
32. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank\RoutingNumber\String'.
33. In the tree, select 'model\Payments\Creditor\Agent\RoutingNumber'.
34. Click Bind.
35. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank\AccountNumber\String'.
36. In the tree, select 'model\Payments\Creditor\Account\Number'.
37. Click Bind.
38. In the tree, select 'Xml\Message\Payments\Item\Payer\Name\String'.
39. In the tree, expand 'model\Payments\Debtor'.
40. In the tree, expand 'model\Payments\Debtor\Account'.
41. In the tree, expand 'model\Payments\Debtor\Agent'.
42. In the tree, select 'model\Payments\Debtor\Name'.
43. Click Bind.
44. In the tree, select 'Xml\Message\Payments\Item\Payer\Bank\RoutingNumber\String'.
45. In the tree, select 'model\Payments\Debtor\Agent\RoutingNumber'.
46. Click Bind.
47. In the tree, select 'Xml\Message\Payments\Item\Payer\Bank\AccountNumber\String'.
48. In the tree, select 'model\Payments\Debtor\Account\Number'.
49. Click Bind.
50. In the tree, select 'Xml\Message\Payments\Item'.
51. In the tree, select 'model\Payments'.
52. Click Bind.
53. Click Save.

## Validate format mapping
1. Click Validate.
    * Validate the new mapping to ensure that all bindings are okay.  
2. Close the page.

## Change status of the current version of format configuration
In the next steps, you'll change the status of the format configuration from Draft to Completed to make it available for payment document generation.  
1. Click Change status.
2. Click Complete.
3. In the Description field, type a value.
    * For example, 'version 1'.  
4. Click OK.
5. Select completed version of the current configuration.
    * Note that the configuration is saved as completed version 1.1: version 1 of the format based on the version 1 of the data model.  

## Define effective date for completed version of format
Each format version can be configured as available for usage starting from a certain date. When more than one format version is active on a certain date, the latest format (based on version number) will be selected for usage. The session date value is used for proper version selection.  

## Restrict access to created format from companies
1. Expand the ISO Country/region codes section.
    * Each format access can be restricted by identifying particular countries/regions in which a format is applicable. When the list of countries/regions for particular format is empty, this format can be used in any company. When some ISO country/region codes are inserted in the list of countries/regions, the format can only be use in companies if the primary address is in the country/region.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
