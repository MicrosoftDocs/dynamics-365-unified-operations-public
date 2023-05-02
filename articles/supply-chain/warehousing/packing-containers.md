---
title: Pack containers for shipment
description: This article describes the packing process that lets you validate inventory items and pack them into containers.
author: perlynne
ms.date: 7/13/2022
ms.topic: how-to
ms.search.form: WHSLocationType, WHSLocationProfile, WHSParameters, WHSContainerType, WHSPackProfile, WHSCloseContainerProfile, InventLocationIdLookup, UnitOfMeasureLookup, WHSPack, WHSContainerTable, WHSPackingSlipPostingParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Pack containers for shipment

[!include [banner](../../includes/banner.md)]

The container packing process lets you validate inventory items and pack them into containers. During this process, warehouse workers typically pick inventory items from bulk storage areas and move them to a packing area. There, multiple warehouse workers check the item quantities and types, and assign them to appropriate container sizes. When a container is fully packed, it's closed and moved to the outbound dock area, where it's made ready for shipment.

Containers represent physical structures that items are packed in, and you can track container information in the system. This information can be useful during transportation planning, especially if you calculate shipping charges based on containers. Before you ship, you can view the number of containers that are used in a shipment, the types of containers that are used, and the physical dimensions of each container (such as the total volume and weight).

Several related outbound warehouse capabilities can be used with containers. For more information, see the following articles:

- [Wave containerization](wave-containerization.md)
- [Outbound sorting](outbound-sorting.md)
- [Small parcel shipping](small-parcel-shipping.md)
- [Confirm and transfer](confirm-and-transfer.md)
- [Set different dimensions for packing and storage](packing-vs-storage-dimensions.md)
- [Packing work for packing outbound containers and processing shipments](packing-work.md)
- [Packing containers with the Warehouse Management mobile app](warehouse-app-packing-containers.md)
- [Example scenario – Pack containers with the Warehouse Management mobile app](warehouse-app-pack-containers-scenario.md)
- [Container label layouts and printing](print-container-labels.md)

## Set up your warehouse to use manual packing operations

There are two basic ways to organize your outbound operations:

- **Wave creation and processing** – Workers pick items based on outbound warehouse work. They then put the items directly in an outbound shipping location, where they're ready for immediate shipment. For information about how to set up and use this process, see [Wave creation and processing](wave-processing.md).
- **Manual packing at packing stations** – This process has an additional operation between the picking and shipping operations. Instead of putting the inventory in a *bay door shipping location*, workers put it in a *packing location*. They then manage the packing process at the packing station by using the **Pack** page in the web client. To enable this process, you must configure your system as described in this section.

### Set up warehouse locations for packing

You must have at least one packing location where workers will put inventory items so that they can be packed into containers. For more information about how to create warehouse locations, see [Configure locations in a WMS-enabled warehouse](tasks\configure-locations-wms-enabled-warehouse.md). The following subsections describe how to create and set up packing locations.

#### Set up location types for packing

You must define a *location type* for the packing locations. Location types can be used as filtering options to control the different warehouse management processes. The name of each location type typically describes something about how that location type should be used. The location type that you set up here must be associated with each location that is used for packing operations.

Follow these steps to set up a location type.

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**.
1. On the Action Pane, select **New** to add a location type to the grid.
1. Set the following fields for the new location type:

    - **Location type** – Enter a name for the location type. Each name must be unique and should describe something about how the location type is intended to be used.
    - **Description** – Enter a short description of the location type.

#### Inform the system about the packing location type

After you've created a location type, you must set up your system to recognize it as the location type to use for packing operations.

Follow these steps to set the location type that is used for packing operations.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**
2. On the **General** tab, on the **Location types** FastTab, set the **Packing location type** field to the location type that you'll use to identify packing stations.

> [!NOTE]
> If you're upgrading from a version of Microsoft Dynamics AX, the *In packing* status has been removed from shipments and loads, because it didn't work consistently and caused redundant data. Therefore, the **In shipments** and **Loads in packing** list pages have been deprecated. Containers that must be packed are tracked at the location level.
>
> In previous versions, you defined the packing location by using the **Profile ID for packing location** field on the **Packing** tab of the **Warehouse management parameters** page to specify a *location profile*. In the current version, you use the **Packing location type** field on the **General** tab of the **Warehouse management parameters** page to specify a *location type*, as described in this article. The new field is better aligned with the process for identifying staging locations and final shipping locations.
>
> Although you can continue to use the old **Profile ID for packing location** field, we recommend that you start to use the new **Packing location type** field instead, because the old field will eventually be deprecated.
>
> If you clear the setting of the old **Profile ID for packing location** field and then save the page, the field will be permanently disabled. For installations where the **Profile ID for packing location** field has never been used, it will always be disabled. After you clear the setting of the **Profile ID for packing location** field, use the settings that are described in this article to set up and identify your packing location.

