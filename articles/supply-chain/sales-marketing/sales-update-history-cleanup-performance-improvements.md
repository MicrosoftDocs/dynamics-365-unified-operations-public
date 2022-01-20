---
title: Sales history cleanup performance improvements
description: This topic describes the sales history cleanup performance improvements feature and how to enable it.
author: myvakalo
ms.date: 10/05/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-09-29
ms.dyn365.ops.version: 10.0.19
---

# Sales history cleanup performance improvements

[!include [banner](../includes/banner.md)]

The **Sales update history cleanup** periodic batch job can take a long time if it is run infrequently on environments with a high volume of sales updates. In these situations, the *Sales history cleanup performance improvements* feature can help reduce the run duration and improve reliability.

The feature improves the existing cleanup job in the following ways:

- It splits the clean-up into batches (you can change the batch size through customizations).
- It will run for a maximum of 2 hours (you can change the duration through customizations).
- Where possible, it leverages database capabilities to minimize locking contention and avoid joining transactional tables during cleanup.

After enabling the feature, the **Sales update history cleanup** batch job (**Sales and marketing \> Period tasks \> Cleanup \> Sales update history cleanup**) will run as it did before, but with better performance and for a maximum of 2 hours. This means it might need to run several times to clean up all the data for a specific retention time frame.

## Turn on the sales history cleanup performance improvements feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Sales and marketing*
- **Feature name:** *Sales history cleanup performance improvements*
