---
title: Use tax calculation in sales quotation in Brazil tax reform
description: Learn how to calculate taxes in sales quotations using the Brazil tax reform solution
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use tax calculation in sales quotation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to calculate taxes in sales quotations using the Brazil tax reform solution.

## Create a sales quotation with Brazilian taxes

Create a quotation by specifying fiscal information like the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a quotation line, select a CFOP code in the **CFOP** field. The CFOP codes available in this field depend on the fiscal establishment of the site selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules maintained in Global studio. 

To create a sales quotation that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Sales and marketing** > **Sales quotations** > **All quotations**.
1. Select **New**.
1. In the **Account type** field, select an option.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. Select **Yes**.
1. In the **Lines or header** field, select an option.
1. In the **Final user** field, select **Yes** if all lines from the quotation are for a final user. If you select **Yes**, the Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) tax includes the Imposto Sobre Produtos Industrializados (IPI) tax and any freight charges.  
1. In the **Item** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
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
1. Select **sales tax** in the **Quotation** tab.
   - The targeted tax codes are displayed during the transition period.
   - **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from Brazilian government.
1. Expand the **Line details** section, then select the **Setup** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**, **IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
1. Select **Total** in the **Sales quotation** tab.
   - You can view the summary by tax type for Brazilian tax.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
