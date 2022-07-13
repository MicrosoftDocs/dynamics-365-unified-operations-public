---
title: Packing containers
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

# Packing containers

[!include [banner](../../includes/banner.md)]

The manual packing of containers process allows you to validate and pack inventory items  into containers. In this process, warehouse workers would typically pick the inventory items from the bulk storage areas and move them to a packing area where multiple warehouse workers will check the item quantities and types, and assign them to appropriate container sizes.
When a container is fully packed, they can get closed and moved to the outbound dock area to get ready for shipment.

Containers represent the physical structure in which items are packed and you can keep track of the container information in the system. This can be useful during transportation planning, especially in the case where shipping charges are calculated based on containers. You can see the number of containers that are used in a shipment, the types of containers that are used, and physical dimensions such as total volume, weight, and so on, prior to shipping.

Several related outbound warehouse capabilities can be used with containers, please refer to the following documentation to read more:
<!--[Packing work for packing operations](packing-work-for-packing-operations.md)   -   NEW COMMING PAGE -->
<!--[Manual packing on the Warehouse management mobile app](manual-packing-on-the-warehouse-management-mobile-app.md) -   NEW COMMING PAGE -->
- [Wave containerization](wave-containerization.md)
- [Outbound sorting](outbound-sorting.md)
- [Small parcel shipping](small-parcel-shipping.md)
- [Confirm and transfer](confirm-and-transfer.md)
- [Set different dimensions for packing and storage](packing-vs-storage-dimensions.md)

## Setup your warehouse to use manual packing operations
<!--To use either the web client **Pack** page or the **Warehouse management mobile app** for the *Packing* activity code, please make sure to have the below setup enabled.-->
When picking items based on outbound warehouse work and putting them directly to an outbound shipping location the inventory will be ready to get shipped immediately.
Please refer to the general outbound warehouse process documentation for this [part](wave-processing.md).

When using the manual packing process you will add an additional operation between the picking and shipping operations. So instead of putting the inventory to a *baydoor shipping location* you put the items to a *packing location*. For this you will need at least one location used to place the inventory items going to get packed and to use the web client **Pack** page <!-- or the **Warehouse management mobile app** packing process-->, several other predefined setup data will be needed.

In the following it is assumed that the inventory going to get packed into containers will get brought to a packing location ready to get packed into containers.

### Setup warehouse locations for packing

You will need at least one location used to place the inventory items going to get packed into containers. To read about how to create warehouse locations see [Configure locations in a WMS-enabled warehouse](tasks\configure-locations-wms-enabled-warehouse.md). In the following sections you can read about how to create and setup packing locations.

#### Set up location types for packing

You will need to define a location type for the packing locations. This type must get associated with all the locations used for the packing operations.

To set up your location types:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location types**
1. Select **New** on the Action Pane to add a new location type to the grid
1. Make the following settings for your new location type:
    - **Location type** – Enter a name for the location type. Each name must be unique
    - **Description** – Enter a short description of the location type

#### Inform the system about packing location type

You must inform the system about what location type to use for the packing operations.
To set the location type to be used in your organization for packing operations:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**
2. Select the **General** tab and expand the **Location types** FastTab
3. Set the **Packing location type** field to the location type that is specified for packing purposes

> [!NOTE]
> If you are upgrading from a previous Microsoft Dynamics AX version the *In packing* status has been removed from the shipments and loads as they were not working consistently and resulted in redundant data. Consequently, the list pages for **In shipments** and **Loads in packing** have been deprecated. Containers in packing are tracked at the location level.
>
> In previous versions, the packing location was defined as a **Location profile ID**. In the current version, this is changed so setup of packing location will be defined using location types, as described above, to align with the process for identifying staging and final shipping locations.
>
> It is possible to continue with the current setting, but we recommend that you update the setting because the legacy packing setting will be deprecated in future versions.
>
> [!IMPORTANT]
> After clearing and saving the **Profile ID for packing location field**, the field will be disabled and can't be used anymore. For installations where the legacy has not been used, the legacy setting will always be disabled. After having the value cleared you can follow the above setup process.

