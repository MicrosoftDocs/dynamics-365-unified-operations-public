---
title: Purge commerce transactions
description: This article describes how to use the Purge commerce transactions capability to delete the old commerce transactions.
author: shajain
ms.date: 12/08/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2024-09-30

---

# Purge commerce transactions

[!include [banner](../includes/banner.md)]

This article details how Dynamics 365 Commerce allows organizations to delete old transactional data when it is no longer needed. 

Retaining large amounts of data in Commerce backend systems can increase data costs and impact system performance. Therefore, organizations often want to remove outdated data. With 10.0.42, Dynamics 365 Commerce provides a feature for organizations to delete old transactional data themselves. A new form called **"Purge commerce sales transactions"** is available under the **Retail and Commerce IT** -> **Clean up** section. By default, this option is hidden, and organizations need to contact the support team to enable it in their environments. In the future, this capability will be enabled by default in all environments. 
Users with the appropriate role can select a date range to delete transactions irrespective of their posting status. Currently, the date range is limited to a maximum of six months at a time, with both dates prior to the previous calendar year. For example, if the current year is 2024, both dates must be from 2022 or earlier. 

> [!NOTE]
> Currently, this feature is available to users with the "Retail operations manager" role, but due to the risk associated with this action since transaction deletion is irreversible, it will soon be restricted to the "Information technology officer" role. 

The purge job runs as a batch job, with only one active job per legal entity. Once complete, the info log for the batch job displays details of the tables and record counts deleted. The purge job does not lock the tables it deletes from, allowing the system to continue using these tables for various business processes. Refer the below image showcasing the Purge commerce sales transactions form details.

 ![Purge commerce transactions](./articles/commerce/media/Purge_commerce_transactions_1.png "Purge commerce transactions")