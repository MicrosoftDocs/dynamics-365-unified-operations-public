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

The container packing process allows you to validate and pack inventory items into containers. During this process, warehouse workers typically pick inventory items from bulk storage areas and move them to a packing area where multiple warehouse workers then check the item quantities and types, and assign them to appropriate container sizes. When a container is fully packed, it is closed and moved to the outbound dock area to get ready for shipment.

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

- **Wave creation and processing**: Workers pick items based on outbound warehouse work and then put the items directly to an outbound shipping location, where they are ready for immediate shipment. For details about how to set up and use this process, see [Wave creation and processing](wave-processing.md).
- **Manual packing at packing stations**: This process makes use of an additional operation between the picking and shipping operations. Instead of putting the inventory to a *baydoor shipping location* workers will put them to a *packing location*. Workers will then manage the packing process at the packing station using the web client **Pack** page and/or the Warehouse Management mobile app *Packing* work flow. To enable this process, you must configure your system as described in this section and its subsections.

### Set up warehouse locations for packing

You must have at least one packing location where workers will place inventory items to be packed into containers. To learn about how to create warehouse locations, see [Configure locations in a WMS-enabled warehouse](tasks\configure-locations-wms-enabled-warehouse.md). The following subsections describe how to create and set up packing locations.

#### Set up location types for packing

You must define a location type for the packing locations. Location types can be used as filtering options to control the different warehouse management processes, and are typically named to describe something about how each of them should be used. The location type you are setting up now must be associated with each location that is used for packing operations.

To set up a location type:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**.
1. Select **New** on the Action Pane to add a new location type to the grid.
1. Make the following settings for the new location type:
    - **Location type** – Enter a name for the location type. Each name must be unique and should usually describe something about how it is intended to be used.
    - **Description** – Enter a short description of the location type

#### Inform the system about packing location type

After you have created a location type to use for packing operations, you must configure it as such in your system.

To set the location type to be used for packing operations:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**
2. Open the **General** tab and expand the **Location types** FastTab
3. Set the **Packing location type** field to the location type that you will use to identify packing stations.

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

Each *location profile* establishes information and rules that apply for the associated locations. Because you need at least one location to use for packing operations, you must create a location profile for it in addition to a location type. Each profile can be used by multiple locations as needed. Locations used for packing must be set up to track license plates.

To set up a location profile for a packing location: 

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select **New** on the Action Pane to add a new location profile
1. Make the following settings in the header for the new or selected profile:
    - **Location profile ID** – Enter a unique ID for the profile
    - **Name** – Enter a descriptive name for the profile
1. Expand the **General** FastTab and make the following settings:
    - **Location format** – Select the location format to use for the current location. Location formats are a naming system used to create unique and consistent names for the different location bin positions used within a warehouse. If you don't already have the format you need, you can create a new one by going to **Warehouse management > Setup > Warehouse > Location formats** (see also [Configure locations in a WMS-enabled warehouse](tasks/configure-locations-wms-enabled-warehouse.md)).
    - **Location type** – Select the location type you set up as the **Packing location type** on the **Warehouse management parameters** page, as described previously.
    - **Use license plate tracking** – For packing locations, set this to *Yes*. It is mandatory that the system be able to track license plate IDs at packing locations so it can control the packing process.
    - **Allow negative inventory** – For packing locations, set this to *No*.
    - **Allow mixed items** – For packing locations, set this to *Yes*. This is required because many different item numbers are typically brought forward to the packing locations at the same time.
    - **Allow mixed inventory statuses** – For packing locations, set this to *Yes*.  This is required because items with different inventory statuses are typically brought forward to the packing locations at the same time.
    - **Allow mixed inventory batches** – For packing locations, set this to *Yes*. This setting is automatically set to *Yes* whenever **Allow mixed items** is set to *Yes*.

#### Set up packing locations <!-- KFM: Continue here. -->

You will need at least one location used to place the inventory items going to get packed into containers.

To set up a packing location at least three field values must get applied:

1. Go to **Warehouse management \> Setup \> Warehouse \> Locations**
1. Select **New** on the Action Pane to add a new location
1. Make the following settings for the new location:
    - **Warehouse** – The warehouse in which the packing location must exist
    - **Location** – Name for the new location
    - **Location profile ID** – Make sure this use the ID created in the previous section

## Set up the packing process

This section describes how to make settings that enables the packing process and allow workers to pack inventory into containers.
You will need to define the following:

### Set up container packing policies

Each *Container packing policy* defines how a container should be processed. Each time you create a new container, you will also select a container packing policy to apply to it.

To create a container packing policy:

1. Go to **Warehouse management > Setup > Containers > Container packing policies**
1. Select **New** on the Action Pane to add a new container packing policy
1. Make the following settings in the header for the new or selected policy:
    - **Container packing policy** – Enter a unique name for the policy
    - **Description** – Enter a descriptive name for the policy
