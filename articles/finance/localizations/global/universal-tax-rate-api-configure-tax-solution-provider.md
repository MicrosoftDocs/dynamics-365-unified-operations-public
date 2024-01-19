---
title: Configure tax solution provider
description: This article explains how to configure tax solution provider section for Tax calculation.
author: Kai-Cloud
ms.date: 10/04/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: 
ms.reviewer: 
ms.search.region: 
ms.author: kailiang
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---
# Configure tax solution provider

After completed the steps following the implementation guidance of your tax rate provider, you shall select your tax feature setup in the Tax calculation paramters for the corresponding legal entity.

1. In the Tax module, select **Setup > Tax configuration > Tax calculation parameters**.
2. In  **General**, under **Tax solution provider** section, select **Enable tax solution provider**.
3. In the **FEATURE** field group, select your tax feature setup in the **Name** field.
4. If there is new tax codes defined in the feature setup, the **Maintain mandatory fields for new tax codes** page will appear. You must select the corrsponding **Settlement period** and **Ledger posting group** for each tax code. You can select all tax codes and select the **Bulk update** dropdown buttion to bulk update the mandatory fields.
5. Select **Confirm** buttion. A log file will be downloaded in your browser in which the detail information for the imported and/or updated tax codes, tax groups and item tax groups for the current legal entity is available.
6. In the **Business process** field, select the corresponding processes which shall access the external tax service for tax calculation.
    >[!Note]
    >Contact your tax solution provider to learn the supported **Business process** that shall be selected in this field.
7. Select **Enable address validaton** and select the country/region keys that are supported by your tax rate provider.
    >[!Note]
    >For an accurate location-based tax calculation, the addresses in the master data shall be validated and corrected by your tax rate provider. Once enabled, the **Validate** button is available when you adding or maintaining the addresses in the master data.
    >In additon, in **Organization administration > Global address book > Global address book** under the **Registration** tab, select **Address validation** for a batch mode validation.
8. For US legal entities, enable the **Accrue use tax** option and maintain the fields in **OVERCHARGE TOLERANCE** group to activate the assessment and processing of vendor charged sales taxes for AP invoicing scenarios. See more details in [Use tax assessment](./universal-tax-rate-api-use-tax-assessment.md)