#### Set up location profiles for packing locations

Each *location profile* establishes information and rules that apply to the associated locations. Because you need at least one location to use for packing operations, you must create a location profile for it in addition to a location type. Each profile can be used by any number of locations. Locations that are used for packing must be set up to track license plates.

Follow these steps to set up a location profile for a packing location.

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Either select an existing profile from the list pane or select **New** on the Action Pane to create a new one.
1. On the header of the new or selected profile, set the following fields:

    - **Location profile ID** – Enter a unique ID for the profile.
    - **Name** – Enter a descriptive name for the profile.

1. On the **General** FastTab, set the following fields:

    - **Location format** – Select the location format to use for the current location. Location formats are a naming system that is used to create unique and consistent names for the different location bin positions that are used in a warehouse. If you don't already have the format that you need, you can create it by going to **Warehouse management \> Setup \> Warehouse \> Location formats**. For more information, see [Configure locations in a WMS-enabled warehouse](tasks/configure-locations-wms-enabled-warehouse.md).
    - **Location type** – Select the location type that is set up as the packing location type on the **Warehouse management parameters** page, as described earlier in this article.
    - **Use license plate tracking** – For packing locations, set this option to *Yes*. The system must be able to track license plate IDs at packing locations, so that it can control the packing process.
    - **Allow negative inventory** – For packing locations, set this option to *No*.
    - **Allow mixed items** – For packing locations, set this option to *Yes*. This setting is required because many different item numbers are typically brought to the packing locations at the same time.
    - **Allow mixed inventory statuses** – For packing locations, set this option to *Yes*. This setting is required because items that have different inventory statuses are typically brought to the packing locations at the same time.
    - **Allow mixed inventory batches** – For packing locations, set this option to *Yes*. This option is automatically set to *Yes* whenever the **Allow mixed items** option is set to *Yes*.

#### Set up packing locations

You must have at least one *location* where workers will put inventory items that must be packed into containers.

Follow these steps to add a packing location.

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. On the Action Pane, select **New** to add a location.
1. Set the following fields for the new location:

    - **Warehouse** – Specify the warehouse where the packing location must exist.
    - **Location** – Enter a name for the new location.
    - **Location profile ID** – Be sure to specify the ID that you created in the previous section.

## Set up the packing process

This section describes how to configure settings that enable the packing process and let workers pack inventory into containers.

### <a name="packing-policy"></a>Set up container packing policies

Each *container packing policy* defines how a container should be processed. Each time that you create a new container, you'll also select a container packing policy to apply to it.

Follow these steps to set up a container packing policy.

1. Go to **Warehouse management \> Setup \> Containers \> Container packing policies**.
1. Either select an existing policy from the list pane or select **New** on the Action Pane to create a new one.
1. On the header of the new or selected policy, set the following fields:

    - **Container packing policy** – Enter a unique name for the policy.
    - **Description** – Enter a descriptive name for the policy.

1. On the **Overview** tab, set the following fields. These fields let you specify what actions should be taken when the container is closed, whether to operate with or without work creation, and when the container should be released from the packing station.

    - **Weight unit** – Select the default unit of measure to use when a container is closed and manifested. Typically, this unit of measure will be the unit of measure that is used by a scale at the packing station. This field applies to policies with or without work creation.
    - **Container closing policy** – Select one of the following options to define what should occur when the container is closed:

        - *Automatic release* – The container will be considered released from the packing station, and the action that is specified in the **Container release policy** field will be triggered.
        - *Delayed release* – The container won't immediately be released from the packing station. A warehouse worker must manually release it later.
        - *Optional* – While a worker is closing the container, they'll be able to choose whether the container should be released.

        If the packing station mainly handles single containers that are shipped directly to customers, the most natural approach is to release the containers immediately. If the packing station handles shipments that consist of multiple containers or even pallets, it's probably best to delay the release until the whole shipment or pallet has been packed and is ready for pickup.

    - **Container release policy** – Select one of the following options to define what should occur when the container is released from the packing location:

        - *Make available at final shipping location* – Update the container to the final shipping location. If you select this option, use the **Default location for final shipment** field to specify a preferred location for the container after it's closed.
        - *Create work to move container from packing station* – Create work to move the container from the packing station to the staging area or directly to the bay door. Use the **Work template** field to specify the work template that should be applied when work is created for the container.
        - *Assign container to outbound sorting position* – This option is used with the [outbound sorting](outbound-sorting.md) capability.

        In most cases, we recommend that you create work to move containers, because this approach better represents the actual manual processes in the warehouse. However, for simple scenarios, or situations where the packing station is located directly in the bay door area, it might be preferable for the container to be immediately available at the final shipping location.

    - **Work template** – Select the work template that should be applied when work is created for the container. This field is available only when the **Container release policy** field is set to *Create work to move container from packing station* and related to a work order type that is named *Packed container picking*. For more information, see [Work templates and location directives](control-warehouse-location-directives.md).

