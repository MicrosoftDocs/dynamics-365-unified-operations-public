---
title: Enable and configure unannounced returns in Warehouse management only mode
description: Learn how to set up Supply Chain Management to handle unannounced returns when you're using Warehouse management only mode. Most aspects of the unannounced returns process work the same way regardless of whether you're using Warehouse management only mode or not. This article highlights the differences.
author: mq55qm
ms.author: ivanma
ms.reviewer: kamaybac
ms.search.form: WHSSourceSystem, WHSSourceSystemDispositionCode, WHSInboundShipmentOrder, WHSParameters, WHSInboundShipmentOrderMessage, WHSReturnItemReceivingPolicy
ms.topic: how-to
ms.date: 08/05/2024
ms.custom: 
  - bap-template
---

# Enable and configure unannounced returns in Warehouse management only mode

[!include [banner](../includes/banner.md)]

This article explains how to set up Supply Chain Management to handle unannounced returns when you're using Warehouse management only mode. Most aspects of the unannounced returns process work the same way regardless of whether you're using Warehouse management only mode or not. This article highlights the differences. For more information about the unannounced returns process and how to set it up, see [Receive unannounced sales returns](sales-returns-unannounced.md).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.41 or later.

## <a name="source-systems"></a>Set up source systems

To use Warehouse management only mode, you must have at least one *source system* set up. Each source system record configures the way a specific external system integrates with Supply Chain Management in Warehouse management only mode.

For general information about how to set up source systems for use with Warehouse management only mode, see [Configure your source systems](wms-only-mode-setup.md#source-systems). The following procedure highlights the settings that are important for setting up unannounced returns.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
1. Either select the source system you want to set up from the list pane or create a new one. 
1. On the **Inbound shipment orders** FastTab, set up unannounced returns options by making the following settings:
    - **Enable returns process** – Set to *Yes*.
    - **Number sequence code** – Select the number sequence that should be used to generate order numbers for inbound shipment orders created during the returns process.
    - **Return order type** – Enter the name used to identify the document type for return orders in the source system. Refer to your external system's documentation to find this value.
  
    > [!IMPORTANT]
    > If your source system is Dynamics 365 Supply Chain Management (as it would be when running an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse.md)), then you must set **Return order type** to `Return` because that's the return order type used in Supply Chain Management.

1. On the **Outbound shipment orders** FastTab, set up unannounced returns options by making the following settings:
    - **Outbound shipment processing policy** – Select a policy that has **Enforce shipment to order matching** set to *Yes*. See also [Outbound shipment processing policies](outbound-load-handling.md#outbound-shipment-policies)
    - **Enable return details creation** – If you're using return details receiving, set this to *Yes*. If you only use blind returns, then you can save system resources by setting this to *No*.

## Set up return item receiving policies and mobile device menu items

To enable workers to process unannounced returns in the warehouse, you must set up mobile device menu items and return item receiving policies. The required settings are nearly the same as those used for [receiving unannounced returns](sales-returns-unannounced.md) without Warehouse management only mode; this section points out the differences.

### Return item receiving policies

Return item receiving policies enable each menu item to process the return correctly. You set them up by going to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**. Policies for use with Warehouse management only mode must use the following settings:

- **Return process** – Set to either *Blind return* or *Return details*, depending on the type of return your menu item should process.
- **Create return order** – Set to *Inbound shipment order*.
- **Return order identification** – This field is visible when **Return process** is set to *Blind return*. Set it to one of the following values
    - *None* – The system doesn't return any extra identifying information when registering return orders with your external system. The app won't ask the worker to enter any additional information during receiving.
    - *Account number* – When Supply Chain Management registers the return with your external system, it returns an account number to help identify the return order. The way you use it depends on the needs of your external system (see the documentation for your external system). This could typically be the ID of the customer who is returning the items (their customer account number). The mobile app will ask the worker to scan or enter this number during receiving.

- **Return order type** – This field is visible when **Return order identification** is set to *Account number*. Like the account number, the value in this field is returned to the source system when registering the return with your external system. It's intended to hold the name used to identify the document type for return orders in the source system. The way you use it depends on the needs of your external system (see the documentation for your external system). If you leave this blank, then this setting will be inherited from the relevant [source system configuration](#source-systems).

> [!IMPORTANT]
> If your source system is Dynamics 365 Supply Chain Management (as it would be when running an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse.md)), then you must set the following values for your blind return policies:
>
> - **Return order identification** – Set to *Account number* and instruct workers to enter the customer ID (account number) when prompted by the mobile app during receiving.
> - **Return order type** – Set to `Return` because that's the return order type used in Supply Chain Management (or leave it blank if `Return` is already specified as the default for the [source system](#source-systems)).

For more information, see [Create return item receiving policies](sales-returns-unannounced.md#return-receive-policy).

### Mobile device menu items

Follow the instructions given in [Set up mobile device menu items to process unannounced returns](sales-returns-unannounced.md#mdmi) to create the mobile device menu items you'll need. Be sure to configure each of them to use a return item receiving policy set up as described in the previous section.
