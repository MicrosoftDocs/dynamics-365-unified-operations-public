---
title: Enable and configure unannounced returns in Warehouse management only mode
description: Learn how to set up Microsoft Dynamics 365 Supply Chain Management to handle unannounced returns when you use Warehouse management only mode. This article highlights aspects of the unannounced returns process that work differently, depending on whether you use Warehouse management only mode.
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

This article explains how to set up Microsoft Dynamics 365 Supply Chain Management to handle unannounced returns when you use Warehouse management only mode. Most aspects of the unannounced returns process work in the same way, regardless of whether you use Warehouse management only mode. This article highlights the differences. Learn more about the unannounced returns process and how to set it up in [Receive unannounced sales returns](sales-returns-unannounced.md).

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.41 or later.

## <a name="source-systems"></a>Set up source systems

To use Warehouse management only mode, you must have at least one *source system*. Each source system record configures the way that a specific external system integrates with Supply Chain Management in Warehouse management only mode.

In [Configure your source systems](wms-only-mode-setup.md#source-systems), you can find general information about how to set up source systems so that they can be used with Warehouse management only mode. The following procedure highlights the settings that are important for unannounced returns.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
1. In the list pane, select the source system that you want to set up. Alternatively, create a new source system 
1. On the **Inbound shipment orders** FastTab, set the following fields to configure the options for unannounced returns:

    - **Enable returns process** – Set this option to *Yes*.
    - **Number sequence code** – Select the number sequence that should be used to generate order numbers for inbound shipment orders that are created during the returns process.
    - **Return order type** – Enter the name that identifies the document type for return orders in the source system. To find the value, consult your external system's documentation.

    > [!IMPORTANT]
    > If your source system is Dynamics 365 Supply Chain Management (as is the case when you run an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse.md)), you must set the **Return order type** field to *Return*, which is the return order type that is used in Supply Chain Management.

1. On the **Outbound shipment orders** FastTab, set the following fields to configure the options for unannounced returns:

    - **Outbound shipment processing policy** – Select a policy where the **Enforce shipment to order matching** option is set to *Yes*. Learn more in [Outbound shipment processing policies](outbound-load-handling.md#outbound-shipment-policies).
    - **Enable return details creation** – If you use return details receiving, set this option to *Yes*. If you use only blind returns, you can save system resources by setting this option to *No*.

## Set up return item receiving policies and mobile device menu items

To enable workers to process unannounced returns in the warehouse, you must set up mobile device menu items and return item receiving policies. The required settings are almost the same as the settings for [receiving unannounced returns](sales-returns-unannounced.md) without Warehouse management only mode. This section points out the differences.

### Return item receiving policies

Return item receiving policies enable each menu item to process the return correctly. You set them up by going to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**. Policies that are used with Warehouse management only mode must have the following settings:

- **Return process** – Select either *Blind return* or *Return details*, depending on the type of return that your menu item should process.
- **Create return order** – Select *Inbound shipment order*.
- **Return order identification** – This field is available only when the **Return process** field is set to *Blind return*. Select the type of extra identifying information that the system should return when it registers a return order with your external system:

    - *None* – The system doesn't return any extra identifying information, and the app doesn't prompt the worker to enter any additional information during receiving.
    - *Account number* – When Supply Chain Management registers a return with your external system, it returns an account number to help identify the return order. The way that you use this value depends on the needs of your external system. (See the documentation for your external system.) It's typically the ID of the customer who is returning the items (their customer account number). The mobile app prompts the worker to scan or enter this number during receiving.

- **Return order type** – This field is available only when the **Return order identification** field is set to *Account number*. Like the account number, the value in this field is returned to the source system when a return is registered with your external system. It's intended to hold the name that identifies the document type for return orders in the source system. The way that you use it depends on the needs of your external system. (See the documentation for your external system.) If you leave this field blank, the value is inherited from the relevant [source system configuration](#source-systems).

> [!IMPORTANT]
> If your source system is Dynamics 365 Supply Chain Management (as is the case when you run an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse.md)), you must set the following values for your blind return policies:
>
> - **Return order identification** – Select *Account number*, and instruct workers to enter the customer ID (account number) when the mobile app prompts them during receiving.
> - **Return order type** – Enter *Return*, which is the return order type that is used in Supply Chain Management. (Alternatively, if *Return* is already specified as the default return order type for the [source system](#source-systems), leave this field blank.)

Learn more in [Create return item receiving policies](sales-returns-unannounced.md#return-receive-policy).

### Mobile device menu items

To create the mobile device menu items that you need, follow the instructions in [Set up mobile device menu items to process unannounced returns](sales-returns-unannounced.md#mdmi). Be sure to configure each menu item so that it uses a return item receiving policy that was set up as described in the previous section.
