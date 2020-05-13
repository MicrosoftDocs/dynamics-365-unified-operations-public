---
# required metadata

title: Entity modeling
description: Description goes here.
author: Sunil-Garg
manager: AnnBe
ms.date: 05/20/2020
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

## Generating virtual entities

Virtual entities for Finance and Operations do not exist in Common Data Service by default. A user is required to query the catalog entity to view the entities available in the linked instance of Finance and Operations. From the catalog, the user can select one or more entities and ask Common Data Service to generate the virtual entities. This procedure if explained in subsequent sections.

## Entity fields

When a virtual entity is generated for a Finance and Operations entity, each field in the Finance and Operations entity is attempted to be created in the corresponding virtual entity in Common Data Service. In an ideal case, the total number of fields should be the same in both entities unless there is any mismatch in supported data types between Finance and Operations and Common Data Service as explained below. For data types that are supported, the field properties in Common Data Service are set based on the properties in Finance and Operations. The supported and not supported data
types are discussed next. More information about fields in Common Data Service can be found [here](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/fields-overview).

| **Finance and Operations Data type**               | **Modelled data type in Common Data Service**                                                                                                                                                                                                                                                                                                                                                                                              |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Real                            | Decimal (possible mismatch explained below)                                                                                                                                                                                                                                                                                                                                                                                |
| Long                            | Decimal with precision = 0                                                                                                                                                                                                                                                                                                                                                                                                 |
| Int                             | Integer                                                                                                                                                                                                                                                                                                                                                                                                                    |
| String (non-memo) String (memo) | String – single line of text String – multiple lines of text                                                                                                                                                                                                                                                                                                                                                               |
| UtcDateTime                     | DateTime - DateTimeFormat.DateAndTime, DateTimeBehavior.TimeZoneIndependent Empty date of 1/1/1900 in F&O is surfaced as an null value in Common Data Service                                                                                                                                                                                                                                                                              |
| Date                            | DateTime - DateTimeFormat.DateOnly, DateTimeBehavior.TimeZoneIndependent Empty date of 1/1/1900 in F&O is surfaced as an empty value in Common Data Service                                                                                                                                                                                                                                                                                |
| Enum                            | Picklist F&O Enum is generated as global OptionSets in Common Data Service solution Matching between systems is done by the "External Name" property of values Enum integer value on Common Data Service is not guaranteed stable between systems and should not be relied upon (especially in the case of extensible enums in F&O which do not have a stable ID either) Option set metadata is refreshed when an entity using the option set is refreshed |

Fields of data type *real* and *long* in Finance and Operations are modelled as
data type *decimal* in Common Data Service. Due to the mismatch in precision and scale between
the two data types, the following behavior must be considered.

| **Use case**                            | **Resulting behavior**                                                                                                                                                                                                                                                                                             |
|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Common Data Service has higher precision                | Should never happen unless the metadata is out of sync                                                                                                                                                                                                                                                             |
| F&O has higher precision                | On read, value is rounded in Common Data Service to the closest precision value If value is edited in Common Data Service, it gets rounded to the closest precision in Finance and Operations On write, writes the value specified in Common Data Service (since F&O supports more precision)                                                                      |
| Common Data Service has higher scale                    | Not applicable                                                                                                                                                                                                                                                                                                     |
| Finance and Operations has higher scale | Common Data Service will show F&O value even if it exceeds 100 billion, though precision losses will occur. For instance, 987,654,100,000,000,000 is displayed in Common Data Service as "987,654,099,999,999,900" If the value of this field is edited in Common Data Service, Common Data Service validation throws an error that it exceeds the max value before sending to F&O |

The following data types in F&O are not supported in Common Data Service. Fields of such a data type in Finance and Operations entity will not be made available in the corresponding virtual entity in Common Data Service. If such fields are used as parameters in OData actions, those actions will not be available for use in the corresponding virtual entity. OData actions are explained in a subsequent section.

-   AnyType 

-   BLOB 