1. On the **Warehouse selection** FastTab, set the following fields:

    - **Warehouse selection**  – Select one of the following values:

        - *All* – Use this policy for all warehouses where a more specific policy hasn't been assigned.
        - *Warehouse group* – Use this policy for all warehouses in the warehouse group that's selected in the **Warehouse group** field.
        - *Warehouse* – Use this policy only for the specific warehouse that's selected in the **Warehouse** field.

    - **Warehouse** – If the **Warehouse selection** field is set to *Warehouse*, select the warehouse where the packing policy applies.
    - **Warehouse group** – If the **Warehouse selection** field is set to *Warehouse group*, select the warehouse group where the packing policy applies. For more information about how to set up warehouse groups, see [Warehouse groups](warehouse-groups.md).
    - **Default location for final shipment** – Specify the preferred location for the container after it's closed. This field is available only when the **Container release policy** field is set to *Make available at final shipping location* and the **Warehouse selection** field is set to *Warehouse*.
    - **Default location for sorting** – This field is used with the [outbound sorting](outbound-sorting.md) capability. It's available only when the **Warehouse selection** field is set to *Warehouse*.

    In the remaining steps, you'll configure settings that are related to *manifesting*. Manifesting is the process of specifying the weight of a container, container group, or shipment, together with the tracking ID that's received from a transportation provider. Dynamics 365 Supply Chain Management doesn't integrate with external transportation provider systems. Instead, warehouse workers must print labels that are received from the transportation provider and then scan a tracking number when they complete the manifest procedure.

    Because manifest requirements vary from customer to customer, and even from shipment to shipment, packing policies allow for significant flexibility in the workflow. You can set up manifests for containers, container groups, and shipments in any combination.

    If you're using a multi-level manifest procedure, workers must manifest all containers before they manifest the related container group, and they must manifest all container groups before they manifest the related shipment.

1. On the **Container manifest** FastTab, set the following fields:

    - **Automatic manifest at container close** – Set this option to *Yes* to apply manifest information as part of the container closing process. If you aren't using transportation integration, the information must be manually recorded.
    - **Manifest requirements for container** – Select one of the following options:

        - *None* – No manifesting process will be used.
        - *Manual* – Manifesting will be required by the packing workflow. The system won't allow a container to be closed or released until manifesting is completed.
        - *Transportation management* – Manifesting will be done through Transportation management (TMS) rate engines. Because this option requires custom development to implement a specific engine for the transportation provider, it won't work out of the box in the current version.

    - **Print container contents** – Set this option to *Yes* to automatically print the container contents report when a container is registered as closed. The report can also be printed on demand.

1. On the **Container group manifest** FastTab, in the **Manifest requirements for container group** field, select one of the following options:

    - *None* – The container group manifest won't be included as a requirement in the packing workflow.
    - *Manual* – The container group manifest will be included as a requirement in the packing workflow. All containers that are included in the group must be closed before the group can be manifested. Select this option if you're required to complete a manifest for every container group that is packed at the packing station. You'll typically select this option if containers are packed on a pallet and the whole pallet is manifested.

    > [!NOTE]
    > The current version doesn't support manifest reports for container groups, and there is no TMS engine support for container groups.

