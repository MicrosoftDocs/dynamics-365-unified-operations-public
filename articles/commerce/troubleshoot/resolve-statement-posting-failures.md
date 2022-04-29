---
# required metadata

title: Resolve statement posting failures
description: This topic provides troubleshooting guidance that can help resolve failures during statement posting process
author: Frank-Zhang
ms.date: 04/29/2022
ms.topic: Troubleshooting
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: fangzhan
ms.search.validFrom: 2022-04-29
ms.dyn365.ops.version: 10.0.28

---

# Resolve statement posting failures

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when facing statement posting failures.

## Error-based troubleshooting

If an error that occurs doesn't appear in the following table, create a support request, as required, so that Microsoft Support can help you fix the issue. This topic is focused on issues that you can work on directly, without the help of Microsoft Support.


| Error | Description |
|-------|-------------|
| You receive the following error message: "While processing the state Customer order invoiced, generic exception encountered in retail statement XXX in the controller : Posting Posting Sales order: XXX Item: XXX Size=XX,Style=XX Inventory is closed for physical and financial transactions until MM/dd/yyyy. Posting Posting Sales order: XXX Item: XXX Size=XX,Style=XX Update has been canceled." | As the error message indicated "Inventory is closed for physical and financial transactions until MM/dd/yyyy", you have to modify the business date of the problematic transaction either before or after the inventory closing period. Specifically, you need to clear the statement first, then leverage [edit and audit](https://docs.microsoft.com/en-us/dynamics365/commerce/edit-cash-trans) functionality to modify the business date of the problematic transaction then repost the statement.|


## Additional resources

- [Edit and audit cash and carry and cash management transactions](https://docs.microsoft.com/en-us/dynamics365/commerce/edit-cash-trans)
- [Create an Excel workbook to edit retail transactions](https://docs.microsoft.com/en-us/dynamics365/commerce/create-excel-edit)
- [Validate store transactions for statement calculation](https://docs.microsoft.com/en-us/dynamics365/commerce/valid-checker)
