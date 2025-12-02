---
title: Create an accelerated depreciation document and enter usage data
description: Learn how to create an accelerated depreciation document and enter usage data for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook, LedgerJournalTable, LedgerJournalTransAsset, AssetAcceleratedDepDocument_JP, SysQueryForm
ms.custom: 
  - bap-template
---

# Create an accelerated depreciation document and enter usage data

[!include [banner](../../includes/banner.md)]

This article explains how to create an accelerated depreciation document and enter usage data for Japan in Microsoft Dynamics 365 Finance.

For Japan, accelerated depreciation is declared on a per document basis. Each document can contain multiple fixed assets. You must calculate an overuse rate on the accelerated depreciation document and multiply it by the ordinary depreciation amount to get the amount for the accelerated depreciation. The details of the accelerated depreciation declaration are listed on the document. Only a confirmed accelerated depreciation document can be used at accelerated depreciation proposal for posting. 

The following procedures walk you through how to create a fixed asset with an accelerated depreciation profile, create an accelerated depreciation document and assign the fixed asset to it, enter overuse hours for the fixed asset, and calculate the overuse rate on the document. The procedures were created using the demo data company JPMF.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Create a fixed asset with accelerated depreciation

To create a fixed asset with accelerated depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, enter a value. For example enter "VEHI-M".  
1. Note the fixed asset number for later reference.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Books**.
1. Expand the **Depreciation** section.
1. Confirm that the **Accelerated depreciation profile** field is configured properly. For the existing fixed assets, you can also manually enter this value to apply accelerated depreciation profile to it.  

## Acquire the fixed asset

To acquire the fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Journal entries \> Fixed assets journal**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. Select **Save**.
1. Select **Lines**.
1. In the **Date** field, enter a date.
1. Use the previously noted fixed asset number.
1. In the **Debit** field, enter a number.
1. Select **Save**.
1. Select **Post**.

## Enter overuse information in the accelerated depreciation document

To enter overuse information in the accelerated depreciation document, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Accelerated depreciation \> Accelerated depreciation document**.
1. Select **New**.
1. In the **Description** field, enter a value.
1. In the **Fixed asset equipment group** field, enter a value.
1. In the **From date** field, enter a date. The **From date** and **To date** values are used to define the declaration period during which to apply and declare the accelerated depreciation. 
1. In the **To date** field, enter a date.
1. Expand the **Fixed assets and working hours detail** section. Microsoft recommends that you enter working hours by fixed assets so that the data is accurate and complete.  
1. Select **Add by query**.
1. In the **Criteria** field, filter to find the fixed assets.
1. Select **OK**.
1. In the **Planned** field, enter a number. Other than planned hours, you can also choose to enter reserved or actual hours if they apply.  
1. Select **Save**.
1. Select **Calculate daily average hour**.
1. Confirm that the overuse rate is calculated and updated. If you've already calculated the overuse rate, you can choose to skip the calculate step and directly enter the overuse rate and confirm the document for proposal purpose.  
1. Select **Confirm**. Only confirmed accelerated depreciation documents can be used for the proposal.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
