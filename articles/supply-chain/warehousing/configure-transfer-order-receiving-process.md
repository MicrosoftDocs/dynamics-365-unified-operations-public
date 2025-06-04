---
title: Configure the transfer order receiving process
description: Learn how to configure the receiving process for a warehouse.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSParameters, WHSTransferOrderReceivingProcess, WHSTransferOrderReceivingASNCleanupPolicy
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Configure the transfer order receiving process

[!include [banner](../includes/banner.md)]

This article explains how to configure the receiving process for a warehouse. It includes information about the parameters that are available for warehouse receiving and how to configure them.

## Prerequisites

Two fields are used to configure the receiving process. The **Transfer order receiving process** field is a standard part of all current versions of Microsoft Dynamics 365 Supply Chain Management. However, the **Transfer order receiving ASN cleanup** field requires Supply Chain Management version 10.0.44 or later.

## Configure the receiving process for a warehouse

To configure the receiving process for a warehouse, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **General** tab, on the **Receiving** FastTab, set the following fields:

    - **Transfer order receiving process** – Specify whether the registration and cost-update processes should be split for transfer orders.

        When the processes are split, receiving clerks can use the Warehouse Management mobile app to update a transfer order receipt without waiting for any financial background processing, regardless of the receiving flow. After the registration is completed, transfer order receiving can be done either manually or as part of a scheduled batch job.

        Select one of the following options:

        - *Combine the registration and receiving* – Run registration and receiving together.
        - *Split the registration and receiving for license plate receiving* – Run registration and receiving separately for license plate receiving.
        - *Split the registration and receiving for all flows* – Run registration and receiving separately for all flows.

        > [!NOTE]
        > We recommend that you select the *Split the registration and receiving for all flows* option, because it covers all flows. By contrast, the *Split the registration and receiving for license plate receiving* option covers only license plate receiving.

    - **Transfer order receiving ASN cleanup** – Specify when associated advance shipping notice (ASN) data should be deleted during transfer order receiving.

        This field covers scenarios where ASN data is required beyond the default settings of the receiving process. For example, it's applicable when you use both the Warehouse Management mobile app and the web client to partially receive a transfer order that has multiple license plates.

        Select one of the following options:

        - *Default* – ASN data is deleted when the following events occur:

            - Putaway work creation or cancellation
            - Mobile application receiving, if the work policy is set not to create work
            - Transfer order line registration from the web client
            - Transfer order receipt posting

        - *On transfer order status received* – ASN data is deleted when the following events occur:

            - Putaway work creation or cancellation
            - Mobile application receiving, if the work policy is set not to create work
            - Update of the transfer order status to *Received*

## Related information

- Learn more about how to use a mobile device for license plate receiving in [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md).
