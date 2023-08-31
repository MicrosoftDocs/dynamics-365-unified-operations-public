---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.37 (November 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.37 preview release.
author: twheeloc
ms.date: 08/28/2023
ms.topic: faq
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.37

---

# What's new or changed in Dynamics 365 Finance 10.0.37 (November 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** September 2023
- **General availability of release (self-update):** October 2023
- **General availability of release (auto-update):** November 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
|Accounts payable|Default option for **Approved by** field in the **Invoice register**|This feature allows administrators control the mandatory status of the **Approved by** field on the **Invoice register**. The field can be set as optional when formal approval isn't required within the Invoice register's business process.|


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, 
they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank management|Import bank statement|Bank statement importing for ISO20022 camt053.001.08 version is supported in Dynamics 365 Finance version 10.0.37. Users can import the latest Advanced bank reconciliation statement configuration ABR Camt.053 format version 3.13.|
|Accounts payable|Match the detail for vendor invoices|In Dynamics 365 Finance version 10.0.37, invoice validation is available on different invoice amount fields. This enhancement provides specific control over the round-off amount.|
|Cash and bank management|	ISO20022 Credit Transfer|	The Generic Credit Transfer payment format is supported for the ISO20022 pain.001.001.09 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 version 43.73.|
|Cash and bank management|	ISO20022 Direct Debit	|The Generic Direct Debit payment format is supported for the ISO20022 pain.008.001.08 version. Users can generate the latest Direct Debit configuration, ISO20022 Direct debit 2019 version 12.38.|
|Cash and bank management|	ISO20022 Credit Transfer format for Italy|The Italian Credit Transfer payment format is supported for the CBI 00.04.01 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 (IT) version 43.73.18.|
|Cash and bank management|	ISO20022 Direct Debit format for Italy|The Italian Direct Debit payment format is supported for the CBI 00.01.01 version. Users can generate the latest Direct Debit configuration, ISO20022 Direct debit 2019 (IT) version 12.38.14.|
|Cash and bank management|	ISO20022 Credit Transfer format for Norway|	The Norwegian Credit Transfer payment format for the ISO20022 pain.001.001.09 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 (NO) version 43.73.28.|


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.37. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/
get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change 
ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless 
they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
