---
title: Computed columns and virtual fields in data entities
description: Learn about computed and virtual fields, which are the two types of unmapped fields that a data entity can have.
author: jaredha
ms.author: jaredha
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 01/14/2026
ms.reviewer: twheeloc
audience: Developer
ms.assetid: 88d230af-7d3d-49b3-bf19-69ecf81ed751
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Computed columns and virtual fields in data entities

[!include [banner](../includes/banner.md)]

This article provides information about computed and virtual fields, which are the two types of unmapped fields that a data entity can have. It includes information about the properties of unmapped fields, and examples that show how to create, use, and test them.

The sample code is targeted toward creating or modifying an entity that is part of a solution that you own. Extending an existing entity requires slight modifications.

## Overview

A data entity can have additional *unmapped* fields beyond those that are directly mapped to fields of the data sources. You can generate values for unmapped fields by using two mechanisms:

- Custom X++ code
- SQL executed by Microsoft SQL Server

The two types of unmapped fields are computed and virtual. Unmapped fields always support read actions, but the feature specification might not require any development effort to support write actions.

### Computed field

- A SQL view computed column generates the value.
- During read, SQL computes the data and fetches it directly from the view.
- For writes, custom X++ code parses the input value and then writes the parsed values to the regular fields of the data entity. The values are stored in the regular fields of the data sources of the entity.
- Use computed fields mostly for reads.
- If possible, use computed columns instead of virtual fields, because computed columns are computed at the SQL Server level, whereas, virtual fields are computed row by row in X++.

### Virtual field

- Is a non-persisted field.
- Is controlled by custom X++ code.
- Read and write happens through custom X++ code.
- Use virtual fields for intake values that are calculated by using X++ code and can't be replaced by computed columns.
- Search and filtering on virtual fields aren't supported.

### Properties of unmapped fields

| Category | Name | Type | Default value | Behavior |
|----------|------|------|---------------|----------|
| Data | IsComputedField | NoYes | Yes | <ul><li><strong>Yes</strong> – The field is synchronized as a SQL view computed column. Requires an X++ method to compute the SQL definition string for the column. The virtual column definition is static and is used when the entity is synchronized. After that, the X++ method isn't called at run time.</li><li><strong>No</strong> – The field is a true virtual field, where inbound and outbound values are fully controlled through custom code.</li></ul> |
| Data | ComputedFieldMethod | String | | A static <strong>DataEntity</strong> method in X++ to build the SQL expression that generates the field definition. This property is disabled and irrelevant if the property <strong>IsComputedField</strong> is set to <strong>No</strong>. The method is required if the property <strong>IsComputedField</strong> is set to <strong>Yes</strong>. |
| Data | ExtendedDataType | String | | |

## Example: Create a computed field

In this example, you add a computed field to the **FMCustomerEntity** entity. For reads, the field combines the name and address of the customer into a formatted string. For writes, your X++ code parses the combined value into its separate name and address values, and then the code updates the regular name and address fields.

1. In Microsoft Visual Studio, right-click your project, and add the existing **FMCustomerEntity**.
1. In Solution Explorer, right-click the **FMCustomerEntity** node, and then select **Open**.
1. In the designer for **FMCustomerEntity**, right-click the **Fields** node, and then select **New** &gt; **String Unmapped Field**.

    :::image type="content" source="./media/computedcolumnsandvirtualfields11.png" alt-text="Screenshot of creating a new string unmapped field." lightbox="./media/computedcolumnsandvirtualfields11.png":::

1. Rename the new field **NameAndAddress**.
1. Update properties of the **NameAndAddress** unmapped field, as shown in the following screenshot.

    :::image type="content" source="./media/computedcolumnsandvirtualfields21.png" alt-text="Screenshot of updating the properties of the NameAndAddress unmapped field." lightbox="./media/computedcolumnsandvirtualfields21.png":::

1. Go to **FMCustomerEntity** &gt; **Methods**. Right-click the **Methods** node, and then select **New**. Ensure that the method name matches the **DataEntityView Method** property value of the unmapped computed field.
1. Paste the following X++ code into the method. The method returns the combined and formatted **NameAndAddress** value.

    ```xpp
    private static str formatNameAndAddress()   // X++
    {
        DataEntityName      dataEntityName= tablestr(FMCustomerEntity);
        List                fieldList = new List(types::String);
        ////Format name and address to look like following
        ////John Smith, 123 Main St, Redmond, WA 98052
        fieldList.addEnd(SysComputedColumn::returnField(DataEntityName, identifierstr(FMCustomer), fieldstr(FMCustomer, FirstName)));
        fieldList.addEnd(SysComputedColumn::returnLiteral(" "));
        fieldList.addEnd(SysComputedColumn::returnField(DataEntityName, identifierstr(FMCustomer), fieldstr(FMCustomer, LastName)));
        fieldList.addEnd(SysComputedColumn::returnLiteral("; "));
        fieldList.addEnd(SysComputedColumn::returnField(DataEntityName, identifierstr(FMAddressTable), fieldstr(FMAddressTable, AddressLine1)));
        fieldList.addEnd(SysComputedColumn::returnLiteral(", "));
        fieldList.addEnd(SysComputedColumn::returnField(DataEntityName, identifierstr(FMAddressTable), fieldstr(FMAddressTable, City)));
        fieldList.addEnd(SysComputedColumn::returnLiteral(", "));
        fieldList.addEnd(SysComputedColumn::returnField(DataEntityName, identifierstr(FMAddressTable), fieldstr(FMAddressTable, State)));
        fieldList.addEnd(SysComputedColumn::returnLiteral(", "));
        fieldList.addEnd(SysComputedColumn::cast(
            SysComputedColumn::returnField(DataEntityName, identifierstr(FMAddressTable), fieldstr(FMAddressTable, ZipCode)), "NVARCHAR"));
        return SysComputedColumn::addList(fieldList);
    }

    T-SQL for the computed column.

    ( Cast (( ( T1.firstname ) + ( N' ' ) + ( T1.lastname ) + ( N'; ' ) +
        ( T5.addressline1 )
        + ( N', ' ) + ( T5.city ) + ( N', ' ) + ( T5.state ) + (
        N', '
        ) +
        ( Cast(T5.zipcode AS NVARCHAR) ) ) AS NVARCHAR(100))
    )
    AS
    NAMEANDADDRESS
    ```

    > [!TIP]
    > If you receive an error in data entity synchronization because of computed columns, it's easier to come up with the SQL definition in Microsoft SQL Server Management Studio (SSMS) before using it in X++.

