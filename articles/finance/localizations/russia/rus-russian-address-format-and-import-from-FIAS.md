---
title: Russian address formats
description: Learn how to work with Russian address formats and import data from FIAS with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/05/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-03-01
---

# Russian address formats

[!include [banner](../../includes/banner.md)]

This article explains how to work with Russian address formats and import data from the Russian Federation Information Address System (FIAS) with Microsoft Dynamics 365 Finance.

Address formats determine how address data will appear when it's printed. In the system, you can set up address formats for every country or region where business is done. In Russia, addresses have a standardized form. However, additional information can be included, such as the district, street code, building complement, building, apartment, group of houses, group of flats, and land plot.

The Federal Informational Address System (or FIAS) address database might be required for businesses in the Russian Federation. You can use specialized tools to import FIAS into your system and keep it up to date. This article explains how to set up and use the FIAS import mechanisms.

> [!NOTE]
> The Federal Tax Service (FTS) stopped updating files with address information in the FIAS format in August 2021. The new format was approved by an order of the FTS that was dated May 13, 2020: No. ED-7-6 / 329 @ FIAS (old format that contains information about addresses in the structure of the administrative-territorial division); State address register (GAR, a new format that contains information about addresses in the municipal division). 
>
> For more information about how to import addresses in the GAR format, see [Import from GAR](rus-russian-address-format-import-gar.md)

## Set up Russian address formats

### Set up the address format, country or region, state or province, county, city and postal code

To set up the address format, country or region, state or province, county, city and postal code, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup** to open the **Address setup** page.
1. On the **Address format**, **Country/region**, **State/province**, **County**, **City** and **ZIP/postal codes** tabs, you can set up the address format, country or region, state or province, county, city, and postal code.

### Set up a new district

To set up a new district, follow these steps:

1. On the **Address setup** page, on the **District** tab, select the country or region, state or province, county code, and city code.
1. Select **New** to create a new district for the selected country or region, state or province, county, and city.
1. In the **District** field, enter the unique code for the district.
1. In the **Description** field, enter the official name of the district.
1. In the **ZIP/postal code** field, select the postal code.

   ![Address setup page District tab.](../media/1%20Address%20setup.jpg)

1. Select **Save**.

### Set up a street code

To set up a street code, follow these steps:

1. On the **Address setup** page, on the **Street** tab, verify that **RUS** is selected in the **Country/region** field.
1. Select the state or province, county code, city code, and district code.
1. Select **New** to create a new street for the selected country or region, state or province, county, city, and district.
1. In the **Street code** field, enter the unique code for the street.
1. In the **Street** field, enter the official name of the street.
1. In the **ZIP/postal code** field, select the postal code.

   ![Address setup page Street tab.](../media/2%20Address%20setup.jpg)

1. Select **Save**.

### Set up a group of houses

To set up a group of houses, follow these steps:

1. On the **Address setup** page, on the **Group of houses** tab, verify that **RUS** is selected in the **Country/region** field.
1. Select the state or province, county code, city code, district code, and street code.
1. Select **New** to create a new group of houses for the selected country or region, state or province, county, city, district, and street.
1. In the **Group of houses code** field, enter the unique code for the group of houses.
1. In the **Numbers of buildings** field, enter a comma-separated list of the building numbers of the houses in the group.
1. In the **ZIP/postal code** field, select the postal code.

   ![Address setup page Group of houses tab.](../media/3%20Address%20setup.jpg)

1. Select **Save**.

### Set up a group of flats

To set up a group of flats, follow these steps:

1. On the **Address setup** page, on the **Group of flats** tab, verify that **RUS** is selected in the **Country/region** field.
1. Select the state or province, county code, city code, district code, street code, and group of houses code.
1. Select **New** to create a new group of flats for the selected country or region, state or province, county, city, district, street, and group of houses.
1. In the **Group of flats code** field, enter the unique code for the group of flats.
1. In the **Group of flats** field, enter a comma-separate list of the flat numbers of the flats in the group.
1. In the **ZIP/postal code** field, select the postal code.

   ![Address setup page Group of flats tab.](../media/4%20Address%20setup.jpg)

1. Select **Save**.

### Set up land plots

To set up land plots, follow these steps:

1. On the **Address setup** page, on the **Land plots** tab, verify that **RUS** is selected in the **Country/region** field.
1. Select the state or province, county code, city code, district code, and street code.
1. Select **New** to create a new land plot for the selected country or region, state or province, county, city, district, and street.
1. In the **Land plot code** field, enter the unique code for the land plot.
1. In the **Numbers of land plots** field, enter a comma-separated list of the numbers of the land plots.
1. In the **ZIP/postal code** field, select the postal code.

   ![Address setup page Land plots tab.](../media/5%20Address%20setup.jpg)

1. Select **Save**.

## Create an address for a customer

To create an address for a customer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Open a customer record, and then, on the **Addresses** FastTab, select **More options \> Advanced** to open the **Manage addresses** page.

   ![Addresses FastTab on customer record.](../media/6%20All%20customers.jpg)

1. On the **Address** FastTab, in the **Country/region** field, select **RUS**.
1. In the **ZIP/postal code** field, select the postal code. After you select a postal code, the **District** field shows the district code and name.
1. In the **Street code** field, select the street code. The street name is shown on the right side of the **Street code** field and is also entered in the **Street** field.
1. In the **Building complement** field, enter the name of the building. The building name is also entered in the **Street** field.
1. In the **Building** field, enter the building number. The building number is also entered in the **Street** field.
1. In the **Apartment** field, enter the apartment number. The apartment number is also entered in the **Street** field.
1. In the **Group of houses** field, select the group of houses code. The corresponding building numbers are shown.
1. In the **Group of flats** field, select the group of flats code. The corresponding flat numbers are shown.

   ![Manage addresses page Addresses FastTab.](../media/7%20Manage%20addresses.jpg)

1. Select **Save**.

## Import from FIAS

### Import an FIAS metadata package

To import an FIAS metadata package, follow these steps:

1. Go to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/Logon/Index), and in the Shared asset library, on the **Data package** tab, download the **RU FIAS – FiasMetadataPackage**. This package file contains the required data for the import jobs runtime.

   ![Shared asset library in .](../media/8%20Shared%20asset%20library.jpg)

1. In Dynamics 365 Finance, go to **System administration** \> **Workspaces** \> **Data management**.
1. In the **Import / Export** section, select the **Import** tile to create a new import job.
    
   ![Data management workspace, Import/export section, Import tile.](../media/9%20Data%20management.jpg)

1. In the **Group name** field, enter **ImportFiasMetadata**.
1. In the **Description** field, enter a description.
1. On the **Selected entities** FastTab, select **Add file** to add the following files from the package file that you downloaded earlier:
    - Abridgements of addresses
    - FiasEstateStatusEntity
    - FiasFlatTypeEntity
    - FIASOperationStatusesEntity
    - FiasStructureStatusEntity
  
   After you select each file, select **Upload and add**.

1. Select **Save**.

### Set up a template to import FIAS data

To set up a template to import FIAS data, follow these steps:

1. In Dynamics 365 Finance, go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Templates** tile to open the **Template** page.
1. Select **New** to create a new template.
1. In the **Template ID** field, enter the identification number of the template.
1. In the **Description** field, enter a description.
1. In the **Template status** field, select **Validated**.
1. On the **Entities** FastTab, select **Add entity** to add the following data entities:
    - FiasAddressObjectEntity
    - FiasHouseEntity
    - FiasSteadEntity
    - FiasRoomEntity

    After you select each entity in the **Entity name** field, select **Add entity**.

1. Select **Save**.

   ![List of entities just added.](../media/11%20Template.jpg)

### Set up a job for a full FIAS import

When you import FIAS data into the system the first time, you should create a job for a full FIAS import.

To set up a job for a full FIAS import, follow these steps:

1. In Dynamics 365 Finance, go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Import** tile to create a new import job.
1. In the **Group name** field, enter **FiasFullImportJob**.
1. In the **Description** field, enter a description.
1. On the **Selected entities** FastTab, select **Add template** to add the template that you created earlier.
1. In the **Entity replace or merge** field group, select **Merge**.
1. In the **Source data format** field, select **VerticalBarSeparated-Unicode**.
1. Select **OK**, and then select **Save**.

    ![Import page, with fias full import job details.](../media/12%20Import.jpg)

