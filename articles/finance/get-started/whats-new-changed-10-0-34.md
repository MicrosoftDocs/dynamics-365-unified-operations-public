---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.34 (June 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.34 preview release.
author: twheeloc
ms.date: 04/10/2023
ms.topic: article
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
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Finance 10.0.34 (June 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.34. This version has a build number of 10.0.XXXXX and is available 
on the following schedule:

- **Preview of release:** April 2023
- **General availability of release (self-update):** June 2023
- **General availability of release (auto-update):** July 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing 
feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank|Reverse posted bank statement with new transactions|This feature enhances existing feature “Reverse posted bank statement”. So, “Reverse posted bank statement” feature must be enabled before this new functionality is enabled. After enabling this feature, when user clicks the “Reverse Statement” button, new transactions posted from bank statements will also be reversed.|
|Cash and bank|Advanced bank reconciliation improvement: enable filtering and provide separate grid for new transactions|When this feature is enabled, in advanced bank reconciliation, filtering will be available for user to select bank statement lines and bank transactions. Meanwhile, a new grid will be available to display bank statement lines marked as new, which are mixed up with matched transactions before.|
|Cash and bank|Enable batch mode for "Mark as reconciled" in advance bank reconciliation|In advanced bank reconciliation, once all matchings are done, user clicks "Mark as reconciled" to complete the reconciliation. If data volume is large, it will take long time for system to complete the reconciliation online, which sometimes results in session timeout. If this feature is switched on, batch processing option will be available for "Mark as reconciled".|
|Cash and bank|Display vouchers in bank statement|When this feature is enabled, in bank statement, user can directly check vouchers from posted new transactions.|


