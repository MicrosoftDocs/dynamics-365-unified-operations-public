---
title: Tax engine import configuration
description: Learn about import tax engine configuration, including a step-by-step process for creating a Lifecycle Services configuration repository.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 07/31/2026
ms.reviewer: twheeloc
audience: IT Pro 
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, GTE
ms.dyn365.ops.version: 7.3
---

# Tax engine import configuration

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

This article provides information about import tax engine configuration.

### Create a Lifecycle Services (LCS) configuration repository

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. In the **Configuration providers** section, click **Repositories** on the **Microsoft** provider tile.

![Configuration providers tile with Repositories link highlighted.](../general-ledger/media/gte-extension-repositories.png)

1. Click **Add**.
2. Select the **LCS** option.
3. Click **Create repository** to create an LCS configuration repository.
4. Enter a name and description for the repository and then click **OK**.

### Import configurations from LCS

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. In the **Configuration providers** section, click **Repositories** on the **Microsoft** provider tile.
3. Select the configuration repository that you just created.
4. Click **Open**.
5. In the tree, select the latest tax document (for example, select **Tax (India GST)**).
6. In the **Versions** section, click **Import**.

![Configuration repository page](../general-ledger/media/gte-extension-import-configurations.png)

1. Click **Yes** to confirm the import.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
