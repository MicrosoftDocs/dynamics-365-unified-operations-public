---
title: Brazilian withholding taxes
description: This article describes how to set up a withholding tax code, a withholding tax type, and a calculation parameter to calculate withholding taxes for consultancy services in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---

# Brazilian withholding taxes 

[!include [banner](../../includes/banner.md)]

This article describes how to set up a withholding tax code, a withholding tax type, and a calculation parameter to calculate withholding taxes for consultancy services in Brazil with Microsoft Dynamics 365 Finance.

The following procedure walks you through how to set up a withholding tax code, a withholding tax type, and a calculation parameter to calculate withholding taxes for consultancy services or professional service payments. The procedure uses the BRMF demo company.

To set up withholding taxes, follow these steps: 

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Withholding tax \> Withholding tax settlement periods**.
1. Select **New**.
1. In the **Settlement period** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Authority** field, enter or select a value.
1. In the **Period interval unit** field, select an option.
1. In the **Period interval duration** field, enter a number.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. On the Action Pane, select the **Action Pane** tab.
1. Select **New period**.
1. Select **Save**.
1. Close the page.
1. Go to **Tax \> Indirect taxes \> Withholding tax \> Withholding tax codes**.
1. Select **New**.
1. In the **Withholding tax code** field, enter a value.
1. In the **Brazilian tax withhold type** field, select an option.
1. In the **Main account** field, enter the desired values.
1. In the **Withholding tax receivable** field, enter the desired values.
1. In the **Settlement period** field, enter or select a value.
1. Expand the **Calculation** section.
1. In the **Origin** field, select an option.
1. Select **Save**.
1. Select **Values**.
1. In the **Value** field, enter a number.
1. Select **Save**.
1. Close the page.
1. Go to **Tax \> Indirect taxes \> Withholding tax \> Withholding tax groups**.
1. Select **New**.
1. In the **Withholding tax group** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Withholding tax code** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Go to **Tax \> Indirect taxes \> Withholding tax \> Item withholding tax groups**.
1. Select **New**.
1. In the **Item withholding tax group** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Withholding tax code** field, enter or select a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