-   Class 

-   Container 

-   Guid 

-   Record 

-   Time 

-   UserType 

-   VarArg 

-   Void (void return types on OData actions are supported)

Data type that are supported in Common Data Service but not in Finance and Operations cannot be supported in virtual entities for Finance and Operations.

## Entity key/Primary key

In Finance and Operations, entities can have one or more fields of varying data types as the entity key. Entity key uniquely identifies a record in a Finance and Operations entity. Additionally, a record in an entity can also be uniquely identified by a Rec Id primary key of type Int64.

In Common Data Service, the primary key is always a GUID. The GUID based primary key allows to uniquely identify a record in an entity in Common Data Service.

In order to bridge this implementation gap between Finance and Operations and Common Data Service, the primary key of the virtual entity for Finance and Operations is a GUID (to comply with Common Data Service) which is comprised of the data entity ID in the first 4 bytes, and the rec ID of the root data source in the entity as the last 8 bytes. This design satisfies Common Data Service’s requirements to have a GUID as the entity key and
allows unique identification of the entity record in Finance and Operations using the table Id and rec ID.

## Primary field

In Common Data Service, each entity must have a primary field which must be a single field of type string. The primary field is used in Common Data Service in the following scenarios.

-   The default views that are created for an entity includes the primary field

-   The quick view form for an entity includes the primary field

-   When a look up to another entity is added to a form, the look up shows the data from the primary field

Based on the above usage of the primary field in Common Data Service, the design of the primary field for a virtual entity for Finance and Operations is to use the entity key of the corresponding entity in Finance and Operations.

Since the primary field in Common Data Service is expected to only have one field of type string, while the entity key in Finance and Operations can have multiple fields of varying data type, the entity key fields are converted to string and the values are concatenated and \| separated to a max length of 255. Any value longer than 255 will be truncated. This virtual entity field representing the
primary field is called mserp_primaryfield.

## Relations

Relations in Finance and Operations entity is modelled as a 1:n or n:1. This is modelled as a relationship in the virtual entity in Common Data Service. Note, n:n relations are not supported in Finance and Operations. As an example, in Finance and Operations, if Entity A has a foreign key to Entity B, this relation will be modelled as a n:1 relationship in the virtual entity Entity A in Common Data Service. The schema name of this relationship in Common Data Service will have a naming convention of mserp_FK_\<source entity name\>_\<relation name\> which has a max string length
limit of 120 characters. Any relation whose schema name would result in a longer name will not be generated in the virtual entity in Common Data Service. The external name of this relationship follows a naming convention of FK_\<relation name\>. The external name is used to determine the relation in Finance and Operations when building the query sent to Finance and Operations.

When a relationship is generated in Common Data Service for a virtual entity, a new field of type look up is also added to the source entity. In the above example, when the relationship was created, a new field of type look up with naming convention of mserp_fk_\<target_entity\>_id is added to the source entity Entity A. Since there can be several relations in an entity in Finance and Operations, there will be as many look up fields (one per related entity) created in the source virtual entity. When this look up field is added to a form or a view, the look up will show the primary field value from the related entity.

A relationship in the virtual entity in Common Data Service will be generated if and only if the related entity in the relation already exists as a virtual entity in Common Data Service. In the above example, if Entity B did not exist as a virtual entity in Common Data Service, the relation to Entity B would not be created in Entity A when Entity A was generated as a virtual entity. This relation will only get added to Entity A when Entity B is generated as a virtual entity. This means, when generating a virtual entity for Finance and Operations, validations are done to ensure only relationships that can be complete and functional are generated in the virtual entity being generated. So, in summary, the following can be one of the reasons for why a relationship to another Finance and Operations virtual entity does not exist in the virtual entity.

-   The Finance and Operations entity participating in the relationship does not exist as a virtual entity

-   The name length of the relationship name exceeds 120 characters

Note, if an error is encountered when generating any part of a Finance and Operations virtual entity in Common Data Service, the virtual entity will not be created at all. The above factors are not considered as errors.

