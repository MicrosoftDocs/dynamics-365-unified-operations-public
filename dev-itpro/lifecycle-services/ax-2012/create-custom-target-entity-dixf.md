---
# required metadata

title: Create a custom target entity for the Data import/export framework (AX 2012)
description: This topic describes how to create a custom entity, so that you can use the Microsoft Dynamics AX Data Import/Export Framework to import, export, or migrate data that does not fit a predefined entity.
author: kfend
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18181
ms.assetid: 60c79bd4-1090-4e79-9a8c-2117d963647a
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Create a custom target entity for the Data import/export framework (AX 2012)

This topic describes how to create a custom entity, so that you can use the Microsoft Dynamics AX Data Import/Export Framework to import, export, or migrate data that does not fit a predefined entity.

A custom entity requires a staging table, a project, a query, a class, and functions. You can use the **Create a custom entity for data import/export Wizard** to create these elements for you, or you can create them manually.

## Prerequisites
Before you begin, you must know which table in Microsoft Dynamics AX maps to the entity that you are creating. This table is either the source of the data that you are exporting or the target of the data that you are importing. If you have to create a new table, follow the instructions in [How to: Create Tables](create-tables.md).

## Create a custom entity by using the Create a custom entity for data import/export Wizard
The **Create a custom entity for data import/export Wizard** lets you quickly create a custom entity.

1.  Go to **Data Import/Export Framework** &gt; **Common** &gt; **Create a custom entity for data import/export**.
2.  Select the table that is related to the entity that you want to migrate, and then click **Next**.
   **Caution**: The wizard can be used to create custom entities that are associated only with tables that do not inherit data structures from other tables.