1. On the **Shipment manifest** FastTab, set the following fields:

    - **Manifest requirements for shipment** – Select one of the following options:

        - *None* – The shipment manifest won't be included as a requirement in the packing workflow.
        - *Manual* – The shipment manifest will be included as a requirement in the packing workflow. No containers for a shipment can be released until manifesting is completed.
        - *Transportation management* – Manifesting will be done through TMS rate engines. Because this option requires custom development to implement a specific engine for the transportation provider, it won't work out of the box in the current version.

        Shipment manifesting should be enabled if you're required to complete a manifest for the whole shipment that is packed at the packing station. It's typically used when one consolidated manifest is required even though the shipment consists of multiple containers or container groups.

    - **Print packing slip** – Set this option to *Yes* to automatically print the packing slip as part of the shipment manifest. The packing slip can also be printed on demand.
    - **Print packing slip asynchronously** – This option is available only when the **Print packing slip** option is set to *Yes*. Set this option to *Yes* to process sales packing slips asynchronously by using the message processor. In this case, the system will queue sales packing slip postings to the message processors by using messages of the *Run packing slip for container* type to the *Warehouse* queue. This setting requires that you also set the **Packing slip posting parameters ID** field. For more information about how to set up and use the message processor, and how to schedule the batch job that's required to process the messages, see [Create and process custom message queues and message types](../supply-chain-dev/message-processor.md).
    - **Packing slip posting parameters ID** – This setting applies when the **Print packing slip asynchronously** option is set to *Yes*. You must define at least one set of parameter settings on the **Packing slip posting parameters** page (**Warehouse management \> Setup \> Packing \> Packing slip posting parameters**) and select the ID for the set of settings that you want to use here. The parameter settings will be used when the last container for a shipment is closed. Warehouse workers won't be prompted to confirm the values. If you're using the [*Container closing*](warehouse-app-packing-containers.md) process for the Warehouse Management mobile app, this process will be the only one that's supported for automatic posting of packing slips.

### Set up container types

During the manual packing process, containers must be created before items can be packed into them. Each container must be based on a *container type*, which defines a container's maximum physical volume and weight capacity.

Follow these steps to create a container type.

1. Go to **Warehouse management \> Setup \> Containers \> Container types**.
1. On the Action Pane, select **New** to add a container type.
1. Set the following fields for the new container type:

    - **Container type code** – Enter a unique ID for the container type.
    - **Description** – Enter a description of the new container type.
    - **Tare weight** – Enter the actual or estimated weight of the container.
    - **Maximum net weight** – Enter the maximum weight that the container can hold.

1. In the **Container dimensions** section, in the **Length**, **Width**, **Height**, and **Volume** fields, enter the physical dimensions of the container itself.
1. In the **Maximums** section, in the **Length**, **Width**, **Height**, and **Volume** fields, enter the maximum physical dimensions that the container can handle.
1. You can define additional attributes for container types that are associated with other operations that use containers. For more information, see [Containerization](wave-containerization.md).

> [!NOTE]
> For the manual packing process, the system uses only the value of the **Maximum net weight** field and the value of the **Volume** field in the **Maximums** section.

### Set up packing profiles

*Packing profiles* are required for the packing process. They can be selected or set by default when you start a packing operation on the **Pack** page.