1. Rebuild the project.
1. Synchronize the database. Don't forget this step. You can do this by going to **Dynamics 365 &gt; Synchronize database &gt; Synchronize**.

## Example: Create a virtual field

In this example, you add a virtual field to the **FMCustomerEntity** entity. This field displays the full name as a combination of the last name and first name. X++ code generates the combined value.

1. In the designer for the **FMCustomerEntity** entity, right-click the **Fields** node, and then select **New > String Unmapped Field**.
1. In the properties pane for the unmapped field, set the **Name** property to **FullName**.
1. Set the **Is Computed Field** property to **No**. Notice that you leave the **DataEntityView Method** empty.

    :::image type="content" source="./media/computedcolumnsandvirtualfields31.png" alt-text="Screenshot of setting the properties for the unmapped field." lightbox="./media/computedcolumnsandvirtualfields31.png":::

1. In the **FMCustomerEntity** designer, right-click the **Methods** node, and then select **Override > postLoad**. Your X++ code in this method generates the values for the virtual field.
1. Paste the following X++ code in for the **postLoad** override. Notice that the **postLoad** method returns **void**.

    ```xpp
    public void postLoad()
    {
        super();
        //Populate virtual field once entity has been loaded from database
        //Format full name - "Doe, John"
        this.FullName = this.LastName + ", " + this.FirstName;
    }
    ```

1. Compile your project.

## Example: Use a virtual field to receive and parse an inbound field

Imagine that an external system sends the name of a person as a compound value that combines the last and first names in one field that comes into your system. However, your system stores the last and first names separately. For this scenario, you can use the **FullName** virtual field that you created. In this example, the major addition is an override of the **mapEntityToDataSource** method. When you call **update**, the **mapEntityToDataSource** methods are invoked for each data source.

1. In the designer for the **FMCustomerEntity**, right-click the **Methods** node, and then select **Override > mapEntityToDataSource**.
1. Paste the following X++ code in for the **mapEntityToDataSource** method.

    ```xpp
    public void mapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
    {
        super(entityCtx, dataSourceCtx);
        //Check if desired data source context is available
        if (dataSourceCtx.name() == "FMCustomer")
        {
            FMCustomer dsCustomer = dataSourceCtx.getBuffer();
            //Find position of "," to parse full name format "Doe, John"
            int commaPosition = strfind(this.FullName, ",",0,strlen(this.FullName));
            //Update FirstName and LastName in the data source buffer to update
            dsCustomer.LastName = substr(this.FullName,0,commaPosition-1);
            dsCustomer.FirstName = substr(this.FullName, commaPosition+1, strlen(this.FullName));
        }
    }
    ```

## Test the computed and virtual fields

The following **main** method tests your computed and virtual fields. It tests both fields in a read action, and tests the virtual field in an update action.

1. For this example, make sure you have the data set named **Fleet Management (migrated)**. You can find this data set from the dashboard in the browser. Select the menu icon in the upper-right corner, select the **APP LINKS** menu, and then scroll to find the data set named **Fleet Management (migrated)**.
1. Paste the following X++ code into the startup object of your project. Run your project.

    ```xpp
    public static void main(Args _args)   // X++
    {
        FMCustomerEntity customer;
        //Using transactions to avoid committing updates to database
        ttsbegin;
        //SELECT single customer entity record from the database
        select customer
            where customer.Email == "phil.spencer@adatum.com";
        //Read full name (Virtual Field)
        info(customer.FullName);
        //Read formatted NameAndAddress(computed Field)
        info(customer.NameAndAddress);
        //UPDATE full name (virtual field)
        customer.FullName = "Doe, John";
        customer.update();
        //Reselect data from database to get updated information
        select customer
            where customer.Email == "phil.spencer@adatum.com";
        //Read full name (virtual field)
        info(customer.FullName);
        ttsabort;
    }
    ```

### Note on computed column generation failures

> [!NOTE]
> If the X++ method that generates the SQL for a computed column throws an exception, DbSync catches the exception, sets the value of that column to `NULL`, and logs a *warning*.
>
> To avoid hitting a `NULL` value, check configuration keys manually in computed column methods.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
