---
title: PIS and COFINS fixed assets (Brazil)
description: This article describes how to configure the fixed asset PIS and COFINS tax credit to be appropriated in installments in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# PIS and COFINS fixed assets (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to configure the fixed asset Program of Social Integration (PIS) and Contribution for the Financing of Social Security (COFINS) tax credit to be appropriated in installments in Brazil with Microsoft Dynamics 365 Finance.

When a legal entity purchases a fixed asset, the PIS and COFINS tax credit that is calculated on that transaction can be appropriated in a specific number of installments. For the correct calculation for this tax refund, the legal entity must present a specific fiscal book or report for the information in the Sistema Publico de Escrituração Digital (SPED) Escrituracao Fiscal Digital (EFD) contributions file to demonstrate correct appropriation of the PIS and COFINS tax credit amount. The control of credit that's appropriated in the tax assessment period is detailed in records F120 and F130 of SPED EFD contributions. 

The following procedure uses the BRMF demo company.

To configure the fixed asset PIS and COFINS tax credit to be appropriated in installments, follow these steps:

1. In Dynamics 365 Finance, go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit** price field, enter a number.
1. Expand the **Line details** section.
1. Select the **Fixed assets** tab.
1. In the **New fixed asset?** field, select **Yes**.
1. In the **Fixed asset group** field, enter or select a value.
1. Select the **Financial dimensions** tab.
1. In the **CostCenter** field, enter or select a value.
1. In the **Filial** field, enter or select a value.
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
1. In the **Posting date** field, enter a date.
1. Select **Post**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Booking period**.
1. Select **Create new booking period** to open the drop dialog.
1. In the **Fiscal establishment** field, enter or select a value.
1. In the **Month** field, select a month.
1. In the **Year** field, enter a year.
1. Select **OK**.
1. Select **Sync**.
1. Select **OK**.
1. Select **PIS-COFINS**.
1. Select **PIS and COFINS tax assessment** to open the drop dialog.
1. Select **OK**.
1. Close the page.
1. Go to **Fiscal books \> Common \> Fixed assets \> All PIS and COFINS fixed assets**.
1. In the list, select the link in the selected row.
1. Expand the **PIS and COFINS fixed asset transactions** section.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
