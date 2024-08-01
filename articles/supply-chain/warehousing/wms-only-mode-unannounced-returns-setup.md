---
title: Configure unannounced returns in Warehouse management only mode
description: Learn how to set up unannounced returns when you are using Warehouse management only mode. Most aspects of the unannounced returns process work the same way regardless of whether you're using Warehouse management only mode or not. This article highlights the differences.
author: mq55qm
ms.author: ivanma
ms.topic: how-to
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSSourceSystemDispositionCode, WHSInboundShipmentOrder, WHSParameters, WHSInboundShipmentOrderMessage, WHSReturnItemReceivingPolicy
ms.topic: how-to
ms.date: 08/01/2024
ms.custom: 
  - bap-template
---

# Configure unannounced returns in Warehouse management only mode

[!include [banner](../includes/banner.md)]

This article explains how to set up unannounced returns when you are using Warehouse management only mode. Most aspects of the unannounced returns process work the same way regardless of whether you're using Warehouse management only mode or not. This article highlights the differences. For more information about the unannounced returns process and how to set it up, see [Receive unannounced sales returns](sales-returns-unannounced.md).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.

<!--KFM: I removed mentions of enabling WMO mode and/or external warehouse. I think that's implied for all topics in this area of the TOC. -->

## Source system configuration

To use Warehouse management only mode, you must have at least one *source system* set up. Each source system record configures the way a specific external system integrates with Supply Chain Management in Warehouse management only mode. Follow these steps to configure the options that are related to unannounced returns.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
1. Either select the source system you want to set up from the list pane or create a new one. For details, see [Configure your source systems](wms-only-mode-setup.md#source-systems).
1. On the **Inbound shipment orders** FastTab, set up unannounced returns options by making the following settings:
    - **Enable returns process** – Set to *Yes*.
    - **Number sequence code** – Select the number sequence that should be used to generate order numbers for inbound shipment orders created during the returns process.
    - **Return order type** – Enter the name used to identify return orders in the source system. Refer to your external system's documentation to find this value.
  
    > [!IMPORTANT]
    > If your source system is Dynamics 365 Supply Chain Management (as it would be when running an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse)), then you must set **Return order type** to `Return` because that's the return order type used in Supply Chain Management.

1. On the **Outbound shipment orders** FastTab, set up unannounced returns options by making the following settings:
    - **Outbound shipment processing policy** – Select a policy that has **Enforce shipment to order matching** set to *Yes*. See also [Outbound shipment processing policies](outbound-load-handling.md#outbound-shipment-policies)
    - **Enable return details creation** – If you're using return details receiving, set this to *Yes*. <!--KFM: Always *No* for blind returns? -->

## Mobile device menu item configuration

To enable workers to process unannounced returns in the warehouse, you must set up mobile device menu items and return item receiving policies for blind returns and/or return details receiving. The required menu items are nearly the same as those used for [receiving unannounced returns](sales-returns-unannounced.md) without Warehouse management only mode. This section points out the differences.

### Return item receiving policy

Return item receiving policies enable each menu item to process the return correctly. You set them up by going to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**.

When setting up policies for use with Warehouse management only mode, you must use return receiving policies that have the following settings:

- **Return process** – Set to either *Blind return* or *Return details*, depending on the type of return you're menu item should process.
- **Create return order** – Set to *Inbound shipment order*.
- **Return order identification** – This field is visible when **Return process** is set to *Blind return*. Set it to one of the following values
    - *None* – The system doesn't use any specific identification method. The app won't ask the worker to enter any additional information during receiving.
    - *Account number* – The system uses an account number to identify the return order. The app will ask the worker to enter the account number during receiving.
- **Return order type** – This field is visible when **Return order identification** is set to *Account number*. Enter the name used to identify return orders in the source system. Refer to your external system's documentation to find this value. If you leave this blank, then this setting will be inherited from the relevant [source system configuration](wms-only-mode-setup.md#source-systems).

> [!IMPORTANT]
> If your source system is Dynamics 365 Supply Chain Management (as it would be when running an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse)), then you must set **Return order type** to `Return` because that's the return order type used in Supply Chain Management (or leave it blank if `Return` is already specified as the default for the source system).

For more information, see [Create return item receiving policies](sales-returns-unannounced.md#return-receive-policy).

### Mobile device menu items

Follow the instructions given in [Set up mobile device menu items to process unannounced returns](sales-returns-unannounced.md#mdmi) to create the mobile device menu items you'll need. Be sure to configure each of them to use a return item receiving policy configured as described in the previous section.