Follow these steps to set up a packing profile.

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. Either select an existing profile from the list pane or select **New** on the Action Pane to create a new one.
1. On the header of the new or selected profile, set the following fields:

    - **Packing profile ID** – Enter a short ID for the profile.
    - **Description** – Enter a description of the packing profile.
    - **Container packing policy** – Select the packing policy that applies to the profile. For more information, see the [Set up container packing policies](#packing-policy) section of this article.
    - **Container ID mode** – Select whether a container ID should automatically be generated when a container is created, or whether it must be manually created.
    - **Container type** – Select the container type that is used by default when a new container is created.
    - **Autocreate container at container close** – Select this checkbox to automatically create a new container if the previous container is closed, and one or more lines remain in the current shipment.
    - **Print container label at container creation** – Select this checkbox to automatically print a container label when a new container is created. For more information about how to set up your container label layouts, see [Container label layouts and printing](print-container-labels.md).
    - **Prevent editing container Id** - Select this setting to prevent editing of the container Id if it is automatically assigned.
    - **Prevent container creation without items to pack** - Select this setting to prevent container creation when there are no items to pack for a given shipment and packing location.


### Set up warehouse workers

Every user or worker who packs containers by using the **Pack** page of the web client or the *Packing* activity code in the Warehouse Management mobile app must have a user account that is associated with a *worker/person* record that the required security access rights are assigned to. (For more information about how to set up users, see [Create new users](../../fin-ops-core/dev-itpro/sysadmin/tasks/create-new-users.md).)

Follow these steps to set up a *worker/person* record for the packing process.

1. Go to **Warehouse management \> Setup \> Worker**.
1. On the Action Pane, select **New** to add a work user.
1. Set the **Worker** field to the existing worker record that is defined in the **Human resources** module for the user who will complete the packing process.
1. On the **Profile** FastTab, set the following fields:

    - **Container packing policy** – Select a container packing policy that defines how containers at the packing station should be processed. The container packing policy that you select will be pre-selected for the worker when they open the packing station. For more information, see the following blog post: [Improved packing functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/12/01/improved-packing-functionality-dynamics-365-for-operations-1611).
    - **Packing profile ID** – Select a packing profile ID that defines the packing policy and container settings that should be used. If the selected packing profile ID is associated with a container packing policy, you won't be able to change the setting of the **Container packing policy** field on this page.

1. On the **Default packing station** FastTab, select the default site, warehouse, and location that apply to the worker.
1. If the worker will use the Warehouse Management mobile app to manage and register their container packing work, on the **Users** FastTab, set up one or more accounts that the worker can use to sign in to the app. For more information, see [Mobile device user accounts](mobile-device-work-users.md).

## <a name="scenario"></a>Example scenario

This section provides an example scenario that shows how to create an order and pack the items.

### Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Sign in as a user that can do packing work

Sign in to Supply Chain Management by using a user account that has the permissions that are required to pack containers. The user *Julia Funderburk* is included as part of the demo data and has the required permissions. This user has the user ID *Admin*.

### Create a sales order and complete the work

Follow these steps to create a sales order and complete the work of moving the ordered items to the packing station.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, in the **Customer account** field, select *US-005*.
1. Select **OK** to close the dialog box.
1. The new sales order is opened and includes a single, empty line on the **Sales order lines** FastTab. Set the following values for the new order line:

    - **Item number:** *A0001*
    - **Quantity:** *2*
    - **Site:** *6*
    - **Warehouse:** *62*

1. While the order line is still selected, select **Inventory \> Reservation** on the toolbar of the **Sales order lines** FastTab.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**.

    A message shows the shipment and wave IDs for the order.

1. While the order line is still selected, select **Warehouse** \> **Work details** on the toolbar of the **Sales order lines** FastTab. If you use batch processing to run your waves, you might have to wait a short time for the work to be created.
1. On the **Work** page, on the Action Pane, on the **Work** tab, select **Complete work**.
1. On the **Work completion** page, set the **User ID** field to *62*.
1. On the Action Pane, select **Validate work**.
1. When you receive a message that indicates that your work is valid, select **Complete work** to complete the process of picking the inventory items and putting them in the *Pack* location.
1. Make a note of the **Shipment ID** value that is shown for the work in the upper grid.

### Pack the ordered items into a container

The inventory items have now been brought to the packing area and are ready to be packed into containers. Follow these steps to create a new container in the system and pack it.

1. Go to **Warehouse management \> Packing and containerization \> Pack**.
1. In the **Select packing station** dialog box, set the following values:

    - **Site:** *6*
    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Packing profile ID:** *WH62*

1. Select **OK**.
1. On the **Pack** page, in the **License plate or shipment** field, enter the shipment ID that you noted earlier. You should now see the remaining unpacked items on the **Open lines** FastTab.
1. On the Action Pane, select **New container** to create a container in the system.
1. In the **ID of the new container** dialog box, set the **Container type** field to *SmallBox*.
1. Select **OK** to create the container.
1. Select **OK** to return to the **Pack** page. The **Open containers** FastTab now shows the **Container ID** value of the container that you created.
1. For this scenario, you'll pack just one of the ordered items for now. Therefore, on the **Item packing** FastTab, set the following values:

    - **Quantity:** *1.00*
    - **Identifier:** *A0001*

    Immediately after you select the **Identifier** value, the page updates the **Open lines** and **All lines** FastTabs to indicate that one item has been packed. You should now have packed one of the two pieces of item *A0001*.

1. On the Action Pane, select **Close container**.
1. In the **Close container** dialog box, select **Get system weight** to fill in the default **Gross weight** value.
1. Select **OK** to close the container.

> [!TIP]
> There are various ways to view containers based on context. For example, when you pack a shipment, it's often useful to view either containers that are part of the shipment or all containers that are physically at a packing station. The **Packing station** page has buttons that you can use to view all open and closed containers at a packing station. These views aren't restricted to a specific shipment. They can be very helpful in situations where one worker is packing a container, and another worker is manifesting and releasing the container.
>
> A consolidated view of all containers is also available. This view is useful mostly for users who work outside the context of a single packing station. To see it, go to **Warehouse management \> Packing and containerization \> Containers**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
