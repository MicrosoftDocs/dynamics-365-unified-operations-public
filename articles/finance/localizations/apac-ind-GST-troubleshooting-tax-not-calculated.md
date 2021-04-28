---
# required metadata

title: Tax isn't calculated
description: This topic provides troubleshooting information to resolve the issue when tax isn't being calculated on tax documents.
author: qire
manager: beya
ms.date: 04/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---



# Tax isn't calculated

[!include [banner](../includes/banner.md)]

When you discover that there either tax component or tax document lines are missing from a tax document, complete the sections in this topic to troubleshoot the issue.
For more information about concepts, such as Tax document and Tax components, related to the Tax engine or GTE, see [Tax engine overview](../general-ledger/tax-engine.md).

In this topic, a purchase order is used to show the troubleshooting process. 

## Check the tax applicability in tax configuration

1. Refer to [How to open designer of current used tax configuration](./apac-ind-GST-troubleshooting-open-designer-current-used-tax-configuration.md)  to open designer for current tax configuration.
2. For no tax document lines case, check whether the *Condition/Lookups* on Header node are correct. 

      [![Direct taxes (tab)](./media/tax-not-calculated-Picture1.png)](./media/tax-not-calculated-Picture1.png)

3. For no tax component lines case, check whether the *Condition/Lookups* on *Lines*, *Tax type* or Tax component nodes are correct. 

      [![Direct taxes (tab)](./media/tax-not-calculated-Picture2.png)](./media/tax-not-calculated-Picture2.png)

## Compare the transaction details with other conditions

1. Click *Tax document* button to open tax document.
2. Select *Header* node, then click *View tax input* button. The transaction header details will be displayed. Check all those fields are correctly set for tax calculation.

     [![Direct taxes (tab)](./media/tax-not-calculated-Picture3.png)](./media/tax-not-calculated-Picture3.png)

3. Select *Line* node, then click *View tax input* button. The transaction line details will be displayed. Check all those fields are correctly set for tax calculation.

     [![Direct taxes (tab)](./media/tax-not-calculated-Picture4.png)](./media/tax-not-calculated-Picture4.png)

4. Compare the transaction fields in *Tax document > View tax input* dialog with the conditions that is found in step 1, check all those fields are met the corresponding conditions or lookups.

## Determine whether customization exists

If you've completed the steps in the previous sections but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.

## Prevent posting transaction without GST calculated

If you'd like to prevent to post the transaction without GST calculated, you can enable the feature **[India] GTE calculation validation** following the steps below.

1. Go to **Workspaces** > **Feature management**.
2. Find the feature, **[India] GTE calculation validation**, and then select **Enable now**.

     [![Feature management Enable now button](./media/tax-not-calculated-Picture5.png)](./media/tax-not-calculated-Picture5.png)

3. Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup**. Select the company in which you want to enable the validation, and then select **Parameters**.

   [![Parameters button](./media/tax-not-calculated-Picture6.png)](./media/tax-not-calculated-Picture6.png)

4. In the dialog box, set up the validation parameter, **Empty tax component** and **Zero tax**, and then select **OK** to complete setup.

   None: no validation

   Warning: Prompt a warning message, but won't block the posting operation.

   Error: Prompt a error message and block the posting operation.

   [![Validation field group](./media/tax-not-calculated-Picture7.png)](./media/tax-not-calculated-Picture7.png)

5. Then when you posting transaction without GST calculated, the corresponding error/warning     message will be prompted.

   - No tax lines: "No tax document lines are found in tax document. If it is not expected, please contact your system administrator, check the tax configuration, and try again."
   - No tax component lines: "No tax component is applicable for line %1, please contact your system administrator, check the tax setup, and try again. "
   - Tax amount is zero: "The tax amount is 0 for line %1, please contact your system administrator, check the tax setup, and try again."

> [!NOTE]
> Enabling the validation may also block some normal scenarios such as exempt or zero-rate scenarios. You must decide how to perform the validation setup based on your business.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
