---
title: Pack containers for shipment
description: The packing process allows you to validate and pack inventory items into containers. 
author: perlynne
ms.date: 7/13/2022
ms.topic: business-process
ms.search.form: WHSLocationType, WHSLocationProfile, WHSParameters, WHSContainerType, WHSPackProfile, WHSCloseContainerProfile, InventLocationIdLookup, UnitOfMeasureLookup, WHSPack, WHSContainerTable, 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Pack containers for shipment

[!include [banner](../../includes/banner.md)]

The container packing process allows you to validate and pack inventory items into containers. During this process, warehouse workers typically pick inventory items from bulk storage areas and move them to a packing area where multiple warehouse workers then check the item quantities and types, and assign them to appropriate container sizes. When a container is fully packed, it's then closed and moved to the outbound dock area to get ready for shipment.

Containers represent physical structures in which items are packed, and you can keep track of container information in the system. This can be useful during transportation planning, especially if you calculate shipping charges based on containers. Prior to shipping, you can see the number of containers that are used in a shipment, the types of containers that are used, and the physical dimensions of each container (such as total volume, weight, and so on).

Several related outbound warehouse capabilities can be used with containers. See the following articles to learn more:

- [Wave containerization](wave-containerization.md)
- [Outbound sorting](outbound-sorting.md)
- [Small parcel shipping](small-parcel-shipping.md)
- [Confirm and transfer](confirm-and-transfer.md)
- [Set different dimensions for packing and storage](packing-vs-storage-dimensions.md)
- [Packing work for packing outbound containers and processing shipments](packing-work.md)
<!-- KFM: When published, add link to [Manual packing on the Warehouse management mobile app](manual-packing-on-the-warehouse-management-mobile-app.md) -->

## Set up your warehouse to use manual packing operations

There are two basic ways to organize your outbound operations:

<!-- KFM: Confirm the following terminology and concept with Per -->

- **Wave creation and processing**: Workers pick items based on outbound warehouse work and then put the items directly to an outbound shipping location, where they're ready for immediate shipment. For details about how to set up and use this process, see [Wave creation and processing](wave-processing.md).
- **Manual packing at packing stations**: This process makes use of an additional operation between the picking and shipping operations. Instead of putting the inventory to a *bay door shipping location*, workers will put them to a *packing location*. Workers will then manage the packing process at the packing station using the web client **Pack** page and/or the Warehouse Management mobile app *Packing* work flow. To enable this process, you must configure your system as described in this section and its subsections.

### Set up warehouse locations for packing

You must have at least one packing location where workers will place inventory items to be packed into containers. To learn about how to create warehouse locations, see [Configure locations in a WMS-enabled warehouse](tasks\configure-locations-wms-enabled-warehouse.md). The following subsections describe how to create and set up packing locations.

#### Set up location types for packing

You must define a *location type* for the packing locations. Location types can be used as filtering options to control the different warehouse management processes, and are typically named to describe something about how each of them should be used. The location type you're setting up now must be associated with each location that is used for packing operations.

To set up a location type:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**.
1. Select **New** on the Action Pane to add a new location type to the grid.
1. Make the following settings for the new location type:
    - **Location type** – Enter a name for the location type. Each name must be unique and should describe something about how it's intended to be used.
    - **Description** – Enter a short description of the location type

#### Inform the system about packing location type

After you've created a location type to use for packing operations, you must set you system to recognize it as such.

Follow these steps to set the location type to be used for packing operations:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**
2. Open the **General** tab and expand the **Location types** FastTab
3. Set the **Packing location type** field to the location type that you'll use to identify packing stations.

<!-- KFM: The following note may be obsolete and should maybe be removed. -->

