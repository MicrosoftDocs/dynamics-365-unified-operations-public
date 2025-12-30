---
title: JP-00027 Form 26 for depreciable tax declaration
description: Learn how to assign a registration number to a fixed asset and print the Form 26 report for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: OMLegalEntity, LogisticsPostalAddress, SysLookupMultiSelectGrid, LogisticsAddressCityLookup, AssetLocation, AssetLocationEdit_JP, AssetGroup, AssetTable, LedgerJournalTable, LedgerJournalTransAsset, DefaultDashboard
ms.custom: 
  - bap-template
---

# JP-00027 Form 26 for depreciable tax declaration

[!include [banner](../../includes/banner.md)]

This article explains how to assign a registration number to a fixed asset and print the Form 26 report for Japan in Microsoft Dynamics 365 Finance.

The following procedure shows you how to assign a registration number to a fixed asset and print the form 26 report. The procedures use the JPMF demo company data. 

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Create a registration number

To create a registration number, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Select **Registration IDs**.
1. Select **New**.
1. In the **Purpose** field, enter or select a fixed asset value.  
1. In the **Name or description** field, enter a value.
1. Expand the **Address** section.
1. In the **Country/region** field, enter a value.
1. In the **State** field, enter or select a value.
1. In the **City** field, enter or select a value.
1. Select **Save**.
1. Expand the **Registration ID** section.
1. Select **Add**.
1. In the **Registration type** field, enter or select a value.
1. In the **Registration number** field, enter a value.
1. Select the **General** tab.
1. In the **Effective** field, enter a date.
1. In the **Depreciation method** field, select an option.
1. Select **Save**.

## Create a fixed asset location and assign registration number

To create a fixed asset location and assign registration number, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset attributes \> Fixed assets locations**.
1. Select **New**.
1. In the **Location** field, enter a value.
1. In the **Name** field, enter a value.
1. Expand the **Address** section.
1. Select **New**.
1. In the **Name or description** field, enter or select a value.
1. In the **Registration number** field, enter or select a value.
1. Select **OK**.
1. Select **Save**.

## Define location to a fixed asset group

To define location to a fixed asset group, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset groups**.
1. In the list, find and select the desired record. For example, select **VEHI-A**.  
1. Select **Edit**.
1. In the **Location** field, enter or select a value.
1. Select **Save**.

## Create a fixed asset

To create a fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, enter or select a value.
1. Expand the **Location** section.
1. Validate location defaults for the fixed asset  

## Create an acquisition

To create an acquisition, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Save**.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. In the **Account** field, enter a value.
1. In the **Debit** field, enter a number.
1. Select **Post**.

## Verify the Form 26 report

To verify the Form 26 report, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Inquiries and reports \> Depreciable asset declaration reports \> Form 26: Depreciable assets taxation ledger report**.
1. In the **Calendar year** field, enter or select a value.
1. In the **Office building asset** number field, enter or select a value.
1. In the **Registration number** field, enter or select a value.
1. Open and save the report in the required location.
1. Validate the printed report. The fixed assets should be sorted and grouped by registration number. Similar sorting of fixed assets is also provided for the Form 26-1 n Form 26-2 reports.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