### Native entity to native entity relationship

This is the standard Common Data Service functionality where the relationships are resolved using the GUID of the related entity which is the entity key. The GUID identifies the unique entity record in the related entity.

### Virtual entity to virtual entity relationship

The relationships between two Finance and Operations virtual entities are driven by the relation metadata in the Finance and Operations entity. As explained above, these relations are generated as relationships in Common Data Service when the virtual entity is generated. Like native entity behavior in Common Data Service, such relationships use the GUID to identify the unique record of the entity in Finance and Operations.
Semantically, the GUID on the Finance and Operations virtual entity behaves like the GUID on the native Common Data Service entity. The implementation details of the GUID in the Finance and Operations virtual entity is explained in an earlier section.

In the above example, the GUID of the related entity, which is the entity key of Entity B in this example, will be used to build queries to identify a record in Finance and Operation using the relation Entity A has to Entity B.

So, in effect, the only information in a relation coming from Finance and Operations that is used is the entity name. The entity name gives access to the primary field in the related entity to show in the look up while, it also gives access to the GUID of the related entity to use in other queries as explained above. The actual field on which the relation is built in the Finance and
Operations entity is not used at all.

### Virtual entity to native entity relationship

As stated above, GUID is the only information that is used to identify a record uniquely in a native Common Data Service entity (including native to native relationships) or a Finance and Operations virtual entity (including virtual entity to virtual entity relationship). However, let’s take an example where, we want to show sales orders from Finance and Operations for an account Account A in Common Data Service. The
query sent to Finance and Operations for this relationship will have a WHERE clause on the GUID of the entity key of the native accounts entity in Common Data Service. This is because, the scenario is asking to filter the sales orders for a specific account in Common Data Service.

Finance and Operations does not know anything about the GUID of the entity in Common Data Service and hence, the query is not going to return any sales orders. The query will be successful only if the WHERE clause had conditions based on the fields that Finance and Operations knew. This leads to the question as to, how can the GUID of the accounts entity in Common Data Service be replaced with field(s) that are in Finance and Operations such that, the query sent to Finance and Operations will be executed to return the correct list of sales orders?

To solve this problem and enable a rich set of scenarios that allows for virtual entity to native entity relationships, relations can be added to such an entity in Finance and Operations. The relation will show up as a relationship when the virtual entity is synced. Sample x++ code is shown below.

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

When this additional relations are made avaialble in Common Data Service information is made available in the relationship definition, the query generated will have the WHERE clause based on the fields that Finance and Operations will understand and the query will return the filtered list of sales orders as expected.

### Native entity to virtual entity relationship

The native entity to virtual entity relationships works much the same way as the native to native works. The users associate native records to virtual records in Finance and Operations, the GUID of the virtual entity is saved on the native entity record. Recall from the earlier discussion that the entities participating in a relationship will have the related entity’s GUID field on it. As a result, when a quote in Common Data Service is associated to a customer in Finance and Operations virtual entity, the GUID of the customer virtual entity will be saved in the quote entity. This allows for retrieval of records as expected which is per standard Common Data Service functionality. 

## Enum

Enums in Finance and Operations are modelled as OptionSets in Common Data Service. When a virtual entity for Finance and Operations is generated, the required Enum(s) are also generated as OptionSets. If an OptionSet already exists, it is used instead.

## Company

An entity in Finance and Operations can be bound to a company or be global. Virtual entity for a Finance and Operations entity that is bound to company will have a relationship to the cdm_company entity in Common Data Service. The cdm_company entity is a native entity in Common Data Service and is part of the Dynamics365Company solution. As always, when a relationship is created, a look up field is also created in the virtual entity for the related entity which in this case is the cdm_company entity. This look up field is called Company and must be used to provide optimal user experience where users can pick a value from a list of values or can navigate to the details of the related record. A field called Company Code also gets added as a four-character string field in the virtual entity. This field must be used in programming.

