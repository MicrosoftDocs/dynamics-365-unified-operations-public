---
title: Purge Commerce transactions
description: Learn how to use the Purge Commerce sales transactions capability to delete old transactional data that's no longer needed in Microsoft Dynamics 365 Commerce.
author: shajain
ms.date: 12/10/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2024-09-30

---

# Purge Commerce transactions

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes how to use the Purge Commerce sales transactions capability to delete old transactional data that is no longer needed in Microsoft Dynamics 365 Commerce.

Because the retention of large amounts of data in Commerce back-end systems can increase data costs and affect system performance, organizations often want to remove outdated data. The Commerce version 10.0.42 release gives organizations the capability to delete old transactional data themselves. The **Purge commerce sales transactions** dialog box is available in Commerce headquarters at **Retail and Commerce IT** \> **Clean up** \> **Purge commerce sales transactions**. However, it's hidden by default. Organizations that run Commerce version 10.0.42 must contact the Microsoft Support team to enable the capability in their environments. In later Commerce releases, this capability is enabled by default in all environments.

Users who have the appropriate role can select a date range for the deletion of transactions regardless of their posting status. Currently, the date range is limited to a maximum of six months at a time, and both the start and end dates must be before the previous calendar year. For example, if the current year is 2024, both the start and end dates of the date range must be in 2022 or earlier.

> [!NOTE]
> Currently, this capability is available only to users who are assigned the **Retail operations manager** role. However, because of the risks that are associated with irreversible transaction deletion, in later releases, this capability will be restricted to users who are assigned the **Information technology officer** role.

The purge job runs as a batch job. There can be only one active job per legal entity. After the purge batch job is completed, the information log for the job shows details of the tables and record counts that were deleted. The purge job doesn't lock the tables that it deletes transactions from. Therefore, the system can continue to use those tables for other business processes.

The following image shows an example of the **Purge commerce sales transactions** dialog box, the navigation that is used to open it, and the details of the purge batch job that runs.

![Screenshot that shows the Purge commerce transactions dialog box, the navigation to it, and the details of the purge batch job.](media/Purge_commerce_transactions_1.png)
