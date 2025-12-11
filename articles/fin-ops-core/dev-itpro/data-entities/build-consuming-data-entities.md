---
title: Build and consume data entities
description: Learn how to build an entity and how to consume some out-of-band (OOB) entities in an integration scenario, including prerequisites and key concepts.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/29/2025
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: 1de997fb-d5c4-4668-9759-0758d141a3eb
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Build and consume data entities

[!include [banner](../includes/banner.md)]

This tutorial shows how to build an entity and how to consume some out-of-band (OOB) entities in an integration scenario. You'll also preview how these data entities are consumed in various integration scenarios, such as data import and export, integration, and OData services.

When you're ready to build your first entity for production, you need to:

- Create your own package and model. For more information, see [Models and packages](../dev-tools/models.md).
- Create a new project and set the model property to the one that you created.

## Prerequisites

This tutorial requires that you access an environment by using Remote Desktop, and that you're provisioned as an administrator on the instance.

Throughout this tutorial, baseUrl refers to the base URL of the instance.

- In the cloud environment, get the base URL from Microsoft Dynamics Lifecycle Services (LCS).
- On a [local virtual machine (VM)](../dev-tools/access-instances.md#vm-that-is-running-locally), the base URL is `https://usnconeboxax1aos.cloud.onebox.dynamics.com`.
- Download FMLab sample code to C:. For details, see [FMLab sample code](https://github.com/Microsoft/FMLab).

## Key concepts

- Develop a data entity in Microsoft Visual Studio.
- Enable a data entity for data management and OData services.
- Consume a data entity in integration scenarios.

## Business problem

Fleet Management stores customer data in the FMCustomer table and address data in the FMAddressTable table. To access or update customer information, users must access multiple tables. Instead, create a business object that functionally represents customer information, and use it to build integration solutions.

## Building the FMLabCustomer entity

In this section, you must create a data entity for FMLabCustomer in the Fleet Management model. This entity is used to manage master data through import/export and integration services. The primary data source is FMCustomer, and the secondary data source is FMAddressTable.

### Data entity

FMLabCustomerEntity

#### Data entity fields

| Name          | Mapping                     |
|---------------|-----------------------------|
| CellPhone     | FMCustomer.CellPhone        |
| DriversLicense| FMCustomer.DriversLicense   |
| Email         | FMCustomer.Email            |
| FirstName     | FMCustomer.FirstName        |
| LastName      | FMCustomer.LastName         |
| CustomerGroup | FMCustomer.CustGroup        |
| AddressLine1  | FMAddressTable.AddressLine1 |
| AddressLine2  | FMAddressTable.AddressLine2 |
| City          | FMAddressTable.City         |
| State         | FMAddressTable.State        |
| ZipCode       | FMAddressTable.ZipCode      |
| Country/region| FMAddressTable.Country      |

#### Corresponding staging table

Staging tables are used in import/export scenarios to provide intermediary storage during file parsing and transformation. These tables are also used in connector integration scenarios. In many cases, staging tables are mapped 1:1 to an entity. The staging table that corresponds to the **FMLabCustomerEntity** entity is named FMLabCustomerStaging.

### Create a new project

1. In Visual Studio select **File** &gt; **New** &gt; **Project**, and then select **finance and operations Project**.
1. Right-click the project, select **Properties**, and verify that the project is in the Fleet Management model. If it isn't, set the **Model** property to **Fleet Management**.

### Add a new data entity to your project

1. Create a new entity that is named **FMLabCustomerEntity**. Right-click you project, and then select **Add** &gt; **New item**. The **Add New Item** dialog box opens.
1. Select **Data Entity**, and then set the **Name** property to **FMLabCustomerEntity**.
1. Select **Add**.
1. In the **Data entity** wizard, specify the properties for the data entity that you're creating. Use the values that are shown in the following image.

    > [!NOTE]
    > The name of an entity must not have '\_' or any numeric digits (0…9). Using these characters may result in mapping errors later.

    :::image type="content" source="./media/data-entity-wizard.png" alt-text="Screenshot of Data Entity Wizard.":::

1. Select **Next**. For more information about the function of each property, see "Categories of entities" and "Building an entity" in [Data entities overview](data-entities.md).
1. Add fields to the new entity from your data source, as shown in the following image. You can add fields from the primary data source, **FMCustomer**. For this entity, clear the check box for the **Image** and **LicenseImage** container types to simplify testing.
1. Rename the data entity fields to reflect public data contract standards, or select **Convert labels to field names** to generate names from the existing labels.
1. On the line for the **DriversLicense** field, select the **Is mandatory** check box. This field is used as the natural key for the entity.

    :::image type="content" source="./media/data-entity-wizard-2.png" alt-text="Screenshot of Data Entity Wizard 2.":::

1. In the **Data source** field, select **PrimaryAddress**. Notice that the **PrimaryAddress** data source is automatically added because of automatic expansion or the surrogate foreign key replacement of **AddressID**.

    :::image type="content" source="./media/steps-and-add-fields.png" alt-text="Screenshot of steps and add fields.":::

1. Select the fields from the **PrimaryAddress** data source that you want to be part of your entity. Additionally, rename the following fields to reflect proper public data contract naming:

    - PrimaryAddress \_AddressLine1 &gt; AddressLine1
    - PrimaryAddress \_AddressLine2 &gt; AddressLine2
    - PrimaryAddress \_City &gt; City
    - PrimaryAddress \_State &gt; State
    - PrimaryAddress \_ZipCode &gt; ZipCode
    - PrimaryAddress \_Country &gt; Country

    :::image type="content" source="./media/data-entity-wizard-3.png" alt-text="Screenshot of Data entity wizard.":::

1. Select **Finish**. A data entity item and staging table are added to the project.

    :::image type="content" source="./media/solution-explorer.png" alt-text="Screenshot of Solution explorer.":::

### Build your project

1. In Solution Explorer, right-click your project, and then select **Properties**.
1. Change the value of the **Synchronize database on build** property to **True**, and then select **OK**. This property must be set only one time per project.

    > [!NOTE]
    > Entities are created as views in Microsoft SQL Server, and staging tables are also added. Therefore, you must sync a database when you build entities.

    :::image type="content" source="./media/property-pages.png" alt-text="Screenshot of Property pages.":::

1. On the Visual Studio toolbar, Select **Build** &gt; **Build Solution** to build the project.
1. Verify that the build doesn't contain any errors. At this point in the tutorial, warnings are allowed.

### Visually validate and customize an entity

1. In Solution Explorer, right-click the **FMLabCustomerEntity** node, and then select **Open**. The designer for the entity opens in the middle pane.
1. Validate the properties of the **FMLabCustomerEntity** entity. Select the entity in Solution Explorer, and compare the **Properties** pane values to the following image.
1. Set the **Label** property to **Fleet Lab Customers**.

    :::image type="content" source="./media/fmlabcustomerentity-properties.png" alt-text="Screenshot of FMLabCustomerEntity - Properties.":::

1. In the left pane, select **Data Sources** &gt; **FMCustomer** &gt; **Data Sources** &gt; **FMAddressTable**.
1. Change the **Is Read Only** property to **No**. This is a known issue. Eventually, the value is set to **Yes** or **No** automatically, based on the type of join. The value should be **Yes** for composition scenarios, and **No** for associations (surrogate foreign key expansions). This property enables the data source to be read/write.

    :::image type="content" source="./media/fmlabcustomerentity-properties2.png" alt-text="Screenshot of FMLabCustomerEntity - Properties2.":::

1. In the **FMLabCustomerEntity** designer, select **Keys** &gt; **EntityKey**, and then expand the **Fields** node. Verify that the list of fields matches the following image.

    :::image type="content" source="./media/fmlabcustomerentity.png" alt-text="Screenshot of FMLabCustomerEntity.":::

1. To visually validate the staging table that will be used for import/export, open the **FMLabCustomerStaging** table in the designer, and then select the **FMLabCustomerStaging** node.

    :::image type="content" source="./media/fmlabcustomerstaging-properties.png" alt-text="Screenshot of fMLabCustomerStaging - Properties.":::

1. Select **FMLabCustomerStaging** &gt; **Fields**. In the following image, the standard fields of the staging tables are selected. All entity staging tables have these standard fields. The image also shows the data fields that belong on this data entity.

    :::image type="content" source="./media/fmlabcustomerstaging.png" alt-text="Screenshot of FMLabCustomerStaging.":::

1. In Solution Explorer, right-click your project, and then select **Rebuild** to rebuild and synchronize the project.

## Testing data entities

Entities can be tested by using various methods in X++, through data import/export, or through integrations. In this section, we explore scenarios for validating entities.

### Test the entity by using X++ code

One of the most common ways of interacting with data entities is through X++, by using a unit test or a runnable job to validate that the entities have been built. In this example, we'll use a runnable job.

1. In Solution Explorer, select **Add** > **New item** > **Runnable class** to add a runnable class to your project.
1. Copy and paste the following code into the class to test your data entity.

    ```xpp
    public static void main(Args _args)
    {
        FMLabCustomerEntity customer;
        str license = "License";
        Random r = new Random();
        int rand = r.nextInt();
        license = license + int2str(rand);

        //Create a new record in FM lab customer entity
        customer.clear();
        customer.FirstName = "Bob";
        customer.LastName = "Smith";
        customer.DriversLicense = license;
        customer.insert();

        info(strfmt("Tried to insert customer '%1 %2' with license %3", 
            customer.FirstName, customer.LastName, customer.DriversLicense));

        //Display newly created record
        select forupdate customer where customer.DriversLicense==license;
        info(strfmt("Found newly created customer '%1 %2' with license %3", 
            customer.FirstName, customer.LastName, customer.DriversLicense));

        //Now delete the record from the entity
        customer.delete();
        select customer where customer.DriversLicense==license ;
        info(strfmt("Deleted customer does not exist: license- %1", customer.DriversLicense));
    }
    ```

1. Run the code in the debugger to set it as a startup object.
1. To validate the entity, view the Infolog in the debugger window or in notifications on the website. You see that three successful messages are logged. You also see the actions that were taken.

## Importing data by using entities

You can use data entities that have the **Data Management Enabled** property to import and export data in various file formats. In this section, you import data in a CSV file format for the **FMLabCustomer** entity.

### File import

After you create your data entity, validate import/export.

1. Create a sample CSV file that you can import. Copy the following text and save it as **FM Lab Customer Import.csv**.

    ```Console
    CELLPHONE,DRIVERSLICENSE,EMAIL,FIRSTNAME,LASTNAME,CUSTOMERGROUP,ADDRESSLINE1,ADDRESSLINE2,CITY,STATE,ZIPCODE,COUNTRY(999) 555-0100,S615-3939-2349,chris.spencer@adatum.com,Chris,Spencer,adv\_mem\_1,444 Main Street,,Orlando,FL,77899,US(188) 555-0101,S615-3939-2350,Ichiro.lannin@blueyonderairlines.com,Ichiro,Lannin,non\_mem\_1,12 Long Street,,New York City,NY,99087,US(777) 555-0102,S615-3939-2351,josh.smith@fourthcoffee.com,Josh,Smith,adv\_mem\_1,9606 122th Avenue,,Sydney,TX,99874,US(456) 555-0103,S615-3939-2352,Vince@fabrikam.us,Vince,Ahmed,non\_mem\_1,123 Microsoft Way,Unit 87,Seattle,WA,90001,US(345) 555-0104,S615-3939-2353,tony.parker@lucernepublishing.com,Tony,Parker,non\_mem\_1,12012 11th PLNE,Apt 160,San Francisco,CA,75645,US(312) 555-0105,S615-3939-2354,Julia@fineartschool.net,Julia,Natarajan,exec\_mem\_1,449 Long Street,Apt 160,Bruxelles,ID,34213,US
    ```

1. Select **User Dashboard** > **Data management**.
1. In the **Data Management** workspace, select the **Import** tile.
1. On the **Import** page, enter the import details as shown in the following image.

    :::image type="content" source="./media/import-new-record.png" alt-text="Screenshot of Import new record.":::

1. Select the **Upload data** button next to the **Upload file for entity** field, and select the CSV file that you created.
1. After the file is uploaded, you notice that the entity is added to the middle section. You also receive an error that states that the mapping isn't valid. A few fields aren't mapped correctly between the source file and the target entity.
1. In the entities list, select **View map**.
1. **AddressLine1** and **AddressLine2** are two fields in the source that aren't mapped to target fields. In the visual mapper or details view, map these fields as follows, and then select **Save**:

    - AddressLine1 – Address1
    - AddressLine2 – Address2

    :::image type="content" source="./media/map-source-to-staging.png" alt-text="Screenshot of Map source to staging.":::

1. Select the **Back** button in your browser to go back to the **Import job** page. The check mark in the entities list indicates that the entity is now ready for import.

    :::image type="content" source="./media/import-new-record-2.png" alt-text="Screenshot of Import new record 2.":::

1. Select **Import Now**. After the import is completed, the job status page opens.

## Consuming entities by using OData

In this section, you learn how to expose and consume an entity for OData. Before you begin, verify that the Fleet demo data is loaded from the client: \[baseURL\]/?f=FMSetup

### Review the FleetRental entity and add a navigation property for OData

You review the existing **FleetRental** entity and then create a relationship from one data entity to another. This relationship is used as a navigation property for OData entities.

1. In Solution Explorer, verify that you're in the **FMEntityLab** project.
1. In Application Explorer, search for **FMRentalEntity**, right-click it, and then select **Add to Project**.
1. In Application Explorer, search for **FMCustomerEntity**, right-click it, and then select **Add to project**.
1. In Solution Explorer, right-click **FMRentalEntity**, and then select **Open**.
1. In the view designer, select the root node, **FMRentalEntity**, and review the following properties.

    | Property               | Value        | Description |
    |------------------------|--------------|-------------|
    | IsPublic               | Yes          | When this property is set to **Yes**, the entity is visible by using the OData application programming interface (API). |
    | Public Entity Name     | FleetRental  | The name that is used in the OData APIs for **EntityType**. |
    | Public Collection Name | FleetRentals | The name that is used for the OData collection entity. |

1. In the view designer, expand the **Relations** node.
1. Select **Customer Relation**, and then select **Delete**.
1. Right-click **Relations**, and then select **New** &gt; **Relation**.
1. Select **Relation1**, and set the following properties.

    | Property                        | Value            |
    |---------------------------------|------------------|
    | Cardinality                     | ZeroMore         |
    | Name                            | CustomerRelation |
    | Related Data Entity             | FMCustomerEntity |
    | Related Data Entity Cardinality | ExactlyOne       |
    | Related Data Entity Role        | CustomerRole     |
    | Relationship Type               | Association      |
    | Role                            | Rental           |

1. In the view designer, right-click the **CustomerRelation** node, and then select **New** &gt; **Normal**.
1. Right-click the new node under **CustomerRelation**, and then select **Properties**.
1. Set the following properties.

    | Property      | Value                                                                         |
    |---------------|-------------------------------------------------------------------------------|
    | Field         | **CustomerDriversLicense** - This is the foreign key field on **FMRentalEntity**. |
    | Related Field | **DriversLicense** - This is the unique key on **FMCustomerEntity**.              |

    The following image shows the relation in Visual Studio.

    :::image type="content" source="./media/fmrentalentity-solution-explorer.png" alt-text="Screenshot of FMRentalEntity - Solution explorer.":::

1. On the **BUILD** menu, select **Build Solution** to save your changes and build the project. You can view the build progress in the **Output** window.
1. To update the OData endpoint with the changes, you must run an **iisreset** command. Open a **Command Prompt** window as an administrator, and enter **iisreset**.

You now create a navigation property between **FMRentalEntity** and **FMCustomerEntity**.

### Use standard OData syntax to retrieve data

In this section, you use some of the standard OData syntax to navigate and query the OData entities that are exposed in the Fleet Management model. First, follow these steps to enable Internet Explorer to view JSON formatted data.

1. Close all Internet Explorer windows.
1. Go to C:\\FMLab, and select and double-click the json-ie.reg file.
1. In the **Registry Editor** dialog box, select **Yes**.
1. Select **OK**.

You can now use Internet Explorer to explore some OData URIs.

1. Start Internet Explorer, and enter the following URL in the address bar: \[baseURL\]/data/$metadata You see all the metadata that is associated with OData entities.

    > [!NOTE]
    > The metadata can take a few minutes to appear the first time that you access it. In the XML, you can see all of the properties and navigation properties associated with the OData entities.

1. In the browser, find **FleetRental**. The following image shows the metadata of the **FleetRental** entity, together with the new relationship, **NavigationProperty**.

    :::image type="content" source="./media/fleetrental-metadata.png" alt-text="Screenshot of FleetRental metadata.":::

1. To view all the customers in the Fleet Management application in JSON format, enter the following URL into the address bar of your browser: \[baseURL\]/data/FleetCustomer

    > [!NOTE]
    > Entity names are case-sensitive.

1. If you don't want to retrieve all properties for the customers, you can retrieve selected properties. For example, to retrieve only **FirstName** and **LastName**, enter the following URL: \[baseURL\]/data/FleetCustomers?$filter=FirstName.LastName
1. You can also apply filters. For example, to filter on all customers where **FirstName**=**Phil**, enter the following URL: \[baseUrl\]/data/FleetCustomers?$filter=FirstName%20eq%20'Phil'

    > [!NOTE]
    > These URLs don't work if you copy and paste them. You must manually enter them in the address bar.

1. To retrieve all the **Rental** records, together with all details of the customers, enter the following URL: \[baseURL\]/data/FleetRentals?$expand=CustomerRole The following example shows a **Rental** record, together with details of the linked customer, in JSON format.

    ```Text
    "@odata.context":"https://testax32aos.cloud.test.dynamics.com/en/data/$metadata#FleetRentals","value":
    {  
        { 
            "@odata.etag":"W/"JzEsNTYzNzE0NDU3NjsxLDU2MzcxNDQ1NzY7MTc4NjA2OTg1Niw1NjM3MTQ0NjA1Jw=="",
            "Comments":"","StartMileage":0,"VehicleRatePerDay":40,"CustomerDriversLicense":
            "S468-3184-6541","VehicleRateTotal":280,"VehicleId":"Litware_LitwareFour_1",
            "RentalId":"000001",
            "StartFuelLevel":"Full","StartDate":"2010-04-09T00:00:00Z","CustomerLastName":"Spencer",
            "EndMileage":0,"VehicleVIN":"2J4FY19P0NJ710529",
            "RecId":5637144576,"EndDate":"2010-04-16T00:00:00Z",
            "VehicleRatePerWeek":270,"CustomerFirstName":"Phil","State":3,
            "EndFuelLevel":"","CustomerRole":

            {"@odata.etag":"W/"JzEsNTYzNzE0NDU3NjsxLDU2MzcxNDQ1NzYn"",
            "CellPhone":"(999) 555-0100",
            "DriversLicense":"S468-3184-6541","AddressLine2":"",
            "State":"FL","Country":"US","FirstName":"Phil",
            "Email":"phil.spencer@adatum.com","CustomerGroup":
            "adv_mem_1","AddressLine1":"167 BBN Way","City":"Orlando",
            "ZipCode":77899,"RecId":5637144576,"LastName":"Spencer"
        }  
    }
    ```

### Add an action to OData entity

Actions provide a way to inject behaviors into the data model. In Dynamics 'AX 7,' you add actions by adding a method to the data entity and then decorating the method with specific attributes. In this section, we walk through the steps for adding an action.

1. In Solution Explorer, right-click **FMRentalEntity**, and then select **View code**.
1. Copy the following code lines, and paste them into the **Code** window.

    ```xpp
    public class FMRentalEntity extends common
    {
        [SysODataActionAttribute("ReturnRental", true)]
        public str ReturnRental()
        {
            //do something
            return "Rental was successfully returned. Thanks for your business";
        }
    }
    ```

1. On the **BUILD** menu, select **Rebuild Solution** to save your changes and build the project. You can view the build progress in the **Output** window.
1. To update the OData endpoint with the changes, you must run an **iisreset** command. Open a **Command Prompt** window as an administrator, and enter **iisreset**.

    The action that you just added can be invoked through code, as you'll see in the next section.

### Consume the OData API from an external console application

In this section, you use a console application to consume the OData endpoints that are exposed in the Fleet Management application. The console application first creates a new customer and then creates a new reservation for that customer. This tutorial shows how easy it's to use OData together with standard .NET Windows Communication Foundation (WCF) data service libraries to integrate with Dynamics AX.

1. Start a new instance of Visual Studio.
1. On the **File** menu, select **Open** &gt; **Project/Solution**.
1. In the **Open Project** dialog box, browse to **C:\\FMLab\\Odata4ConsoleApplication**, and then select **Odata4ConsoleApplication.csproj**.
1. Select **Open**. The **Odata4ConsoleApplication** project appears in Solution Explorer.
1. In Solution Explorer, double-click **OdataProxyGenerator.tt**.
1. In the code editor, replace the following string with your organization's URL.

    ```xpp
    <baseURL> public const string MetadataDocumentUri = "<baseURL>/data/"
    ```

1. Save the OdataProxyGenerator.tt file.
1. In the **Save of Read-only file** dialog box, select **Overwrite**. The proxy class for the OData metadata endpoint is generated. This operation might take a few minutes.
1. In Solution Explorer, double-click **Program.cs**.
1. Replace the value of the **dynamicsBaseUri** variable with your organization's URL.
1. Verify that there's a final closing slash (/) in the URL, and then select **Save**.
1. In the **Save of Read-only file** dialog box, select **Overwrite**.
1. Press F5 to run the application, and then follow the instructions in the output console window. The application might prompt you for your Dynamics AX credentials. After the application has run, the new customer and the corresponding reservation are created.
1. Follow these steps to verify that the new reservation appears on the **Rental** page:

    1. Start Internet Explorer, and enter the following URL in the address bar: \[baseURL\]/?mi=FMRental The **FMRental** page shows the list of rentals.

        :::image type="content" source="./media/rental-list.png" alt-text="Screenshot of Rental list.":::

    1. At the bottom of the list, select **Next** to view the next page. On this page, you can see that the reservation was created for the new customer that you added.

        :::image type="content" source="./media/customer-reservation.png" alt-text="Screenshot of customer reservation.":::

This completes the walkthrough, where you see an external client interacting with the Fleet Management model by using the OData endpoint.

## Casing rules in data entities

### XML format

During export, the entity name and field names are exported in uppercase. If there's a need to apply a transformation, the transformation must use uppercase in all references.

During import, data management accepts input files in any casing. But ensure that you use the same format for a given attribute or element in the file. When applying a transformation, ensure that the transformation uses the same casing rules in all references as in the incoming file.

### Excel format

During export, column names are exported in uppercase. Imports aren't case sensitive.

### CSV format

During an export, column names are exported in uppercase. Imports aren't case sensitive.

## Tips and tricks

### Max join limits

During entity development, ensure that the overall structure of the entity doesn't exceed the max join limit of 26. This is the default limit. Increasing the join limit isn't recommended because it can have unintended consequences. If this limit is exceeded, the entity most likely fails to process records and results in the following SQL error. We also recommend managing the total number of columns in the entity to avoid this error.

```Console
Cannot create a row of size xxx which is greater than the allowable maximum row size of 8060
```

### Exporting container fields

If an entity has container fields and these fields need to be exported, the entity must implement **getFieldsToBeConvertedToFile** to let each container field export its data value to a separate file. This allows for container fields to be exportable and at the same time, prevents making the entity export file (core entity data without the container fields) unreadable. If **getFieldsToBeConvertedToFile** isn't implemented, then these fields won't be exported but the rest of the entity data exports as usual.

## Related information

[Develop entities for data migration](develop-entity-for-data-migration.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]