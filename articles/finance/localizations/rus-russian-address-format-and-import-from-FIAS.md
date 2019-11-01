
# Russian address


## Introduction

Address formats determine how address data will appear when it's printed. In the
system, you can set up address formats for every country or region where
business is done. In Russia, addresses have a standardized form. However,
additional information can be included, such as the district, street code,
building complement, building, apartment, group of houses, group of flats, and
land plot.

The Federal Informational Address System (or FIAS) address database might be
required for businesses in the Russian Federation. You can use specialized tools
to import FIAS into your system and keep it up to date. This topic explains how
to set up and use the FIAS import mechanisms.

## Set up Russian address formats

### Set up the address format, country or region, state or province, county, city and postal code

1.  Go to **Organization administration \> Global address book \> Addresses \>
    Address setup** to open the **Address setup** page.

2.  On the **Address format**, **Country/region**, **State/province**,
    **County**, **City** and **ZIP/postal codes** tabs, you can set up the
    address format, country or region, state or province, county, city, and
    postal code.

### Set up a new district

1.  On the **Address setup** page, on the **District** tab, select the country
    or region, state or province, county code, and city code.

2.  Select **New** to create a new district for the selected country or region,
    state or province, county, and city.

3.  In the **District** field, enter the unique code for the district.

4.  In the **Description** field, enter the official name of the district.

5.  In the **ZIP/postal code** field, select the postal code.

![](media/5f30fdd4a3e33e1250147ce8f9851074.png)

6.  Select **Save**.

### Set up a street code

1.  On the **Address setup** page, on the **Street** tab, verify that **RUS** is
    selected in the **Country/region** field.

2.  Select the state or province, county code, city code, and district code.

3.  Select **New** to create a new street for the selected country or region,
    state or province, county, city, and district.

4.  In the **Street code** field, enter the unique code for the street.

5.  In the **Street** field, enter the official name of the street.

6.  In the **ZIP/postal code** field, select the postal code.

![](media/278fffff5e9f1154dfbc02ca8fbdaca4.jpg)

7.  Select **Save**.

### Set up a group of houses

1.  On the **Address setup** page, on the **Group of houses** tab, verify that
    **RUS** is selected in the **Country/region** field.

2.  Select the state or province, county code, city code, district code, and
    street code.

3.  Select **New** to create a new group of houses for the selected country or
    region, state or province, county, city, district, and street.

4.  In the **Group of houses code** field, enter the unique code for the group
    of houses.

5.  In the **Numbers of buildings** field, enter a comma-separated list of the
    building numbers of the houses in the group.

6.  In the **ZIP/postal code** field, select the postal code.

![](media/402bbf153fd04e9ae14ce9bf2d2a9bb0.jpg)

7.  Select **Save**.

### Set up a group of flats

1.  On the **Address setup** page, on the **Group of flats** tab, verify that
    **RUS** is selected in the **Country/region** field.

2.  Select the state or province, county code, city code, district code, street
    code, and group of houses code.

3.  Select **New** to create a new group of flats for the selected country or
    region, state or province, county, city, district, street, and group of
    houses.

4.  In the **Group of flats code** field, enter the unique code for the group of
    flats.

5.  In the **Group of flats** field, enter a comma-separate list of the flat
    numbers of the flats in the group.

6.  In the **ZIP/postal code** field, select the postal code.

![](media/5d685d220004bcfaa59336e85755ede6.jpg)

7.  Select **Save**.

### Set up land plots

1.  On the **Address setup** page, on the **Land plots** tab, verify that
    **RUS** is selected in the **Country/region** field.

2.  Select the state or province, county code, city code, district code, and
    street code.

3.  Select **New** to create a new land plot for the selected country or region,
    state or province, county, city, district, and street.

4.  In the **Land plot code** field, enter the unique code for the land plot.

5.  In the **Numbers of land plots** field, enter a comma-separated list of the
    numbers of the land plots.

6.  In the **ZIP/postal code** field, select the postal code.

![](media/d0de9fd0896f0d20b52962fe583119b2.jpg)

7.  Select **Save**.

Create an address for a customer
--------------------------------

