---
title: Set up service order stages 
description: Learn how to set up service order stages, including a step-by-step process for setting up service order stages and selecting parent stages. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
ms.topic: how-to
ms.date: 07/10/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
---

# Set up service order stages

[!include [banner](../includes/banner.md)]

1. Go to **Service management** \> **Setup** \> **Service orders** \> **Service stages**.

2. Select **New** to create a new record.

3. In the **Service stage** and **Description** fields, specify a service stage ID and description.

4. Select the appropriate parameters for the stage.

5. Select the parent stage for the current stage or leave the **Parent** field blank if the stage is the initial stage in the stage setup.

> [!NOTE]
> You can't modify the **Parent** field after you save the stage. Instead, you can delete the record and create the record again with a different selection in the **Parent** field.
>
> Also, you can only create one stage with a blank **Parent** field. That is, only one initial stage is permitted.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