1. Expand the **Overview** tab. These settings let you specify the actions when closing the container and to operate with or without work creation as well as defining when the container should be released from the packing station. Make the following settings:
    - **Warehouse** – Select the warehouse where this packing policy applies
    - **Default location for final shipment** – Specify the preferred location for the container after closing it. This setting is only available when **Container release policy** is set to *Make available at final shipping location*
    - **Default location for sorting** – This setting is used with the [Outbound sorting](outbound-sorting.md) capability
    - **Weight unit** – Choose a default unit of measure to use when closing and manifesting a container. Usually this will be the unit of measure used by a scale at the packing station. This setting applies for policies with or without work creation
    - **Container closing policy** – Define what should happen when closing the container. Select one of the following options:
        - *Automatic release* – The container will be considered released from the packing station and the action specified for the **Container release policy** will be triggered
        - *Delayed release* – The container will not be released from the packing station immediately. A warehouse worker must manually release it later.
        - *Optional* – While closing the container, the worker will be able to choose whether the container should be released

       If the packing station is mainly handling single container shipments directly to customers, it will be most natural to release the containers immediately. If the packing station is handling shipments with multiple containers or even pallets it will probably be optimal to delay the release until the entire shipment or pallet is packed and ready for pick up

    - **Container release policy** – Choose what should happen when the container is released from the packing location. Select one of the following options:
        - *Make available at final shipping location* – Update to the final shipping location. When using this option, use  **Default location for final shipment** to specify a preferred location for the container after closing it
        - *Create work to move container from packing station* – Create work for moving the container from the packing station to the staging area or directly to the bay door. You can use the **Work template** field to specify the work template that always should be applied when creating the work for the container
        - *Assign container to outbound sorting position* – This setting is used with the [Outbound sorting](outbound-sorting.md) capability

        In most cases, we recommend creating work for moving containers because this results in a better representation of the actual manual processes in the warehouse. There might be setups that are very simple or where the packing station is located directly in the bay door area where it would be preferable to let the container be available at the final shipping location immediately.

    - **Work template** – Optional specification of the work template that should be applied when creating the work for the container. This setting is only available when **Container release policy** is set to *Create work to move container from packing station* and related to a work order type called *Packed container picking*. Here you can read more abouut [work templates and location directives](control-warehouse-location-directives.md).

1. Expand the **Container manifest** FastTab

    *Manifesting* is the process of specifying the weight of a container, container group, or shipment together with the tracking ID provided by a transportation provider.

    Supply Chain Management doesn't integrate with external transportation provider systems. Instead, warehouse workers must print labels provided by the transportation provider and then scan a tracking number when completing the manifest procedure.

    Because manifest requirements vary from customer to customer, and even from shipment to shipment, packing policies allow for significant flexibility when it comes to the workflow. You can set up manifests for containers, container groups, and shipments in any combination.

    If you are using a multi-level manifest procedure all containers must be manifested before the related container group is manifested and all container groups must be manifested before the related shipment is manifested.

    - **Automatic manifest at container close** – When *Yes* manifest information must get applied as part of the **Close container**. In case of not using an transportation integration the information must get manually recorded
    - **Manifest requirements for container**
        - *None* – No manifesting process used
        - *Manual* – Manifesting will be included as a requirement in the packing workflow, so the system won't allow a container to be closed or released until manifesting is completed.
        - *Transportation management** – Manifesting will be performed through Transportation management (TMS) rate engines. This requires custom development to implement a specific engine for the transportation provider, so this option won't work out of the box in the current version.
    - **Print container contents** – Set this to *Yes* to have the system automatically print the container contents report when a container is registered as closed. The report can also be printed on demand.

1. Expand the **Container group manifest** FastTab
  
    Container group manifesting should be enabled if it is required to complete a manifest for every single container group packed at the packing station. This will normally be used if containers are packed on a pallet and the entire pallet is manifested.
  
    - **Manifest requirements for container group**
      - *None* – Not enabled
      - *Manual* – Manifesting will be included as a requirement in the packing workflow. All containers included in the group must be closed before the group can be manifested. Select this option if you require a manifest for every single container group packed at the packing station. You would typically use this option if containers are packed on a pallet and the entire pallet is manifested.

    > [!NOTE]
    > The current version doesn't support manifest reports for container groups, nor is there TMS engine support for container groups.

1. Expand the **Shipment manifest** FastTab
  
   Shipment manifest should be enabled if it is required to complete a manifest for the entire shipment packed at the packing station. This will normally be used when one consolidated manifest is required even though the shipment consists of multiple containers or container groups.
    - **Manifest requirements for shipment**
        - *None* – Not enabled
        - *Manual* – The shipment manifest will be included as a requirement in the packing workflow. It will not be possible to release any containers on the shipment before the manifesting is completed.
        - *Transportation management** – Manifesting will be performed through Transportation management (TMS) rate engines. This requires custom development to implement a specific engine for the transportation provider, so this option won't work out of the box in the current version.
    - **Print packing slip** – Set this to *Yes* to have the system automatically print the packing slip as part of the shipment manifest. The report can also be printed on demand.

