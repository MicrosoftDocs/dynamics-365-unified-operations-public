---
title: Control raw material consumption by using flushing principles
description: This article describes the four flushing principles that are used for raw material consumption.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: JmgShopSupervisorReleaseOrders
ms.topic: how-to
ms.date: 12/08/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Control raw material consumption by using flushing principles

[!include [banner](../includes/banner.md)]

Flushing principles reflect different consumption strategies for raw materials that are used in production processes. Consumption is the process that deducts material from the on-hand inventory and sets the value of the consumed materials to *Work in progress* (WIP) for production orders and batch orders. Raw materials are usually consumed from a location that is configured for the process that consumes the material. This location is known as the production input location.

Before material consumption, the materials are moved to the input location. The following illustration shows the process.

![Before material consumption, the materials are moved to the input location.](media/scenario4a.png "Before material consumption, the materials are moved to the input location")

The following elements are shown in the illustration:

1. Material warehouse
2. Raw material picking
3. Production input location
4. Raw material consumption
5. Production process

Material consumption is controlled by the following four flushing principles:

- Manual
- Start
- Finish
- Available at location

The flushing principles are configured in a hierarchy of default values. The hierarchy starts at the released product, where the flushing principle has the value *Start*. On the bill of materials (BOM) or formula line, the flushing principle from the product can be overridden. The default flushing principle on the production BOM lines or batch order formula lines is taken from the product or the overridden value on the BOM or formulas.

## Description of the flushing principles

### Manual

The *Manual* flushing principle indicates that the registration of material consumption is a manual operation. This principle is relevant if, for example, you want to be able to track time, and the quantity of consumed batch numbers or serial numbers must be accounted for, for tracking purposes. Manual consumption is registered in a production picking list journal. For items that are enabled for warehouse management processes (WMS), a hand-held flow can be applied.

### Start

The *Start* flushing principle indicates that material will be automatically consumed when the production order is started. The amount of material that is consumed is proportional to the quantity that is started. When the Start flushing principle is used together with the manufacturing execution system, it can also be used to flush materials when an operation or a process job is started. This principle is relevant if, for example, the variance in the consumption is low, the materials are low-value materials, there are no tracking requirements, or there's a short run time on operations.

### Finish

The *Finish* flushing principle indicates that material will be automatically consumed when the production order is reported as finished, or when an operation that is set up to consume the materials is registered as completed. The amount of material that is consumed is proportional to the quantity that is reported as finished. When the *Finish* flushing principle is used together with the manufacturing execution system, it can also be used to flush materials when an operation or a process job is completed. This principle is relevant in the same situations as the Start principle. However, the *Finish* principle is for operations that have a longer run time, where materials shouldn't be set to *Work in progress* before the operation is completed.

> [!NOTE]
> You can't use the *Finish* flushing principle together with planning items. Instead, we recommend that you use the *Start* flushing principle. Planning items have a production type of *Planning item*, and only co-products and by-products can be reported as finished on batch orders that are created for planning items.

### Available at location

The *Available at location* flushing principle indicates that the material will be automatically consumed when it's registered as picked for production. The material is registered as picked from location when work for the raw material picking is completed, or when material is available on the production input location and the material line is released to the warehouse. The picking list that is generated during the process is posted in a batch job. This principle is relevant if, for example, you have many picking activities against one production order. In this case, you don't have to update the picking list manually, and you can get a current view of the WIP balance. 

> [!NOTE]
> The *Available at location* flushing principle only applies for products that are enabled for warehouse management processes (WMS).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