> [!NOTE]
> If you are upgrading from a version of Microsoft Dynamics AX, note that the *In packing* status has been removed from shipments and loads because the status wasn't working consistently and resulted in redundant data. Consequently, the list pages for **In shipments** and **Loads in packing** have been deprecated. Containers to be packed are tracked at the location level.
>
> In previous versions, the packing location was defined by identifying a *location profile* using the **Profile ID for packing location** field on the **Packing** tab of the **Warehouse management parameters** page. In the current version, packing location are instead defined by identifying a *location type* using the **Packing location type** field on the **General** tab of the **Warehouse management parameters** page, as described in this article. The new setting aligns better with the process for identifying staging and final shipping locations.
>
> It is possible to continue using the legacy setting, but we recommend that you instead update to using the new setting because the legacy packing setting will eventually be deprecated.
>
> If you clear the legacy **Profile ID for packing location** field and then save the page, the field will be permanently disabled. For installations where the legacy setting has never been used, the legacy setting will always be disabled. After clearing this setting, use the settings described in this article to set up and identify your packing location.

#### Set up location profiles for packing locations

Each *location profile* establishes information and rules that apply for the associated locations. Because you need at least one location to use for packing operations, you must create a location profile for it in addition to a location type. Each profile can be used by any number of locations as needed. Locations used for packing must be set up to track license plates.

Follow these steps to set up a location profile for a packing location:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select **New** on the Action Pane to add a new location profile
1. Make the following settings in the header for the new or selected profile:
    - **Location profile ID** – Enter a unique ID for the profile
    - **Name** – Enter a descriptive name for the profile
1. Expand the **General** FastTab and make the following settings:
    - **Location format** – Select the location format to use for the current location. Location formats are a naming system used to create unique and consistent names for the various location bin positions used within a warehouse. If you don't already have the format you need, you can create a new one by going to **Warehouse management > Setup > Warehouse > Location formats** (see also [Configure locations in a WMS-enabled warehouse](tasks/configure-locations-wms-enabled-warehouse.md)).
    - **Location type** – Select the location type set up as the **Packing location type** on the **Warehouse management parameters** page, as described previously.
    - **Use license plate tracking** – For packing locations, set this option to *Yes*. The system must be able to track license plate IDs at packing locations so it can control the packing process.
    - **Allow negative inventory** – For packing locations, set this option to *No*.
    - **Allow mixed items** – For packing locations, set this option to *Yes*. This is required because many different item numbers are typically brought forward to the packing locations at the same time.
    - **Allow mixed inventory statuses** – For packing locations, set this option to *Yes*.  This is required because items with different inventory statuses are typically brought forward to the packing locations at the same time.
    - **Allow mixed inventory batches** – For packing locations, set this option to *Yes*. This option is automatically set to *Yes* whenever **Allow mixed items** is set to *Yes*.

#### Set up packing locations

You must have at least one *location* where workers will place inventory items that will be packed into containers.

Follow these steps to add a packing location:

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**
1. Select **New** on the Action Pane to add a new location
1. Make the following settings for the new location:
    - **Warehouse** – The warehouse in which the packing location must exist
    - **Location** – Name for the new location
    - **Location profile ID** – Make sure this use the ID created in the previous section

## Set up the packing process

The subsections of this section describe how to make settings that enable the packing process and allow workers to pack inventory into containers.

### <a name="packing-policy"></a>Set up container packing policies

Each *container packing policy* defines how a container should be processed. Each time you create a new container, you'll also select a container packing policy to apply to it.

To create a container packing policy:

1. Go to **Warehouse management > Setup > Containers > Container packing policies**
1. Select **New** on the Action Pane to add a new container packing policy
1. Make the following settings in the header for the new or selected policy:
    - **Container packing policy** – Enter a unique name for the policy
    - **Description** – Enter a descriptive name for the policy
