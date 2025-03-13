---
title: Configure transfer order receiving process
description: Learn how to configure the receiving process for a warehouse.
author: Samuel Oliveira
ms.author: sservulo
ms.topic: conceptual
ms.date: 03/10/2025
ms.custom: bap-template
ms.reviewer: TBD
ms.search.form: WHSParameters, WHSTransferOrderReceivingProcess, WHSTransferOrderReceivingASNCleanupPolicy
---

# Configure transfer order receiving process

This article explains how to configure the receiving process for a warehouse. It includes information about parameters available to warehouse receiving and how to configure them.

## Warehouse transfer order receiving parameters

### Transfer order receiving process

This parameter makes it possible to split the registration and cost-update processes for transfer orders, which lets receiving clerks use the Warehouse Management mobile app to update a transfer order receipt without waiting for any financial background processing, regardless of the receiving flow. If the process is split, the transfer order receiving can be done manually or as part of a scheduled batch job after the registration.

Available options and effect to the system:
|*Option*|*Effect*|
|---|---|
|Combine the registration and receiving|Both registration and receiving are executed together.|
|Split the registration and receiving for license plate receiving|Registration and receiving are executed separately for license plate receiving.|
|Split the registration and receiving for all flows|Registration and receiving are executed separately for all flows.<br/> Note: Choosing Split the registration and receiving for all flows option is recommended. This option was introduced to cover all flows, as Split the registration and receiving for license plate applies only to that particular case.|

To change this parameter, go to the **Warehouse management parameters** \> **General** \> **Receiving** and set `Transfer order receiving process` to the required value.

### Transfer order receiving ASN cleanup

This parameter changes when the associated ASN data is deleted during the transfer order receiving process. It was introduced to cover scenarios where ASN data is required beyond default settings on the receiving process, for example when partially receiving a transfer order with multiple license plates from both mobile device and form.

Available options and effect to the system:
|*Option*|*Effect*|
|---|---|
|Default|ASN is deleted in the following cases:<br/> - On put away work creation or cancellation;<br/> - On mobile application receiving, if work policy is set to not create work;<br/> - On transfer order line registration from the form;<br/> - On transfer order receipt posting;|
|On transfer order status received|ASN is deleted in the following cases:<br/> - On put away work creation or cancellation;<br/> - On mobile application receiving, if work policy is set to not create work;<br/> - When transfer order status is updated to "Received";|

To change this parameter, go to the **Warehouse management parameters** \> **General** \> **Receiving** and set `Transfer order receiving ASN cleanup` to the required value.

This parameter requires Supply Chain Management version 10.0.44 or later.

## More information

- For more information about license plate receiving using mobile device, see [License plate receiving via the Warehouse Management mobile app](warehousing-mobile-device-app-license-plate-receiving.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
