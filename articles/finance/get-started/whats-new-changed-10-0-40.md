---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.40 (June 2024)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.40 preview release.
author: twheeloc
ms.date: 4/26/2024
ms.topic: faq
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global

---

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.40. This version has a build number of 7.0.NNNN.NN and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** May 2024
- **General availability of release (auto-update):** June 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Cash and bank management|Bank account lifecycle management|This feature enables approval workflow for bank account activation, modification and deactivation. It also provides bank account change history for auditing purpose. Protected field list is available to control the bank account fields to trigger modification approval workflow. |Feature management|
|Cash and bank management|Customer and vendor netting|This feature enables netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is general available in Dynamics 365 Finance version 10.0.40.|Feature management|
|Cash and bank management|Modern bank reconciliation|Redesigned bank reconciliation report is available when feature "Modern bank reconciliation" is turned on. The new report saves snapshots by bank reconciliation cut-off date. Both unreconciled transaction details and reconciled transaction details are available in the report.|Feature management|
|Cash and bank management|Modern bank reconciliation|Matching ID field is available when feature "Modern bank reconciliation" is turned on. A unique matching ID is generated when bank statement transactions are matched. This ID is displayed on matched transaction tab.|Feature management|
|Cash and bank management|Modern bank reconciliation|Matching type field is available when feature "Modern bank reconciliation" is turned on. Matching type indicates how the bank statement transactions are reconciled such as matching with bank document, generate voucher, etc. This ID is displayed on matched transaction tab.|Feature management|


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Cash and bank management|Import bank statement|Importing bank statements through data entities is supported in 10.0.40. Data entities "Bank statement header" and "Bank statement lines" are available now.|Default on|



### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNNNN).