1. Expand the **Overview** tab. These settings let you specify actions to take when closing the container, whether to operate with or without work creation, and to define when the container should be released from the packing station. Make the following settings:
    - **Warehouse** – Select the warehouse where this packing policy applies
    - **Default location for final shipment** – Specify the preferred location for the container after closing it. This setting is only available when **Container release policy** is set to *Make available at final shipping location*.
    - **Default location for sorting** – This setting is used with the [Outbound sorting](outbound-sorting.md) capability.
    - **Weight unit** – Choose a default unit of measure to use when closing and manifesting a container. Usually this will be the unit of measure used by a scale at the packing station. This setting applies for policies with or without work creation.
    - **Container closing policy** – Define what should happen when closing the container. Select one of the following options:
        - *Automatic release* – The container will be considered released from the packing station and the action specified for the **Container release policy** will be triggered.
        - *Delayed release* – The container won't be released from the packing station immediately. A warehouse worker must manually release it later.
        - *Optional* – While closing the container, the worker will be able to choose whether the container should be released.

       If the packing station is mainly handling single container shipments directly to customers, it's most natural to release the containers immediately. If the packing station is handling shipments with multiple containers or even pallets, it will probably be best to delay the release until the entire shipment or pallet is packed and ready for pickup.

    - **Container release policy** – Choose what should happen when the container is released from the packing location. Select one of the following options:
        - *Make available at final shipping location* – Update to the final shipping location. When using this option, use  **Default location for final shipment** to specify a preferred location for the container after closing it
        - *Create work to move container from packing station* – Create work for moving the container from the packing station to the staging area or directly to the bay door. Use the **Work template** field to specify the work template that should be applied when creating work for the container.
        - *Assign container to outbound sorting position* – This setting is used with the [Outbound sorting](outbound-sorting.md) capability.

        In most cases, we recommend creating work for moving containers because this results in a better representation of the actual manual processes in the warehouse. However, for simple scenarios, or situations where the packing station is located directly in the bay door area, it might be preferable to let the container be available at the final shipping location immediately.

    - **Work template** – Select the work template that should be applied when creating work for the container. This setting is only available when **Container release policy** is set to *Create work to move container from packing station* and related to a work order type called *Packed container picking*. For more information, see [work templates and location directives](control-warehouse-location-directives.md).

1. Expand the **Container manifest** FastTab.

    *Manifesting* is the process of specifying the weight of a container, container group, or shipment together with the tracking ID received from a transportation provider.

    Supply Chain Management doesn't integrate with external transportation provider systems. Instead, warehouse workers must print labels received from the transportation provider and then scan a tracking number when completing the manifest procedure.

    Because manifest requirements vary from customer to customer, and even from shipment to shipment, packing policies allow for significant flexibility when it comes to the workflow. You can set up manifests for containers, container groups, and shipments in any combination.

    If you're using a multi-level manifest procedure, workers must manifest all containers before manifesting the related container group, and all container groups must be manifested before the related shipment is manifested.

    - **Automatic manifest at container close** – Set to *Yes* to apply manifest information as part of the close-container process. If you aren't using transportation integration, the information must be recorded manually.
    - **Manifest requirements for container** – Select one of the following options:
        - *None* – No manifesting process will be used.
        - *Manual* – Manifesting will be required by the packing workflow. The system won't allow a container to be closed or released until manifesting is completed.
        - *Transportation management* – Manifesting will be performed through Transportation management (TMS) rate engines. This requires custom development to implement a specific engine for the transportation provider, so this option won't work out of the box in the current version.
    - **Print container contents** – Set this option to *Yes* to have the system automatically print the container contents report when a container is registered as closed. The report can also be printed on demand.

1. Expand the **Container group manifest** FastTab.
  
    You should enable container group manifesting if you're required to complete a manifest for every single container group packed at the packing station. This will normally be used if containers are packed on a pallet and the entire pallet is manifested. Set **Manifest requirements for container group** to one of the following options:

    - *None* – Manifesting won't be included as a requirement in the packing workflow.
    - *Manual* – Manifesting will be included as a requirement in the packing workflow. All containers included in the group must be closed before the group can be manifested. Select this option if you require a manifest for every single container group packed at the packing station. You would typically use this option if containers are packed on a pallet and the entire pallet is manifested.

    > [!NOTE]
    > The current version doesn't support manifest reports for container groups, nor is there TMS engine support for container groups.

