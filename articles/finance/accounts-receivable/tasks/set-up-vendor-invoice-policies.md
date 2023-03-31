--- 
# required metadata 
 
title: Set up vendor invoice policies
description: This article explains how to set up vendor invoice policies. 
author: ShivamPandey-msft
ms.date: 02/11/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendParameters,  SysPolicyListPage, SysPolicyParameters, SysPolicySourceDocumentRuleType, SysPolicy, SysPolicySourceDocumentRule, SysQueryForm, SysQueryTableLookUp, SysQueryPrefixLookUp, SysQueryFieldLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up vendor invoice policies

[!include [banner](../../includes/banner.md)]

This article explains how to set up vendor invoice policies. Vendor invoice policies are run when you post a vendor invoice by using the **Vendor invoice** page and when you open the vendor invoice **Policy violations** page. You can also configure the vendor invoice workflow to run vendor invoice policies every time that you submit an invoice to workflow. 

- Vendor invoice policies do not apply to invoices that were created in the invoice register or invoice journal.  
- Invoice matching validation does not use vendor invoice policies, but is instead set up in the **Accounts payable parameters** page.  
- This recording uses the USMF demo company. The accounts payable manager or accounting manager role would perform these steps. Before you begin, make sure that the **Invoice matching** configuration key is selected.


## Prepare to create vendor invoice policies
1. Go to **Navigation pane > Modules > Accounts payable > Setup > Accounts payable parameters**.
2. Select the **Invoice validation** tab.
3. Select or clear the **Automatically update invoice header** status check box.
4. Select **OK**.
5. In the **Post invoice with discrepancies** field, select an option.
6. Close the page.
7. Go to **Navigation pane > Modules > Accounts payable > Policy setup > Vendor invoice policies**.
8. Select **Parameters**.
9. Select **Add**.
10. Close the page to return to the home page.

## Create policy rule types for vendor invoices
1. Go to **Navigation pane > Modules > Accounts payable > Policy setup > Vendor invoice policy rule types**.
2. Select **New**.
3. In the **Rule name** and **Description** fields, type values.
4. In the **Query name** field, select the drop-down button to open the lookup, then select the desired record.
5. Select **Save**.
6. Close the page to return to the home page.

## Define a vendor invoice policy
1. Go to **Navigation pane > Modules > Accounts payable > Policy setup > Vendor invoice policies**.
2. Select **New**.
3. In the **Name** and **Description** fields, type values.
4. Expand or collapse the **Policy organizations** section.
5. In the tree, select **Contoso Entertainment System USA**.
6. Select **Add**.
7. Expand or collapse the **Policy rules** section.
8. Select **Create policy rule**.
9. In the **Policy rule description** field, type a value.
10. Select **Filter**.
11. Select **Add**. Select the desired record.
12. In the **Table**, **Derived table**, and **Field** fields, select or enter options from the drop-down menus.
13. Close the page.
14. In the **Criteria** field, type a value.
15. Select **OK**.
16. Select **OK**.
17. Close the pages to return to the home page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
