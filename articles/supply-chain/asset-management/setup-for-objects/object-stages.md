---
# required metadata

title: Asset lifecycle states
description: This article explains asset lifecycle states and lifecycle models in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetLifecycleModelStateNext, EntAssetObjectLifecycleState, EntAssetLifecycleStateUpdate, EntAssetObjectLifecycleModel
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset lifecycle states

[!include [banner](../../includes/banner.md)]

 

This article explains asset lifecycle states and lifecycle models in Asset Management. Asset lifecycle states are used to define whether an asset is active or inactive. For example, you can set up asset lifecycle states such as **Created**, **Active**, and **Terminated**.

> [!NOTE]
> - Request lifecycle states are linked to asset lifecycle states. Therefore, when a request is changed to a new request lifecycle state, the asset that is attached to the request is changed to a new asset lifecycle state. For example, if the lifecycle state of a request is changed to **Inbound**, the lifecycle state of the attached asset is changed to the lifecycle state that is selected in the **Inbound lifecycle state** field on the **Asset lifecycle state** FastTab of the **Asset lifecycle state models** page. 


Asset lifecycle states can be set up in asset lifecycle models, where you can define the required lifecycle states for various types of assets. You first set up lifecycle states. You then create a lifecycle model and select lifecycle states for it.

1. Select **Asset management** \> **Setup** \> **Assets** \> **Lifecycle states**.
2. Select **New** to create a new asset lifecycle state.
3. In the **Lifecycle state** field, enter the lifecycle state ID.
4. In the **Name** field, enter a description.

    The **Lifecycle models** field shows the number of asset lifecycle models that use the asset lifecycle state.

5. Set the **Active** option to **Yes** if this lifecycle state should be an active lifecycle state (in other words, if work orders can be created for assets that are in this lifecycle state).
6. Set the **Delete open calendar lines** option to **Yes** if open asset calendar lines that have an asset lifecycle state of **Created** should be deleted when they are in this lifecycle state. This setting is useful if you want to clean up any open maintenance schedules that are no longer relevant for the asset (for example, if the asset is no longer active).

> [!NOTE]
> Asset lifecycle states, asset lifecycle models, and asset types are related. They are used in the same way as work order lifecycle states, work order lifecycle models, and work order types. 


After you've created the required asset lifecycle states, you can set up lifecycle states in asset lifecycle models.

1. Select **Asset management** \> **Setup** \> **assets** \> **lifecycle models**.
2. Select **New** to create a new asset lifecycle model.
3. In the **Lifecycle model** field, enter the lifecycle model ID.
4. In the **Name** field, enter a description.

    The **Lifecycle states** field shows the number of asset lifecycle states that are selected in the asset lifecycle model. The **Asset types** field shows the number of asset types that use the lifecycle model.

5. On the **Lifecycle states** FastTab, select the asset lifecycle states that should be included in the asset lifecycle model:

    - To use a lifecycle state for the model, select it in the **Lifecycle states remaining** section, and then select the right arrow button ![Right arrow.](media/15-setup-for-objects.png) to move it to the **Lifecycle states selected** section.
    - To use all the available lifecycle states for the model, select the **All available lifecycle states** button ![All available lifecycle states.](media/20-setup-for-objects.png). All lifecycle states are transferred to the **Lifecycle states selected** section.
    - To remove a lifecycle state from the model, select it in the **lifecycle states selected** section, and then select the left arrow button ![Left arrow.](media/16-setup-for-objects.png) to move it to the **Lifecycle states remaining** section.

6. Select **Lifecycle state updates** to define the asset lifecycle states that can follow a selected lifecycle state.
7. You use the **Asset state** FastTab if you handle assets that you receive for repair. In the **Inbound/outbound** section, you can select asset lifecycle states to indicate the workflow of an asset that you receive for repair. If you offer loan assets to customers or departments, in the **Loan** section, you can select lifecycle states for loan assets.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]