1. Expand the **Shipment manifest** FastTab.
  
   Shipment manifesting should be enabled if you're required to complete a manifest for the entire shipment packed at the packing station. This will normally be used when one consolidated manifest is required even though the shipment consists of multiple containers or container groups. Make the following settings:

    - **Manifest requirements for shipment** – Select one of the following options:
        - *None* – The shipment manifest won't be included as a requirement in the packing workflow.
        - *Manual* – The shipment manifest will be included as a requirement in the packing workflow. It won't be possible to release any containers for a shipment before the manifesting is completed.
        - *Transportation management** – Manifesting will be performed through Transportation management (TMS) rate engines. This requires custom development to implement a specific engine for the transportation provider, so this option won't work out of the box in the current version.
    - **Print packing slip** – Set this option to *Yes* to automatically print the packing slip as part of the shipment manifest. The report can also be printed on demand.

### Container type

During the manual packing process, containers must be created before items can get packed into them. Each container must be defined based on a *container type*, which defines a container's maximum physical volume and weight capacity.

To create a container type, follow these steps:

1. Go to **Warehouse management > Setup > Containers > Container types**.
1. Select **New** on the Action Pane to add a new container type.
1. Make the following settings for the new container type:
    - **Container type code** – Unique identifier (ID) for the container type.
    - **Description** – Description for the new container type.
    - **Tare weight** – Enter the actual or estimated weight of the container.
    - **Maximum net weight** – Enter the maximum weight that the container can hold.
1. In the **Container dimensions** section, enter the physical dimensions for the container itself (**Length**, **Width**, **Height**, **Volume**).
1. In the **Maximums** section, enter the maximum physical dimensions the container will be able to handle (**Length**, **Width**, **Height**, **Volume**).
1. Additional attributes can be defined for container types associated with other operations that use containers. For details, see [Containerization](wave-containerization.md).

> [!NOTE]
> Only the **Maximum net weight** and maximum **Volume** field values are used by the system for the manual packing process.

### Set up packing profiles

*Packing profiles* are required for the packing process and can be selected or set by default when you start a packing operation on the **Pack** page.

