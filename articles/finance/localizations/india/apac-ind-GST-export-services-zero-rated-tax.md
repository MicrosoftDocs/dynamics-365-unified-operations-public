---
title: Export services that have zero-rated tax
description: Learn how to export services that have zero-rated tax in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.custom: 
  - bap-template
---

# Export services that have zero-rated tax

[!include [banner](../../includes/banner.md)]

This article explains how to export services that have zero-rated tax in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to export services that have zero-rated tax and then validate the tax details.

To export services that have zero-rated tax, follow these steps:

1. In Dynamics 365 Finance, go to **General journal \> Journals \> Invoices \> General journal**.
1. Create a journal.
1. Select **Lines**.
1. Create a sale of services for a foreign customer.
1. Save the record.
1. Select **Tax information**.
1. On the **GST** FastTab, in the **SAC** field, select a value.
1. Select the **Customer tax information** FastTab.
1. Select **OK**.

## Validate the tax details

To validate the tax details, follow these steps:

1. Select **Tax document**.
1. Select **Close**.
1. Select **Post \> Post**.
1. Close the message that you receive.
1. Select **Inquiries \> Voucher**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
