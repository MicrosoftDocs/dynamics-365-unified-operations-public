--- 
title: MY-00005 Print GST tax invoices
description: Learn how to print a GST tax invoice for Malaysia in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak 
audience: Application User  
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxGroupLookup, TaxTmpWorkTrans, SalesEditLines,  SrsReportViewerForm, CustFree**Invoice**, CustTableLookup, DimensionLookup, CustPost**Invoice**Job, SRSPrintDestinationSettingsForm  
ms.custom: 
  - bap-template
---

# MY-00005 Print GST tax invoices

[!include [banner](../../includes/banner.md)]

This article explains how to print a GST tax invoice for Malaysia in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to print a GST tax invoice. The procedures use the MYMF demo data company.

Before you can complete the procedures, you must select the **GST invoice** invoice type in general ledger parameters, and also select the **MYMF** legal entity. The accounts receivable clerk role is required for these procedures.

## Print a GST invoice

To print a GST invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Expand or collapse the **General** section.
1. In the **Site** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Warehouse** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**. The ****Invoice** type** field has the default value of **GST invoice**.  
1. Expand or collapse the Financial dimensions section.
1. In the **BusinessUnit** field, enter a value.
1. In the Department field, enter a value.
1. Select **Save**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Line view**.
1. In the list, mark the selected row.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Unit price** field, enter a number.
1. Expand or collapse the **Line details** section.
1. Select the **Setup** tab.
1. In the ****Sales tax** group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Sell**.
1. Select **Sales tax**.
1. Validate the calculated sales tax.  
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Expand or collapse the **Parameters** section.
1. In the **Quantity** field, select an option.
1. Select or clear the **Print invoice** checkbox.
1. Select **OK**.
1. Select **Yes**.
1. In the **ISO** field, enter a value.
1. Select **OK**.
1. Validate the printed tax invoice report, which contains a GST summary section with GST code, amount origin, quantity, and GST amount.     
1. Close the page.

## Print a GST invoice report

To print a GST invoice report, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. Validate that the **Invoice** type is **GST invoice**.  
1. Expand or collapse the **Financial dimensions** section.
1. In the **BusinessUnit** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Department** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Line view**.
1. In the list, mark the selected row.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter a value.
1. In the ****Sales tax** group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Unit price** field, enter a number.
1. Select **Save**.
1. Select **Sales tax**.
1. Validate the calculated sales tax.  
1. Select **OK**.
1. Select **Post**.
1. Select or clear the **Print invoice** checkbox.
1. Select **OK**.
1. Select **OK**.
1. In the **ISO** field, enter a value.
1. Select **OK**.
1. Validate the printed tax invoice report, which contains a GST summary section with GST code, amount origin, and GST amount.    
1. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
