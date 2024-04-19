---
# required metadata
title: What's new or changed in Dynamics 365 Finance 10.0.40 (June 2024)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.40 preview release.
author: twheeloc
ms.date: 4/26/2024
ms.author: twheeloc
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
|Cash and bank management|Bank account lifecycle management|This feature enables approval workflow for bank account activation, modification, and deactivation. It provides bank account change history for auditing purposes. A protected field list is available to control the bank account fields that trigger modification approval workflow. |Feature management|
|Cash and bank management|Customer and vendor netting|This feature enables netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is general available in Dynamics 365 Finance version 10.0.40.|Feature management|
|Accounts receivable |	Improve performance and efficiency of Sales invoice entities.|	To enhance the performance and efficiency of our sales invoice entities, we have made significant improvements by eliminating inefficient views and computed columns. The new entities no longer rely on inefficient views but instead directly fetch all columns from the data sources, allowing for faster data retrieval.|Feature management|	 
|Accounts payable|	Post document with distribution process splitting	|This feature optmizes the memory usage and avoids memory overflow when handling long invoices by splitting the disturbution prcesss as an individual batch tasks. |	Feature management |


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Cash and bank management|Import bank statement|Import bank statements through data entities is supported. **Bank statement header** and **Bank statement lines** data entities are available.|Default on|
|Cash and bank management|Modern bank reconciliation|When the **Modern bank reconciliation** feature is enabled, a redesigned bank reconciliation report is available. The new report saves snapshots by bank reconciliation cut-off date. Both unreconciled transaction details and reconciled transaction details are available on the report.|Feature management|
|Cash and bank management|Modern bank reconciliation| When the **Modern bank reconciliation** feature is enabled, the **Matching ID** field is available. A unique matching ID is generated when bank statement transactions are matched. This ID is displayed on the **Matched transactions** tab.|Feature management|
|Cash and bank management|Modern bank reconciliation| When the **Modern bank reconciliation** feature is enabled, the **Matching type** field is available. **Matching type** indicates how the bank statement transactions are reconciled such as matching with bank document or generate voucher. This ID is displayed on the **Matched transactions** tab.|Feature management|
|Cash and bank management|Modern bank reconciliation|If a bank statement transaction is posted to general ledger as a voucher, relevant company transaction are displayed on the **Company transaction** page.|Feature management|
|Accounts payable|	Vendor invoice center (Preview)|	This feature is enhanced so users can drill down to the detailed invoice list pages by clicking the subtitle number in the new **Vendor invoice center** workspace.| Feature management	|
|Accounts payable (Invoice capture)	|Support line level financial dimensions|	The line level financial dimensions (business unit, cost center, department) have been introduced in Invoice capture with version number 1.3.0.x or higher. To streamline the process, this feature transfers the financial dimensions value from Invoice capture to Dynamics 365 Finance without any additional extensions.	|    |




### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNNNN).
