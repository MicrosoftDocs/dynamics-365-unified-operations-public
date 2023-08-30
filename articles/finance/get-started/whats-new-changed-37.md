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
|Accounts payable|Default option for field "Approved by" in Invoice register|This feature allows admin to control the mandatory status of the "Approved by" field within the Invoice register. The field can be set as optional when formal approval is not required within the Invoice register's business process.|


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, 
they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank management|Import bank statement|Bank statement importing for ISO20022 camt053.001.08 version is supported in 10.0.37. User can import the latest Advanced bank reconciliation statement configuration ABR Camt.053 format version 3.13 for this feature enhancement.|
|Accounts payable|Match the detail for vendor invoices|The functionality has been enhanced in version 10.0.37 to enhance invoice validation on different invoice amount fields. This enhancement provides specific control over the round-off amount.|

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.37. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/
get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change 
ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless 
they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
