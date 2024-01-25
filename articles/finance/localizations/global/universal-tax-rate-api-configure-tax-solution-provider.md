---
title: Configure a tax solution provider
description: This article explains how to configure tax solution provider section for Tax calculation.
author: Kai-Cloud
ms.date: 10/04/2023
ms.topic: how-to
ms.custom: 
  - bap-template
ms.prod: 
ms.technology: 
ms.reviewer: johnmichalak
ms.search.region: 
ms.author: kailiang
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
# Configure a tax solution provider

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to configure tax solution provider section for Tax calculation. After completing the steps following the implementation guidance of your tax rate provider, select your tax feature setup in the **Tax calculation parameters** for the corresponding legal entity.

To configure your tax solution provider, follow these steps.

1. In the Tax module, select **Setup** \> **Tax configuration** \> **Tax calculation parameters**.
2. In  **General**, under **Tax solution provider** section, select **Enable tax solution provider**.
3. In the **FEATURE** field group, select your tax feature setup in the **Name** field.
4. If there are new tax codes defined in the feature setup, the **Maintain mandatory fields for new tax codes** page appears. You must select the corresponding **Settlement period** and **Ledger posting group** for each tax code. You can select all tax codes and select the **Bulk update** dropdown button to bulk update the mandatory fields.
5. Select the **Confirm** button. A log file is downloaded in your browser. The downloaded file contains the information for the imported and/or updated tax codes, tax groups, and item tax groups for the current legal entity.
6. In the **Business process** field, select the corresponding processes that shall access the external tax service for tax calculation.
    >[!NOTE]
    >Contact your tax solution provider to learn the supported **Business process** that shall be selected in this field.
7. Select **Enable address validation**, and select the country/region keys that are supported by your tax rate provider.
    >[!NOTE]
    >For an accurate location-based tax calculation, the addresses in the master data shall be validated and corrected by your tax rate provider. Once enabled, the **Validate** button is available when you add or maintain the addresses in the master data.
    >In **Organization administration** \> **Global address book** \> **Global address book** under the **Registration** tab, select **Address validation** for a batch mode validation.
8. For US legal entities, enable the **Accrue use tax** option, and maintain the fields in the **OVERCHARGE TOLERANCE** group to activate the assessment and processing of vendor charged sales taxes for AP invoicing scenarios. For more information, see [Use tax assessment](./universal-tax-rate-api-use-tax-assessment.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
