---
title: Brazilian tax in sales quotations
description: This article describes how to create a sales quotation that uses Brazilian taxes with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.search.industry: Manufacturing;Distribution;Service industries
---

# Brazilian tax in sales quotations

[!include [banner](../../includes/banner.md)]

This article describes how to create a sales quotation that uses Brazilian taxes with Microsoft Dynamics 365 Finance.

Use following procedure to create a sales quotation that uses Brazilian taxes. You can create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a quotation line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix. 

The procedure uses the BRMF demo company.

To create a sales quotation that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Sales and marketing \> Sales quotations \> All quotations**.
1. Select **New**.
1. In the **Account type** field, select an option.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. Select **Yes**.
1. In the Lines or header field, select an option.
1. Expand the **Fiscal information** section.
1. In the **Final user** field, select **Yes** if all lines from the quotation are for a final user. If you select **Yes**, the Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) tax includes the Imposto Sobre Produtos Industrializados (IPI) tax and any freight charges.  
1. In the **Lines or header** field, select an option.
1. In the list, mark the selected row.
1. In the **Item** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
1. On the Action Pane, select **Quotation**.
1. Select **Send quotation**.
1. In the **Print quotation** field, select **Yes**.
1. Select **OK**.
1. Close the page.
1. On the Action Pane, select **Follow up**.
1. Select **Confirm**.
1. Select **Yes**.
1. In the **Reason** field, enter or select a value.
1. Select the **Print confirmation** checkbox.
1. Select **OK**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
