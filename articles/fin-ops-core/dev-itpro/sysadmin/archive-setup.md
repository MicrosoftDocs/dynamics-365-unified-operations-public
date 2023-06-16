---
title: Set up the archive solution
description: This article describes how to set up your system to support archiving of different types of records.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/13/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up the archive solution

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->

## <a name="install-addin"></a>Install the Archive add-in from Lifecycle Services

Before you can enable the archive solution, you must install the *Archive* add-in from Microsoft Dynamics Lifecycle Services.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/).
1. Open the environment details page for your environment.
1. On the **Power Platform integration** FastTab, select **Install a new add-in**.
1. In the list of add-ins, select **(Preview) Archive**.
1. Follow the on-screen instructions.

## <a name="enable-features"></a>Enable the features that you need

After you install the *(Preview) Archive* add-in from Lifecycle Services, you can enable the archiving features that you need. Use the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace to enable the following features as you require:

- *(Preview) Archive* – This feature is required for all archiving scenarios. It provides basic archiving support and adds the **Archive** workspace.
- *(Preview) Ledger archive automation* – This feature moves general ledger records to the relevant history tables. After the data is copied to the history tables, the matching data from the day-to-day general ledger tables is purged. For more information about how to use this feature, see [Archive general ledger data](archive-general-ledger.md).
- *(Preview) Archive sales orders to history tables* – This feature is required for archiving of sales orders. It provides a framework for moving sales orders from day-to-day transaction tables to local history tables. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md).
- *(Preview) Archive sales orders to history tables using archive service* – This feature is required for archiving of sales orders. It moves sales orders from day-to-day transaction tables to history tables. After the data is copied to the history tables, the matching data from the day-to-day transaction tables is purged. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md).

## Next steps

- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Work with the Archive workspace](archive-using.md)
- [Archive sales orders](archive-sales-orders.md)
- [Archive general ledger data](archive-general-ledger.md)
