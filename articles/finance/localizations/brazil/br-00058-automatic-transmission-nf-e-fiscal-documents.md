---
title: Automatic transmission of NF-e fiscal documents (Brazil)
description: This article describes how to set up email parameters to automatically send a Nota Fiscal eletrônica (NF-e) to a vendor or customer after the NF-e is approved or canceled in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.search.industry: Manufacturing;Distribution;Service industries
---

# Automatic transmission of NF-e fiscal documents (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up email parameters to automatically send a Nota Fiscal eletrônica (NF-e) to a vendor or customer after the NF-e is approved or canceled in Brazil with Microsoft Dynamics 365 Finance.

Use the following procedure to set up email parameters to automatically send an NF-e to a vendor or customer after the NF-e is approved or canceled, or if you generate a correction letter. You can set up a batch group and email templates for an NF-e. You must create separate email templates for an approved NF-e, a canceled NF-e, and a correction letter. You can then create a batch process to send the NF-e by email. 

This task uses the BRMF demo company.

To set up email parameters to automatically send an NF-e to a vendor or customer after the NF-e is approved or canceled, follow these steps.

1. In Dynamics 365 Finance, go to **System administration \> Setup \> Batch group**.
1. Select **New**.
1. In the **Group** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Go to **System administration \> Periodic tasks \> Email processing \> Batch**.
1. Expand the **Run in the background** section.
1. In the **Batch processing** field, select **Yes**.
1. In the **Batch group** field, enter or select a value.
1. Select **Recurrence**.
1. Select the **No end date** option.
1. In the **Count** field, enter a number.
1. In the **Time zone** field, select an option.
1. Select **OK**.
1. Select **OK**.
1. Go to **Organization administration \> Setup \> Email templates**.
1. Select **New**.
1. In the **Email ID** field, enter a value.
1. In the **Sender email** field, enter a value.
1. In the **Sender name** field, enter a value.
1. In the **Default language** code field, enter or select a value.
1. In the **Lines or header** field, select an option.
1. In the **Batch group** field, enter or select a value.
1. In the **Email description** field, enter a value.
1. In the **Lines or header** field, select an option.
1. Select **Save**.
1. In the list, mark the selected row.
1. In the **Subject** field, enter a value.
1. In the **Language** field, enter or select a value.
1. Select **Edit**.
1. In the **WritableContent** field, enter a value.
1. Select **OK**.
1. Select **Save**.
1. Close the page.
1. Go to **Organization administration \> Organizations \> Fiscal establishments \> Fiscal establishments**.
1. Use the Quick Filter to find records. For example, filter on the **Fiscal establishment ID** field with a value of "Matriz".
1. Expand the **NF-e and NFC-e federal** section.
1. Select **Edit**.
1. In the **Approved NF-e** field, enter or select a value.
1. In the **Attach the DANFE as PDF file to email** field, select **Yes**.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