#### Set up location profiles for packing locations

Each location profile establishes information and rules that apply for associated locations and because you at least need one location used for a packing operation, you as well need to create a *Location profile*. Each profile can be used by multiple locations as needed, but for the locations used for packing you will need to track license plates.

To set up a location profile for a packing location:

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select **New** on the Action Pane to add a new location profile
1. Make the following settings in the header for the new or selected profile:
    - **Location profile ID** – Enter a unique ID for the profile
    - **Name** – Enter a descriptive name for the profile
1. Expand the **General** FastTab and make the following settings:
    - **Location format** – Select the location format to use for the current location. Location formats are a naming-system used to create unique and consistent names for the different location bin positions used within a warehouse. If not already existing you will need to create a new format under **Warehouse management > Setup > Warehouse > Location formats**
    - **Location type** – Select the type used in the previous section. Location types can be used as filtering options to control the different warehouse management processes and does here inform the system about use
    - **Allow negative inventory** – For packing locations, set this to *No*. The system must have knowledged about what to pack and thereby being able to get tracked physically
    - **Use license plate tracking** – For packing locations, set this to *Yes*. Mandatory to track the license plate IDs on the packing locations to be able to control the packing process
    - **Allow mixed items** – For packing locations, set this to *Yes*. Typically many different item numbers will need to get brought forward to the packing locations at the same time
    - **Allow mixed inventory statuses** – For packing locations, set this to *Yes*. Typically many different inventory statuses will need to get brought forward to the packing locations at the same time
    - **Allow mixed inventory batches** – For packing locations, set this to *Yes*. Typically many different batch numbers will need to get brought forward to the packing locations at the same time

#### Set up packing locations

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

<!-- HERE ;-) -->

# Example scenario

In this scenario we will use the already existing demo data for company *USMF* warehouse *62*.
Please make sure that you are running as an user with proper security role access and associated with the *Worker*/*Person* 'Julia Funderburk' or with same setup.

## Create sales orders

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. On the **Create sales order** dialog box, set the following values:
    - **Customer account:** *US-005*
1. Select **OK** to close the dialog box.
    The new sales order is opened.
1. If a new, empty line isn't automatically added to the grid on the **Sales order lines** FastTab, select **Add line** to add one.
1. On the new order line, set the following values:
    - **Item number:** *A0001*
    - **Quantity:** *2*
    - **Warehouse** *62*
1. While the new order line is still selected on the **Sales order lines** FastTab, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order.
1. From the line select **Warehouse** > **Work details** (Note that in case the waving runs in batch processing it might take a some time before the work gets created)
1. From the **Work** page Action select **Work** > **Complete work** to open the *Work completion* page
1. Select **User ID** 62 and Action **Validate work** followed by **Complete work** to process the picking and putting of the inventory items to the *Pack* location
1. Make a note about the *Shipment ID*

The inventory items have now been brought forward to the packing area and are ready to get packed into containers.

1. Go to **Warehouse management \> Packing and containerization \> Pack**.
1. On the dialog select
   - **Site** 6
   - **Warehouse** 62
   - **Location** Pack
   - **Packing profile ID** WH62
1. Select **OK** 
1. In the **Pack** page enter the noted shipment ID into the **License plate or shipment** field. You will now see the items remaining to get packed in the **Open lines** section.
1. On the Action Pane select **New container** to create a container in the system
1. Select **Container type** SmallBox
1. Click **OK** to create a new container with the automatically assigned ID
1. Back in the **Pack** page select **Pack** in the Action to pack all the inventory items into the new container

All the items for the shipment has now been packed into containers

1. On the Action Pane select **Close container**
1. On the **Close container** dialog click **Get system weight** to default the item master gross weight
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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]