1.  Go to **Accounts receivable \> Customers \> All customers**.

2.  Open a customer record, and then, on the **Addresses** FastTab, select
    **More options \> Advanced** to open the **Manage addresses** page.

![](media/0597084166eb870638a0db78d590a11f.png)

3.  On the **Address** FastTab, in the **Country/region** field, select **RUS**.

4.  In the **ZIP/postal code** field, select the postal code.

-   After you select a postal code, the **District** field shows the district
    code and name.

5.  In the **Street code** field, select the street code. The street name is
    shown on the right side of the **Street code** field and is also entered in
    the **Street** field.

6.  In the **Building complement** field, enter the name of the building. The
    building name is also entered in the **Street** field.

7.  In the **Building** field, enter the building number. The building number is
    also entered in the **Street** field.

8.  In the **Apartment** field, enter the apartment number. The apartment number
    is also entered in the **Street** field.

9.  In the **Group of houses** field, select the group of houses code. The
    corresponding building numbers are shown.

10.  In the **Group of flats** field, select the group of flats code. The
    corresponding flat numbers are shown.

![](media/f10cc61de15d4460d36d9d61d2e91b07.jpg)

11.  Select **Save**.

Import from FIAS
----------------

### Import an FIAS metadata package

1.  Download the **RU FIAS – FiasMetadataPackage** file from the **Data
    package** tab of the Shared asset library in Microsoft Dynamics Lifecycle
    Services (LCS). This package file contains the required data for the import
    jobs runtime.

![](media/a844d323405e286961a931752a875ba6.jpg)

2.  Go to **System administration \> Workspaces \> Data management**.

3.  In the **Import / Export** section, select the **Import** tile to create a
    new import job.

![](media/4eda7079be1838894a52f86da00c9cc6.jpg)

4.  In the **Group name** field, enter **ImportFiasMetadata**.

5.  In the **Description** field, enter a description.

6.  On the **Selected entities** FastTab, select **Add file** to add the
    following files from the package file that you downloaded earlier:

-   Abridgements of addresses

-   FiasEstateStatusEntity

-   FiasFlatTypeEntity

-   FIASOperationStatusesEntity

-   FiasStructureStatusEntity

>   After you select each file, select **Upload and add**.

7.  Select **Save**.

![A screenshot of a social media post Description automatically generated](media/90c779e3d50ba606639e7b9c0bac33a8.jpg)

### Set up a template to import FIAS data

1.  Go to **System administration \> Workspaces \> Data management**.

2.  In the **Import / Export** section, select the **Templates** tile to open
    the **Template** page.

3.  Select **New** to create a new template.

4.  In the **Template ID** field, enter the identification number of the
    template.

5.  In the **Description** field, enter a description.

6.  In the **Template status** field, select **Validated**.

7.  On the **Entities** FastTab, select **Add entity** to add the following data
    entities:

-   FiasAddressObjectEntity

-   FiasHouseEntity

-   FiasSteadEntity

-   FiasRoomEntity

>   After you select each entity in the **Entity name** field, select **Add
>   entity**.

8.  Select **Save**.

![A screenshot of a social media post Description automatically generated](media/6c31b3dd4004cedd554e6602dbf9748a.jpg)

### Set up a job for a full FIAS import

When you import FIAS data into the system the first time, you should create a
job for a full FIAS import.

1.  Go to **System administration \> Workspaces \> Data management**.

2.  In the **Import / Export** section, select the **Import** tile to create a
    new import job.

3.  In the **Group name** field, enter **FiasFullImportJob**.

4.  In the **Description** field, enter a description.

5.  On the **Selected entities** FastTab, select **Add template** to add the
    template that you created earlier.

6.  In the **Entity replace or merge** field group, select **Merge**.

7.  In the **Source data format** field, select
    **VerticalBarSeparated-Unicode**.

8.  Select **OK**, and then select **Save**.

![A screenshot of a social media post Description automatically generated](media/f4c92c810ccb840bd97c7337755ff762.jpg)

### Set up a job to import FIAS delta

To update existing address data, you should create a job to import FIAS delta.

