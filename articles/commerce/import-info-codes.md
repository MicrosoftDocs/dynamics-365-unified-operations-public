---
title: Import info codes
description: This article describes how to import info codes in Microsoft Dynamics 365 Commerce.
author: rgindulin
ms.date: 26/01/2025
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Customer search

[!include [banner](includes/banner.md)]

This article describes customer search capabilities in Microsoft Dynamics 365 Commerce.

Customer search is used to find customers for various purposes. For example, cashiers might want to view a customer's wish list or purchase history, or add the customer to a transaction. Employees can search for customers who are associated with the current store or any other store in the company. Employees can also search for customers who are associated with a different company in the parent organization.  


![Global customer search.](./media/Globalcustomersearch.png "Global customer search")

## Cloud-powered customer search

Public preview of the customer search capability using the Azure Cognitive Search service was released as part of the Commerce 10.0.18 release. In addition to performance improvements, users of the service also benefit from rich refinement and improved relevance capabilities. The performance improvements are especially evident when the global search feature ("Search all stores") of the POS is used, because search results are fetched from the Azure search index instead of queried from the data in Commerce headquarters. 

### Enable the cloud-powered search feature

> [!NOTE]
> It is required that both Commerce headquarters and Commerce Scale Unit are updated to version 10.0.18. Updating the POS is not required.

To enable the cloud-powered search feature in Commerce headquarters, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
1. Find and select the **(Preview) Cloud powered customer search** feature, and then select **Enable now**.
1. Go to **Retail and Commerce > Headquarters setup > Commerce scheduler > Initialize commerce scheduler** and select **OK** to display the new **1010_CustomerSearch** job on the **Distribution schedule** form.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. Run the **1010_CustomerSearch** job. This job publishes the date to the Azure search index. When publishing of the index is completed, the status of the job will be set to **Applied**.
1. After the **1010_CustomerSearch** job status is set to **Applied**, run the **1110 - Global configuration** job to update the POS channels of the newly enabled feature in **Feature management**.
1. Subsequently, run the **1010_CustomerSearch** job at regular intervals to send customer updates to the search index.
