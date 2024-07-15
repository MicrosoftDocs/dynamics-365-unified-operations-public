---
title: What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.41 preview release distributed in September 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 7/28/2024
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)


[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.41. This version has a build number of 10.0.xxxxx and is available on the following schedule:

- **Preview of release:** July 2024
- **General availability of release (self-update):** September 2024
- **General availability of release (auto-update):** October 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Fixed assets |Consider split transaction in derived books posting (Public preview)|This feature automates the process of posting split transactions from the main book to specified derived books, based on configuration set up in the **Asset book** page. The configuration in the **Asset book** page defines how transactions should be posted based on transaction type. After the feature is enabled, split transactions are automatcially posted according to the predefined settings, eliminating the need for manual intervention.| Feature management |
|Fixed assets |Allow depreciation when placed in service and disposal are in the same fiscal year (Pubic preview)|This feature propagates allow depreciation when assets are placed in service and disposed in the same fiscal year option on the **Fixed assets parameters** page. When **Allow depreciation when placed in service and disposal are in the same fiscal year** option is enabled in the **Fixed assets parameters**,  depreciation calculations proceed when an asset is both placed into service and disposed of within the same fiscal year. This setting becomes the default behavior for any new asset books created. Any changes made at the asset book level applies to new asset books created after the modification and don't retroactively affect existing asset books. |Feature management |
|Fixed assets |Lease import framework update|This feature involves enhancements made to the Asset leasing's lease import framework affects two tables: AssetLeaseLeaseImportHeader and AssetLeaseLeaseDetailsImport. Additional functionality allows for easier deletion in the lease import records. | |
|General ledger |Validation feature for year-end close process|This feature validates the year-end closing to detect issues and suggests a resolution. It ensures accurate ledger balances in both accounting and reporting currencies and advises best practices for managing large dimension sets.  |  |
