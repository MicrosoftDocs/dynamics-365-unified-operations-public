---
# required metadata

title: Maintain fixed assets (Russia)
description: This topic explains how to deactivate, reactivate, and update a fixed asset in Microsoft Dynamics 365 for Finance and Operations in Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 10/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Maintain fixed assets (Russia)
[!include [banner](../includes/banner.md)]

If a fixed asset is closed down or inactive for more than three months, or if refurbishment of the asset is conducted for more than 12 months, calculation of depreciation is suspended. Depreciation calculation resumes when the fixed asset is placed back into service.

## Inactivate a fixed asset temporarily

1.  Click **Fixed assets** \> **Common** \> **Fixed assets** \> **Fixed assets**.
2.  Select the fixed asset to be temporarily deactivated. The asset is shown in **In operation** status.
3.  In the Action pane, select **FIXED ASSET** \> **History** \> **Temporary closing-down** to open the **Temporary closing-down** page.
4.  In the **Start date** field, select the deactivation date and close the page
   
    > [!NOTE]
    > Depreciation is not accrued when the status of the fixed asset is **Temporary closing-down**.

## Reactivate a fixed asset

1.  Click **Fixed assets** \> **Common** \> **Fixed assets** \> **Fixed assets**.
2.  Select the fixed asset with the **Temporary closing-down** status.
3.   In the Action pane, select **FIXED ASSET** \> **History** \> **Temporary closing-down** to open the **Temporary closing-down** page.
4.  In the **Finish date** field, select the deactivation date and close the page

    > [!NOTE]
    > Depreciation will be calculated from the period specified in the **Date of depreciation beginning** field in the **Depreciation groups** page.

## Post an update for a major refurbishment of a fixed asset 

Capital improvements is a special asset category that includes capital renovations, improvements, technical updates, additional construction, and the acquisition of additional equipment for a fixed asset. When you update capital improvements, calculated depreciation is not revalued. However, the depreciated cost and service life of the fixed asset change. When major repair work is performed on a fixed asset, bonus depreciation is applicable for the asset on or after the major repair transaction date. You can create a transaction for a major repair of a fixed asset, and specify the bonus depreciation and bonus start date. The start date of the bonus depreciation can be the same as the major repair transaction date, or it can be the next depreciation date.

You must complete the following tasks before you can post an update for a major repair of a fixed asset:

  - Create dimensions for depreciation. For more information, see [Define financial dimensions](../general-ledger/tasks/define-financial-dimensions.md).
  - Set up expense codes. 
  - Set up bonus depreciation.
  - Set up depreciation groups.

### Create a journal for a major repair of a fixed asset

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a fixed asset (FA) journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, view or modify the description of the journal.
5.  Click **Lines**.
6.  Create a journal line.
7.  In the **Transaction date** field, select the date to update the transaction.
8.  In the **Transaction type** field, select **Major repairs**.
9.  In the **FA inventory number** field, select the fixed asset number.
10. In the **Value model** field, select the fixed asset value model.
11. In the **Reason code** field, select a reason code.
12. In the **Reason comment** field, update the reason for the major repair of the fixed asset.
13. Click **OK**. The improvement lines for the asset are displayed in the journal.
14. In the **Description** field, select transaction text.
15. In the **Debit** or **Credit** field, enter the transaction amount.
16. In the **Offset account type** field, select the offset account type.
17. In the **Offset account** field, select the offset account number.
    > [!TIP]
    > You can also click **Group operations** > **Major repairs** to create transactions for several fixed assets.

18. Click **Post** \> **Post** to post the journal.

### Update a value model for a fixed asset

1.  Click **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2.  Select a fixed asset, and then click **Value models**.
3.  On the Action pane, Click **FA lifetime history**.
4.  Click **New**, and then in the **Date** field, select the lifetime change date.
5.  In the **New lifetime** and **New factor** fields, enter a lifetime and factor for the fixed asset.
6.  In the **Depreciation method** and **Depreciation subgroup** fields, select a depreciation method and subgroup.
7.  In the **Reason code** field, select a reason code.
8.  In the **Reason comment** field, update the reason for the transaction.