1.  Download the **RU FIAS – FiasTransformations** file from the **Data
    package** tab of the Shared asset library in LCS.

2.  Go to **System administration \> Workspaces \> Data management**.

3.  In the **Import / Export** section, select the **Import** tile to create a
    new import job.

4.  In the **Group name** field, enter **FiasDeltaImportJob**.

5.  In the **Description** field, enter a description.

6.  On the **Selected entities** FastTab, select **Add template** to add the
    template that you created earlier.

7.  In the **Entity replace or merge** field group, select **Merge**.

8.  In the **Source data format** field, select **XML-Attribute**.

9.  Select **OK**.

![](media/3e52b078a17053cc192334e9ebbfbc2e.jpg)

10.  For each entity, select the button in the **View map** column to open the
    **Map source to staging** page.

![A screenshot of a cell phone Description automatically generated](media/2eeb3241425ce4d6e8f9a1e738e07cb7.jpg)

11.  On the **Transformations** tab, select **New**, and then select **Upload
    file** to open the **Select a file** dialog box.

12.  Select **Browse**, and select the following transformations:

-   For the **FiasAddressObjectEntity** entity, select the **fiasAddrObjTrans**
    transformation.

-   For the **FiasHouseEntity** entity, select the **fiasHousesTrans**
    transformation.

-   For the **FiasSteadEntity** entity, select the **fiasSteadsTrans**
    transformation.

-   For the **FiasRoomEntity** entity, select the **fiasRoomsTrans**
    transformation.

## FIAS import

### Do a full FIAS import to an empty database

Because the full FIAS database contains a very large number of records, some
performance issues might occur during import. To help prevent these issues, the
first time that you do an import, you should use the FIAS database file in TXT
format. You can find this file in the Shared asset library in LCS. It contains
the FIAS database on December 1, 2018.

1.  Download the **RU FIAS - addrObjCSV** file from the **Data package** tab of
    the Shared asset library in LCS. Verify that the file contains the
    AS_ADDROBJ_20181216_\<number of state\>.txt file and, optionally, House,
    Stead, and Room files.

2.  Create a zip archive that contains the files from the downloaded package for
    one or more states.

3.  Go to **Organization administration \> Global address book \> Import from
    FIAS**.

4.  Select **Import FIAS** to open the **Import of data** dialog box.

5.  On the **Parameters** FastTab, select **Browse** to select the zip archive
    that you created earlier.

6.  Set the **Full import** option to **Yes**.

7.  If you intend to import houses and steads, set the **Does include houses**
    option to **Yes**.

8.  If you intend to import rooms, set the **Does include rooms** option to
    **Yes**.

![](media/fb049754cabb82b3f12c34e0e9556fdc.jpg)

9.  Select **OK** to start the import.

10.  Select the **Refresh** button in the upper right of the page to view the
    line together with the results of the full import.

![](media/6ce87833d9aa480e53574ac8fde3f78d.jpg)

### Update addresses from FIAS

1.  Download the database from the last update date from
    <https://fias.nalog.ru/>.

2.  Select the downloaded database in ZIP format, and do the import just as you
    did in the previous section. However, in the **Import of data** dialog box,
    set the **Full import** option to **No**.

### Tips for speeding up the import process

The time that is required to import FIAS data depends on the amount of data that
is being imported and the system setup. Here are some tips that might help speed
up the import process.

-   Try the following procedure:

    1.  Go to **System administration \> Workspaces \> Data management**.

    2.  In the **Import / Export** section, select the **Framework parameters** tile
    to open the **Data import/export framework parameters** page.

    3.  On the **Entity settings** tab, select **Configure entity execution
    parameters** to open the **Entity import execution parameters** page.

    4.  Set the following fields to configure multithreading for FIAS entities that
    are used in import jobs:

        -   In the **Entity** field, select the FIAS entity.

        -   In the **Import threshold record count** field, enter the threshold
        record count for import.

        -   In the **Import task count** field, enter the count of import tasks.

![](media/6d893f05e1992578b324232c0cb6ef64.jpg)

-   When you run a full import job, provide several regions, but not all
    regions, at the same time.
