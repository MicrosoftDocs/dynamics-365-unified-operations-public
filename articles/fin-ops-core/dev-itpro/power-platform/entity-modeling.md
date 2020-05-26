---
# required metadata

title: Entity modeling
description: This topic explains relational modeling concepts using virtual entities for Finance and Operations entities.
author: Sunil-Garg
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Entity modeling

[!include[banner](../includes/banner.md)]

Building an app requires capabilities to perform relational modeling between entities that are being used in the app. In the context of virtual entities, there will be scenarios where virtual entities and native entities in Common Data Service must work together to enable the desired user experience. This topic explains concepts of relational modeling that can be implemented using virtual entities for Finance and Operations.

## Generating virtual entities

By default, virtual entities for Finance and Operations apps don't exist in Common Data Service. A user must query the catalog entity to view the entities that are available in the linked instance of Finance and Operations. From the catalog, the user can select one or more entities, and then request that Common Data Service generate the virtual entities. This procedure is explained in later sections.

## Entity fields

When a virtual entity is generated for a Finance and Operations entity, the system tries to create each field in the Finance and Operations entity in the corresponding virtual entity in Common Data Service. In an ideal case, the total number of fields will be the same in both entities, unless there is a mismatch in supported data types between Finance and Operations and Common Data Service. For data types that are supported, the field properties in Common Data Service are set based on the properties in Finance and Operations.

