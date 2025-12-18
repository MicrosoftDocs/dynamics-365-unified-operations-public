---
title: Bank data usability enhancement
description: Learn how you can help save time and simplify bank data registration for customers and vendors, including an outline on import bank groups.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2019-11-29
ms.search.form:
ms.dyn365.ops.version: 10.0.7
---

# Bank data usability enhancement

[!include [banner](../../includes/banner.md)]

Companies often need to enter and maintain a large amount of banking information. The cost of entering incorrect bank information can be very high. To help save time and simplify bank data registration, you can import Italian bank information from reliable sources. By using this method, you reduce the risk of errors when entering bank data for customers and vendors.

## Prerequisites

Before you begin, make sure the following prerequisites are met:

- The primary address of the legal entity is in Italy.
- The **Bank account setup enhancement** feature is turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Import bank groups

You can import the list of banks by using the **Bank groups** entity and the Data management framework. For more information, see [Data import and export jobs overview](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md).

Present the source data for importing bank groups as a Microsoft Excel file that has the following column names:

- BANKGROUPID
- ADDRESSCITY
- ADDRESSCOUNTRY
- ADDRESSCOUNTY
- ADDRESSDESCRIPTION
- ADDRESSDISTRICTNAME
- ADDRESSLATITUDE
- ADDRESSLOCATIONID
- ADDRESSLONGITUDE
- ADDRESSSTATE
- ADDRESSSTREET
- ADDRESSTIMEZONE
- ADDRESSVALIDFROM
- ADDRESSVALIDTO
- ADDRESSZIPCODE
- NAME
- ROUTINGNUMBER
- ROUTINGNUMBERTYPE
- STATEMENTFORMATID
- SUFFIX
- BRANCHNAME\_IT

> [!NOTE]
> The **BANKGROUPID** value must match the **ROUTINGNUMBER** value.

## Use the enhanced list of bank groups

When you turn on the Bank account setup enhancement feature, two extra descriptive fields, **Branch name** and **City**, are available for bank groups.

:::image type="content" source="../media/emea-ita-exil-bank-pic.jpg" alt-text="Screenshot of the bank groups page showing the Branch name and City fields.":::

When you set up a bank account, you can use these extra descriptive fields for bank groups to select a bank more precisely.

:::image type="content" source="../media/emea-ita-exil-bank-pic2.jpg" alt-text="Screenshot of the bank account setup page displaying additional descriptive fields for bank groups.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
