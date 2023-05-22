---
title: Set up record archiving
description: This article describes how to set up your system to support archiving of various types of records.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up record archiving

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Intro needed -->

## Prerequisites

<!--KFM: Explain that power platform integration must be complete. Give a link or instructions. -->

## Install the archiving add-in from LCS add-in

To enable the archiving features for finance and operations apps, start by installing the *Archive* add-in from Microsoft Dynamics Lifecycle Services (LCS). Follow these steps to install the add-in:

1. Sign in to [LCS](https://lcs.dynamics.com/).
1. Open your environment page.
1. Open the **Power Platform integration** FastTab.
1. Select **Install a new add-in**.
1. From the list of add-ins select **(Preview) Archive**.
1. Follow the instructions on your screen.

## Enable the features you need

Once you have installed the *(Preview) Archive* add-in from LCS, you'll be able to enable the archiving features you need. Use the [**Feature management** workspace](../../fin-ops/get-started/feature-management/feature-management-overview.md) to enable the following features as needed:

- *(Preview) Archive* – Required for all of the following archiving scenarios. It provides basic archiving support and adds the **Archive** workspace.
- *(Preview) Ledger archive automation* – Archives general ledger records to the relevant history tables. Once archived to history tables, archived data from the day-to-day general ledger tables will be purged. <!--KFM: Add link to scenario topic.  -->
- *(Preview) Archive sales orders to history tables* – Required for archiving sales orders. This feature provides a framework for archiving sales orders from day-to-day transaction tables to local history tables. For more information about how to use this feature, see [Archive sales orders](archiving-sales-orders.md)
- *(Preview) Archive sales orders to history tables using archive service* – Required for archiving sales orders. This feature performs the archiving of sales orders from day-to-day transaction tables to history tables. Once archived to history tables, archived data from the day-to-day transaction tables will be purged. For more information about how to use this feature, see [Archive sales orders](archiving-sales-orders.md)

## Next steps

- [Using Archive](archive-using.md)
- [Archive sales orders](archive-sales-orders.md)
- [Archive general ledger](archive-general-ledger.md)
- 
