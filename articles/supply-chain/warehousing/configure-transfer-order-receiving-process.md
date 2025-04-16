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

This article explains how to configure the receiving process for a warehouse. It includes information about parameters available to warehouse receiving and how to configure them.

## Prerequisites

The **Transfer order receiving process** setting is a standard part of all current versions of Supply Chain Management. However, for the **Transfer order receiving ASN cleanup** setting to be available, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.

## Configure the receiving process for a warehouse

To configure the receiving process for a warehouse, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**
1. Open the **General** tab.
1. Make the following settings on the **Receiving** FastTab.
    - **Transfer order receiving process** – This setting lets you choose to split the registration and cost-update processes for transfer orders, which lets receiving clerks use the Warehouse Management mobile app to update a transfer order receipt without waiting for any financial background processing, regardless of the receiving flow. If the process is split, the transfer order receiving can be done manually or as part of a scheduled batch job after the registration. Choose one of the following options:
        - *Combine the registration and receiving* – Execute registration and receiving together.
        - *Split the registration and receiving for license plate receiving* – Execute registration and receiving separately for license plate receiving.
        - *Split the registration and receiving for all flows* – Execute registration and receiving separately for all flows.  

        **Note:** We recommend using the *Split the registration and receiving for all flows* option because it covers all flows, while the *Split the registration and receiving for license plate* option applies only to that particular case.

    - **Transfer order receiving ASN cleanup** – This setting lets you choose when the associated advance shipping notice (ASN) data is deleted during the transfer order receiving process. It covers scenarios where ASN data is required beyond default settings on the receiving process, for example when partially receiving a transfer order with multiple license plates using both the Warehouse Management mobile app and the web client. Choose one of the following options:
        - *Default* – ASN is deleted in the following cases:  
            - On putaway work creation or cancellation.  
            - On mobile application receiving, if the work policy is set to not create work.  
            - On transfer order line registration from the web client.  
            - On transfer order receipt posting.  

        - *On transfer order status received* – ASN is deleted in the following cases:  
            - On putaway work creation or cancellation.  
            - On mobile application receiving, if work policy is set to not create work.  
            - When transfer order status is updated to *Received*.

## Related information

- For more information about license plate receiving using mobile device, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md).
