---
title: Define a tax configuration and deploy it to legal entities
description: Learn how to define a tax configuration, and then deploy it to one or more legal entities, including a process for updating the configuration version.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Define a tax configuration and deploy it to legal entities

[!include [banner](../../includes/banner.md)]

1. Go to **Tax** > **Setup** > **Tax Configuration** > **Tax Setup**.
1. Select **New**.
1. In the **Tax Setup** field, enter a value.
1. In the **Description** field, enter a value, and then select **Save**.
1. Select **Configurations**.
1. On the **Tax configuration** tab, in the **Available configurations** section, select **New**.
1. In the **Configuration version** field, select a value.

    The new tax configuration appears in the **Available configurations** grid.

    :::image type="content" source="../media/configuration-version_upd.png" alt-text="Screenshot of selecting a configuration version.":::

1. Select **Save**, and then select **Synchronize**.
1. Select **Activate**.

    :::image type="content" source="../media/active_upd.png" alt-text="Screenshot of the active configuration.":::

    The configuration that you activated becomes the current configuration. 
    > [!NOTE]
    > Mark **Skip model mapping** if the configuration is the standard configuration (which Microsoft provides), or extended configuration without adding or modifying model mapping.

1. Select the **Report configurations** tab.

    The **Available configurations** grid lists the configurations that are related to the report.

1. Select the **Select** check box.
1. In the **Report controller** field, select a value.
1. Select **Save**, and then select **Close**.
1. On the **Companies** FastTab, create a record.
1. In the **Companies** field, select a value.

    > [!NOTE]
    > Assign only one legal entity to each tax configuration.

1. Save the record.
1. Select **Activate** to activate the configuration for the company.

    :::image type="content" source="../media/gst-company_upd.PNG" alt-text="Screenshot of the GST company configuration.":::

## Update the configuration version

1. Select **Deactivate**.
1. Select **Configurations**.
1. On the **Tax configuration** tab, in the **Available configurations** section, select **New**.
1. In the **Configurations** field, select a value.  

    The new tax configuration appears in the **Available configurations** grid.

    :::image type="content" source="../media/update-configuration.png" alt-text="Screenshot of updating the configuration.":::

1. Select **Save**.
1. Select the record, and then select **Synchronize**.
1. Select **Activate**.

    The configuration that you activated becomes the current configuration.

1. Select **Save**, and then select **Close**.

    :::image type="content" source="../media/update-configuration-2.png" alt-text="Screenshot of the new active configuration.":::


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
