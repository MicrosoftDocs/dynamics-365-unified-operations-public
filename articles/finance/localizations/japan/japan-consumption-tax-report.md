---
title: Generate Japan consumption tax report
description: Learn how to generate the Japan consumption tax report in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/25/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerConsumptionTaxCalcTrans_JP, LedgerConsumptionTaxReportTrans_JP
ms.custom: 
  - bap-template
---

# Generate Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This article explains how to generate the Japan consumption tax report in Microsoft Dynamics 365 Finance.

The following procedure was created using the demo data company JPMF.

To generate the Japan consumption tax report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Sales tax \> Japanese sales tax report**.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. In the **Settlement period** field, enter a value.
1. In the **Declaration type** field, select an option.
1. In the **Calculation method** field, select an option.
1. In the **Amendment** field, select **Yes**. If you already generated the report and you're generating it again, you must choose to update the existing record on the amendment.  
1. Select **OK**.
1. Select **Edit**.
1. In the **Item 6** field, enter a number. The data is retrieved and summarized from the transactions. You can update the editable fields for adjustment purposes.  
1. Select **Save**.
1. Select **Update amount**. This action recalculates the amounts.  
1. Select **Finalize**.
1. Select **Yes**.
1. Select **Consumption tax report**.
1. Select the **Tax calculation** tab.
1. Select **Edit**.
1. In the **Item 10** field, enter a number.
1. Select **Save**.
1. Select **Update amount**.
1. Select the **Additional information** tab. The information is printed as configured. You can set the **Installment basis** slider to be **Yes** to print a "Yes" on the final report.  
1. Select **Finalize**.
1. Select **Yes**.
1. On the Action Pane, select **Consumption tax report**.
1. To generate the final report, select **Print reports**.  

> [!NOTE]
> To calculate the consumption tax report that should be submitted from October 1, 2019, you must turn on the **Japanese sales tax report** feature in the **Feature management** workspace. Learn more at [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
