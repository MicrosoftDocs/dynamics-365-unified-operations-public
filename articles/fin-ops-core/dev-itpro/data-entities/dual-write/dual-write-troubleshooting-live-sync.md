---
title: Troubleshoot live synchronization issues
description: This topic provides troubleshooting information that can help you fix issues with live synchronization.
author: RamaKrishnamoorthy 
ms.date: 08/19/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-03-16
---

# Troubleshoot live synchronization issues

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Microsoft Dataverse. Specifically, it provides information that can help you fix issues with live synchronization.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Azure Active Directory (Azure AD) tenant admin credentials. Each section explains whether a specific role or credentials are required.

## Live synchronization displays an error when you create a row

You might receive the following error message when you create a row in a Finance and Operations app.

*\[{\\"error\\":{\\"code\\":\\"0x80072560\\",\\"message\\":\\"The user is not a
member of the organization.\\"}}\], The remote server returned an error: (403)
Forbidden."}}".*

To fix the issue, follow the steps in [System requirements and prerequisites](requirements-and-prerequisites.md). To complete those steps, dual-write application users who were created in Dataverse must have the system admin role. The default owning team must also have the system admin role.

## Live synchronization displays an error when you try to save table data

**Required role to fix the issue:** System admin

You might receive the following error message when you try to save table data in a Finance and Operations app.

*Cannot save the changes to the database. Unit of Work can not commit transaction. Unable to write data to entity uoms. Writes to UnitOfMeasureEntity failed with error message Unable to sync with entity uoms.*

To fix the issue, make sure that prerequisite reference data exists in both the Finance and Operations app and Dataverse. For example, if a customer record belongs to a specific customer group, then make sure that the customer group record exists in Dataverse.

If data exists on both places, and you've confirmed that the issue isn't data related, follow these steps:

1. Open the **DualWriteProjectConfigurationEntity** using the Excel add-in. To use the add-in, enable design mode in the Finance and Operations Excel add-in and add the **DualWriteProjectConfigurationEntity** to a worksheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
2. Select the records that have issues in the dual-write map and project. Delete the records. There will be two records for every dual-write mapping.
3. Publish the changes using the Excel add-in. Publishing the changes is important because it deletes the records from the entity and underlying tables.

## Handle read or write privilege errors when you create data in a Finance and Operations app

You might receive a "Bad Request" error message when you create data in a Finance and Operations app.

![Example of the Bad Request error message.](media/error_record_id_source.png)

To fix the issue, you must assign the correct security role to the team of mapped Dynamics 365 Sales or Dynamics 365 Customer Service business units to enable the missing privilege.

1. In the Finance and Operations app, find the business unit that is mapped in the Data Integration connection set.

    ![Organization mapping.](media/mapped_business_unit.png)

2. Sign in to the environment in the customer engagement app, go to **Setting \> Security**, and find the team of the mapped business unit.

    ![Team of the mapped business unit.](media/setting_security_page.png)

3. Open the page for the team for editing, and then select **Manage roles** to open the **Manage Team Roles** dialog box.

    ![Manage roles button.](media/manage_team_roles.png)

4. Assign the role that has the read/write privilege for the relevant tables, and then select **OK**.

## Fix synchronization issues in an environment that has a recently changed Dataverse environment

**Required role to fix the issue:** System admin

You might receive the following error message when you create data in a Finance and Operations app.

*{"entityName":"CustCustomerV3Entity","executionStatus":2,"fieldResponses":\[\],"recordResponses":\[{"errorMessage":"**Unable
to generate payload for entity
CustCustomerV3Entity**","logDateTime":"2019-08-27T18:51:52.5843124Z","verboseError":"Payload
creation failed with error Invalid URI: The URI is
empty."}\],"isErrorCountUpdated":true}*

In the customer engagement app, the error looks like the following.

*An unexpected error occurred from ISV code. (ErrorType = ClientError) Unexpected exception from plug-in (Execute): Microsoft.Dynamics.Integrator.DualWriteRuntime.Plugins.PostCommitPlugin: System.Exception: failed to process entity account - (A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.*

This error occurs when the Dataverse environment is incorrectly reset when you try to create data in the Finance and Operations app.

> [!IMPORTANT]
> If you have relinked the environments, you must stop all the entity maps before continuing with the mitigation steps.
> 
To fix the issue, you will need to complete steps using Dataverse and the Finance and Opertions app.

1. In the Finance and Operations app, do the following:
    1. Open the **DualWriteProjectConfigurationEntity** using the Excel add-in. To use the add-in, enable design mode in the Finance and Operations Excel add-in and add the **DualWriteProjectConfigurationEntity** to the sheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
    2. Select the records that have issues in the dual-write map and project. Delete them. There will be 2 records for every dual-write mapping.
    3. Publish the changes using the Excel add-in. Publishing the changes is important because it deletes the records from the entity and underlying tables.
    4. To prevent errors when relinking the Finance and Operations or Dataverse environments, make sure that there are no remaining dual-write configurations.
2. In Dataverse, do the following:
    1. Sign in to your Dataverse environment, for example, `https://*****.crm.dynamics.com/`.
    2. Navigate to **Advanced Settings** \> **Advanced Find**.
    3. Select **DualWrite Runtime Configuration**.
    4. Select the column that you want view.
    5. Select **Results** to view the configurations.
    6. Delete all the instances.
3. In the Finance and Operations app, do the following:
    1. Open the **DualWriteProjectConfigurationEntity** using the Excel add-in. To use the add-in, enable design mode in the Finance and Operations Excel add-in and add the **DualWriteProjectConfigurationEntity** to the sheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
    2. Select the records that have issues in the dual-write map and project. Delete them. There will be 2 records for every dual-write mapping.
    3. Publish the changes using the Excel add-in. Publishing the changes is important because it deletes the records from the entity and underlying tables.
    4. To prevent errors when relinking the Finance and Operations or Dataverse environments, make sure that there are no remaining dual-write configurations.

## Error with live sync after doing a full database copy

You might receive the following error after you run a full database copy from one system to another, and then you try to run a database operation.

*SecureConfig Organization (???) does not match actual CRM Organization (???).*

The error displays from the dual-write runtime plug-in to ensure that the dual-write configuration set up in one system cannot be used in another.

To fix this error, delete all the records in the **msdyn_dualwriteruntimeconfig** table after you restore the database. For more information, see [Unlink and relink dual-write environments](relink-environments.md).

## Live sync issues due to incorrect query filter syntax on the dual-write maps

Even though the query expression for a dual-write map filter is syntactically correct, it might not work as expected. The filter expression is on an entity and not an individual data source of a query object. Therefore, the SQL query that is generated doesn't return the expected results.

For example:

```dos
Query entity = PROJECTENTITY
Query expression = (ParentProject == "")
```

You would expect that projects with no parent are filtered out. However, the filter does not work because the filter translates to a query which looks like the following query.

```sql
SELECT T1.RECID,T1.MODIFIEDDATETIME,T1.RECVERSION,T1.RECID,T1.DIMENSION,
T1.LOCATION,T1.PROJECTCONTROLLER,T1.PROJECTID,T1.PROJECTMANAGER,T1.REFERENCE,
T1.SALESMANAGER,T1.SCHEDULED,T1.RECVERSION#8,T1.RECVERSION#7,
T1.RECVERSION#6,T1.RECVERSION#5,T1.RECVERSION#4,T1.RECVERSION#3,
T1.RECVERSION#2,T1.RECID#8,T1.RECID#7,T1.RECID#6,T1.RECID#5,
T1.RECID#4,T1.RECID#3,T1.RECID#2,T1.PARTITION FROM PROJECTENTITY T1 
WHERE(((((((((((PARTITION=5637144576) AND (DATAAREAID=N'usmf')) AND 
((PARTITION#2=5637144576) OR (PARTITION#2 IS NULL))) AND 
((PARTITION#3=5637144576) OR (PARTITION#3 IS NULL))) AND 
((PARTITION#4=5637144576) OR (PARTITION#4 IS NULL))) AND 
((PARTITION#5=5637144576) OR (PARTITION#5 IS NULL))) AND 
((PARTITION#6=5637144576) OR (PARTITION#6 IS NULL))) AND 
((PARTITION#7=5637144576) OR (PARTITION#7 IS NULL))) AND 
((PARTITION#8=5637144576) OR (PARTITION#8 IS NULL))) AND 
((DATAAREAID#8=N'usmf') OR (DATAAREAID#8 IS NULL))) AND 
(PARENTPROJECT='')) 
ORDER BY T1.PROJECTID
```

The actual result is that the `parentProject` field evaluates to `null`, which is not the same as the empty string. This mismatch is the reason why the query filter does not return valid results.

To fix the issue, follow these steps:

1. Add a computed column that can be added in an extension model, backed by logic to convert `null` to the empty string.

```dos
SysComputedColumn::if(SysComputedColumn::isNullExpression(ParentProject), SysComputedColumn::returnLiteral(""), fieldName);
```

2. Use the filter on the new computed column instead of the default column.

To evaluate the filter in a development environment, you can use following X++ code to validate the results. Run this code as a standalone program. This script can be used to evaluate different kinds of filters applicable for an entity before using them on dual-write maps. The query can be run against the database to evaluate discrepancies.

```xpp
var entityName = "PROJECTENTITY";
var filterExpression = '(ParentProject == "")';
Query query = new Query();
query.literals(NoYes::Yes); 
QueryBuildDataSource qbd = query.addDataSource(tablename2id(entityName));
qbd.addRange(fieldname2id(qbd.table(),identifierStr(RecVersion))).value(filterExpression);
qbd.addSelectionField(fieldname2id(qbd.table(),identifierStr(RecId)));
QueryRun qRun = new QueryRun(query);
// This provides the actual sql statement to execute
var actualSqlStatement = query.getSQLStatement();
while(qRun.next())
{
    var rec = qRun.get(tableName2Id(entityName));   
}
```

## Data from Finance and Operations apps does not sync to Dataverse

You might have an issue during live sync where only a partial data is synchronized from Finance and Operations apps to Dataverse or data is not synchronized at all.

> [!NOTE]
> You must fix this issue during development.

Before you start to fix this issue, review the following prerequisites:

+ Make sure your custom changes are written within a single transaction scope.
+ `doinsert()`, `doUpdate()`, `recordset()` operations and records where `skipBusinessEvents(true)` is marked are not handled by business events and the dual-write framework. If your code is inside these functions, then dual-write will not be triggered.
+ Business events must be registered for the data source that is mapped. There can be data sources that use an outer join and are marked as read only in Finance and Operations apps. These data sources are not tracked.
+ Changes will be triggered only if the modifications are on the mapped fields. Unmapped field modifications will not trigger dual-write.
+ Make sure that filter evaluations provide a valid result.

### Troubleshooting steps

1. Check field mappings on the dual-write admin page. If the field is not mapped from Finance and Operations apps to Dataverse, then that field will not be tracked. For example, in the following screenshot, the field **Description** is tracked from Dataverse but not from Finance and Operations apps. Any changes to that field inside Finance and Operations apps will not be tracked.

    ![A tracked field.](media/live-sync-troubleshooting-1.png)

2. Check if the data source is tracked in the business events definition. For example, in the following screenshot, any field from the **DefaultDimensionDAVs** table and underlying tables won't be tracked for changes. Data sources that are **OuterJoin** and read only are not tracked.

    ![A field that is not tracked.](media/live-sync-troubleshooting-2.png)

3. The mapped table fields appear in the **BUSINESSEVENTSDEFINITION** table, as shown in the following screenshot. If you don't find the field you are looking for in the query result, then it will not be triggered by dual-write.

    ![A tracked field in the table.](media/live-sync-troubleshooting-3.png)

### Sample scenario
  
In Finance and Operations apps, there is an update to the address for a contact record, and the address change does not sync to Dataverse. This scenario happens because there is no record in the **BusinessEventsDefinition** table with the combination of the table affected and the entity. Specifically, the **smmContactpersonCDSV2Entity** entity does not have the **LogisticsPostalAddress** table directly as the data source. The **smmContactpersonCDSV2Entity** entity has **smmContactPersonV2Entity** as the data source, and **smmContactPersonV2Entity** has **LogisticsPostalAddressBaseEntity** as the data source. The **LogisticsPostalAddress** table is the data source for **LogisticsPostalAddressBaseEntity**.

A similar situation can occurr in certain non-standard patterns, such as cases where the table being modified in Finance and Operations apps isn't obviously linked to the entity that contains it. For example, on the **smmContactPersonCDSV2Entity**, the primary address data is computed. The dual-write framework attempts understand how a change to an underlying table maps back to entities, which is usually sufficient. In some cases, the link is so complex that you need to be specific. You have to make sure you have the **RecId** of the related table available on the entity directly, and then add a static method monitor the table for changes.  

For an example, review the **smmContactPersonCDSV2Entity::getEntityDataSourceToFieldMapping()** method. **CustCustomerV3entity** and **VendVendorV2Entity** have been modified to handle this situation.

To fix this error, follow these steps.

1. Add a **PrimaryPostalAddressRecId** field to the **smmContactPersonV2Entity**. Make it internal.

    ![Troubleshoot live sync_issue 1.](media/Troubleshoot_live_sync_issue_1.png)

2. Add the same field to **smmContactPersonCDSV2Entity**.

    ![Troubleshoot live_sync issue 2.](media/Troubleshoot_live_sync_issue_2.png)

3. Add this method to the **smmContactPersonCDSV2Entity** class.

    ```xpp
    public static container getEntityDataSourceToFieldMapping(container mapping)
    {
        mapping += [[tablestr(smmContactPersonCDSV2Entity), tablenum(LogisticsPostalAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryPostalAddressRecId)]];
 
        return mapping;
    }
    ```

4. Sync the database and build the application.

5. Stop all the dual-write maps that are created on the **smmContactPersonCDSV2Entity** entity.

6. Start the map and you will see the new table (**LogisticsPostalAddress** in this example) that you have started to track using the column **RefTableName** for the row with **refentityname** equal to **smmContactPersonCDSV2Entity** in the **BusinessEventsDefinition** table.

## Error while creating a record where multiple records are sent from a Finance and Operations app to Dataverse in the same batch

For any transaction, the Finance and Operations app creates data in a batch and sends it as a batch to Dataverse. If two records are created as part of the same transaction and they reference each other, then you might receive an error similar to the following in the Finance and Operations app:

*Unable to write data to entity aaa_fundingsources. Unable to lookup ebecsfs_contracts with values {PC00...}. Unable to lookup aaa_fundingsources with values {PC00...}. Writes to aaa_fundingsources failed with error message Exception message: The remote server returned an error: (400) Bad Request.*

To fix this issue, create entity relationships within the Finance and Operations app to indicate that the two entities are related to each other and that the related records are handled within the same transaction.

## Enable verbose logging of error messages

You might encounter errors in the Finance and Operations app that are related to the Dataverse environment. The error might not contain the full text of the message or other relevant data. You can enable verbose logging to get more information. To do this, follow these steps:

1. In all project configurations in Finance and Operations apps, there is a flag named **IsDebugMode** on the **DualWriteProjectConfiguration** entity.
2. Open the **DualWriteProjectConfigurationEntity** using the Excel add-in. To use the add-in, enable design mode in the Finance and Operations Excel add-in and add the **DualWriteProjectConfigurationEntity** to the sheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
3. Set **IsDebugMode** to **Yes** on the project.
4. Run the scenario.
5. The verbose logs are available in the **DualWriteErrorLog** table.
6. To look up data using the table browser. use this link: `https://XXXaos.cloudax.dynamics.com/?mi=SysTableBrowser&tableName=DualWriteErrorLog`.
7. Top capture more logs in debug mode, install the update in [KB 4595434 (Fix for blank values being propagated in Dual write live sync)](https://fix.lcs.dynamics.com/Issue/Details?kb=4595434&bugId=527820&dbType=3&qc=c29ce15a80e6b3b4c01a722d9bdae1d7e71aa3662a044cfd0b765f736cfa98e9).

## Error when adding an address for a customer or contact

You might receive the following error when you try to add an address for a customer or contact in Finance and Operations apps or Dataverse.

*Unable to write data to entity msdyn_partypostaladdresses.Writes to DirPartyPostalAddressLocationCDSEntity failed with error message Request failed with status code BadRequest and CDS error code : 0x80040265 response message: An error occurred in plugin. A record that has the attribute values Location ID already exists. The entity key Location ID Key requires that this set of attributes contains unique values. Select unique values and try again.*

To fix this error, install the dual write orchestration package version (2.2.2.60) so that the keys on the **Address** table are defined as in the following table.

Property | Value
---|---
Display Name | **Location Key**
Name | **msdyn_locationkey**
Fields | **msdyn_locationid**, **parentid**
Status | **Active**
System job | (empty)

## Error when adding a customer in Dataverse

You might receive the following error when you try to add a customer in Dataverse.

*"RecordError0":"Write failed for entity Customers V3 with unknown exception - Party record not found for party type 'Organization'"}.*

When a customer is created in Dataverse, a new party number is generated. This error displays when this customer record along with party synchronizes to Finance and Operations apps and there is already a customer record with a different party number.

To fix this issue, find the customer through party lookup. If the customer does not exist, then create a new customer record. If the customer does exist, use the existing party to create the new customer record.

## Error when creating a new customer, vendor, or contact in Dataverse

You might receive the following error when you try to create a new customer, vendor, or contact in Dataverse.

*Cannot update a party's type from 'DirOrganization' to 'DirPerson', a delete of the existing party followed by an insert with the new type should be performed instead.*

There is a number sequence on **msdyn_party** table in Dataverse. When an account is created in Dataverse, a new party is created, for example **Party-001** of type **Organization**. This data is sent to the Finance and Operations app. When the Dataverse environment is reset or the Finance and Operations environment is linked to a different Dataverse environment, then creating a new contact record in Dataverse creates a new party value starting with **Party-001**. This time the party record will be created with **Party-001** of type **Person**. When this data is synced, Finance and Operations apps displays this error because there is already a party record **Party-001** of type **Organization**.

To fix this issue, change the auto number sequence on Dataverse for the **msdyn_partynumber** field in the **msdyn_party** table to a different auto number sequence.

## Performance issue with customer or contact mappings

To improve live sync performance of customers and contacts, customizing the **getEntityDataSourceToFieldMapping** (in **CustCustomerV3Entity**) and **getEntityDataSourceToFieldMapping** (in **smmContactPersonCDSV2Entity**) methods may marginally improve performance. These customizations reduce the number of records in the **BusinessEventsDefinition** table, which reduces number of events raised.

The method **getEntityDataSourceToFieldMapping** in the **CustCustomerV3Entity** entity makes sure that the electronic address or postal address update of the customer triggers business events so that the updated data will be sent to Dataverse. If you don't use all the fields and don’t need this information in dual-write, comment the respective lines in the method. Every tracked field and table added in this method adds a record in the **BusinessEventsDefinition** table for the combination of the tracked table and tracked entity.

```xpp
public static container getEntityDataSourceToFieldMapping(container mapping)
{
    mapping += [
        [tablestr(DirPartyBaseEntity), tablenum(LogisticsPostalAddress), fieldstr(CustCustomerV3Entity, AddressRecordId)],
        [identifierstr(DirPartyBaseEntity), tablenum(LogisticsElectronicAddress), fieldstr(CustCustomerV3Entity, PrimaryContactURLRecordId)],
        [identifierstr(DirPartyBaseEntity1), tablenum(LogisticsElectronicAddress), fieldstr(CustCustomerV3Entity, PrimaryContactPhoneRecordId)],
        [identifierstr(DirPartyBaseEntity2), tablenum(LogisticsElectronicAddress), fieldstr(CustCustomerV3Entity, PrimaryContactEmailRecordId)],
        [identifierstr(DirPartyBaseEntity3), tablenum(LogisticsElectronicAddress), fieldstr(CustCustomerV3Entity, PrimaryContactFaxRecordId)],
        [identifierstr(DirPartyBaseEntity4), tablenum(DirPartyLocation), fieldstr(CustCustomerV3Entity, DirPartyLocationRecordId)],
        [identifierstr(DirPartyBaseEntity5), tablenum(LogisticsPostalAddress), fieldstr(CustCustomerV3Entity, InvoiceAddressRecordId)],
        [identifierstr(DirPartyBaseEntity6), tablenum(LogisticsPostalAddress), fieldstr(CustCustomerV3Entity, DeliveryAddressRecordId)],
        [identifierStr(DirPartyBaseEntity7), tablenum(DirPartyTable), fieldstr(CustCustomerV3Entity, PartyRecordId)]];
    return mapping;
}
 ```

Similarly, the **getEntityDataSourceToFieldMapping** method in the **smmContactPersonCDSV2Entity** entity makes sure that any electronic address or postal address update of the contact triggers business events so that the updated data will be sent to Dataverse. You can comment out the lines in the method for fields that you don't use.

```xpp
public static container getEntityDataSourceToFieldMapping(container mapping)
{
    mapping += [
        [tablestr(DirPartyBaseEntity), tablenum(LogisticsPostalAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryPostalAddressRecId)],
        [identifierStr(DirPartyBaseEntity), tablenum(DirPartyTable), fieldstr(smmContactPersonCDSV2Entity, PrimaryAddressLocation)],
        [identifierStr(DirPartyBaseEntity1), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactEmailRecordId)],
        [identifierStr(DirPartyBaseEntity2), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactFaxRecordId)],
        [identifierStr(DirPartyBaseEntity3), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactPhoneRecordId)],
        [identifierStr(DirPartyBaseEntity4), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactFacebookRecordId)],
        [identifierStr(DirPartyBaseEntity5), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactTwitterRecordId)],
        [identifierStr(DirPartyBaseEntity6), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactURLRecordId)],
        [identifierStr(DirPartyBaseEntity7), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactLinkedInRecordId)],
        [identifierStr(DirPartyBaseEntity8), tablenum(LogisticsElectronicAddress), fieldstr(smmContactPersonCDSV2Entity, PrimaryContactTelexRecordId)],
        [identifierStr(DirPartyBaseEntity9), tablenum(DirPartyTable), fieldstr(smmContactPersonCDSV2Entity, PartyRecordId)]];
    return mapping;
}
```

After you update the methods, follow these steps:

1. Sync the database and build the application.
2. Stop all the dual-write maps on the **smmContactPersonCDSV2Entity** and **CustCustomerV3Entity** entities.
3. Start the maps. You will see fewer records in the **smmContactPersonCDSV2Entity** and **CustCustomerV3Entity** entities and the **BusinessEventsDefinition** table, which might marginally improve performance.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