3.  On the **Select code generation parameters** page, follow these steps:
    1.  The wizard suggests names for the staging table, query, and class. You can accept these names or change them.
    2.  Select a display menu item for the entity. If you have to create a new display menu item, follow the instructions in [How to: Create Menus and Menu Items](https://msdn.microsoft.com/library/5277205c-edb9-498e-b927-406237806217(AX.60).aspx).
    3.  Select whether to use a method or a query to generate data for any foreign keys in the table. Depending on your selection, either a **generate** method is added to the class, or the source tables for the foreign keys are added to the query for the entity.
    4.  If the entity will be used with a data source that contains related data from two tables, select composite entity. The **RowID** field is then created in the staging table. This field is used to map the rows of related data to each other.
    5.  When you have finished setting the values that are required for your entity, click **Next**.

4.  On the **Fields in the target table** page, select the fields for the target table. Click **Next**.
5.  On the **Wizard complete** page, click **Finish**. The Data Import/Export Framework opens the Microsoft Dynamics AX Application Object Tree (AOT) and creates a project for the custom entity in the current layer.
6.  If the table that you selected uses an extended data type (EDT), you are asked two times whether you want to add the ForeignKey relation from the EDT to the new staging table. Click **Yes** each time to create the ForeignKey relationship.
7.  Add the custom entity as a new target entity. Depending on the entity, some manual steps might be required. For more information about how to create a target entity, see [Migrating data using the Data import/export framework (DIXF, DMF)](migrate-data-dixf.md).

## Manually create a custom entity
This section describes how to manually create a custom entity.

### Create a staging table for the entity

1.  In Microsoft Dynamics AX, in the AOT, create a staging table for the entity.
2.  Use the following information to set up the table properties for the staging table.

    | Property name               | Value   |
    |-----------------------------|---------|
    | **SaveDataPerCompany**      | No      |
    | **SupportInheritance**      | No      |
    | **TableType**               | Regular |
    | **ConfigurationKey**        | DMF     |
    | **ValidTimeStateFieldType** | None    |

3.  Create fields that have the following properties.

    | Field name          | Extended data type     | Enum              |
    |---------------------|------------------------|-------------------|
    | **DefinitionGroup** | DMFDefinitionGroupName |                   |
    | **IsSelected**      | DMFIsSelected          | NoYes             |
    | **TransferStatus**  |                        | DMFTransferStatus |
    | **ExecutionId**     | DMFExecutionId         |                   |

4.  Create field groups that have the following properties.

    | Field group name                                                         | Label                                                                         | Field                                                                                        |
    |--------------------------------------------------------------------------|-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
    | **ExclusionList**                                                        | **Exclusion List**                                                            | **DefinitionGroup**                                                                          |
    | ** **                                                                    | ** **                                                                         | **IsSelected**                                                                               |
    | ** **                                                                    | ** **                                                                         | **TransferStatus**                                                                           |
    | ** **                                                                    | ** **                                                                         | **ExecutionId**                                                                              |
    | **Enabled**                                                              | **Enabled**                                                                   | Optional: Fields from the staging table that you want to include in the template by default. |
    | &lt;&lt;FunctionName\_Sequence&gt;&gt;Example – GeneratePostalAddress\_2 | &lt;&lt; Description of function &gt;&gt;Function to generate postal address. | The fields from the staging table that are the source for the specified method.              |
    |                                                                          |                                                                               | **CountryRegionId**                                                                          |
    | ** **                                                                    | ** **                                                                         | **State**                                                                                    |
    | ** **                                                                    | ** **                                                                         | **City**                                                                                     |
    | ** **                                                                    |                                                                               | ..                                                                                           |

5.  Create a primary index for the table.

    | Index name                              | Properties                             | Fields                                                 |
    |-----------------------------------------|----------------------------------------|--------------------------------------------------------|
    | &lt;&lt;any name&gt;&gt;. Example – Idx | AllowDuplicates – NoAlternateKey - Yes | **DefinitionGroup**                                    |
    |                                         |                                        | **ExecutionId**                                        |
    |                                         |                                        | **Fields from the staging table to define uniqueness** |
    |                                         |                                        | ..                                                     |

6.  Specify the relationship between the staging table and the target table. This relation is used to automatically link a particular staging record with the related target entity. If you cannot define the relationship by using the relation node, you should define it by using the addStagingLink() method in the entity class.

    | Index name                                    | Relation properties                  | Relation fields                |
    |-----------------------------------------------|--------------------------------------|--------------------------------|
    | &lt;&lt;Target Table&gt;&gt;. Example -Target | Table - &lt;&lt;Target Table&gt;&gt; | Staging.Field1 = Target.Field1 |
    |                                               |                                      | ..                             |
    |                                               |                                      | ..                             |

### Create a project

In Microsoft Dynamics AX, in the AOT, create a project.

### Create a class for the entity

1.  In Microsoft Dynamics AX, in the AOT, create a class for the entity.
2.  In the class declaration, include the following properties:

    -   Specify “\[DMFAttribute(true)\]”.
    -   Specify “DMFClassName extends DMFEntityBase”.
    -   Declare the object for the staging table that has the name **entity**.
    -   Declare the object for the main table for the target entity with the name **target**.

    The following example shows how the **DMFCustomerEntityClass** class is declared.

        [DMFAttribute(true)]
        class DMFCustomerEntityClass extends DMFEntityBase
        {

        DMFCustomerEntity entity;

        CustTable target;

        }

3.  Create the **new** method as follows:

    -   The method must take the staging table as a parameter.
    -   The value entity should be initialized from a parameter.

    The following example shows the **new** method for **DMFCustomerEntity**.

        Public void new(DMFCustomerEntity _entity)
        {
        entity = _entity;
        }

4.  Create the **construct** method as follows:

    -   The method must take the staging table as a parameter.
    -   The method must create and return the object of the current class by using a parameter.

    The following example shows the **construct** method for **DMFCustomerEntity**.

        public static DMFCustomerEntityClass construct (DMFCustomerEntity _entity)
        {
        DMFCustomerEntityClass entityClass = new DMFCustomerEntityClass(_entity);
        return entityClass;
        }

5.  Create the **setTargetBuffer** method as follows:

    -   A target entity can have multiple data sources. One data source is the main table that represents the entity. In the **setTargetBuffer** method, the **\_dataSourceName** parameter represents the data sources that are present in the target entity query.
    -   Depending on the data source, you might have to initialize a local instance of the table for the data source. The local instance can then be used in the functions that are required for data migration. The target should be initialized by the main table that represents the target entity.

    The following example shows the **setTargetBuffer** method.

        public void setTargetBuffer(Common _common, Name _dataSourceName = ' ')
        {
        switch (_common.TableId)
        {
        Case tableNum(CustTable) :
        Target = _common;
        Break;
        }
        }

6.  Set the value of the **RunOn** property for the class to **CalledFrom**.

### Write functions to import and export data

You can map data from the staging to the target entity in two ways:
-   Assign a field in the staging entity directly to a field in the target entity. In this case, the data types for the staging and target fields must be same.
-   Write an X++ function to transform the field values from staging to target.

Data import and export functions that you define must perform the following actions:
-   **Input/Source** – The whole staging record is available to the class as a local variable. Therefore, you do not have to pass any parameters to this class.
-   **Output/Target** – After the function is run, zero or multiple fields in the target entity are set. The return type of the function is a container that can hold zero or more values that should be set on the target.

The sequence of values that are returned by a particular function must be defined in the **getReturnFields** method.
#### Create a getReturnFields method

The **getReturnFields** method is used to specify the default output or target fields for the functions that are used for data migration. Some of the parameters for the method are as follows:
-   \_entity – The name of the entity.
-   \_name – The name of the function.

**Return**: This method must return the following information:
-   A container
-   The name of the data source in the target entity query with which the method should be run
-   The name of the data source field in the target entity query that should be initialized by the function

#### Create an addStagingLink method

The **addStagingLink** method is used to define the relationship between the staging table and target table when this relationship cannot be defined by using the relations property of the staging table. The target query and the staging record are available in the method. Therefore, the range between target and staging can be added by using code. The following example shows the **addStagingLink** method for the **DMFEmployeeEntityClass** class.
    public Query addStagingLink(Query query, TableId _entityTableId, Common _staging) 
    { 
    QueryBuildDataSource qbd; 
    qbd = query.dataSourceTable(tableNum(HcmWorker)); 
    qbd.addRange(fieldNum(HcmWorker,PersonnelNumber)).value(_staging.(fieldNum(DMFEmployeeEntity,PersonnelNumber))); 
    return query; 
    } 

#### Create a query to populate the target entity

Tables that represent the entity should be added to the target entity query. You must add a query for manual projects.

### Create an enum field in the target entity

The enum field in the target entity is represented by a string field in the staging table. You must create a new EDT of the string type that is of appropriate length to hold the enum label strings. The conversion between the enum field in the target entity and the string field in the staging table is handled automatically by the Data Import/Export Framework.

### Handle the RefRecId field

A staging table usually has natural keys (strings). If the target table contains fields that are RecIds from other tables, you must convert the natural key to a RecId. In this case, you have two options:
-   Add a data source, so that the referenced table can be added to the target entity query.
-   Create a function.

#### Add a data source

You can add a data source, so that the referenced table can be added to the target entity query. For example, the target **VendTable** table contains **VendExceptionGroup**, which is a RecId that comes from the **VendExceptionGroup** table. In this case, the staging table must include **VendExceptionGroup**. The **VendExceptionGroup** table must also be added to the target entity query, under the **VendTable** data source. The relationship between **VendTable** and **VendExecptionGroup** must be specified manually. The relationship should be between the **RefRecId** field in **VendTable** and the RecId on **VendExceptionGroup**. The staging field **DMFVendorEntity.VendExecptionGroup** must be mapped to the target field query for **DMFVendorTargetEntity. DS:VendExceptionGroup.VendExceptionGroup**. In many scenarios, if the name of the field in the target query is same as the staging field, the mapping is performed automatically. You can also manually map target fields to staging fields.

#### Create a function

You can create a function on the entity class. The related fields for the RefRecId field on the staging table should be natural keys from the staging table. You create a method on the entity class to convert the string to a RecId. For example, the CustTable table includes the CompanyNAFCode field, which is the RecId of the CompanyNAFCode table. In this case, you can create a function on DMFCustomerEntityClass to convert the string (DMFCustomerEntity.CompanyIdNAF) to a RecId (CompanyNAFCode.RecID). When you create a function, you must create a field group for the staging table, and the return fields on the target must be specified in the **getReturnFields** method in the entity class.



