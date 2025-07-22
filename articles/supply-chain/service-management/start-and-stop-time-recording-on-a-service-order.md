---
title: Start and stop time recording on a service order 
description: Learn how to start and stop time recording on a service order, including step-by-step processes for starting and stopping time recording.
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

# Start and stop time recording on a service order

[!include [banner](../includes/banner.md)]

Use this procedure to start and stop time recording for a service order for which a service level agreement is defined.

## Start time recording

1. Go to **Service management** \> **Service orders** \> **Service orders**.

2. Select the **Service order** tab. On the Action Pane, in the **Service level agreement** group, select **Start**.

3. Enter the date and time that the time recording should be started.

## Stop time recording

1. Go to **Service management** \> **Service orders** \> **Service orders**.

2. Select the **Service order** tab. On the Action Pane, in the **Service level agreement** group, select **Stop**.

3. Enter the date and time that the time recording should be stopped.

4. Select **Add a revocation reason**, and select a reason code in the **Stage reason code** list to provide a reason for stopping the time recording.

> [!NOTE]
> If **Reason code on exceeding time** is selected on the **Service management parameters** page, you must provide a reason code before you can stop the time recording.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