This rest of this section describes supported and unsupported data types. For more information about fields in Common Data Service, see [Fields overview](https://docs.microsoft.com/powerapps/maker/common-data-service/fields-overview).

| Data type in Finance and Operations | Modeled data type in Common Data Service |
|-------------------------------------|------------------------------------------|
| Real                                | Decimal<p>For information about the possible mismatch, see the next table.</p> |
| Long                                | Decimal, where the precision equals 0 (zero) |
| Int                                 | Integer |
| String (non-memo), String (memo)    | String – single line of text, String – multiple lines of text |
| UtcDateTime                         | DateTime (DateTimeFormat.DateAndTime, DateTimeBehavior.TimeZoneIndependent)<p>An empty date (January 1, 1900) in Finance and Operations is surfaced as a null value in Common Data Service.</p> |
| Date                                | DateTime - (DateTimeFormat.DateOnly, DateTimeBehavior.TimeZoneIndependent)<p>An empty date (January 1, 1900) in Finance and Operations is surfaced as an empty value in Common Data Service.</p> |
| Enum                                | Picklist<p>Finance and Operations enumerations (enums) are generated as global OptionSets in Common Data Service. Matching between the systems is done by using the **External Name** property of values. Enum integer values in Common Data Service aren't guaranteed to be stable between the systems. Therefore, you should not rely on them, especially in the case of extensible enums in Finance and Operations, because these enums don't have a stable ID either. OptionSet metadata is updated when an entity that uses the OptionSet is updated. |

Fields of the *real* and *long* data types in Finance and Operations are modeled as the *decimal* data type in Common Data Service. Because of the mismatch in precision and scale between the two data types, the following behavior must be considered.

| Use case                                     | Resulting behavior |
|----------------------------------------------|--------------------|
| Common Data Service has higher precision.    | This use case should never occur unless the metadata is out of sync. |
| Finance and Operations has higher precision. | During a read operation, the value is rounded to the closest precision value in Common Data Service. If the value is edited in Common Data Service, it's rounded to the closest precision value in Finance and Operations. During a write operation, the value that is specified in Common Data Service is written, because Finance and Operations supports higher precision. |
| Common Data Service has higher scale.        | Not applicable |
| Finance and Operations has higher scale.     | Common Data Service shows the Finance and Operations value, even if it exceeds 100 billion. However, there will be a loss of precision. For example, 987,654,100,000,000,000 is shown in Common Data Service as "987,654,099,999,999,900". If the value of this field is edited in Common Data Service, Common Data Service validation throws an error that the value exceeds the maximum value before that value is sent to Finance and Operations. |

The following data types in Finance and Operations aren't supported in Common Data Service. Fields of these data types in Finance and Operations entities won't be made available in the corresponding virtual entities in Common Data Service. If fields of these data types are used as parameters in Open Data Protocol (OData) actions, those actions won't be available for use in the corresponding virtual entities. For more information about OData actions, see the [OData actions](#odata-actions) section later in this topic.

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

Data type that are supported in Common Data Service but not in Finance and Operations aren't supported in virtual entities for Finance and Operations.

## Entity key/primary key

In Finance and Operations, entities can have one or more fields of various data types as the entity key. An entity key uniquely identifies a record in a Finance and Operations entity. Additionally, a record in an entity can be uniquely identified by a record ID primary key of the Int64 type.

In Common Data Service, the primary key is always a globally unique identifier (GUID). The GUID-based primary key enables a record in an entity in Common Data Service to be uniquely identified.

To bridge the implementation gap between Finance and Operations and Common Data Service, the primary key of a virtual entity for Finance and Operations is a GUID (to comply with Common Data Service). This GUID consists of the data entity ID in the first 4 bytes, and the record ID of the root data source in the entity as the last 8 bytes. This design satisfies Common Data Service's requirement that a GUID be used as the entity key. It also enables the table ID and record ID to be used to uniquely identify the entity record in Finance and Operations.

## Primary field

In Common Data Service, each entity must have a primary field. This field must be a single field of the string type. The primary field is used in Common Data Service in the following scenarios:

- The default views that are created for an entity include the primary field.
- The quick view form for an entity includes the primary field.
- A lookup to another entity is added to a page and shows the data from the primary field.

Based on this use of the primary field in Common Data Service, the primary field for a virtual entity for Finance and Operations is designed to use the entity key of the corresponding entity in Finance and Operations.

Because the primary field in Common Data Service is expected to have only one field of the string type, whereas the entity key in Finance and Operations can have multiple fields of various data types, the entity key fields are converted to strings. The strings are concatenated and separated by a pipe (\|), to a maximum length of 255 characters. Any value that exceeds 255 is truncated. This virtual entity field that represents the primary field is named **mserp\_primaryfield**.

## Relations

Relations in Finance and Operations entities are modeled as one-to-many (1:n) or many-to-one (n:1) relations. These relations are modeled as relationships in the virtual entity in Common Data Service. Note that many-to-many (n:n) relations aren't supported in Finance and Operations.

For example, in Finance and Operations, if Entity A has a foreign key to Entity B, this relation will be modeled as an n:1 relationship in virtual entity Entity A in Common Data Service. The schema name of this relationship in Common Data Service uses the naming convention **mserp\_FK\_\<source entity name\>\_\<relation name\>**. This naming convention has a maximum string length of 120 characters. Any relation where the schema name will produce a name that exceeds 120 characters won't be generated in the virtual entity in Common Data Service.

The external name of this relationship uses the naming convention **FK\_\<relation name\>**. The external name is used to determine the relation in Finance and Operations when the query that is sent to Finance and Operations is built.

When a relationship is generated for a virtual entity in Common Data Service, a new field of the lookup type is also added to the source entity. In the preceding example, when the relationship is created, a new lookup field that uses the naming convention **mserp\_fk\_\<target\_entity\>\_id** is added to source entity Entity A. Because there can be several relations in an entity in Finance and Operations, the same number of lookup fields (one per related entity) will be created in the source virtual entity. When this lookup field is added to a page or a view, it will show the primary field value from the related entity.

A relationship in the virtual entity in Common Data Service will be generated only if the related entity in the relation already exists as a virtual entity in Common Data Service. In the preceding example, if Entity B doesn't exist as a virtual entity in Common Data Service, the relation to Entity B won't be created in Entity A when Entity A is generated as a virtual entity. This relation will be added to Entity A only when Entity B is generated as a virtual entity. Therefore, when a virtual entity is generated for Finance and Operations, validations are done to ensure that only relationships that can be complete and functional are generated in the virtual entity that is being generated.

In summary, a relationship to another Finance and Operations virtual entity might not exist in the virtual entity for either of the following reasons:

- The Finance and Operations entity that is participating in the relationship doesn't exist as a virtual entity.
- The length of the name of the relationship exceeds 120 characters.

Note that if an error is encountered when any part of a Finance and Operations virtual entity is generated in Common Data Service, the virtual entity won't be created at all. If relationships don't exist for either of the preceding reasons, the situation isn't considered an error.

### Native entity–to–native entity relationships

Native entity–to–native entity relationships are the standard Common Data Service functionality, where relationships are resolved by using the GUID of the related entity. (This GUID is the entity key.) The GUID identifies the unique entity record in the related entity.

### Virtual entity–to–virtual entity relationships

The relationships between two Finance and Operations virtual entities are driven by the relation metadata in the Finance and Operations entities. As was explained earlier, these relations are generated as relationships in Common Data Service when the virtual entity is generated. As in the behavior for native entities in Common Data Service, these relationships use the GUID to identify the unique record of the entity in Finance and Operations. Semantically, the GUID on the Finance and Operations virtual entity behaves like the GUID on the native Common Data Service entity. For information about the implementation of the GUID in Finance and Operations virtual entities, see the [Entity key/primary key](entity-modeling.md#entity-keyprimary-key) section earlier in this topic.

In the preceding example, the GUID of the related entity is the entity key of Entity B and will be used to build queries to identify a record in Finance and Operation. The relation that Entity A has to Entity B will be used.

Therefore, in effect, the entity name is the only information that is used in a relation that comes from Finance and Operations. The entity name gives access to the primary field in the related entity, so that it can be shown in the lookup. It also gives access to the GUID of the related entity, so that it can be used in other queries, as was explained earlier. The actual field that the relation is built on in the Finance and Operations entity isn't used at all.

### Virtual entity–to–native entity relationship

As was explained earlier, the GUID is the only information that is used to uniquely identify a record in a native Common Data Service entity (including in native entity–to–native entity relationships) or in a Finance and Operations virtual entity (including in virtual entity–to–virtual entity relationships). However, consider an example where you want to show sales orders from Finance and Operations for Account A in Common Data Service. The query that is sent to Finance and Operations for this relationship will have a WHERE clause on the GUID of the entity key of the native accounts entity in Common Data Service, because the sales orders must be filtered for a specific account in Common Data Service. However, because Finance and Operations doesn't have any information about the GUID of the entity in Common Data Service, the query won't return any sales orders. The query will be successful only if the WHERE clause has conditions that are based on the fields that Finance and Operations understands.

Therefore, how can the GUID of the accounts entity in Common Data Service be replaced with fields that are in Finance and Operations, in such a way that the query that is sent to Finance and Operations will return the correct list of sales orders?

To solve this issue and enable a rich set of scenarios that allows for virtual entity–to–native entity relationships, relations can be added to this type of entity in Finance and Operations. The relation will appear as a relationship when the virtual entity is synced. The following example shows sample X++ code.

```x++
[CDSVirtualEntitySyntheticRelationshipAttribute('synthaccount', 'account', '\@SYS11307', 'accountcompanyidx')]
    public static Map syntheticAccountRelationship()
    {
        Map fieldMapping = new Map(Types::String, Types::String);

        // Assumes the Common Data Service account entity has a key on [msdyn_accountnumber, msdyn_companyid]
        // Also assumes that the Common Data Service cdm_Company entity has a key on [msdyn_companycode]
        fieldMapping.insert(fieldStr(CDSVirtualEntityTestEntity, StringField), 'msdyn_accountnumber');
        fieldMapping.insert(fieldStr(CDSVirtualEntityTestEntity, DataAreaId), 'msdyn_companyid');

        return fieldMapping;
    }
```

When these additional relations are made available in Common Data Service, information becomes available in the relationship definition. The query that is generated will have a WHERE clause that is based on the fields that Finance and Operations understands. That query will then return the filtered list of sales orders, as expected.

### Native entity–to–virtual entity relationships

<!--HERE-->Native entity–to–virtual entity relationships works much like native entity–to–native entity relationships. Users associate native records with virtual records in Finance and Operations, and the GUID of the virtual entity is saved on the native entity record. As was explained earlier, the entities that participate in a relationship will have the GUID field of the related entity on them. Therefore, when a quotation in Common Data Service is associated with a customer in a Finance and Operations virtual entity, the GUID of the customer virtual entity will be saved in the quotation entity. This behavior enables records to be retrieved as expected, by using standard Common Data Service functionality.

## Enums

Enums in Finance and Operations are modeled as OptionSets in Common Data Service. When a virtual entity for Finance and Operations is generated, the required enums are generated as OptionSets. If an OptionSet already exists, it's used instead.

## Company

An entity in Finance and Operations can be bound to a company, or it can be global. The virtual entity for a Finance and Operations entity that is bound to a company will have a relationship to the cdm\_company entity in Common Data Service. The cdm\_company entity is a native entity in Common Data Service and is part of the Dynamics365Company solution. As always, when a relationship is created, a lookup field is also created in the virtual entity for the related entity (cdm\_company in this case). This lookup field is named **Company**, and it must be used to provide an optimal user experience where users can select a value in a list or go to the details of the related record. A field that is named **Company Code** is also added in the virtual entity. The value is a four-character string. This field must be used in programming.

## Attachments

Attachments in Finance and Operations entities are supported on a per-entity basis. For example, an invoice header entity will implement an invoice-related attachments entity to [enable attachments via entities](../../fin-ops/organization-administration/configure-document-management.md#how-can-attachments-be-extracted-from-the-system).

Entities of this type will have relations with the corresponding attachments entity in Finance and Operations. Therefore, they will follow the same pattern as the other relations that were discussed earlier. In other words, Finance and Operations entities that have implemented attachments functionality will also make attachments available by using virtual entities. Finance and Operations entities that don't support attachments also won't support attachments when they are virtualized in Common Data Service.

Note that Finance and Operations virtual entities support only the reading of attachments. They don't currently support the creation, update, or deletion of attachments by using virtual entities.

## Default views

When an entity (either native or virtual) is created in Common Data Service, five default views are also created for it:

- Default public view
- Quick find view
- Advanced find view
- Associated view
- Lookup view

Common Data Service adds the primary field of the entity to all these views. Makers can add additional fields to these views as they require.

By default, Finance and Operations entities have five field groups:

- AutoReport
- AutoLookup
- AutoIdentification
- AutoSummary
- AutoBrowse

The field groups are used to fill in additional fields for the Finance and Operations virtual entities in the default views in Common Data Service. The following table shows the mapping of the field groups to the default views.

| Field group        | Default view        |
|--------------------|---------------------|
| AutoReport         | Default public view |
| AutoLookup         | Lookup view         |
| AutoIdentification | Quick find view     |
| AutoSummary        | Associated view     |
| AutoBrowse         | Advanced find view  |

## OData actions

OData actions in the Finance and Operations entities are made available as custom actions in Common Data Service. For more information about custom actions and what they enable in Common Data Service, see [Custom actions](https://docs.microsoft.com/powerapps/developer/common-data-service/custom-actions).

Input and output parameters of the following types are supported. If an input or output parameter is of a different type, the OData action doesn't appear as the SDK message in Common Data Service.

- Integer
- String
- Guid
- Boolean
- Date/Datetime

Here are some examples of OData actions that are supported in Finance and Operations entities, but that aren't supported in the corresponding virtual entities in Common Data Service:

- RetailStoreTenderTypeTable.queryDistinctTenderTypeIdAndName (a collection of RetailStoreTenderTypeTable entity)
- DocumentRoutingClientApp.syncPrinters (DocumentRoutingClientApp entity)
- DocumentRoutingClientApp.updateJobStatus (DocumentRoutingJobStatus enum)
- DimensionCombination.getCombinationDisplayValue (LedgerJournalACType enum)

## Labels and localization

Labels that are defined on metadata, such as entity names and field names in Finance and Operations, are retrieved when virtual entities are generated in Common Data Service. The labels are retrieved by passing the list of language locales that are installed in Common Data Service. Finance and Operations returns each label as a list of locale/value sets that are then used to construct a label instance in Common Data Service. Only the language packs that exist at the time of entity generation or update are included. Additionally, only labels that Finance and Operations has provided a translation for are included. Any missing translations revert to the label ID, such as **\@SYS:DataEntity**. After a new language pack is installed in Common Data Service, existing entities must be updated to pick up the new label information, if labels in that language exist in Finance and Operations.

Any runtime labels are returned in the language of the current user context. In other words, they are returned in the language that is specified on that user's UserInfo record in Finance and Operations. This behavior also applies to error messages.

## Error handling

Finance and Operations create, read, update, and delete (CRUD) business logic on entities and backing tables is run when it's called through the virtual entity in Common Data Service. If any exception is thrown on the Finance and Operations side, the last message in the error log is returned to Common Data Service and is thrown as an InvalidPluginExecutionException exception that contains the message from Finance and Operations. Because the Finance and Operations code runs in the context of the user, the language of the error message is based on the language that is specified on the UserInfo record in Finance and Operations. If any messages that are written to the info log in Finance and Operations don't result in an exception, they aren't shown in Common Data Service.

## Calculated/unmapped fields

Calculated and unmapped fields in Finance and Operations entities are also available in the corresponding virtual entities in Common Data Service.
