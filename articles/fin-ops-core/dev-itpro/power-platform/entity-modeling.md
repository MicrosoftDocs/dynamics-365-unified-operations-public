---
title: Entity modeling
description: Learn about relational modeling concepts using virtual entities for finance and operations entities, including an overview on generating virtual entities.
author: mkannapiran
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.custom: NotInToc
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-05-31
ms.dyn365.ops.version: 10.0.12
---

# Entity modeling

[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> This functionality requires version 10.0.12 for finance and operations apps, while service update 189 is required for Microsoft Dataverse. The release information for Dataverse is published on the [latest version availability page](/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).
>
> The public entity name that appears in Dataverse metadata for the finance and operations virtual table uses the physical name of the finance and operations entity. This name might differ from the public name of the entity as exposed by the OData metadata.

Building an app requires capabilities to perform relational modeling between entities that you use in the app. In the context of virtual tables, some scenarios require virtual tables and native tables in Dataverse to work together to enable the desired user experience. This article explains concepts of relational modeling that you can implement by using virtual tables for finance and operations apps.

## Generating virtual entities

By default, virtual tables for finance and operations apps don't exist in Dataverse. You must query the catalog entity to view the entities that are available in the linked instance of finance and operations apps. From the catalog, you can select one or more entities, and then request that Dataverse generate virtual tables in Dataverse for these finance and operations entities. The later sections explain this procedure.

## Entity fields

When you generate a virtual table for a finance and operations entity, the system tries to create each field in the finance and operations entity in the corresponding virtual table in Dataverse. Ideally, both finance and operations entities and Dataverse virtual tables have the same total number of fields, unless there's a mismatch in supported data types between the finance and operations apps and Dataverse. For supported data types, the system sets the field properties in Dataverse based on the properties in the finance and operations app.

The rest of this section describes supported and unsupported data types. For more information about fields in Dataverse, see [Fields overview](/powerapps/maker/common-data-service/fields-overview).

| Data type in finance and operations apps | Modeled data type in Dataverse |
|-------------------------------------|------------------------------------------|
| Real                                | Decimal<br><br>For information about the possible mismatch, see the next table.</p> |
| Long                                | Decimal, where the precision equals 0 (zero) |
| Int                                 | Integer |
| String (nonmemo), String (memo)    | String – single line of text, String – multiple lines of text |
| UtcDateTime                         | DateTime (DateTimeFormat.DateAndTime, DateTimeBehavior.TimeZoneIndependent)<br><br>An empty date (January 1, 1900) in finance and operations apps appears as a null value in Dataverse. |
| Date                                | DateTime - (DateTimeFormat.DateOnly, DateTimeBehavior.TimeZoneIndependent)<br><br>An empty date (January 1, 1900) in finance and operations apps appears as an empty value in Dataverse. |
| Enum                                | Picklist<br><br>Finance and operations enumerations (enums) are generated as global OptionSets in Dataverse. Matching between the systems is done by using the **External Name** property of values. Enum integer values in Dataverse aren't guaranteed to be stable between the systems. Therefore, you shouldn't rely on them, especially with extensible enums, because these enums don't have a stable ID either. OptionSet metadata is updated when an entity that uses the OptionSet is updated. |

Fields of the *real* and *long* data types in finance and operations apps are modeled as the *decimal* data type in Dataverse. Because of the mismatch in precision and scale between the two data types, consider the following behavior.

| Use case                                     | Resulting behavior |
|----------------------------------------------|--------------------|
| Dataverse has higher precision.    | This use case never occurs unless the metadata is out of sync. |
| Finance and operations apps have higher precision. | During a read operation, the value is rounded to the closest precision value in Dataverse. If the value is edited in Dataverse, it's rounded to the closest precision value. During a write operation, the value that you specify in Dataverse is written, because finance and operations apps support higher precision. |
| Dataverse has higher scale.        | Not applicable |
| Finance and operations apps have higher scale.     | Dataverse shows the finance and operations value, even if it exceeds 100 billion. However, there's a loss of precision. For example, 987,654,100,000,000,000 is shown in Dataverse as "987,654,099,999,999,900". If you edit the value of this field in Dataverse, Dataverse validation throws an error that the value exceeds the maximum value before that value is sent to the finance and operations app. |

The following data types in finance and operations apps aren't supported in Dataverse. Fields of these data types in finance and operations entities aren't available in the corresponding virtual tables in Dataverse. If you use fields of these data types as parameters in Open Data Protocol (OData) actions, those actions aren't available for use in the corresponding virtual entities. For more information about OData actions, see the [OData actions](#odata-actions) section later in this article.

- AnyType
- BLOB
- Class
- Container
- Guid
- Record
- Time
- UserType
- VarArg
- Void (Void return types on OData actions are supported.)

Data types that are supported in Dataverse but not in finance and operations apps aren't supported in virtual entities for finance and operations apps.

## Entity key and primary key

In finance and operations apps, entities can have one or more fields of various data types as the entity key. An entity key uniquely identifies a record in a finance and operations entity. Additionally, a record in an entity can be uniquely identified by a record ID primary key of the Int64 type.

In Dataverse, the primary key is always a globally unique identifier (GUID). The GUID-based primary key enables a record in a Dataverse table to be uniquely identified.

To bridge the implementation gap between finance and operations apps and Dataverse, the primary key of a virtual entity for finance and operations apps is a GUID (to comply with Dataverse). This GUID consists of the data entity ID in the first 4 bytes, and the record ID of the root data source in the entity as the last 8 bytes. This design satisfies Dataverse's requirement that GUIDs are used as the entity key. It also enables the table ID and record ID to be used to uniquely identify the finance and operations entity record.

When you use entities in finance and operations apps, you need to ensure that the root data source always has a unique RecID. If this design is violated, duplicate GUIDs appear in Dataverse for the corresponding virtual table. For the same reason, aggregate views aren't supported via virtual tables because these views might not have unique RecIDs.

## Primary field

In Dataverse, each table must have a primary field. This field must be a single field of the string type. Use the primary field in Dataverse in the following scenarios:

- The default views that are created for an entity include the primary field.
- The quick view form for an entity includes the primary field.
- A lookup to another entity is added to a page and shows the data from the primary field.

Based on this use of the primary field in Dataverse, the primary field for a finance and operations virtual table is designed to use the entity key of the corresponding entity in the finance and operations app.

Because the primary field in Dataverse is expected to have only one field of the string type, whereas the finance and operations entity key can have multiple fields of various data types, the entity key fields are converted to strings. The strings are concatenated and separated by a pipe (\|), to a maximum length of 255 characters. Any value that exceeds 255 is truncated. This virtual entity field that represents the primary field is named **mserp\_primaryfield**. If an entity key isn't made up of single string field, then filtering or any operation like aggregation isn't allowed on that field. You can use any other available columns for filtering.

> [!NOTE]
> After you generate a virtual table for finance and operations apps in the associated Dataverse environment, you can't modify the primary key and primary field. To change a primary field, you must remove the table from the Dataverse environment. For information about how to disable virtual tables and remove the finance and operations entity metadata from the Dataverse environment, see [Disable virtual entities](enable-virtual-entities.md#disable-virtual-entities). After you change the primary fields in the finance and operations app, you can reenable the entity. For information, see [Generate virtual entities](enable-virtual-entities.md#generate-virtual-entities).

## Relations

> [!IMPORTANT]
> A write transaction that spans a virtual table and a native entity isn't supported. Don't use this form of transaction, as there's no way to ensure consistency.

Relations in finance and operations entities are modeled as one-to-many (1:n) or many-to-one (n:1) relations. You model these relations as relationships in the virtual table in Dataverse. Many-to-many (n:n) relations aren't supported in finance and operations apps.

For example, in finance and operations apps, if Entity A has a foreign key to Entity B, you model this relation as an n:1 relationship in virtual table Table A in Dataverse. The schema name of this relationship in Dataverse uses the naming convention **mserp\_FK\_\<source entity name\>\_\<relation name\>**. This naming convention has a maximum string length of 92 characters. Any relation where the schema name produces a name that exceeds 92 characters isn't generated in the virtual entity in Dataverse.

The external name of this relationship uses the naming convention **FK\_\<relation name\>**. The external name is used to determine the relation in the finance and operations app when the query that is sent and built.

When you generate a relationship for a virtual table in Dataverse, you also add a new field of the lookup type to the source entity. In the preceding example, when you create the relationship, you add a new lookup field that uses the naming convention **mserp\_fk\_\<target\_entity\>\_id** to source entity Entity A. Because there can be several relations in a finance and operations entity, you create the same number of lookup fields (one per related entity) in the source virtual entity. When you add this lookup field to a page or a view, it shows the primary field value from the related entity.

You generate a relationship in the virtual table in Dataverse only if the related entity in the relation already exists as a virtual table in Dataverse. In the preceding example, if Entity B doesn't exist as a virtual table in Dataverse, the relation to Entity B isn't created in Entity A when Entity A is generated as a virtual table. This relation is added to Entity A only when Entity B is generated as a virtual table. Therefore, when you generate a virtual table for the finance and operations app, validations ensure that only relationships that can be complete and functional are generated in the virtual table that's being generated.

In summary, a relationship to another finance and operations virtual entity might not exist in the virtual entity for either of the following reasons:

- The finance and operations entity that's participating in the relationship doesn't exist as a virtual entity.
- The length of the name of the relationship exceeds 92 characters.

If you encounter an error when generating any part of a finance and operations virtual entity in Dataverse, the virtual entity isn't created. If relationships don't exist for either of the preceding reasons, the situation isn't considered an error.

### Native entity–to–native entity relationships

Native table–to–native table relationships are the standard Dataverse functionality, where relationships are resolved by using the GUID of the related entity. This GUID is the entity key. The GUID identifies the unique entity record in the related table.

### Virtual table–to–virtual table relationships

The relationships between two finance and operations virtual tables come from the relation metadata in the finance and operations entities. As explained earlier, these relations become relationships in Dataverse when you create the virtual table. Like native tables in Dataverse, these relationships use the GUID to identify the unique record of the finance and operations entity key. Semantically, the GUID on the finance and operations virtual entity works like the GUID on the native Dataverse table. For more information about the implementation of the GUID in finance and operations virtual tables, see the [Entity key/primary key](entity-modeling.md#entity-key-and-primary-key) section earlier in this article.

In the preceding example, the GUID of the related table is the entity key of Entity B and is used to build queries to identify a record in the finance and operations app. The relation that Entity A has to Entity B is used.

Therefore, in effect, the entity name is the only information that is used in a relation that comes from the finance and operations app. The entity name gives access to the primary field in the related entity, so that it can be shown in the lookup. It also gives access to the GUID of the related entity, so that it can be used in other queries, as explained earlier. The actual field that the relation is built on in the finance and operations entity isn't used.

### Virtual table–to–native table relationship

As explained earlier, the GUID is the only information that uniquely identifies a record in a native Dataverse table (including in native table–to–native table relationships) or in a finance and operations virtual table (including in virtual table–to–virtual table relationships). However, consider an example where you want to show finance and operations sales orders for Account A in Dataverse. The query that is sent to the finance and operations app for this relationship has a WHERE clause on the GUID of the entity key of the native accounts entity in Dataverse, because the sales orders must be filtered for a specific account in Dataverse. However, because the finance and operations app doesn't have any information about the GUID of the entity in Dataverse, the query doesn't return any sales orders. The query is successful only if the WHERE clause has conditions that are based on the fields that the finance and operations app understands.

Therefore, how can you replace the GUID of the accounts table in Dataverse with finance and operations fields so that the query sent to the finance and operations app returns the correct list of sales orders?

To solve this problem and enable a rich set of scenarios that allow for virtual table–to–native table relationships, add relationships to this type of entity. The relation appears as a relationship when the virtual table is synced.

In the preceding example, the relationship between the SalesOrderHeader virtual table and the Account native table should be based on the Account Number and Company fields. By default, the native account entity in Dataverse doesn't have a company field. For this example, add a company lookup field named new_testcompany to the native Account entity.

Next, add a new key named new_accountcompanyidx, which specifies that (accountnumber, new_testcompany) together represent a unique row in the account table in Dataverse.

The next step is to define this relationship in X++. The following example shows sample X++ code. The names of the fields, index, and mapping information should match the names of the fields and indexes created in Dataverse. In this example, a relationship named "synthaccount" is created between the virtual SalesorderHeader table and the native account table in Dataverse. The mapped fields make up the new_accountcompanyidx index. The display name for the relationship is @SYS11307. Note the backslash at the start of the display name. This ensures that the label defines the relationship, so that it's appropriately translated.

The field mapping indicates which field on the virtual table maps to the field on the native table. In the field mapping, the key is the virtual table field, and the value is the native table field.

```x++
[CDSVirtualEntitySyntheticRelationshipAttribute('synthaccount', 'account', 'accountcompanyidx', '\@SYS11307')]
    public static Map syntheticAccountRelationship()
    {
        Map fieldMapping = new Map(Types::String, Types::String);

        // Assumes the Dataverse account entity has a key on [msdyn_accountnumber, msdyn_companyid]
        // Also assumes that the Dataverse cdm_Company entity has a key on [msdyn_companycode]
        fieldMapping.insert(fieldStr(CDSVirtualEntityTestEntity, StringField), 'msdyn_accountnumber');
        fieldMapping.insert(fieldStr(CDSVirtualEntityTestEntity, DataAreaId), 'msdyn_companyid');

        return fieldMapping;
    }
```
The next step is to generate or refresh the virtual table to get the new relationship. You can't update relationships between a virtual table and a native table in Dataverse once they're created. To update the relationship, you must physically remove the relationship, refresh the entity, and then physically readd the relationship to resolve the issue.

This relationship looks like a typical GUID-based relationship, but it has extra metadata to translate query filters on the relationship into restrictions on the backing fields. The query that is now generated has a WHERE clause that's based on the fields that finance and operations apps recognize. That query then returns the filtered list of sales orders, as expected.

### Native entity to virtual entity relationships

Native entities to virtual entity relationships work much like native entity to native entity relationships. Users associate native records with finance and operations virtual records, and the GUID of the virtual entity is saved on the native entity record. As explained earlier, the entities that participate in a relationship have the GUID field of the related entity on them. Therefore, when a quotation in Dataverse is associated with a customer in a finance and operations virtual entity, the GUID of the customer virtual entity is saved in the quotation entity. This behavior enables records to be retrieved as expected by using standard Dataverse functionality.

## Enums

Finance and operations enums are modeled as OptionSets in Dataverse. When a virtual entity for finance and operations apps is generated, the required enums are generated as OptionSets. If an OptionSet already exists, it's used instead.

## Company

A finance and operations entity can be bound to a company, or it can be global. The virtual entity for a finance and operations entity that is bound to a company has a relationship to the cdm\_company table in Dataverse. The cdm\_company table is a native table in Dataverse and is part of the Dynamics365Company solution. As always, when you create a relationship, you also create a lookup field in the virtual table for the related table (cdm\_company in this case). This lookup field is named **Company**, and you must use it to provide an optimal user experience where users can select a value in a list or go to the details of the related record. A field that is named **Company Code** is also added in the virtual entity. The value is a four-character string. This field must be used in programming.

## Attachments

Attachments in finance and operations entities are supported on a per-entity basis. For example, an invoice header entity implements an invoice-related attachments entity to [enable attachments via entities](../../fin-ops/organization-administration/configure-document-management.md#how-can-attachments-be-extracted-from-the-system).

Entities of this type have relations with the corresponding attachments entity in the finance and operations app. Therefore, they follow the same pattern as the other relations that were discussed earlier. In other words, finance and operations entities that implement attachments functionality also make attachments available by using virtual tables. Finance and operations entities that don't support attachments also don't support attachments when they're virtualized in Dataverse.

Finance and operations virtual tables support only the reading of attachments. They don't currently support the creation, update, or deletion of attachments by using virtual tables.

## OData actions

Dataverse makes OData actions in the finance and operations entities available as custom actions. For more information about custom actions and what they enable in Dataverse, see [Custom actions](/powerapps/developer/common-data-service/custom-actions).

The following types support input and output parameters. If an input or output parameter uses a different type, the OData action doesn't appear as the SDK message in Dataverse.

- Integer
- String
- Guid
- Boolean
- Date/Datetime

Here are some examples of OData actions that finance and operations entities support but that the corresponding virtual tables in Dataverse don't support:

- RetailStoreTenderTypeTable.queryDistinctTenderTypeIdAndName (a collection of RetailStoreTenderTypeTable entities)
- DocumentRoutingClientApp.syncPrinters (DocumentRoutingClientApp entity)
- DocumentRoutingClientApp.updateJobStatus (DocumentRoutingJobStatus enum)
- DimensionCombination.getCombinationDisplayValue (LedgerJournalACType enum)

## Labels and localization

When you generate virtual tables in Dataverse, you retrieve labels that are defined on metadata, such as entity names and field names in finance and operations apps. You retrieve the labels by passing the list of language locales that are installed in Dataverse. The finance and operations app returns each label as a list of locale/value sets that you use to construct a label instance in Dataverse. The generation or update process includes only the language packs that exist at that time. Additionally, the process includes only labels that the finance and operations app provides a translation for. Any missing translations revert to the label ID, such as **\@SYS:DataEntity**. After you install a new language pack in Dataverse, you must update existing entities to pick up the new label information, if labels in that language exist in the finance and operations app.

The current user context returns any runtime labels in the language of the current user context. In other words, the language is specified on the user's UserInfo record in the finance and operations app. This behavior also applies to error messages.

## Error handling

Finance and operations apps create, read, update, and delete (CRUD) business logic on entities and backing tables. This logic runs when you call it through the virtual table in Dataverse. If the finance and operations app throws an exception, the last message in the error log is returned to Dataverse. Dataverse throws an InvalidPluginExecutionException exception that contains the message from the finance and operations app. Because the app code runs in the context of the user, the language of the error message is based on the language that is specified on the UserInfo record in the app. If any messages that are written to the finance and operations info log don't result in an exception, they aren't shown in Dataverse.

## Calculated and unmapped fields

Calculated and unmapped fields in finance and operations entities are also available in the corresponding virtual tables in Dataverse.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
