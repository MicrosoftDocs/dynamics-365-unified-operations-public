---
# required metadata

title: Container label printing
description: This article describes container label printing and explains how to set it up.
author: perlynne
ms.date: 01/09/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSDocumentRouting, WHSContainerTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perlynne
ms.search.validFrom: yyyy-mm-dd
ms.dyn365.ops.version: 10.0.31

---

# Container label printing
[!include [banner](../includes/banner.md)]

Container label printing can be used to print labels containing information about a container and the related shipment data. A typical scenario for this type of label would be as part of a container creation process when using the [Pack containers using the Warehouse Management mobile app](warehouse-app-pack-containers.md) where a *Container label* barcode of the created **Container ID** can get printed and applied on a physical container.
Like the [*License plate label*](document-routing-layout-for-license-plates.md) the *Container label* uses the Zebra Programming Language (ZPL) to create label layouts.

## Turn on the Container label printing capability
The *Container label* functionality gets enabled together with the [Pack containers using the Warehouse Management mobile app](warehouse-app-pack-containers.md).

1. If not already on, turn on the feature that is listed in the following way:
    - **Module:** *Warehouse management*
    - **Feature name:** *Pack containers using the Warehouse Management mobile app*

## Scenario: Container label printing at container creation via Warehouse Management mobile app
Some of the setup and processing described in this page is related to the described in [Pack containers using the Warehouse Management mobile app](warehouse-app-pack-containers.md) which is recommended reading to better understand the full container packing process via the Warehouse Management mobile app.
You will be using the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) **USMF** legal entity.

You can also use this scenario as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

### Create a container label layout
The label layout controls what information is printed on the label and how it's laid out. Here, you enter the ZPL code that is sent to the printer (typically copied from a label designer program).
During the label generation process the system can replace field and method names used in the label layout with actual values. You can easily see the text which will get replaced by looking after the *$* character.

1. Go to **Warehouse management \> Setup \> Document routing \>Label layout**.
1. Create a record that has the following settings:
    - **Label layout type:** *Container label*
    - **Label layout ID:** *Container*
    - **Description:** *Container ID barcode*
    - **Label layout data source ID:** - Leave blank (only container data will be used)
1. Copy from the below *ZPL container label example* and insert the text into the **Printer text Layout**
    ```ZPL container label example
    CT~~CD,~CC^~CT~
    ^XA~TA000~JSN^LT0^MNW^MTT^PON^PMN^LH0,0^JMA^PR8,8~SD15^JUS^LRN^CI0^XZ
    ^XA
    ^MMT
    ^PW812
    ^LL0609
    ^LS0
    ^BY5,3,369^FT656,137^BCI,,Y,N
    ^FD>;$WHSContainerTable.ContainerId$^FS
    ^FT513,525^A0I,39,38^FH\^FDContainer ID^FS
    ^PQ1,0,1,Y^XZ
    ```
    > [!NOTE]
    > You can easily find the correct field/method names by selecting the table in the **Tables** list followed by either a field name in **Fields** list or a method name in the **Methods** list and then use the **Insert at end of text** button.
1. Close the page

> [!NOTE]
> In the above label layout only the *Container ID* ($WHSContainerTable.ContainerId$) barcode will get printed, but in case you want to include additional related data information to a label, like for example the delivery name related to a shipment, you can create a **Label layout data source** (*Warehouse > Setup > Document routing > Label layout data source*) including a join to the *Shipment* table.
> In the **Label layout data source** select **New** in the *Action Pane* and specify a **Label layout data source ID**, **Description**, and **Label layout type**.
> Select **Edit query** in the *Action Pane*. Now use the *Joins* option to add the needed table(s).
> Note, that in case you remove tables from a existing query you might risk removing field/method names already used in existing label layouts.
> In the **Label layout** you can now select the created **Label layout data source ID**

### Create a container label rounting
To define which container label layouts to use and where to print you need to define a **Container label routing**.

1. Go to **Warehouse management \> Setup \> Document routing \> Container label routing**.
1. Create a record that has the following settings:
    - **Sequence number:** *1* - The sequence number must be unique and it will get evaluated in ascending order
    - **Name:** *Container packing*
    - **Warehouse:** *62* - Warehouse where printing will happen
    - **Location:** *Pack* - In this example the used printer will physically be placed at the *Pack* location
> [!NOTE]
> When printing a container label from the Warehouse Management mobile app the current user warehouse, location, worker, and user ID gets passed as possible filter values for the selection of printer and layout.
> To use additional selection criteria you can select the **Run query** option and use the **Edit query** on the Action Pane.
1. Select **New** in the *Container label rounting printer* section and provide:
    - **Name:**  Select an appropriate ZPL printer. You can read more about how to install a printer here: [Install the Document Routing Agent to enable network printing](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md)
    - **Label layout ID:** *Container label*

### Define automatic container label printing when creating a new container 
The trigger setting whether a container label must automatically get printed when a new container gets created can be defined in the **Packing profiles**.
1. Go to **Warehouse management > Setup > Packing > Packing profiles**
2. Select **Edit**
3. Select record with *Packing profile ID* **WHS62** in the list.
4. Enable **Print container label at container creation**
5. Close the page
> [!NOTE]
> The **Container ID mode** for the *Packing profile ID* **WH62** is set to **Auto**, which means that the defined [number sequence](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) for *Reference* **Container ID** will be used as part of the container creation process.

### Create a new *Print Container label* mobile device menu item
To manually print a container label you must create a new mobile device menu item for the Warehouse Management mobile app.
1.	Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**
2.	Select **New** on the Action Pane to add a new mobile device menu item
3.	Make the following settings for the new menu item:
    - **Menu item name** - Enter *Print container label* as the name for the new menu item
    - **Title** - Enter *Print container label*, this will get displayed on the Warehouse app
    - **Mode** - Select *Indirect*
    - **Activity code** - Select *Print container label*
4. Close the page

### Add the new mobile device menu item to the menu
With now having the mobile device menu item created, we are ready to get it added to the **Mobile device menu**. In this example we will add it to the existing *Outbound* mobile device menu.
1. Open **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select **Edit**.
1. Select **Outbound** menu in the list
1. Select the new **Print container label** mobile device menu items in the **Available menus and menu items** list.
1. Select the arrow-bottom to move this menu item into the **Menu structure** list in the select **Outbound** menu.
1. Close the page

### Run a scenario to print a container label
To try out a full scenario please follow the [Pack containers using the Warehouse Management mobile app](warehouse-app-pack-containers.md) making sure the above setup gets included.

When selecting the **Print container label** mobile device menu item from the *Outbound* menu the application automatically applies the **User ID** and the **Warehouse** values.
In case you would like to record a *Location* you can edit the details. The *Location* value can as well get auto assigned when opening the **Print container label** from the **Pack inventory into containers** menu item via a [detour]( warehouse-app-detours.md).
> [!NOTE]
> You can use the [**Query data using Warehouse Management mobile app detours**](warehouse-app-data-inquiry.md) capability to look up a container ID instead of entering a value manually.


## Additional resources
- [Pack containers for shipment](packing-containers.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
