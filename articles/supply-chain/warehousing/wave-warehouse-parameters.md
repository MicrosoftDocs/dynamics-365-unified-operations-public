---
# required metadata

title: Warehouse parameters for wave processing
description: This topic describes how to set up warehouse parameters for wave processing. You can use wave processing to group picking work for multiple work orders into a single wave.
author: Mirzaab
ms.date: 03/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-08
ms.dyn365.ops.version: 10.0.18
---

# Warehouse parameters for wave processing

[!include [banner](../includes/banner.md)]

This topic describes how to set up warehouse parameters for wave processing. You can use wave processing to group picking work for multiple work orders into a single wave.

To use wave processing, specify the following on the **Warehouse management parameters** page:

- If you can process waves by using a batch job.
- If you collect information in a log file when waves are processed.

## Set up warehouse management parameters for wave processing

To set up warehouse parameters for wave processing, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.

1. On the **Wave processing** FastTab, make the following settings:

    - **Wave processing batch group** - Select the batch group to use when you process waves by using batch jobs. The batch group specifies the server that batch jobs will run on.
    - **Process waves in batch** - Choose whether to enable waves to be automatically processed by a batch job. You must set this to *Yes* to use parallel processing. You set up the batch job on the **Process waves** page. (See also the note at the end of this list.)
    - **Create wave progress log** - Choose whether the system should generate a log record every time allocation for an item and its dimensions begins and ends. You should only enable this log when you need it, for example, during initial testing or for troubleshooting. For more information, see [Wave allocation](wave-allocation-method.md).
    - **Create wave processing history log** - Choose whether to automatically save information about a wave in a log file after the wave is processed, including during the parallel processing of pending allocations. Typically you should only enable this during troubleshooting because it adds extra overhead. To view the log, go to **Warehouse management \> Outbound waves \> Wave processing history log**. For more information, see [Wave creation and processing](wave-processing.md).
    - **Create containerization history log** - Choose whether to automatically save information about containerization for a wave in a log file after the wave is processed. To view the log, go to **Warehouse management \> Packing and containerization \> Containerization history**.
    - **Wait for lock (ms)** - Enter the time, in milliseconds, that an allocation step will wait for a system resource that is locked by another allocation step. When this time is exceeded, the wave is not processed and an error message is displayed.

1. On the **Release to warehouse** FastTab, make the following setting:

    - **Error on batch failure** - Choose whether to generate an error when a release to warehouse batch job fails. If this is enabled, failed jobs will end with a status of *Error*. If this is disabled, failed jobs will end with a status of *Ended*.

> [!NOTE]
> On the wave template that is used to process the wave, you can specify the settings that automate wave processing. If you set up a schedule for the batch job, you should coordinate the timing with the settings for automation in the wave template. For more information, see [Create a wave template](wave-templates.md).
>
> If you are using *Transportation management* and *Advanced warehouse management*, you can specify whether to consolidate loads when you process a wave. For example, this is useful when several small loads can be shipped at the same time. To consolidate loads when you process a wave, on the **Loads** tab, select the **Consolidate loads during wave processing** check box.</P>

## Set up full or partial reservation for production waves

For sales orders and kanban orders, inventory must be reserved before the order is released to the warehouse. Otherwise, the items or allocation lines cannot be processed in a wave. However, production orders are slightly more flexible. For production orders, you can specify the following:

- Allow production orders to be released to the warehouse although all materials cannot be reserved. If you select this option, you must manually repeat the release to warehouse process when the additional materials become available. For example, this is useful if you have the materials that you need to start a production, and can wait until the additional materials become available.
- Require that all materials are reserved before an order can be released to the warehouse.

To require full reservation or allow partial reservation, follow these steps:

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. On the **General** tab, in the **Release to warehouse** field, select the default setting.