### Container type

During the manual packing process containers must get created before items can get packed into them. Each container must be defined based on a container type which will describe the maximum values for the physical volume and weight capacity constrains.

To create a container type, follow these steps:

1. Go to Warehouse management > Setup > Containers > Container types
1. Select **New** on the Action Pane to add a new container type
1. Make the following settings for the new container type:
    - **Container type code** – Unique identifier (ID) for the container type
    - **Description** – Description for the new container type
    - **Tare weight** – Enter the actual or estimated weight of the container
    - **Maximum net weight** - Enter the maximum weight that the container can hold
1. In the **CONTAINER DIMENSIONS** (length, width, height, volume) enter the physical dimensions for the container
1. In the **MAXIMUMS** (volume, length, width, height) enter the maximum physical dimensions the container will be able to handle
1. Additional policies can get defined for a container type for other operations using containers. Please refer to the following [documentation](wave-containerization.md) regarding this.

> [!NOTE]
> Only the weight and volume maximum field values will be used by the system for the manual packing process.

### Set up packing profiles

Packing profiles are mandatory setup for the packing process and can get defaulted or selected when starting a packing operation on the **Pack** page.

To create a packing profile:

1. Go to **Warehouse management \> Setup \> Packing \> Packing profiles**.
1. Select **New** on the Action Pane to add a new packing profile
1. Make the following settings for the new or selected packing profile:
    - **Packing profile ID** – Use a short ID for the profile
    - **Description** – Description for the packing profile
    - **Container packing policy** – See  
    - **Container ID mode** – This option determines whether a container ID will be automatically generated when a container is created or if a container ID will be created manually.
    - **Container type** – The container type will be used by default when a new container is created
    - **Autocreate container at container close** – Select this check box to automatically create a new container if the previous one is closed and a line exists in the current shipment

### Setup a warehouse workers

To use the web client **Pack** page <!-- or **Warehouse management mobile app** for the *Packing* activity code --> you will need a user account being associated with a *Worker*/*Person* and having the user assigned with proper security access rights. If needed you can read about how to setup users [here](../../fin-ops-core/dev-itpro/sysadmin/tasks/create-new-users.md).

To set up a *Worker*/*Person* for the packing process:

1. Go to **Warehouse management \> Setup \> Worker**
1. Select **New** on the Action Pane to add a new *Work user*
1. Lookup the **Worker** being associated as *Person* for the *User* going to perform the packing process
1. Open **Profile** and assign *Container packing policy* and *Packing profile ID*
1. Open **Default packing station** and enter *Site*, *Warehouse*, and *Location*
<!--1. If using the **Warehouse management mobile app** create a *User* with a startup *Menu item*-->

## <a name="scenario"></a>Example scenario

In this scenario we will use the already existing demo data for company *USMF* warehouse *62*.
Please make sure that you are running as an user with proper security role access and associated with the *Worker*/*Person* 'Julia Funderburk' or with same setup.

## Create a sales order and complete the work

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
1. On the **Reservation** page, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse**.
1. The page displays a message that shows the shipment and wave IDs for this order.
1. With the new order line still selected, select **Warehouse** \> **Work details** from the **Sales order lines** FastTab toolbar. (If you run your waves using batch processing, you may need to wait a short time for the work to be created.)
1. The **Work** page opens. On the Action Pane, open the **Work** tab and select **Complete work**.
1. The **Work completion** page opens. Set **User ID** to *62*.
1. On the Action Pane, select **Validate work**.
1. You should see a message that your work is valid. Select **Complete work** to process the picking and putting of the inventory items to the *Pack* location
1. Write down the **Shipment ID** shown for this work in the top grid.

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
1. Click **OK** to create a new container.
1. Select **OK** to return to the **Pack** page. The **Open containers** FastTab now shows the **Container ID** of the container you created.
1. For this scenario, we will pack just one of the ordered items for now. Therefore, expand the **Item packing** FastTab and make the following settings:
    - **Quantity**: *1.00*
    - **Identifier**: *A0001*
1. Immediately after you select the **Identifier** value, the page updates the **Open lines** and **All lines** FastTabs to indicate that one item has been packed. You should now have packed 1 out of the 2 pieces of item *A0001*.
1. On the Action Pane select **Close container**.
1. The **Close container** dialog opens. Select **Get system weight** to default the **Gross weight**.
1. Select **OK** to close the container

> [!NOTE]
> There are different ways to view containers based on the context. When packing a shipment, it is useful to see containers that are part of the shipment.
>
>It is possible to see all containers that are physically at the packing station. The **Packing station** form has buttons that can be used to view all open and closed containers at the packing station. These views will not be restricted to a specific shipment.
>
>The views can be very helpful in the situation where one worker is packing the containers and the other worker is manifesting and releasing the containers.
>
>Furthermore, a consolidated view of all containers is also available. This will mostly be useful for users working outside the context of a single packing station:
>
>Go to **Warehouse management \> Packing and containerization \> Containers**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]