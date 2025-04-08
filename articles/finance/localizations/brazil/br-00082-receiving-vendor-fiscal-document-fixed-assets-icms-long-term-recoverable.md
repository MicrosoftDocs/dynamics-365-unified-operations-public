---
title: Receive vendor fiscal documents (fixed assets - ICMS long term recoverable) (Brazil)
description: This article describes how to post a fiscal document received from the acquisition of fixed assets and then recover the ICMS taxes in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Receive vendor fiscal documents (fixed assets - ICMS long term recoverable) (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to post a fiscal document received from the acquisition of fixed assets and then recover the ICMS taxes in Brazil with Microsoft Dynamics 365 Finance.

You can post a fiscal document that you receive from the acquisition of fixed assets. You can recover the Imposto Sobre Circulação de Mercadorias e Prestação de Serviços (ICMS) or Program of Social Integration (PIS)/Contribution for the Financing of Social Security (COFINS) taxes, or both. You can also recover monthly refund installments. These amounts are used to deduct the amount that is due during the tax assessment. 

The following procedure uses the BRMF demo company.

To post a fiscal document received from the acquisition of fixed assets and then recover the ICMS taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. Select **Save**.
1. Expand the **Line** details section.
1. Select the **Fixed assets** tab.
1. In the **New fixed asset?** field, select **Yes**.
1. In the **Fixed asset group** field, enter or select a value.
1. Select the **Financial dimensions** tab.
1. In the **CostCenter** field, enter or select a value.
1. In the **Filial** field, enter or select a value.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. Close the page.
1. Go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **Default from: Product receipt quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select an option.
1. Select **OK**.
1. In the **Document model** field, enter or select a value.
1. In the **Access key** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. Select **Save**.
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