To create a packing profile, follow these steps:

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. Select **New** on the Action Pane to add a new packing profile.
1. Make the following settings for the new or selected packing profile:
    - **Packing profile ID** – Enter a short ID for the profile.
    - **Description** – Enter a description for the packing profile.
    - **Container packing policy** – Select the packing policy that applies for this profile. See also [Set up container packing policies](#packing-policy).
    - **Container ID mode** – Choose whether a container ID should be automatically generated when a container is created or if it must be created manually.
    - **Container type** – Select the container type to use by default when creating a new container.
    - **Autocreate container at container close** – Select this check box to automatically create a new container if the previous one is closed and one or more remaining lines exist in the current shipment.

### Set up warehouse workers

Each user or worker that packs containers using the **Pack** page of the web client or the *Packing* activity code in the Warehouse Management mobile app must have a user account associated with a *worker/person* record that is assigned the required security access rights. (For more information about how to set up users, see [Create new users](../../fin-ops-core/dev-itpro/sysadmin/tasks/create-new-users.md).)

To set up a *worker/person* for the packing process:

1. Go to **Warehouse management \> Setup \> Worker**.
1. Select **New** on the Action Pane to add a new work user.
1. Set the **Worker** field to the existing worker record (defined in the Human resources module) for the user who will perform the packing process.
1. Expand the **Profile** FastTab and make the following settings:
    - **Container packing policy** – Select a container packing policy that defines how containers at the packing station should be processed. The container packing policy that is selected here will be pre-selected for the worker when they open the packing station. For more information, see the following blog post: [Improved packing functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/12/01/improved-packing-functionality-dynamics-365-for-operations-1611),
    - **Packing profile ID** – Select a packing profile ID that defines the packing policy and container settings that are used. If the selected packing profile ID is associated with a container packing policy, you won't be able to change the **Container packing policy** setting on this page.
1. Expand the **Default packing station** FastTab and select the default **Site**, **Warehouse**, and **Location** that apply for this worker.
1. If the worker will use the Warehouse Management mobile app to manage and register their container packing work, then expand the **Users** FastTab and set up one or more accounts that this worker can use to sign into the app. See also [Mobile device user accounts](mobile-device-work-users.md)

## <a name="scenario"></a>Example scenario

This section provides an example scenario that shows how to create an order and pack the items.

### Make sample data available

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Sign in as a user that can do packing work

Sign in to Supply Chain Management using a user account that has the permissions required to pack containers. The user *Julia Funderburk* (with **User ID** *Admin*) is included as part of the demo data and has the required permissions.

### Create a sales order and complete the work

Follow these steps to create a sales order and complete the work of moving the ordered items to the packing station:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. On the **Create sales order** dialog box, set the following value:
    - **Customer account:** *US-005*
1. Select **OK** to close the dialog box.
1. The new sales order opens and includes a single, empty line on the **Sales order lines** FastTab. Set the following values for the new order line:
    - **Item number:** *A0001*
    - **Quantity:** *2*
    - **Site** *6*
    - **Warehouse** *62*
1. With the new order line still selected, select **Inventory \> Reservation** from the **Sales order lines** FastTab toolbar.
1. The **Reservation** page opens. Select **Reserve lot** on the Action Pane to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse**.
1. The page displays a message that shows the shipment and wave IDs for this order.
1. With the new order line still selected, select **Warehouse** \> **Work details** from the **Sales order lines** FastTab toolbar. (If you run your waves using batch processing, you may need to wait a short time for the work to be created.)
1. The **Work** page opens. On the Action Pane, open the **Work** tab and select **Complete work**.
1. The **Work completion** page opens. Set **User ID** to *62*.
1. On the Action Pane, select **Validate work**.
1. You should see a message that your work is valid. Select **Complete work** to process the picking and putting of the inventory items to the *Pack* location
1. Write down the **Shipment ID** shown for this work in the top grid.

### Pack the ordered items into a container

The inventory items have now been brought forward to the packing area and are ready to get packed into containers. Now, follow these steps to create a new container in the system and pack it:

1. Go to **Warehouse management \> Packing and containerization \> Pack**.
1. The **Select packing station** dialog opens. Make the following settings:
   - **Site:** *6*
   - **Warehouse:** *62*
   - **Location:** *Pack*
   - **Packing profile ID:** *WH62*
1. Select **OK**.
1. The **Pack** page opens. In the **License plate or shipment** field, enter the shipment ID you noted previously. You should now see the remaining unpacked items on the **Open lines** FastTab.
1. On the Action Pane, select **New container** to create a container in the system.
1. The **ID of the new container** dialog opens. Set **Container type** to *SmallBox*.
1. Select **OK** to create a new container.
1. Select **OK** to return to the **Pack** page. The **Open containers** FastTab now shows the **Container ID** of the container you created.
1. For this scenario, we'll pack just one of the ordered items for now. Therefore, expand the **Item packing** FastTab and make the following settings:
    - **Quantity**: *1.00*
    - **Identifier**: *A0001*
1. Immediately after you select the **Identifier** value, the page updates the **Open lines** and **All lines** FastTabs to indicate that one item has been packed. You should now have packed one out of the two pieces of item *A0001*.
1. On the Action Pane, select **Close container**.
1. The **Close container** dialog opens. Select **Get system weight** to default the **Gross weight**.
1. Select **OK** to close the container

> [!TIP]
> There are various ways to view containers based on context. For example, when packing a shipment, it's often useful to see containers that are part of the shipment or to see all containers that are physically at a packing station. The **Packing station** page has buttons that you can use to view all open and closed containers at a packing station. These views aren't be restricted to a specific shipment. The views can be very helpful in situations where one worker is packing a container and another worker is manifesting and releasing the container.
>
> A consolidated view of all containers is also available, which is mostly useful for users working outside the context of a single packing station. To see it, go to **Warehouse management \> Packing and containerization \> Containers**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]