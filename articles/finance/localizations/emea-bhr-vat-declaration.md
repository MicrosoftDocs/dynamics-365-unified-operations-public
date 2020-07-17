---
# required metadata

title: Configure and generate VAT declaration for Bahrain
description: This topic explains how to configure and generate the VAT return form for Bahrain.
author: sndray
manager: AnnBe
ms.date: 06/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Bahrain
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# VAT declaration for Bahrain

[!include [banner](../includes/banner.md)]

|                     |  |
|------------------------------|-------------------|
| **COUNTRY/REGION**          | BHR - Bahrain|
| **FEATURE TITLE** | VAT declaration for Bahrain |
| **FEATURE REFERENCE**                | BH-00002|
| **BLUEPRINT CLASSIFICATION**                | REGULATORY REPORTING: Tax declaration|
| **CONFIGURABLE**                | Yes. See the configurations in [Import of Electronic Reporting configurations](#ERConfigs).|
| **INTERNAL REFERENCE**                | [Compliance 3982342](https://vstsmbs.visualstudio.com/Compliance/_queries/edit/3982342)|
| **FIRST AVAILABLE IN**                | 2020 Release Wave 2 (Monthly update 10.0.13)|
| **FEATURE UPDATE HISTORY**                |  |
| **FEATURE MANAGEMENT**                | No activation required. See the related features in [Features enabling](#Features).|
| **BUSINESS NEED**                | The VAT declararion must be compliant with Bahraini legal requirements.|
| **FEATURE DESCRIPTION**                | The article explains how to configure and generate the VAT return form in accordance with Bahraini legal requirements.|


## Prerequisites

- The primary address of the legal entity must be in Bahrain.

## <a name="Features"></a>Features enabling

In the **Feature management** workspace, enable the following features:
- (Bahrain) Category hierarchy for Sales and purchase tax report.

For more information how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## <a name="ERConfigs"></a>Import of Electronic Reporting configurations
In **Electronic reporting** workspace, import the following Electronic Reporting formats from the repository:
 - VAT declaration Excel (BH).

> [!NOTE]
> The formats above are based on **Tax declaration model** and use **Tax declaration model mapping**. These additional configurations will be automatically imported.

For more information how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Overview

This topic explains how to set up and generate the VAT return form for legal entities in Bahrain.

The VAT Return form for Bahrain is the official document that summarizes the total output VAT tax amount due, the total input VAT tax amount recoverable and the related VAT tax amount  liability. The form is used for all type of taxpayers, regardless of the size of the VAT payer and it should be completed manually through the tax authority portal. VAT Return Form is commonly referred to as VAT return filing.

The VAT Return form in Dynamics 365 Finance includes the following reports:

	• VAT return form. This reports provides a breakdown of amounts, adjustments and VAT amount  per line item in the VAT Return form as is described in the legislation
	• Sales transactions details grouped by box classification from Box1 to Box 6
	• Purchase transaction details grouped by box classification from Box 8 to Box 12


