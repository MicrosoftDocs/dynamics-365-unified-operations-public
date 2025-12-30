---
title: GB-00002 Set up reverse charge VAT item groups, rules, and parameters
description: Learn how to set up reverse charge item groups, applicability rules for purchasing and for sales purposes, and reverse charge parameters for the United Kingdom in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/04/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: ReverseChargeItemGroup_W, EcoResCategorySingleLookup, ReverseChargeRule_W, LedgerParameters, TaxGroupLookup
---

# GB-00002 Set up reverse charge VAT item groups, rules, and parameters

[!include [banner](../../includes/banner.md)]

This article explains how to set up reverse charge item groups, applicability rules for purchasing and for sales purposes, and reverse charge parameters for the United Kingdom in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to set up reverse charge item groups, applicability rules for purchasing and for sales purposes, and reverse charge parameters for the United Kingdom. Before you complete the procedures, you must first set up sales tax groups and item sales tax groups for reverse charge VAT. 

The procedures use the demo company GBSI.

## Set up reverse charge item groups

To set up reverse charge item groups, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Sales tax** \> **Reverse charge item groups**.
1. Select **New**.
1. In the **Name** field, enter "DEVICES".  
1. Set the **Reverse charge sales list** slider to **Yes**. This action includes the group in the Reverse Charge Sales list report.  
1. Select **Save**.
1. Select **Add**.
1. In the **Item relation** field, enter "S0020".  
1. Select **Add**.
1. In the **Item relation** field, select the drop-down, and then select **Table**.  
1. In the list, find and select **S0012**.  
1. Select **Save**.
1. In the **Sales/Purchase** field, select **Sales**.
1. Select **Add**.
1. In the **Item code** field, select **Group**.  
1. In the **Item relation** field, select the drop-down, and then select **ProjItem**.  
1. In the list, select **ProjItem** in the selected row.  
1. Select **Save**.
1. Select **New**.
1. In the **Name** field, enter **SERVICES**.  
1. Select **Save**.
1. In the **Sales/Purchase** field, select **Purchase**.
1. Select **Add**.
1. In the **Item code** field, select **Group**.
1. In the **Item relation** field, select the drop-down, and then select **Services**.  
1. In the list, find and select **Services**.
1. Select **Add**.
1. In the **Item code** field, select **Category**.
1. In the **Category** field, select the drop-down to open the lookup.
1. In the tree, expand the category tree, and then **Cleaning**.
1. Select **OK**.
1. Select **Save**.

## Set up reverse charge rules

To set up reverse charge rules, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Sales tax** \> **Reverse charge rules**.
1. Select **New**.
1. In the **Partner country/region type** field, select **Domestic**.  
1. In the **Reverse charge item group** field, select the drop-down, and then select **DEVICES**.  
1. In the list, select **DEVICES** in the selected row.
1. In the **Threshold amount** field, enter "5000".  
1. Select the **Empty tax base for outgoing tax** checkbox. This action enters a zero tax base amount in Box 6 of the VAT 100 report.  
1. In the **Action** field, select **Set** to update the sales tax group with the reverse charge VAT group when the rule is applied.  
1. In the **Effective** field, enter a date.
1. Select **Save**.
1. Select **New**.
1. In the **Partner country/region type** field, select **Foreign**.
1. Select the **Domestic delivery address** checkbox if the rule should be applied to domestic delivery.  
1. In the **Reverse charge item group** field, select the drop-down, and then select **SERVICES**.  
1. In the list, find and select the desired record.
1. In the **Action** field, select **Set** to update the sales tax group with the reverse charge VAT group when the rule is applied.  
1. In the **Effective** field, enter a date.
1. Select **New**.
1. In the **Document type** field, select **Vendor invoice**.  
1. In the **Partner country/region type** field, select **EU**.  
1. Select the **Domestic delivery address** checkbox if the rule applies to the domestic delivery.  
1. In the **Reverse charge item group** field, select the drop-down, and then select **SERVICES**.  
1. In the list, find and select the desired record.
1. In the **Action** field, select **Set** to update the sales tax group with the reverse charge VAT group when the rule is applied.  
1. In the **Effective** field, enter a date.
1. Select **New**.
1. In the **Document type** field, select **Sales order**.  
1. In the **Partner country/region type** field, select **Domestic**.  
1. In the **Reverse charge item group** field, select the drop-down, and then select **DEVICES**.  
1. In the Threshold amount field, enter "5000".
1. In the **Action** field, select **Prompt** to get notification when the rule is applied.  
1. In the **Effective** field, enter a date.
1. Select **Save**.
1. Close the page.

## Configure general ledger parameters for reverse charge VAT

To configure general ledger parameters for reverse charge VAT, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Parameters** \> **General ledger parameters**.
1. Select the **Reverse charge** tab.
1. Select the **Enable reverse charge** slider.
1. In the **Purchase order sales tax grou** field, select the drop-down, and then select **RC-VAT**.  
1. In the list, find and select **RC-VAT**.  
1. In the **Sales order sales tax group** field, select the drop-down, and then select **RC-VAT-AR**.  
1. In the list, find and select **RC-VAT-AR**.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
