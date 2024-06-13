---
title: Configure a tax solution provider
description: Learn how to configure a tax solution provider for Tax calculation, including a step-by-step process for configuring a tax solution provider.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 10/04/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: 
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Configure a tax solution provider

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure a tax solution provider for Tax calculation. After you complete the steps according to the implementation guidance that your tax rate provider provides, select your tax feature setup in Tax calculation parameters for the corresponding legal entity.

To configure a tax solution provider, follow these steps.

1. Go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax calculation parameters**.
1. On the **General** tab, in the **Tax solution provider** section, select **Enable tax solution provider**.
1. In the **Feature** section, in the **Name** field, select your tax feature setup.
1. If any new tax codes are defined in the feature setup, the **Maintain mandatory fields for new tax codes** page appears. For each tax code, you must select a settlement period and a ledger posting group. To bulk update the mandatory fields, you can select all tax codes and then select **Bulk update**.
1. Select **Confirm**. A log file is downloaded in your browser. This file contains the information for the imported and/or updated tax codes, tax groups, and item tax groups for the current legal entity.
1. In the **Business process** field, select the processes that will access the external tax service for tax calculation.

    > [!NOTE]
    > To learn about the supported business process that you should select, contact your tax solution provider.

1. Select **Enable address validation**, and select the country/region keys that your tax rate provider supports.

    > [!NOTE]
    > To ensure an accurate location-based tax calculation, your tax rate provider will validate and correct the addresses in the master data. After you enable address validation, a **Validate** button is available when you add or maintain the addresses in the master data.
    > 
    > For batch mode validation, go to **Organization administration** \> **Global address book** \> **Global address book**, and then, on the **Registration** tab, select **Address validation**.

1. For US legal entities, enable the **Accrue use tax** option, and maintain the fields in the **Overcharge tolerance** section to activate the assessment and processing of vendor-charged sales taxes for Accounts Payable (AP) invoicing scenarios. For more information, see [Use tax assessment](./universal-tax-rate-api-use-tax-assessment.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
