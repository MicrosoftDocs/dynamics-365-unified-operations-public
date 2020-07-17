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