## Attachments

Attachments in Finance and Operations entities are supported on a per entity basis. For example, an invoice header entity will implement an invoice related attachments entity to [enable attachments via entities](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-document-management#how-can-attachments-be-extracted-from-the-system).
Such entities will have relations with the corresponding attachments entity in Finance and Operations and thus will follow the same pattern as any other relations discussed earlier. In other words, Finance and Operations entities that have implemented attachments functionality also make attachments available using virtual entities. Finance and Operations entities that do not support attachments will also not support attachments when virtualized in Common Data Service.

It must be noted that, Finance and Operations virtual entities only support reading of attachments. It currently does not support create, update, or delete of attachments using virtual entities.

## Default views

When an entity is created in Common Data Service (native or virtual), five default views are also created for the entity. The following are the types of views that are created.

-   Default public view

-   Quick find view

-   Advanced find view

-   Associated view

-   Lookup view

Common Data Service added the primary field of the entity to all these views. Makers can add additional fields to these views as needed.

Finance and Operations entities have five field groups by default which are the following.

-   AutoReport

-   AutoLookup

-   AutoIdentification

-   AutoSummary

-   AutoBrowse

The field groups are used to populate additional fields in the default views in Common Data Service for the Finance and Operations virtual entities. The mapping of the field groups to the default views is given below.

| **Field group**    | **Default view**    |
|--------------------|---------------------|
| AutoReport         | Default public view |
| AutoLookup         | Lookup view         |
| AutoIdentification | Quick find view     |
| AutoSummary        | Associated view     |
| AutoBrowse         | Advanced find view  |

## OData actions

OData actions in the Finance and Operations entities are made available as SDK messages in Common Data Service. More information on what SDK messages are and what they enable in Common Data Service can be read here.

Input and output parameters of the following types are supported. If an input or output parameter is of a different type, then the OData action does not show up as the SDK message in Common Data Service.

-   Integer

-   String

-   Guid

-   Boolean

-   Date/Datetime

Some examples of OData actions that are supported in Finance and Operations entity but is not supported in the corresponding virtual entity in Common Data Service are listed below.

-   RetailStoreTenderTypeTable.queryDistinctTenderTypeIdAndName (collection of
    RetailStoreTenderTypeTable entity)

-   DocumentRoutingClientApp.syncPrinters (DocumentRoutingClientApp entity)

-   DocumentRoutingClientApp.updateJobStatus (DocumentRoutingJobStatus enum)

-   DimensionCombination.getCombinationDisplayValue (LedgerJournalACType enum)

## Labels and localization

Labels defined on metadata such as entity names and field names in Finance and Operations are retrieved at virtual entity generation time in Common Data Service by passing the list of language locales installed in Common Data Service. Finance and Operations returns each label as a list of locale/value sets, which are then used to construct a label instance in Common Data Service. Only the language packs that existed at the time of entity
generation or refresh will be included and only labels for which Finance and Operations has a translation provided. Any missing translations revert to the label ID, such as \@SYS:DataEntity. After installing a new language pack in Common Data Service,
existing entities would need to be refreshed to pick up the new label information if labels of that language exist in Finance and Operations.

Any runtime labels will be returned in the language of the current user context, meaning the language specified on that user's UserInfo record in Finance and Operations. This includes any error messages.

## Error handling

Finance and Operations CRUD business logic on the entity and backing tables is executed when called through the virtual entity in Common Data Service. If any exception is thrown on the Finance and Operations side, then the last message in the error log is returned back to Common Data Service and thrown as an InvalidPluginExecutionException containing the info log message from Finance and Operations. Since the Finance and Operations code runs in the context of the user, the language of the error message will be based on the specified language for the UserInfo record in
Finance and Operations. Any messages written to the info log in Finance and Operations that do not result in an exception are not shown in Common Data Service.

## Calculated/Unmapped fields

Calculated and un-mapped fields in Finance and Operations entities are also available in the corresponding virtual entities in Common Data Service.

