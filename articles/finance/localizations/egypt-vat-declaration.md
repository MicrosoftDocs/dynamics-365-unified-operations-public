---
# required metadata

title: VAT declaration for Egypt
description: This topic explains how to configure and generate the VAT return form for Egypt.
author: sndray
manager: AnnBe
ms.date: 02/25/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: tfehr
ms.search.validFrom: 2017-06-20
ms.dyn365.ops.version: 10.0.17
---

#  VAT declaration for Egypt (EG-00002)

[!include[banner](../includes/banner.md)]

## Overview
This topic explains how to set up and generate the VAT return form, sales and purchase books for legal entities in Egypt.

The VAT return form for Egypt the official document that summarizes the total output VAT tax amount due, the total input VAT tax amount recoverable, and the related VAT tax amount liability. The form is used for all types of taxpayers and should be completed manually through the tax authority portal. The VAT return form is commonly referred to as VAT return filing.

The VAT return form in Dynamics 365 Finance includes the following reports:

- VAT return form, which provides a breakdown of amounts, adjustments, and VAT amount per line item in the VAT return form as is described in the legislation.
- Sales transactions book
- Purchase transaction book

## Prerequisites
The primary address of the legal entity must be in Egypt.
In the **Feature management** workspace, enable the following features:

- (Egypt) Category hierarchy for Sales and purchase tax report.

For more information about how to enable features, see Feature management overview.

In the **Electronic reporting** workspace, import the following Electronic Reporting formats from the repository:

- VAT declaration Excel (EG)

> [!NOTE]
> The formats above are based on **Tax declaration model** and use **Tax declaration model mapping**. These additional configurations will be automatically imported.

For more information about how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Download Electronic reporting configurations

The implementation of the VAT return form for Bahrain is based on Electronic reporting (ER) configurations. For more information about the capabilities and concepts of configurable reporting, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

For production and user acceptance testing (UAT) environments, follow the instructions [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

To generate the VAT return form and related reports in a Egypt legal entity, you need to upload the following configurations:

- Tax declaration model.version.70.xml or later version
- Tax declaration model mapping.version.70.120.xml or a later version
- VAT Declaration Excel (EG).version.70.32  or a later version

After you've finished downloading the ER configurations from Lifecycle Services (LCS) or the global repository, complete the following steps.

1. Go to the **Electronic reporting** workspace. Select the Reporting configurations tile.
1. On the **Configurations** page, on the Action Pane, select **Exchange > Load from XML file**.
1. Upload all the files in the order in which they are listed in the previous bullets. After all the configurations are uploaded, the configuration tree should be present in Finance.



