---
title: Set up the archive solution
description: This article describes how to set up your system to support archiving of various types of records.
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

## Install the archiving add-in from LCS add-in

To enable the archiving solution, start by installing the *Archive* add-in from Microsoft Dynamics Lifecycle Services (LCS). Follow these steps to install the add-in:

1. Sign in to [LCS](https://lcs.dynamics.com/).
1. Open your environment page.
1. Open the **Power Platform integration** FastTab.
1. Select **Install a new add-in**.
1. From the list of add-ins select **(Preview) Archive**.
1. Follow the instructions on your screen.

## Enable the features you need

Once you have installed the *(Preview) Archive* add-in from LCS, you'll be able to enable the archiving features you need. Use the [**Feature management** workspace](../../fin-ops/get-started/feature-management/feature-management-overview.md) to enable the following features as needed:

- *(Preview) Archive* – Required for all of the following archiving scenarios. It provides basic archiving support and adds the **Archive** workspace.
- *(Preview) Ledger archive automation* – Moves general ledger records to the relevant history tables. Once the data is copied to the history tables, the matching data from the day-to-day general ledger tables is purged. For more information about how to use this feature, see [Archive general ledger data](archive-general-ledger.md)
- *(Preview) Archive sales orders to history tables* – Required for archiving sales orders. This feature provides a framework for moving sales orders from day-to-day transaction tables to local history tables. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md)
- *(Preview) Archive sales orders to history tables using archive service* – Required for archiving sales orders. This feature performs the moving of sales orders from day-to-day transaction tables to history tables. Once the data is copied to the history tables, the matching data from the day-to-day transaction tables is purged. For more information about how to use this feature, see [Archive sales orders](archive-sales-orders.md)

## Next steps

- [Extend the archive solution to support custom tables and fields](archive-customizations.md)
- [Work with the Archive workspace](archive-using.md)
- [Archive sales orders](archive-sales-orders.md)
- [Archive general ledger data](archive-general-ledger.md)