### Set up a job to import FIAS delta

To update existing address data, you should create a job to import FIAS delta.

To set up a job to import FIAS delta, follow these steps:

1. Go to [LCS](https://lcs.dynamics.com/Logon/Index), and in the Shared asset library, on the **Data package** tab, download the **RU FIAS – FiasTransformations** file.
1. In Dynamics 365 Finance, go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Import** tile to create a new import job.
1. In the **Group name** field, enter **FiasDeltaImportJob**.
1. In the **Description** field, enter a description.
1. On the **Selected entities** FastTab, select **Add template** to add the template that you created earlier.
1. In the **Entity replace or merge** field group, select **Merge**.
1. In the **Source data format** field, select **XML-Attribute**.
1. Select **OK**.

    ![Import page wtih fias delta import job details.](../media/13%20Import.jpg)

1. For each entity, select the button in the **View map** column to open the **Map source to staging** page.

    ![Map source to staging page.](../media/14%20Map%20source%20to%20staging.jpg)

1. On the **Transformations** tab, select **New**, and then select **Upload file** to open the **Select a file** dialog.
1. Select **Browse**, and select the following transformations:

    - For the **FiasAddressObjectEntity** entity, select the **fiasAddrObjTrans** transformation.
    - For the **FiasHouseEntity** entity, select the **fiasHousesTrans** transformation.
    - For the **FiasSteadEntity** entity, select the **fiasSteadsTrans** transformation.
    - For the **FiasRoomEntity** entity, select the **fiasRoomsTrans** transformation.

## FIAS import

### Do a full FIAS import to an empty database

Because the full FIAS database contains a very large number of records, some performance issues might occur during import. To help prevent these issues, the first time that you do an import, you should use the FIAS database file in TXT format. You can find this file in the LCS Shared asset library. It contains the FIAS database on December 1, 2018.

To do a full FIAS import to an empty database, follow these steps:

1. Go to [LCS](https://lcs.dynamics.com/Logon/Index), and in the Shared asset library, on the **Data package** tab, download the **RU FIAS - addrObjCSV** file. Verify that the file contains the AS_ADDROBJ_20181216_\<number of state\>.txt file and, optionally, House, Stead, and Room files.
1. Create a zip archive that contains the files from the downloaded package for one or more states.
1. In Dynamics 365 Finance, go to **Organization administration \> Global address book \> Import from FIAS**.
1. Select **Import FIAS** to open the **Import of data** dialog.
1. On the **Parameters** FastTab, select **Browse** to select the zip archive that you created earlier.
1. Set the **Full import** option to **Yes**.
1. If you intend to import houses and steads, set the **Does include houses** option to **Yes**.
1. If you intend to import rooms, set the **Does include rooms** option to **Yes**.

   ![Import data pane.](../media/15%20Import%20of%20data.jpg)

1. Select **OK** to start the import.
1. Select **Refresh** in the upper right of the page to view the line together with the results of the full import.
    
   ![Options tab.](../media/16%20Import%20from%20FIAS.jpg)

### Update addresses from FIAS

To update addresses from FIAS, follow these steps:

1. Download the database with the latest updated date from [The FIAS website](https://fias.nalog.ru/).
1. Select the downloaded database in ZIP format, and do the import just as you did in the previous section. However, in the **Import of data** dialog, set the **Full import** option to **No**.

### Tips for speeding up the import process

The time that is required to import FIAS data depends on the amount of data that is being imported and the system setup. Here are some tips that might help speed up the import process.

To potentially speed up the import process, follow these steps:

1. In Dynamics 365 Finance, go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Framework parameters** tile to open the **Data import/export framework parameters** page.
1. On the **Entity settings** tab, select **Configure entity execution parameters** to open the **Entity import execution parameters** page.
1. Set the following fields to configure multithreading for FIAS entities that are used in import jobs:
    - In the **Entity** field, select the FIAS entity.
    - In the **Import threshold record count** field, enter the threshold record count for import.
    - In the **Import task count** field, enter the count of import tasks.

   ![Entity import execution parameters.](../media/17%20Entity%20import%20execution%20parameters.jpg)

When you run a full import job, provide several regions, but not all regions, at the same time.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
