---
# required metadata

title: Application Explorer properties
description: This article describes the properties that appear in the Properties window of Microsoft Visual Studio for items in Application Explorer.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
ms.topic: reference
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 85213
ms.assetid: ca186dda-8a78-4969-9be0-b81be00892e5
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Application Explorer properties

This article describes the properties that appear in the Properties window of Microsoft Visual Studio for items in Application Explorer.

Many nodes in Application Explorer represent elements that have properties associated with them. You can read or modify these properties in the **Properties** window of Microsoft Visual Studio.

## System and common properties
Most application objects in Application Explorer have a standard set of system properties. These system properties are read-only. You can use the **Properties** window to view the properties for any item in Application Explorer. To open the **Properties** window, right-click a node in Application Explorer, and then click **Properties**. On the **Categories** tab of the **Properties** window, many system properties are listed under the **Statistics** node. This article lists additional common properties that are repeated on many, but not all, Application Explorer nodes. The following table shows the system properties that are found on almost all Application Explorer nodes. All these system properties are read-only.

| Property     | Description                                                       |
|--------------|-------------------------------------------------------------------|
| ChangedBy    | The user who last changed the object (often the release version). |
| ChangedDate  | The date when the object was last changed.                        |
| ChangedTime  | The time when the object was last changed.                        |
| CreatedBy    | The user who created the object.                                  |
| CreationDate | The date when the object was created.                             |
| CreationTime | The time when the object was created.                             |

The following table shows other common properties that are found on many, but not all, Application Explorer nodes.

| Property          | Description                                                                                                                                                                                                                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ConfigurationKey  | Specify the configuration key that controls access to or display of an element. If a user doesn't have access to the configuration key, the element isn't visible. Elements include pages, controls on pages, tables, and other elements.                                                                            |
| LegacyID          | An identifier element from an earlier version. During upgrade from a previous version, the old identifier is assigned to **LegacyID**. An installation-specific identifier isn't assigned, and business logic remains intact. This property isn't used for new elements.                                             |
| NeededAccessLevel | The minimum access level that a user requires. This property is read-only.                                                                                                                                                                                                                                           |
| Origin            | The globally unique identifier (GUID) of an Application Explorer element. This property is used to identify elements during synchronization and in upgrade scenarios. It's a read-only property, and the value never changes after the system assigns it. No origin GUID value is duplicated anywhere in the system. |
| SecurityKey       | This property is obsolete but is retained for reference in systems that were upgraded from an earlier version.                                                                                                                                                                                                       |

## Base enum properties
The following table describes the properties that are available for enumerations.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AnalysisUsage</td>
<td>Specify the role of the enumeration in a cube. This setting is automatically propagated to all table fields that reference the enumeration. However, you can override the setting on a table field. The following options are available:
<ul>
<li><strong>Attribute </strong>– A field that references the enumeration is a dimension attribute.</li>
<li><strong>None </strong>– A field that references the enumeration isn't a dimension attribute.</li>
</ul></td>
</tr>
<tr class="even">
<td>ConfigurationKey</td>
<td>Specify the configuration key.</td>
</tr>
<tr class="odd">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the view is applicable or valid. This property is implemented as a comma-separated list of International Organization for Standardization (ISO) country/region codes in a single string. The values must match data in the global address book. The client framework and application might use this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="even">
<td>DisplayLength</td>
<td>Specify the number of characters that are shown. The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>Help</td>
<td>Create a Help string for the field. The Help string is shown when the field is used on a page.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Specify the label that is shown on pages and reports.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Specify the enumeration name. An enumeration name must indicate either the possible enumeration values or the type of the enumeration value. Examples of enumerations that are named according to the possible values are <strong>InclExcl</strong> and <strong>NextPrevious</strong>. Examples of enumerations that are named according to the type of the enumeration value are <strong>ArrivalPostingType</strong> and <strong>ListStatus</strong>.</td>
</tr>
<tr class="odd">
<td>Style</td>
<td>Change the default appearance of the enumeration. The following options are available:
<ul>
<li>Combo box</li>
<li>Radio button</li>
</ul></td>
</tr>
<tr class="even">
<td>UseEnumValue</td>
<td>A value of <strong>Yes</strong> indicates that default values of the <strong>EnumValue</strong> property were modified. A value of <strong>No</strong> resets the <strong>EnumValue</strong> property to the default values.</td>
</tr>
</tbody>
</table>

## Extended data type properties
Extended data type (EDT) properties are divided into the following groups, based on whether they are common to all EDTs or available only for certain base data types.

### Properties that are common to all EDTs

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alignment</td>
<td>Change the alignment of the text. The available options are <strong>Left</strong>, <strong>Right</strong>, and <strong>Center</strong>.</td>
</tr>
<tr class="even">
<td>AnalysisDefaultSort</td>
<td>Specify the default sort order for a field in a report model that has this EDT.</td>
</tr>
<tr class="odd">
<td>AnalysisDefaultTotal</td>
<td>Specify the aggregate function for a measure. Use this property when the <strong>AnalysisUsage</strong> property is set to <strong>Measure</strong>. The following options are available:
<ul>
<li><strong>Sum </strong>– Return the sum of all the values in a set.</li>
<li><strong>Count </strong>– Return the number of non-null items in a set.</li>
<li><strong>CountDistinct </strong>– Return the number of distinct non-null items in a set.</li>
<li><strong>Min </strong>– Return the minimum value in a set.</li>
<li><strong>Max </strong>– Return the maximum value in a set.</li>
<li><strong>None </strong>– No aggregate function is applied.</li>
<li><strong>Auto </strong>– This option applies to derived EDTs. The value of the <strong>AnalysisUsage</strong> property for the parent EDT is used.</li>
</ul>
You can override the aggregate function at the field level. In other words, you can change the aggregate function for the field by using the <strong>AnalysisDefaultTotal</strong> property for that field.</td>
</tr>
<tr class="even">
<td>AnalysisGrouping</td>
<td>Specify whether a field that has this EDT is grouped by default when the field is added to a report by using Report Builder for Microsoft SQL Server Reporting Services (SSRS). This property is automatically set to <strong>Discouraged</strong> for currency amounts. For other fields that are unique, you should set this property to <strong>Discouraged</strong>.</td>
</tr>
<tr class="odd">
<td>AnalysisUsage</td>
<td>Specify the role of the EDT in a cube. This setting is automatically propagated to all table fields that reference the EDT. However, you can override the setting on a table field. The following options are available:
<ul>
<li><strong>Attribute </strong>– A field that references the EDT is a dimension attribute.</li>
<li><strong>Measure </strong>– A field that references the EDT is a measure.</li>
<li><strong>Both </strong>– A field that references the EDT is both a dimension attribute and a measure.</li>
<li><strong>None </strong>– A field that references the EDT is neither a dimension attribute nor a measure.</li>
<li><strong>Auto </strong>– This option applies to derived EDTs. The value of the <strong>AnalysisUsage</strong> property for the parent EDT is used.</li>
</ul>
<strong>Note:</strong> Data types that are based on enumerations can't be measures.</td>
</tr>
<tr class="even">
<td>ArrayLength</td>
<td>This property is a read-only. The default value is <strong>1</strong>. To add array elements to the EDT, right-click the <strong>Array Element</strong> node, and then click <strong>New Array Element</strong>. The value of the <strong>ArrayLength</strong> property is increased to reflect this change.</td>
</tr>
<tr class="odd">
<td>ButtonImage</td>
<td>Specify the image that is shown when the EDT is used for a lookup button on a page. The following options are available:
<ul>
<li><strong>Arrow</strong></li>
<li><strong>Mail</strong> – You can select this option for the <strong>e-mail</strong> type, for example.</li>
<li><strong>URL</strong> – You can select this option for the <strong>URL</strong> type, for example.</li>
<li><strong>ThreeDots</strong> (...)</li>
<li><strong>OpenFile</strong> – You can select this option for the <strong>FilenameOpen</strong> and <strong>FilenameSave</strong> types, for example.</li>
<li><strong>Calendar</strong> – You can select this option for date types, for example.</li>
</ul>
The default value is <strong>Arrow</strong>.</td>
</tr>
<tr class="even">
<td>CollectionLabel</td>
<td>Specify the label that is used to show the plural name of a field that has this EDT.</td>
</tr>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Specify the configuration key for the EDT.</td>
</tr>
<tr class="even">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the menu is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="odd">
<td>DisplayLength</td>
<td>Specify the maximum number of characters that are shown on a page or report.</td>
</tr>
<tr class="even">
<td>EnumType</td>
<td>Specify an enumerated data type. This property must be set for EDTs of the <strong>enum</strong> type.</td>
</tr>
<tr class="odd">
<td>Extends</td>
<td>Use this property to base the EDT on another EDT.</td>
</tr>
<tr class="even">
<td>FormHelp</td>
<td>Specify the page to use when you perform a lookup from a field on a page.</td>
</tr>
<tr class="odd">
<td>HelpText</td>
<td>Create a Help string for the EDT. The Help string is shown when the type is used on a page.</td>
</tr>
<tr class="even">
<td>ID</td>
<td>This property is read-only.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Specify the label that is used for the type when the type is used on a page or report.</td>
</tr>
<tr class="even">
<td>Model</td>
<td>Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="odd">
<td>Name</td>
<td>Specify the name of the type. The name is used to refer to the type from X++.</td>
</tr>
<tr class="even">
<td>PresenceClass</td>
<td>Specify the X++ class that is used together with the <strong>PresenceMethod</strong> property to return an instance of the <strong>PresenceInfo</strong> object.</td>
</tr>
<tr class="odd">
<td>PresenceIndicatorAllowed</td>
<td>Specify whether the control that references the EDT should use presence. The default value is <strong>Yes</strong>.</td>
</tr>
<tr class="even">
<td>PresenceMethod</td>
<td>For the X++ class that is specified in the <strong>PresenceClass</strong> property, specify the X++ static class method that should be called by using a controls data value. This method returns an instance of the <strong>PresenceInfo</strong> object that contains the data that the Presence indicator requires.</td>
</tr>
<tr class="odd">
<td>ReferenceTable</td>
<td>Specify the table that is referenced by this EDT, and that has the primary key. In other words, this property indicates the primary key table that this EDT references.</td>
</tr>
<tr class="even">
<td>Style</td>
<td>Change the default appearance of the EDT. The following options are available:
<ul>
<li>Auto</li>
<li>Combo box</li>
<li>Radio button</li>
</ul></td>
</tr>
</tbody>
</table>

### Properties that are available for only some base data types

Unless the following table specifies otherwise, you should leave all these properties set to **Auto**.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Type that the property exists for</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Adjustment</td>
<td>String</td>
<td>For strings of fixed length, specify whether the characters that are entered should be stored on the left side or the right side of the padding spaces. The available options are <strong>Left</strong> and <strong>Right</strong>. The default value is <strong>Left</strong>.</td>
</tr>
<tr class="even">
<td>AllowNegative</td>
<td>IntegerInt64Real</td>
<td>Specify whether the field can accept negative values.</td>
</tr>
<tr class="odd">
<td>AutoInsSeparator</td>
<td>Real</td>
<td>Specify whether the system should automatically insert a decimal separator. For example, if you enter <strong>2222</strong>, the system automatically shows <strong>2222.00</strong>.</td>
</tr>
<tr class="even">
<td>ChangeCase</td>
<td>String</td>
<td>Specify how text that is entered in a string control should be formatted. For example, the text can be formatted as all uppercase letters, or it can use title capitalization. <strong>Note:</strong> This property isn't supported for Enterprise Portal.</td>
</tr>
<tr class="odd">
<td>DateDay</td>
<td>DateUtcDateTime</td>
<td>Specify how the day should be shown.</td>
</tr>
<tr class="even">
<td>DateFormat</td>
<td>DateUtcDateTime</td>
<td>Specify the layout of a date.</td>
</tr>
<tr class="odd">
<td>DateMonth</td>
<td>DateUtcDateTime</td>
<td>Specify how the month should be shown.</td>
</tr>
<tr class="even">
<td>DateSeparator</td>
<td>DateUtcDateTime</td>
<td>Specify the separators between year, month, and day.</td>
</tr>
<tr class="odd">
<td>DateYear</td>
<td>DateUtcDateTime</td>
<td>Specify how the year should be shown.</td>
</tr>
<tr class="even">
<td>DecimalSeparator</td>
<td>Real</td>
<td>Specify the decimal separator. When the default setting (<strong>Auto</strong>) is used, the decimal separator that is specified in the system setup is used.</td>
</tr>
<tr class="odd">
<td>DisplaceNegative</td>
<td>IntegerInt64Real</td>
<td>Specify whether to align negative numbers to the left.</td>
</tr>
<tr class="even">
<td>DisplayHeight</td>
<td>String</td>
<td>Specify the number of lines to show at the same time when the EDT is shown on a page.</td>
</tr>
<tr class="odd">
<td>EnumType</td>
<td>Enum</td>
<td>Specify the base enum that is used to create the EDT.</td>
</tr>
<tr class="even">
<td>FormatMST</td>
<td>Real</td>
<td>Specify master currency values should be formatted. The following options are available:
<ul>
<li>Auto</li>
<li>Yes</li>
<li>No</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>NoOfDecimals</td>
<td>Real</td>
<td>Specify the number of decimal places when a value is shown on a page or a report.</td>
</tr>
<tr class="even">
<td>RotateSign</td>
<td>IntegerInt64Real</td>
<td>Select this option to reverse the sign for the number. In other words, change a minus sign (–) to a plus sign (+) or a plus sign to a minus sign.</td>
</tr>
<tr class="odd">
<td>ShowZero</td>
<td>IntegerInt64Real</td>
<td>Specify whether to show a field that has a value of 0 (zero) as an empty field. If a value of 0 in fields of this type means null/nothing, set this property to <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>SignDisplay</td>
<td>IntegerInt64Real</td>
<td>Specify whether to show the sign of a negative number, and also whether the sign should appear before or after the number. Typically, you should set this property to <strong>Auto</strong>. However, you can set it to <strong>None</strong> if the <strong>DisplaceNegative</strong> property is used.</td>
</tr>
<tr class="odd">
<td>StringSize</td>
<td>String</td>
<td>Specify the maximum size of the string.</td>
</tr>
<tr class="even">
<td>ThousandSeparator</td>
<td>Real</td>
<td>Specify the symbol that is used to separate thousands.</td>
</tr>
<tr class="odd">
<td>TimeFormat</td>
<td>TimeUtcDateTime</td>
<td>Specify how times should be formatted.</td>
</tr>
<tr class="even">
<td>TimeHours</td>
<td>TimeUtcDateTime</td>
<td>Specify whether to include hours.</td>
</tr>
<tr class="odd">
<td>TimeMinute</td>
<td>TimeUtcDateTime</td>
<td>Specify whether to include minutes.</td>
</tr>
<tr class="even">
<td>TimeSeconds</td>
<td>TimeUtcDateTime</td>
<td>Specify whether to include seconds.</td>
</tr>
<tr class="odd">
<td>TimeSeparator</td>
<td>TimeUtcDateTime</td>
<td>Specify the separator that is used for times.</td>
</tr>
<tr class="even">
<td>TimezonePreference</td>
<td>UtcDateTime</td>
<td>Specify the time zone to convert the value to from Coordinated Universal Time (UTC).</td>
</tr>
</tbody>
</table>

## Perspective properties
In Application Explorer, under the **Data Dictionary** node, there is a **Perspectives** node. A perspective is a collection of tables and views that contain the measures and dimensions for a cube. The following table describes the properties that can be set for each perspective. For information about the system properties that are available for a perspective, see the "System and common properties" section. For information about the properties for tables that are associated with a perspective, see the "Table properties" and "Table field properties" sections.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Specify the configuration key that is assigned to the perspective. The configuration key determines which configurations of a perspective are included for in report models that are generated.</td>
</tr>
<tr class="even">
<td>HelpText</td>
<td>Create a string to use as a description for the perspective in a report model.</td>
</tr>
<tr class="odd">
<td>ID</td>
<td>Specify the identifier of the perspective.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Specify the name that is shown for the perspective in a report model.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the perspective is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>SharedDimensionContainer</td>
<td>Specify whether to share items in the perspective. When this property is set to <strong>Yes</strong>, the items in the perspective are added to all other perspectives that are in the project, and no cube is created for the perspective. The default value is <strong>No</strong>.</td>
</tr>
<tr class="odd">
<td>Usage</td>
<td>Specify the materialization options for a perspective. The following options are available:
<ul>
<li><strong>AdHocReporting </strong>– The perspective will be used to generate a transactional Semantic Model Definition Language (SMDL) model.</li>
<li><strong>OLAP </strong>– The perspective will be used to generate a cube in a Microsoft SQL Server Analysis Services (SSAS) Business Intelligence project.</li>
<li><strong>Both </strong>– The perspective will be used to generate both a transactional SDML model and a cube in an SSAS Business Intelligence project.</li>
<li><strong>None </strong>– The perspective won't be materialized.</li>
</ul>
The default value is <strong>None</strong>.</td>
</tr>
</tbody>
</table>

## Table properties
This section describes the properties that appear in the **Properties** window for table elements in Application Explorer. Table elements are located under **Data Dictionary** &gt; **Tables**.

### Table properties

The following table describes the properties of table elements in Application Explorer.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Abstract</td>
<td>Specify whether the table supports inheritance. The default value is <strong>No</strong>. If the value is set to <strong>Yes</strong>, the table can't be a direct target of X++ SQL statements such as <strong>update_recordset</strong> and <strong>select</strong>. <strong>Note:</strong> This property is unavailable when the <strong>SupportInheritance</strong> property is set to <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>AnalysisDimensionType</td>
<td>Specify the type of dimension that is created, based on the setting of the <strong>IsLookup</strong> property. If the <strong>IsLookup</strong> property is set to <strong>Yes</strong>, the following options are available:
<ul>
<li><strong>Auto </strong>– The table can contain both factual and dimensional data. The BI Wizard will extract dimensional data, and create dimensions and attributes. Factual data will be extracted to create measures. One child dimension is created that has attributes from the parent table.</li>
<li><strong>MasterInner </strong>– An inner (full) join is used to create relationships with this table to the child table. Each record combination for this table and the child table are generated in the dimension. One child dimension is created that has attributes from the parent table.</li>
<li><strong>MasterLeftOuter </strong>– A left outer join is used to create relationships with this table to the child table. Dimensions will have additional attributes, based on values in this table that can also be empty. One child dimension is created that has attributes from the parent table.</li>
<li><strong>Transaction </strong>– The table should be used to generate only factual data (measures). You should use this option when a table contains only transactional data. One child dimension is created that contains only enumeration fields from the table.</li>
</ul>
If the <strong>IsLookup</strong> property is set to <strong>No</strong>, the following options are available:
<ul>
<li><strong>Auto </strong>– Table can contain both factual and dimensional data. The BI Wizard will extract dimensional data, and create dimensions and attributes, Factual data will be extracted to create measures. One parent and child dimension are created.</li>
<li><strong>MasterInner </strong>– Not applicable. This option is the same as <strong>Auto</strong>.</li>
<li><strong>MasterLeftOuter </strong>– Not applicable. This option is the same as <strong>Auto</strong>.</li>
<li><strong>Transaction </strong>– The table should be used to generate only factual data (measures). You should use this option when a table contains only transactional data. One child dimension is created that contains only enumeration values from the table.</li>
</ul></td>
</tr>
<tr class="odd">
<td>AnalysisIdentifier</td>
<td>Specify the field to use as the identifier for the dimension in an SSAS cube.</td>
</tr>
<tr class="even">
<td>AOSAuthorization</td>
<td>Specify the type of operation that a user can perform on a table, depending on the user's permissions. When this property is set to <strong>None</strong>, no authorization check is performed.</td>
</tr>
<tr class="odd">
<td>CacheLookup</td>
<td>Specify how to cache the records that are retrieved during a lookup operation. This property exists only on tables that don't inherit from another table. On an inheritance root table, you can' set this property to <strong>EntireTable</strong> by using the Application Explorer <strong>Properties</strong> window. You must not use other techniques to assign this value to inheritance root tables. For example, don't use the <strong>AOTsetProperty</strong> method of the <strong>TreeNode</strong> class to assign this value.</td>
</tr>
<tr class="even">
<td>ClusterIndex</td>
<td>Specify the cluster index. This property is used only for SQL optimization.</td>
</tr>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Specify the configuration key for the table. Configuration keys let a system administrator enable and disable specific parts of an application.</td>
</tr>
<tr class="even">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the table is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client framework uses this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="odd">
<td>CountryRegionContextField</td>
<td>Specify the field that is used to identify the country/region context. This property is related to the <strong>CountryRegionCodes</strong> property.</td>
</tr>
<tr class="even">
<td>CreatedBy</td>
<td>Specify whether the system maintains the <strong>CreatedBy</strong> field for the records in a table. This field contains information about the person who created a record.</td>
</tr>
<tr class="odd">
<td>CreatedDateTime</td>
<td>Specify whether the system maintains the <strong>CreationDate</strong> and <strong>CreationTime</strong> fields for the records in a table. This field contains the date when a record was created.</td>
</tr>
<tr class="even">
<td>CreatedTransactionId</td>
<td>Specify whether the system maintains the <strong>CreatedTransactionId</strong> field for the records in a table. This field contains information about the transaction that created a record.</td>
</tr>
<tr class="odd">
<td>CreateRecIdIndex</td>
<td>Specify whether an index on the <strong>Record ID</strong> field is created.</td>
</tr>
<tr class="even">
<td>DeveloperDocumentation</td>
<td>Describe the purpose of a table, and explain how it's used in the program. Typically, a description contains no more than five sentences and is written as a single paragraph.</td>
</tr>
<tr class="odd">
<td>EntityRelationshipType</td>
<td>Classify a table according to common entity relationship (ER) data model notation. A table is classified as either an entity or a relationship. An entity represents an object, whereas a relationship represents an association between two objects.</td>
</tr>
<tr class="even">
<td>Extends</td>
<td>Derive the table from the specified table. The value of this property is <strong>null</strong> when the <strong>SupportInheritance</strong> property is set to <strong>Yes</strong>.</td>
</tr>
<tr class="odd">
<td>FormRef</td>
<td>Specify the display menu item that is activated when a table is referenced. A display menu item is associated with a page. When you use a primary index field on a report, this page is available as a link in the report. You specify a primary index by using the <strong>PrimaryIndex</strong> property. If you leave this property blank, the system tries to display a page that has the same name as the table.</td>
</tr>
<tr class="even">
<td>ID</td>
<td>The system-generated table ID.</td>
</tr>
<tr class="odd">
<td>IsLookup</td>
<td>For report models, use this property to specify whether the table information is incorporated into other tables that reference it when a report model is generated. For online analytical processing (OLAP) cubes, use this property to specify whether to generate a consolidated dimension or a distinct dimension. The following options are available:
<ul>
<li><strong>Yes </strong>– Attributes from the table should be consolidated into the parent dimension (star schema).</li>
<li><strong>No </strong>– A separate dimension should be generated for the table (snowflake schema).</li>
</ul></td>
</tr>
<tr class="even">
<td>Label</td>
<td>Specify the label for a table.</td>
</tr>
<tr class="odd">
<td>ListPageRef</td>
<td>Specify a display menu item that points to a page that can show a list of this record type.</td>
</tr>
<tr class="even">
<td>Model</td>
<td>Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="odd">
<td>ModifiedBy</td>
<td>Specify whether the system maintains the <strong>ModifiedBy</strong> field for the records in a table. This field contains information about the person who last modified a record.</td>
</tr>
<tr class="even">
<td>ModifiedDateTime</td>
<td>Specify whether the system maintains the <strong>ModifiedDate</strong> field for the records in a table. This field contains the date when a record was last modified.</td>
</tr>
<tr class="odd">
<td>ModifiedTime</td>
<td>Specify whether the system maintains the <strong>ModifiedDateTime</strong> field for the records in a table. This field contains the date and time when a record was last modified.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Specify the table name.</td>
</tr>
<tr class="odd">
<td>OccEnabled</td>
<td>Specify whether the optimistic concurrency mode is enabled for a table. When this mode is enabled, data isn't locked from future modification when it's fetched from the database. Data is locked only when the actual update is performed.</td>
</tr>
<tr class="even">
<td>PreviewPartRef</td>
<td>Specify the info part or form part to use in the enhanced preview. An info part shows a collection of data fields from a specified query. It uses metadata to describe how the data appears. A form part represents a pointer to a page.</td>
</tr>
<tr class="odd">
<td>PrimaryIndex</td>
<td>Specify the primary index. Only a unique index can be selected. This property is used for database optimization and to indicate which unique index should be used as the caching key. If you don't specify a primary index, the unique index that has the lowest ID is used as the caching key.</td>
</tr>
<tr class="even">
<td>ReplacementKey</td>
<td>Specify the fields to display as the identifier for data in some page controls.</td>
</tr>
<tr class="odd">
<td>ReportRef</td>
<td>Specify the output menu item that is activated when a table is referenced. An output menu item is associated with a report. When you use a primary index field on a report, this report is available as a link in the report. You specify a primary index by using the <strong>PrimaryIndex</strong> property.</td>
</tr>
<tr class="even">
<td>SaveDataPerCompany</td>
<td>Specify whether the data for the current company is saved. If you set the property to <strong>No</strong>, data is saved without a company identifier (DataAreaId). <strong>Note: </strong>If the <strong>SaveDataPerCompany</strong> property on a table is set to <strong>Yes</strong>, the <strong>SetCompany</strong> property on a page design that uses the table as a data source must also be set to <strong>Yes</strong>. <strong>Tip: </strong>The status line shows the acronym for the company. Double-click the acronym to open a dialog box where you can change the company.</td>
</tr>
<tr class="odd">
<td>SaveDataPerPartition</td>
<td>A value that indicates whether the table has a system field that is named <strong>Partition</strong>. This property is intended to be read-only. If the table has a <strong>Partition</strong> field, each record is assigned to one partition. Each record is hidden from data access operations that are run under the context of other partitions.</td>
</tr>
<tr class="even">
<td>SearchLinkRefName</td>
<td>Specify the name of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results. If the <strong>SearchLinkRefType</strong> property is set to <strong>URL</strong>, select a menu item that links to a Web Part page that shows the table data. Forms and reports on Web Part pages can display data.</td>
</tr>
<tr class="odd">
<td>SearchLinkRefType</td>
<td>Specify the type of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results.</td>
</tr>
<tr class="even">
<td>SingularLabel</td>
<td>Specify the label that is used in a report model or a cube to show the singular name of items that are stored in the table.</td>
</tr>
<tr class="odd">
<td>SupportInheritance</td>
<td>When you set this property to <strong>Yes</strong>, you can set a value for other inheritance-related properties, such as <strong>Extends</strong> and <strong>Abstract</strong>. <strong>Caution:</strong> If you set this property to <strong>Yes</strong>, any fields on the table are dropped and must be created again.</td>
</tr>
<tr class="even">
<td>SystemTable</td>
<td>Indicate whether a table appears as a system table. A table that appears as a system table can be filtered during export and import. System tables are always synchronized when you sign in. Therefore, this property might be useful for tables that you use as soon as you sign in.</td>
</tr>
<tr class="odd">
<td>TableContents</td>
<td>Specify how setup/parameter data can be reused from one customer to another. The following options are available:
<ul>
<li><strong>Not specified </strong>– Use this option for most tables.</li>
<li><strong>Default Data </strong>– Use this option for customer-independent data, such as postal codes, units, and time intervals.</li>
<li><strong>Base Data </strong>– Use this option for customer-dependent data, such as calendars, groups, and parameters.</li>
<li><strong>Default+Base data </strong>– Use this option for data where the local perception varies. For example, Chart of Accounts is customer-independent in Germany but is customer dependent in most other places.</li>
</ul></td>
</tr>
<tr class="even">
<td>TableGroup</td>
<td>Specify the group that the table belongs to. Table groups provide a method for categorizing tables according to the type of data that they contain. You can use table groups to define whether the system should prompt users when they update or delete data from the table on pages by using the table as the data source. When you export data, you can use table groups to filter records.</td>
</tr>
<tr class="odd">
<td>TableType</td>
<td>This property replaces the <strong>Temporary</strong> property that is found in Microsoft Dynamics AX 2009.</td>
</tr>
<tr class="even">
<td>TitleField1, TitleField2</td>
<td>You can use this property in the following ways:
<ul>
<li>Add table field data to a form caption.</li>
<li>Show additional fields on a lookup page. The <strong>TitleField1</strong> property is also used when you activate the lookup list in a field on a page. The fields that you specify for the <strong>TitleField1</strong> and <strong>TitleField2</strong> properties can be merged with the key value.</li>
<li>Show field information in a tooltip.</li>
</ul></td>
</tr>
<tr class="odd">
<td>TypicalRowCount</td>
<td>Specify the number of records that typically appear in a table. If the <strong>AnalysisSelection</strong> property isn't set, this property determines how records are selected by using Report Builder for SSRS. The setting of this property affects whether a drop-down list, a list box, or a filtered list box is used to select table records.</td>
</tr>
<tr class="even">
<td>ValidTimeStateFieldType</td>
<td>Specify the type of date-time field that the system uses when it tracks data within time spans.</td>
</tr>
<tr class="odd">
<td>Visible</td>
<td>Specify the access rights when the table is used as a data source on a page or a report. If the table is used as a data source on a page, the access rights on the page can't exceed the access rights that are defined for the table.</td>
</tr>
</tbody>
</table>

### Tables and report models

The following properties are related to report models that are used to add information to a report:

-   AnalysisSelection
-   AnalysisVisibility
-   IsLookup
-   SingularLabel
-   TypicalRowCount

## Table field properties
The following properties are related to report models that are used to add information to a report:

-   AnalysisDefaultTotal
-   AnalysisLabel
-   AnalysisTotaling
-   AnalysisUsage
-   AnalysisVisibility
-   CurrencyCode
-   CurrencyCodeField
-   CurrencyCodeTable

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Adjustment</td>
<td>Specify whether the string field should be left-aligned or right-aligned when it's stored in the database. For example, if the 11-character string &quot;hello world&quot; is stored in a right-aligned field that has a <strong>StringSize</strong> setting of <strong>40</strong>, 29 space characters are stored as the prefix. <strong>Note:</strong> The <strong>Adjustment</strong> setting affects the search results when you search for a value in a table by using the <strong>&gt;</strong>, <strong>&lt;</strong>, <strong>&gt;=</strong>, and <strong>&lt;=</strong> relational operators. It doesn't affect the search results when you use the <strong>==</strong> operator. The <strong>Adjustment</strong> setting is ignored when the <strong>StringSize</strong> property is set to <strong>(Memo)</strong>.</td>
</tr>
<tr class="even">
<td>AliasFor</td>
<td>Specify the table field that the field is an alias for.</td>
</tr>
<tr class="odd">
<td>AllowEdit</td>
<td>Specify whether users are allowed to modify data in an existing record on a page.</td>
</tr>
<tr class="even">
<td>AllowEditOnCreate</td>
<td>Specify whether users are allowed to enter data in the field when a new record is created from a page.</td>
</tr>
<tr class="odd">
<td>AnalysisDefaultTotal</td>
<td>For report models, use this property to specify how field data is aggregated when an automatic total for the table is displayed in a report that is built by using SSRS and report models. The default value is <strong>No</strong>, which indicates that the field isn't automatically shown as a total. For OLAP cubes, use this property to specify the aggregate function for a measure. Use this property when the <strong>AnalysisUsage</strong> property is set to <strong>Measure</strong>. The following options are available:
<ul>
<li><strong>Sum </strong>– Return the sum of all the values in a set.</li>
<li><strong>Count </strong>– Return the number of non-null items in a set.</li>
<li><strong>CountDistinct </strong>– Return the number of distinct non-null items in a set.</li>
<li><strong>Min </strong>– Return the minimum value in a set.</li>
<li><strong>Max </strong>– Return the maximum value in a set.</li>
<li><strong>None </strong>– No aggregate function is applied.</li>
<li><strong>Auto </strong>– This option applies to derived EDTs. The value of the <strong>AnalysisUsage</strong> property for the parent EDT is used.</li>
</ul></td>
</tr>
<tr class="even">
<td>AnalysisLabel</td>
<td>Specify the label to use as the caption in an SSAS cube for the table field. The label is applied to either a dimension attribute or a measure. This property is intended for situations where one of the following conditions is true:
<ul>
<li>The <strong>Label</strong> property isn't defined.</li>
<li>The <strong>Label</strong> property doesn't work as a caption for a dimension attribute or a measure in a SSAS cube.</li>
</ul></td>
</tr>
<tr class="odd">
<td>AnalysisUsage</td>
<td>Specify the role of the field in a cube. The following options are available
<ul>
<li><strong>Attribute </strong>– The field is a dimension attribute.</li>
<li><strong>Measure </strong>– The field is a measure.</li>
<li><strong>Both </strong>– The field is both a dimension attribute and a measure.</li>
<li><strong>None </strong>– The field is neither a dimension attribute nor a measure.</li>
<li><strong>Auto </strong>– The value of the <strong>AnalysisUsage</strong> property for the EDT or enumeration that the field is based on should be used.</li>
</ul></td>
</tr>
<tr class="even">
<td>ConfigurationKey</td>
<td>Set the configuration key for the field.</td>
</tr>
<tr class="odd">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the table field is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client framework and application might use this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="even">
<td>CountryRegionContextField</td>
<td>Specify the field that is used to identify the country/region context. See the description of the <strong>CountryRegionCodes</strong> property.</td>
</tr>
<tr class="odd">
<td>ExtendedDataType</td>
<td>Specify the EDT to use for this field.</td>
</tr>
<tr class="even">
<td>GroupPrompt</td>
<td>Specify a label that is used for the field when it appears in a group. <strong>Tip:</strong> You can use this property to help guarantee that a field label doesn't repeat text that appears in the label for a field group. For example, if a field group on a page is labeled <strong>Customer</strong>, don't include this text in the <strong>GroupPrompt</strong> property for fields that are included in the field group.</td>
</tr>
<tr class="odd">
<td>HelpText</td>
<td>Specify the Help string for the field. The Help string is shown when the field is used on a page.</td>
</tr>
<tr class="even">
<td>ID</td>
<td>The system-generated field ID.</td>
</tr>
<tr class="odd">
<td>IgnoreEDTRelation</td>
<td>This property is used during the migration of EDT relations. When you migrate relations from an EDT node to a table node, you can skip an invalid relation for a given table field. To skip invalid relations, set this property to <strong>Yes</strong>. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Specify a label for the field. This label will appear on pages and reports. Also see the description of the <strong>AnalysisLabel</strong> property earlier in this table.</td>
</tr>
<tr class="odd">
<td>Mandatory</td>
<td>Specify whether a user must add data to a field on a page. Set this property to <strong>Yes</strong> to indicate that the default or initialization value for each data type isn't acceptable for persistence into the database. The following list shows some default values that can't be used for mandatory fields on a page:
<ul>
<li>Empty isn't acceptable for a str (string) field.</li>
<li>The minimum date-time isn't acceptable for date-time fields such as date and utcdatetime.</li>
<li>A value of 0 (zero) isn't acceptable for numeric fields such as int, real, and enum.</li>
</ul>
Dynamics 365 for Operations doesn't support the semantics for the <strong>null</strong> value that is standard in most SQL database products. Field can't be nulled in the database. Therefore, the <strong>Mandatory</strong> property has nothing to do with the concept of a <strong>null</strong> value. <strong>Caution:</strong> A mandatory table field can have its <strong>EnumType</strong> property set to an enumeration. You might define a field as an enum type that includes an item that has the integer value <strong>0</strong>. In this case, <strong>0</strong> isn't an item that's available for selection on the page. The forms system automatically calls the <strong>validateWrite</strong> method to enforce the setting of the <strong>Mandatory</strong> property. However, the <strong>Mandatory</strong> property has no effect on the behavior of direct X++ SQL that inserts or updates the value of a table field. In your direct X++ SQL, you can include calls to the <strong>validateWrite</strong> method on your table buffer variable. Your buffer variable inherits the method from the <strong>xRecord</strong> class.</td>
</tr>
<tr class="even">
<td>MinReadAccess</td>
<td>Specify the mode of the automatic authorization feature. Automatic authorization has two modes of operation: surrogate foreign key and lookup. If a table in a query is tagged for surrogate foreign key authorization, and the user doesn't have access to that table but hasn't been explicitly denied, view access is granted to the table. However, not all fields will be visible. The visibility is determined by the following rules:
<ul>
<li>If <strong>MinReadAccess</strong> is set to <strong>No</strong>, no access is granted to the field.</li>
<li>If <strong>MinReadAccess</strong> is set to <strong>Yes</strong>, view access is granted to the field.</li>
<li>Otherwise, view access is granted if the field is part of the natural key automatic identification group, if it's a title field, or if it's a system field.</li>
</ul>
If a table in a query is tagged for lookup authorization, access is determined by the following rules:
<ul>
<li>If <strong>MinReadAccess</strong> is set to <strong>No</strong>, no access is granted to the field.</li>
<li>Otherwise, view access is granted to the field.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the table field is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Specify the name of the field.</td>
</tr>
<tr class="odd">
<td>RelationContext</td>
<td>Specify the mapping of a field to a specific table relation. Typically, this property is used in unit-of-measure scenarios to model data that is related to currency codes or quantities. The relation that is associated with the field can then be used to show a lookup of currency codes or quantities. There is no default value.</td>
</tr>
<tr class="even">
<td>SaveContents</td>
<td>Specify whether the field data is saved in the database or treated as virtual field data. Virtual field data is calculated at run time when the field is displayed. This data has no physical representation in the database. <strong>Tip:</strong> Instead of virtual fields, you can use display and edit methods.</td>
</tr>
<tr class="odd">
<td>StringSize</td>
<td>Set the field length, in the number of characters. The maximum field length depends on the database. A value of <strong>(Memo)</strong> indicates that the field length is unlimited.</td>
</tr>
<tr class="even">
<td>Type</td>
<td>Specify the base type of a field.</td>
</tr>
<tr class="odd">
<td>Visible</td>
<td>Specify whether the field should be visible in the user interface.</td>
</tr>
</tbody>
</table>

## Table index properties
The following table describes the properties that are available for indexes on tables.

| Property              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowDuplicates       | If you set this property to **Yes**, the index can be non-unique. If you don't create at least one unique index, Dynamics 365 for Operations creates a unique index by combining the first index and the RecId.                                                                                                                                                                                                                                                     |
| AlternateKey          | Specify whether this index is part of an alternate key. The index field must have a unique value in every record.                                                                                                                                                                                                                                                                                                                                                   |
| ConfigurationKey      | Set the configuration key. An index field that is disabled through a configuration key is automatically removed from the index.                                                                                                                                                                                                                                                                                                                                     |
| Enabled               | You can use this property to disable the index.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ID                    | The internal identifier of the object.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Model                 | Specify the model that the table index is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.                                                                                                                                                                   |
| Name                  | Specify the index name.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| UniqueAcrossCompanies | This property is for internal Microsoft use only. The available values are **Yes** and **No**. The default value is **No**. The value of this property is ignored when the **AllowDuplicates** property is set to **No**. However, when **AllowDuplicates** is set to **Yes**, a value of **Yes** for **UniqueAcrossCompanies** can improve the performance of some cross-company queries. The performance improvement is caused by changes to the caching of data. |
| ValidTimeStateKey     | Specify whether this index key is used to determine the valid time state relationship with the parent table. The default value is **No**. **Tip:** To enable this property, you must set the **AllowDuplicates** property to **No** and the **AlternateKey** property to **Yes**.                                                                                                                                                                                   |
| ValidTimeStateMode    | Specify whether gaps are allowed between two date-effective records. The default value is **NoGap**. **Tip:** To enable this property, you must set the **AllowDuplicates** property to **No**, the **AlternateKey** property to **Yes**, and the **ValidTimeStateKey** property to **Yes**.                                                                                                                                                                        |

**Note:** Pages sort on the first index.

## Table relation properties
### List of properties

The following table describes the properties for a table relation in Application Explorer.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cardinality</td>
<td>The number of times that each primary key value from the referenced table must occur in the foreign key column of the current table. For example, the <strong>OneMore</strong> value means one or more, but not zero. This value indicates that every parent key value must occur in the child table's foreign key column at least one time. A relation node under a SalesLine table might use the <strong>OneMore</strong> value when the business rule requires that every record in the parent SalesTable table relate to at least one item that is being sold. Currently, Dynamics 365 for Operations doesn't use the <strong>Cardinality</strong> property. However, future releases might use this property and the <strong>RelatedTableCardinality</strong> property.</td>
</tr>
<tr class="even">
<td>CreateNavigationPropertyMethods</td>
<td>A value of <strong>Yes</strong> instructs the system to generate navigation methods on the table buffer class for each foreign key relation node.</td>
</tr>
<tr class="odd">
<td>EDTRelation</td>
<td>If the value is set to <strong>Yes</strong>, a software tool was used to migrate this relation to its current location from an old EDT relation.</td>
</tr>
<tr class="even">
<td>EntityRelationshipRole</td>
<td>This property is used to clarify the semantics of a relationship that is defined on a table. A role name should be either a noun or a noun phrase. The role name should indicate the role of the associated table in relation to the associating object. Alternatively, the role name should be a short phrase that starts with a present-tense verb that indicates the role that the table plays in the relationship. Role names aren't required when the relationship is unambiguous.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>The model that this relation is part of.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>A descriptive name that you choose for the relation.</td>
</tr>
<tr class="odd">
<td>NavigationPropertyMethodNameOverride</td>
<td>Specify the name of the navigation method. If no value is specified, the navigation method uses the value from the <strong>RelatedTableRole</strong> property.</td>
</tr>
<tr class="even">
<td>RelatedTableCardinality</td>
<td>Specify whether the foreign key field value in the current table can be <strong>null</strong> in some or all records of the current table. The following options are available:
<ul>
<li><strong>ZeroOne</strong> means zero or one. This value indicates that the foreign key field in a child record can be <strong>null</strong>.</li>
<li><strong>ExactlyOne</strong> indicates that the foreign key field can't be <strong>null</strong> in any child record.</li>
</ul></td>
</tr>
<tr class="odd">
<td>RelatedTableRole</td>
<td>Enter a text value to describe the purpose of the referenced parent table in this relationship. When a table has only one relation that references a given parent table, you can use the name of the parent table. Sometimes, a table has more than one relation to a given referenced parent table. this case, the value of the <strong>RelatedTableRole</strong> property should describe the relation well enough to distinguish the relation's purpose from the other relation to the same parent table. The value of this property can be used as the value of the <strong>JoinRelation</strong> property of a data source relation under an Application Explorer query. In standard cases, this usage is recommended, because it reduces denormalization. This property interacts with the <strong>UseDefaultRoleNames</strong> property.</td>
</tr>
<tr class="even">
<td>RelationshipType</td>
<td>Select a value that describes the subtle relationship between two tables. For example, the <strong>Composition</strong> value indicates that the child record can't meaningfully exist unless it's related to a specific parent record. The record for the fourth floor in the Floor table can't exist unless it references a record in the parent Building table. <strong>Note:</strong> The DeleteActions should be compatible with this property setting. For a Composition relationship, the DeleteActions should include delete cascade behavior. Currently, Dynamics 365 for Operations doesn't use the <strong>RelationshipType</strong> property. However, a future release might use this property.</td>
</tr>
<tr class="odd">
<td>Role</td>
<td>Specify a name that describes the meaning or role of the relation. For example, one relation to a Department table could track the department that the employee currently belongs to. Another relation could track the department that the employee has requested a transfer to. Although both these relations are relations to the Department table, they fill different roles. As the value of this property, it's a good idea to join the names of the child table and parent table by using an underscore (_) character. For example, enter <strong>SalesTable_SalesLine</strong>. This property interacts with the <strong>UseDefaultRoleNames</strong> property.</td>
</tr>
<tr class="even">
<td>Table</td>
<td>The table that the relation refers to.</td>
</tr>
<tr class="odd">
<td>UseDefaultRoleNames</td>
<td>A value of <strong>Yes</strong> indicates that the system must generate default values for the <strong>Role</strong> and <strong>RelatedTableRole</strong> properties. Even when this property is set to <strong>Yes</strong>, the values for that are generated for <strong>Role</strong> and <strong>RelatedTableRole</strong> don't appear in the <strong>Properties</strong> window. Additionally, the <strong>TreeNode</strong> class doesn't use the generate values. However, the <strong>DictRelation</strong> reflection class does use the generated values.</td>
</tr>
<tr class="even">
<td>Validate</td>
<td>A value of <strong>Yes</strong> indicates that when a page inserts a record into the child table, the insertion is rejected unless the related record exists in the referenced parent table. Additionally, when a page deletes a record from the parent table, the deletion is either rejected or cascades to the related records in the child table. Set the value to <strong>No</strong> when the <strong>RelationshipType</strong> property is set to <strong>Link</strong>. You might also set the value to <strong>No</strong> in special temporary cases, such as during some upgrade scenarios. When the value is set back to <strong>Yes</strong>, no validation occurs for records that were inserted or deleted while the value was <strong>No</strong>. <strong>Caution:</strong> A value of <strong>Yes</strong> for the <strong>Validate</strong> property doesn't prevent direct X++ SQL data operations from deleting parent records or inserting child records that violate the integrity of foreign key data.</td>
</tr>
</tbody>
</table>

**Note:** When the **SaveDataPerCompany** property is set to **Yes** for both tables, the system adds the **DataAreaId** field to each relationship.

### RelatedTableRole and query JoinRelation

This section describes how you can use the **RelatedTableRole** property to simplify the creation of a new query. If you enter an explicit value for the **RelatedTableRole** property on a table relation, you can use that value to populate the **JoinRelation** property on a data source relation under a **Queries** &gt; **MyQuery** node in Application Explorer. You can use this method to specify the fields of the join in one location. If the join fields ever change, you must update the join in only one location. Before you can set a value for the **JoinRelation** property, you must delete the values of the **Field** and **RelatedField** properties.

### CreateNavigationPropertyMethods and RelatedTableRole

When you set the **CreateNavigationPropertyMethods** property to **Yes** on a table relation, the system generates navigation methods for the table buffer class. A navigation method links two table buffer instances by using their foreign key relationship. The **UnitOfWork** class is one area where this navigation linkage is used. The name of a navigation method is copied from the value of the **RelatedTableRole** property on the table relation. This behavior is used when the **RelatedTableRole** value is explicitly set in the **Properties** window, and when the system generates the **RelatedTableRole** value because the **UseDefaultRoleNames** property is set to **Yes**. The property values generate the following navigation method on the child CustTable buffer. Most directly, the navigation method name is copied from the value of the **RelatedTableRole** property.

    public final CustBankAccount BankAccounts([CustBankAccount relatedTable])

#### NavigationPropertyMethodNameOverride property

The following list describes cases where you must override the name that the system generates for a navigation method on a table buffer class:

-   The table class already has a method name that matches the values of the **RelatedTableRole** property.
-   The value of the **RelatedTableRole** property exceeds the maximum length that can be used for a method name.

In these cases, you must choose a valid name for the navigation method and assign that name as the value of the **NavigationPropertyMethodNameOverride** property on the table relation.

## Understanding the RelationshipType enumeration
When you add a node under table relations, you can set the value of the **RelationshipType** property for the new relation. The list of possible values for the **RelationshipType** property is the list of elements in the **RelationshipType** enumeration. This section describes the meaning of each element in the **RelationshipType** enumeration.

### Description of elements

The following table describes the elements of the **RelationshipType** property.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element name</th>
<th>Description</th>
<th>Automatic inference</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NotSpecified</td>
<td>This element is often the default value of the <strong>RelationshipType</strong> property.</td>
<td>When the <strong>RelationshipType</strong> property has a value of <strong>NotSpecified</strong>, the system infers an appropriate value. The system infers the value in the following sequence:
<ol>
<li>Specialization</li>
<li>Link</li>
<li>Composition</li>
<li>Aggregation</li>
<li>Association</li>
</ol>
For example, if the criteria for both Composition and Aggregation are met, the system infers Composition, because Composition occurs earlier in the list.</td>
</tr>
<tr class="even">
<td>Specialization</td>
<td>This element applies only to table inheritance, to relationships between base and derived tables.</td>
<td>The system sets the <strong>RelationshipType</strong> property to <strong>Specialization</strong> whenever table inheritance is involved.</td>
</tr>
<tr class="odd">
<td>Link</td>
<td>This element is a non-relational relationship. It requires that the <strong>Validate</strong> property be set to <strong>No</strong>. This type of relationship supports navigation between pages that list many records from a table and pages that provide detail fields for one record from the table.</td>
<td>Link is used only to support the migration of EDT link relations during upgrade from earlier versions. Migration tools create this type relationship, but you must not.</td>
</tr>
<tr class="even">
<td>Composition</td>
<td>This element is a stronger type of Aggregation relation. A table must not have more than one Composition relation. For example, a building is composed of rooms, and a given room can't exist in more than one building.</td>
<td>If the criteria for Composition are met, but you manually assign a value of <strong>Aggregation</strong> or <strong>Association</strong>, the system leaves the value as <strong>Aggregation</strong> or <strong>Association</strong>.</td>
</tr>
<tr class="odd">
<td>Aggregation</td>
<td>This element is appropriate when the child table is considered subordinate to the entity of the parent table.</td>
<td>The system infers Aggregation when one of the following conditions is true:
<ul>
<li>The parent table has a delete action node that is defined to use this relation node.</li>
<li>Any foreign key field for this relation in the child table has the <strong>Mandatory</strong> property set to <strong>Yes</strong>.</li>
</ul>
If the criteria for Aggregation are met, but you manually assign a value of <strong>Association</strong>, the system leaves the value as <strong>Association</strong>.</td>
</tr>
<tr class="even">
<td>Association</td>
<td>This element is the concept of a standard foreign key.</td>
<td>You must set the <strong>RelationshipType</strong> property to <strong>Association</strong> if the system doesn't set the value of the property to anything, and if both Aggregation and Composition are inappropriate.</td>
</tr>
</tbody>
</table>

## View properties
The properties for views are the same as the properties for tables. However, because views are read-only, most of their properties can't be changed. Some of these properties have fixed values, and some are inherited from the data sources that are used in the query that defines the view. The following properties for views are related to data analysis when you're using SSRS. All these properties can be changed.

-   AnalysisVisibility
-   AnalysisSelection
-   TypicalRowCount
-   IsLookup
-   SingularLabel

The following table describes the properties that can be set for a view.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AOSAuthorization</td>
<td>Use this property to specify which data access operations require verification of user permissions.</td>
</tr>
<tr class="even">
<td>CacheLookup</td>
<td>The record cache level for the table.</td>
</tr>
<tr class="odd">
<td>ClusterIndex</td>
<td>The cluster index of the table, if there is a cluster index.</td>
</tr>
<tr class="even">
<td>ConfigurationKey</td>
<td>Set the configuration key for the view.</td>
</tr>
<tr class="odd">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the menu is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="even">
<td>CountryRegionContextField</td>
<td>Specify the field that is used to identify the country/region context. See the description of the <strong>CountryRegionCodes</strong> property.</td>
</tr>
<tr class="odd">
<td>DeveloperDocumentation</td>
<td>Describe the purpose of a view, and explain how it's used in the program. Typically, a description contains no more than five sentences and is written as a single paragraph.</td>
</tr>
<tr class="even">
<td>EntityRelationshipType</td>
<td>Classify a view according to common entity relationship (ER) data model notation. A view is classified as either an entity or a relationship. An entity represents an object, whereas a relationship represents an association between two objects.</td>
</tr>
<tr class="odd">
<td>FormRef</td>
<td>Specify the default page for the view. The default page is the page that is shown when the user activates Jump to Main Table by using the shortcut menu for a field on a page. The page is referenced through a menu item of the <strong>Display</strong> type. If you leave this property blank, MorphX tries to activate a page that has the same name as the table that you're referring to.</td>
</tr>
<tr class="even">
<td>ID</td>
<td>The internal identifier of the object.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Specify a user-friendly name for the view.</td>
</tr>
<tr class="even">
<td>ListPageRef</td>
<td>Specify a display menu item that points to a page that can show a list of this record type.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the view is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Specify the name of the view. This name is used when you refer to the view from the X++ language.</td>
</tr>
<tr class="odd">
<td>PreviewPartRef</td>
<td>Specify the info part or form part to use in the enhanced preview. An info part shows a collection of data fields from a specified query. It uses metadata to describe how the data appears. A form part represents a pointer to a page.</td>
</tr>
<tr class="even">
<td>PrimaryIndex</td>
<td>Specify the primary index of the view. Only a unique index can be selected. This property is used for database optimization and to indicate which unique index should be used as the caching key. If you don't specify a primary index, the unique index that has the lowest ID is used as the caching key.</td>
</tr>
<tr class="odd">
<td>Query</td>
<td>Specify the query that is the source of data for the view. You can use this property instead of adding data sources directly to the view.</td>
</tr>
<tr class="even">
<td>ReportRef</td>
<td>The name of the default report for the table.</td>
</tr>
<tr class="odd">
<td>SaveDataPerCompany</td>
<td>Set this property to <strong>Yes</strong> for company-specific tables. Set it to <strong>No</strong> if the data is related to cross-companies, installation, a database, Application Explorer, tracing, or OLAP. For example, the SysTraceTable or OLAPServerTable table specifies whether data should be saved for that table on a per-company basis, or whether the data should be available without any company affiliation. If the <strong>SaveDataPerCompany</strong> property on a table is set to <strong>Yes</strong>, that table has a <strong>DataAreaId</strong> column that contains the company identifier. If the table property is set to <strong>No</strong>, the <strong>DataAreaId</strong> column is removed from the table.</td>
</tr>
<tr class="even">
<td>SaveDataPerPartition</td>
<td>A value that indicates whether the view has a system field that is named <strong>Partition</strong>. This property is intended to be read-only. If the view has a <strong>Partition</strong> field, each record is assigned to one partition. Each record is hidden from data access operations that are run under the context of other partitions.</td>
</tr>
<tr class="odd">
<td>SearchLinkRefName</td>
<td>The name of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results.</td>
</tr>
<tr class="even">
<td>SearchLinkRefType</td>
<td>The type of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results.</td>
</tr>
<tr class="odd">
<td>SystemTable</td>
<td>A value that indicates whether a table is a system table. System tables can be filtered during export and import, and are always synchronized when you sign in. Therefore, this property might be useful for tables that you use as soon as you sign in.</td>
</tr>
<tr class="even">
<td>TableContents</td>
<td>Specify how setup/parameter data can be reused from one customer to another. The following options are available:
<ul>
<li><strong>Not specified</strong> – Use this option for most tables.</li>
<li><strong>Default Data</strong> – Use this option for customer-independent data, such as postal codes, units, and time intervals.</li>
<li><strong>Base Data</strong> – Use this option for customer-dependent data, such as calendars, groups, and parameters.</li>
<li><strong>Default+Base data</strong> – Use this option for data where the local perception varies. For example, Chart of Accounts is customer-independent in Germany but is customer dependent in most other places.</li>
</ul></td>
</tr>
<tr class="odd">
<td>TableGroup</td>
<td>Specify the group that the view belongs to. Table groups categorize tables and views according to the type of data that they contain. Views can belong to the same table groups as a table.</td>
</tr>
<tr class="even">
<td>TitleField1, TitleField2</td>
<td>The information that is shown in the window caption for the view. The caption is constructed from the following elements:
<ul>
<li>The <strong>TitleField1</strong> label, followed by colon (:) and a space</li>
<li>The value of the current record in the column that is used for <strong>TitleField1</strong>, followed by a comma (,)</li>
<li>The value of the current record in the column that is used for <strong>TitleField2</strong></li>
</ul></td>
</tr>
<tr class="odd">
<td>ValidTimeStateEnabled</td>
<td>Specify whether the view supports the valid time state feature of the underlying table. The default value is <strong>No</strong>. You can set this property to <strong>Yes</strong> only if both the following conditions are true:
<ul>
<li>The underlying table is a valid time state table.</li>
<li>The view has <strong>ValidFrom</strong> and <strong>ValidTo</strong> in its <strong>Fields</strong> list.</li>
</ul></td>
</tr>
<tr class="even">
<td>Visible</td>
<td>Specify the access rights when the table is used as a data source on a page or a report. If the table is used as a data source on a page, the access rights on the page can't exceed the access rights that are defined for the table.</td>
</tr>
</tbody>
</table>

## Data set properties
This section contains descriptions of the properties on data set elements in Application Explorer. The **Data Sets** node is a high-level node in Application Explorer. Data sets are used to access data in Enterprise Portal.

### Description of properties

The following table describes the properties that are available on data set nodes in Application Explorer.

| Property | Description                   |
|----------|-------------------------------|
| Name     | Set the name of the data set. |

### Data Sources properties

The following table describes the properties for the **Data Sources** node of the data set.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ChangeGroupMode</td>
<td>Specify how changes to the data sources are committed. The following options are available:
<ul>
<li><strong>None </strong>– The changes to any data source for the data set are committed independently of changes to the other data sources.</li>
<li><strong>ImplicitInnerOuter </strong>– All the data sources that are inner-joined or outer-joined work as a single unit. All changes are committed successfully, or they are rolled back if an error occurs.</li>
</ul></td>
</tr>
</tbody>
</table>

## Data set data source properties
The following table describes the properties that are available for data set data sources.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AllowCheck</td>
<td>Specify whether security checks occur before the data set is accessed. The following options are available:
<ul>
<li><strong>Yes </strong>– The user's read permissions are verified before the data set is accessed.</li>
<li><strong>No </strong>– The user's read permissions are verified only after the data set is accessed. No data is retrieved if the user lacks sufficient permission for the underlying data sources.</li>
</ul>
<strong>Yes</strong> is the default value and is usually recommended.</td>
</tr>
<tr class="even">
<td>AllowCreate</td>
<td>Specify whether users can create new records in the data source (that is, in the table for the data source).</td>
</tr>
<tr class="odd">
<td>AllowDelete</td>
<td>Specify whether users can delete records in the data source (that is, in the table for the data source).</td>
</tr>
<tr class="even">
<td>AllowEdit</td>
<td>Specify whether users can modify the data. <strong>Tip:</strong> You can set the <strong>AllowEdit</strong> property for the whole data source here. The same property also exists on each field in the data source, so that you can prohibit modifications for individual fields.</td>
</tr>
<tr class="odd">
<td>AutoNotify</td>
<td>This property isn't used for data sets.</td>
</tr>
<tr class="even">
<td>AutoQuery</td>
<td>This property isn't used for data sets.</td>
</tr>
<tr class="odd">
<td>AutoSearch</td>
<td>This property isn't used for data sets.</td>
</tr>
<tr class="even">
<td>CounterField</td>
<td>Specify one of the fields in the data source as a counter for the data set. The field must be an index on the underlying table for the data source, and it must be of the <strong>real</strong> type. This property helps guarantee that a record that is inserted in a data set has a line number that corresponds to the actual sequential position in the data. For example, if a new line is inserted between lines 3 and 4, the new line becomes line number 3.5.</td>
</tr>
<tr class="odd">
<td>CrossCompanyAutoQuery</td>
<td>Specify whether the data source retrieves data from more than one company database.</td>
</tr>
<tr class="even">
<td>DelayActive</td>
<td>Use this property to delay execution of the active method for the data source. If you set this property to <strong>Yes</strong>, the active method is activated only after a delay of 20 milliseconds. When a user scrolls through a data source, the active method isn't called on every record. Instead. it's called only on the final record that the user selects. <strong>Tip:</strong> The <strong>DelayActive </strong>property is particularly useful when two data sources are linked (that is, when the <strong>LinkType</strong> property is set to <strong>Delayed</strong>). This property is part of the AutoJoin system.</td>
</tr>
<tr class="odd">
<td>Index</td>
<td>Set the index that is used to specify a sorting order. You can choose any of the indexes on the table. If you specify an index in this manner, it's used as an index hint on each query to the database. The index specifies both an access path and a sort order for the records in the data set, based on this data source. The initial sort order for the records is prioritized in this manner:
<ol>
<li>If sort fields are added to the data source query, the sort specification is used.</li>
<li>If an index is specified in the <strong>Index</strong> property on the data source, the sort order that is implicitly specified in that index is used.</li>
<li>If the data source is autojoined with another data source, the system finds the most appropriate index for this join and then sorts the data according to that index.</li>
<li>If nothing else is specified, the sort order that is implicitly specified in the first index (the index that has the lowest ID) on the table that is used in the page data source is used.</li>
</ol>
When no index hints are specified, the database management system locates an applicable access path. This access path is based on the information in the query that is supplied. The user can change the sort order for a page by using the query dialog box.</td>
</tr>
<tr class="even">
<td>InsertAtEnd</td>
<td>Specify whether a new record is created when the user moves focus past the last record in the table.</td>
</tr>
<tr class="odd">
<td>InsertIfEmpty</td>
<td>Specify whether a blank record is inserted if there are no records in the table. If you set this property to <strong>No</strong>, you must manually create a new record.</td>
</tr>
<tr class="even">
<td>JoinSource</td>
<td>Use this property to join two data sources. Set this property when two or more tables are used as the data source, and you want to join them.</td>
</tr>
<tr class="odd">
<td>LinkType</td>
<td>Use this property to maintain an active link between two data sources. When focus changes in the first data source, the corresponding record or records in the second data source are selected. For example, a customer table and a table of transactions is used for each customer. When the user scroll from one customer to the next, the transaction list is automatically updated to show transactions for the current customer. Set this property to <strong>Delayed</strong> for the outer (externally linked) data source. The linked data source is updated only after a delay of 100 milliseconds. This delay helps guarantee that the linked data source isn't updated while the user is scrolling through a data source. The update occurs only after the user finally focuses on a record. This property is part of the AutoJoin system.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Set the name of the data source. This name should be the same as the name of the underlying table.</td>
</tr>
<tr class="odd">
<td>OnlyFetchActive</td>
<td>Specify whether to fetch all fields in the data source or only those fields that are used by the data set. When this property is set to <strong>Yes</strong>, records can't be deleted from the data set. This restriction helps preserve data integrity, because it helps guarantee that a delete operation is never tried on incomplete records.</td>
</tr>
<tr class="even">
<td>OptionalRecordMode</td>
<td>Specify the create and delete behavior for records on an outer-joined table. The following options are available:
<ul>
<li><strong>ImplicitCreate</strong> – When no record is saved in the database, create an outer-joined record and joined tables as soon as the parent record becomes active. If the outer-joined record or its children aren't changed, they will be deleted when the parent record is no longer active.</li>
<li><strong>ExplicitCreate</strong> – When no record is saved in the database, treat this record as disabled until the user explicitly triggers creation by using the <strong>Optional Record</strong> check box. When the record exists, clearing the check box will delete this record.</li>
<li><strong>None</strong> – No special create or delete behavior occurs for an outer-joined record.</li>
</ul></td>
</tr>
<tr class="odd">
<td>StartPosition</td>
<td>Specify whether the first record or the last record should be the current record when the data set is accessed.</td>
</tr>
<tr class="even">
<td>Table</td>
<td>Set the table that is used as the data source.</td>
</tr>
<tr class="odd">
<td>ValidTimeStateAutoQuery</td>
<td>Specify the types of queries for date effectivity (<strong>AsOfDate</strong> or <strong>DateRange</strong>).</td>
</tr>
<tr class="even">
<td>ValidTimeStateUpdate</td>
<td>Specify the types of updates for an existing date-effective record. The following options are available:
<ul>
<li><strong>CreateNewTimePeriod </strong>– On the record that is becoming the previous record, the <strong>ValidTo</strong> date field is set to a date that is no later than the current date. In the same transaction, the new current record has its <strong>ValidFrom</strong> field set to immediately after <strong>ValidTo</strong> date of the previous record.</li>
<li><strong>Correction </strong>– The <strong>ValidFrom</strong> or <strong>ValidTo</strong> value of existing rows must be modified to keep the date-effective data valid after the record set is updated.</li>
<li><strong>EffectiveBased </strong>– Records in the past can't be edited. Records that are currently active are edited in a manner that resembles CreateNewTimePeriod mode. Future records are edited in a manner that resembles Correction mode.</li>
</ul>
The default value is <strong>CreateNewTimePeriod</strong>.</td>
</tr>
</tbody>
</table>

## Form properties
This section describes the properties that you set on forms in Application Explorer. To provide a uniform application interface, many properties have **Auto** values. You can create forms by using a drag-and-drop operation and then manually setting several properties. To specify the name of a form, you set the **Name** property in the **Properties** window for the form. All other properties on the top-level node for the form are system properties and are read-only.

## Form design properties
Most properties on the **Design** node for a form also exist on the individual controls. Examples include the **Width** and **Height** properties. However, when you set a property on the **Design** node instead of setting it on a control, the setting affects the whole form. A few properties exist only on the **Design** node. The following table describes these properties.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AlignChild</td>
<td>Specify whether a control within a group follows the <strong>AlignChildren</strong> property setting for the group or for the overall form design. For example, <strong>AlignChildren</strong> is set to <strong>Yes</strong> on the <strong>Design</strong> node for the form, but you don't want a particular group to be arranged together with the other groups. In this case, set <strong>AlignChild</strong> to <strong>No</strong> for that group.</td>
</tr>
<tr class="even">
<td>AlignChildren</td>
<td>Align the child controls within a container.</td>
</tr>
<tr class="odd">
<td>AllowDocking</td>
<td>Specify whether a form can be attached to the client workspace. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>AllowFormCompanyChange</td>
<td>Specify whether the form supports company changes when it's used as a child form with a cross-company dynamic-link library (DLL). The default value is <strong>No</strong>.</td>
</tr>
<tr class="odd">
<td>AllowUserSetUp</td>
<td>Specify whether a user can move controls on a form and can change the value of control properties. This property is also found on the design of a form. The following options are available:
<ul>
<li><strong>No </strong>– Users can't customize any controls in this container.</li>
<li><strong>Restricted </strong>– Users can change properties of individual controls, but they can't move controls.</li>
<li><strong>Yes </strong>– There are no restrictions on the user setup.</li>
</ul>
The default value is <strong>Yes</strong>. <strong>Caution:</strong> Full user setup isn't allowed if any of the parent containers for the control have restrictions on the user setup level. The <strong>AllowAdd</strong> property on form data sources determines whether a user can add a field to a form.</td>
</tr>
<tr class="even">
<td>AlwaysOnTop</td>
<td>Specify whether the form always appears on top of other windows in the z-order. The default value is <strong>No</strong>.</td>
</tr>
<tr class="odd">
<td>ArrangeMethod</td>
<td>Specify whether to arrange child field groups in columns or in rows.</td>
</tr>
<tr class="even">
<td>ArrangeWhen</td>
<td>Specify when the controls in the container should be arranged. The following options are available:
<ul>
<li>Startup</li>
<li>On demand</li>
<li>Never</li>
<li>Default</li>
<li>Auto</li>
</ul>
The default value is <strong>Startup</strong>.</td>
</tr>
<tr class="odd">
<td>BackgroundColor</td>
<td>Specify the color that is used for the background of the control. To make the background opaque or transparent, use the <strong>BackStyle</strong> property.</td>
</tr>
<tr class="even">
<td>BottomMargin</td>
<td>Set the bottom margin of the form in pixels. The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>Caption</td>
<td>Specify the heading for grouped controls. Use a label for this property.</td>
</tr>
<tr class="even">
<td>ColorScheme</td>
<td>Specify the color palette for the control. To change the color palette for the whole form, set the <strong>ColorScheme</strong> property for the largest container, and keep the default values for the individual controls.</td>
</tr>
<tr class="odd">
<td>Columns</td>
<td>Specify the number of columns that show the information. <strong>Caution:</strong> Field groups on the underlying table are never split into more than one column.</td>
</tr>
<tr class="even">
<td>ColumnSpace</td>
<td>Set the amount of space between columns in container controls.</td>
</tr>
<tr class="odd">
<td>DataSource</td>
<td>Specify the table that data in the control comes from. To set a particular field within the table, use the <strong>DataField</strong> property. If the control opens another form, relations between the data source for the control, as specified by this property, and the data source on the other form help guarantee that records in the second form are dynamically selected. For example, a customer is selected in one form, and the control opens a form that shows customer transactions. In this case, the second form shows a range of customer transactions that apply to the current customer. <strong>Caution:</strong> If you set the <strong>DataSource</strong> and <strong>DataField</strong> properties, their settings override any settings for the <strong>DataMethod</strong> or <strong>ExtendedDataType</strong> properties.</td>
</tr>
<tr class="even">
<td>Font</td>
<td>Change the font properties for the control by using the <strong>Font</strong> dialog box. Use the dialog font to specify the font, font style, and font size.</td>
</tr>
<tr class="odd">
<td>Frame</td>
<td>Specify the frame style that the form uses.</td>
</tr>
<tr class="even">
<td>Height</td>
<td>Specify the height of the form or control in pixels.</td>
</tr>
<tr class="odd">
<td>HideIfEmpty</td>
<td>Use this property to hide a container control if it's empty. This property has no affect if the <strong>Width</strong> and <strong>Height</strong> properties of the container are set to <strong>Auto</strong>, because the size of the control is 0 (zero) in this case.</td>
</tr>
<tr class="even">
<td>HideToolBar</td>
<td>Hide form-specific buttons on the toolbar.</td>
</tr>
<tr class="odd">
<td>ImageMode</td>
<td>Define how the bitmap that is specified by the <strong>ImageName</strong> property appears in a control. The following options are available:
<ul>
<li>Normal</li>
<li>Size to fit</li>
<li>Side by side</li>
<li>Center</li>
</ul>
The default value is <strong>Normal</strong>.</td>
</tr>
<tr class="even">
<td>ImageName</td>
<td>Specify the image that is shown for a control. You can select only .bmp files. To use one of the resource files, use the <strong>ImageResource</strong> property instead.</td>
</tr>
<tr class="odd">
<td>ImageResource</td>
<td>Use one of the images from the image resource file as the image for a control. Specify the ID of the image. You can select only an image from the integrated resource file. To use another file type, use the <strong>ImageName</strong> property.</td>
</tr>
<tr class="even">
<td>LabelFont</td>
<td>Change the font for the text that is supplied in the <strong>Label</strong> property.</td>
</tr>
<tr class="odd">
<td>Left</td>
<td>Change the position of the upper-left corner of the form. There are several predefined settings. You can also specify an exact position in pixels. The following predefined settings are available:
<ul>
<li>Auto (left)</li>
<li>Auto (right)</li>
<li>Left edge</li>
<li>Right edge</li>
<li>Center</li>
</ul>
The default value is <strong>Auto (left)</strong>.</td>
</tr>
<tr class="even">
<td>LeftMargin</td>
<td>Change the default left margin of the form. The margin is specified in pixels.</td>
</tr>
<tr class="odd">
<td>MaximizeBox</td>
<td>Specify whether to include the maximize box in the upper-right corner of the enclosing window. The default value is <strong>Yes</strong>.</td>
</tr>
<tr class="even">
<td>MinimizeBox</td>
<td>Specify whether to include the minimize box in the upper-right corner of the enclosing window. The default value is <strong>Yes</strong>.</td>
</tr>
<tr class="odd">
<td>Mode</td>
<td>Specify the data entry mode for the form.</td>
</tr>
<tr class="even">
<td>Model</td>
<td>Specify the model that the form is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="odd">
<td>RightMargin</td>
<td>Change the default right margin of the form. The margin is specified in pixels.</td>
</tr>
<tr class="even">
<td>SaveSize</td>
<td>Set this property to <strong>Yes</strong> to save the size of the form.</td>
</tr>
<tr class="odd">
<td>ScrollBars</td>
<td>Specify whether scroll bars are enabled in the form.</td>
</tr>
<tr class="even">
<td>SetCompany</td>
<td>Cause the system to change the company when the form receives focus. <strong>Note:</strong> If the <strong>SaveDataPerCompany</strong> property on a table is set to <strong>Yes</strong>, the <strong>SetCompany</strong> property on a form design that uses the table as a data source must also be set to <strong>Yes</strong>.</td>
</tr>
<tr class="odd">
<td>StatusBarStyle</td>
<td>Specify how the status bar appears in a form. Use this property to hide the status bar, show only Help information, show status bar elements according to the <strong>WindowType</strong> setting, or always show the full status bar. <strong>Note:</strong> Forms that have a WindowType setting of <strong>ListPage</strong>, <strong>ContentPage</strong>, or <strong>Workspace</strong> ignore this property.</td>
</tr>
<tr class="even">
<td>Style</td>
<td>Specify the style of the form. This property controls the form design pattern that is used for the form. The following options are available:
<ul>
<li>Auto</li>
<li>DetailsFormMaster</li>
<li>DetailsFormTransaction</li>
<li>Dialog</li>
<li>DropDialog</li>
<li>FormPart</li>
<li>ListPage</li>
<li>Lookup</li>
<li>SimpleList</li>
<li>SimpleListDetails</li>
<li>TableOfContents</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>TitleDataSource</td>
<td>Specify the data source to use in the form caption.</td>
</tr>
<tr class="even">
<td>Top</td>
<td>Change the position of the top of the form. There are several predefined settings. You can also specify an exact position in pixels. The following predefined settings are available:
<ul>
<li>Auto</li>
<li>Top edge</li>
<li>Bottom edge</li>
<li>Center</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>TopMargin</td>
<td>Set the top margin of the form in pixels. The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>UseCaptionFromMenuItem</td>
<td>Specify whether to replace the form caption with the label from the calling menu item. This property enables the caption of the form to be changed when the form is opened. The default value is <strong>No</strong>.</td>
</tr>
<tr class="odd">
<td>ViewEditMode</td>
<td>Specify whether the form opens in read-only mode or as a form that allows you to change fields. The following options are available:
<ul>
<li><strong>View </strong>– Open the form as read-only.</li>
<li><strong>Edit </strong>– Open the form in edit mode.</li>
<li><strong>Auto </strong>– Open the form in the appropriate mode.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>Visible</td>
<td>Use this property to hide the form. <strong>Caution:</strong> You can't use the <strong>Visible</strong> property to enforce access restrictions. The user can change the visibility for the controls in the <strong>Form Setup</strong> dialog box. To enforce access restrictions, use the <strong>Enabled</strong> and <strong>NeededAccessLevel</strong> properties instead.</td>
</tr>
<tr class="odd">
<td>Width</td>
<td>Change the width of the form in pixels.</td>
</tr>
<tr class="even">
<td>WindowResize</td>
<td>Specify whether the form can be resized.</td>
</tr>
<tr class="odd">
<td>WindowType</td>
<td>Specify the type of window.</td>
</tr>
<tr class="even">
<td>WorkflowDataSource</td>
<td>Set the root data source for the workflow on a form. The root data source that you specify should be the same root data source that is specified in the query that used for the <strong>Document</strong> property on the workflow template.</td>
</tr>
<tr class="odd">
<td>WorkflowEnabled</td>
<td>Set this property to <strong>Yes</strong> to enable the workflow menu bar on the form. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>WorkflowType</td>
<td>Specify the workflow type, which determines the following items and behaviors:
<ul>
<li>The workflow document to use. The workflow document exposes calculated fields and identifies the query that exposes data fields for the workflow.</li>
<li>Whether the user can configure tasks and approvals.</li>
<li>The workflow categories to use when a workflow type is assigned to a specific module.</li>
<li>Menu items and event handlers.</li>
</ul></td>
</tr>
</tbody>
</table>

## Help document set properties
A document set is a collection of Help documentation that is associated with a workspace. When you publish a content element, you use metadata to add your content element or table of contents information to a document set. To manage the relationship between a workspace and a document set, Application Explorer includes a node that is named **Help Document Sets**. Each document set in the **Help Document Sets** node includes a collection of properties. You edit these properties when you add a new document set or change the relationship between a document set and a workspace. **Caution:** A workspace can be associated with only one document set. Although Application Explorer lets you add a new document set and associate it with a workspace, you will no longer see documentation from the document set that you replaced. Typically, you use **UserDocumentation** as the document set for any content element or table of contents entries that you publish to the Help server. The following table describes the properties for a document set in the **Help Document Sets** node of Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>DocumentSetName</td>
<td>String</td>
<td>A name that uniquely identifies the document set. The name is limited to 40 characters and must not contain whitespace. Use the value of this property when you set the value of the <strong>DocumentSets</strong> metadata element in a content element or table of contents file.</td>
</tr>
<tr class="even">
<td>DocumentSetDescription</td>
<td>String</td>
<td>The text or label to display for the document set. This value appears in the <strong>Search content from</strong> list of the <strong>Options</strong> menu of the Help viewer.</td>
</tr>
<tr class="odd">
<td>AddToApplicationHelpMenu</td>
<td>Boolean</td>
<td>Set this property to <strong>Yes</strong> if you want the document set to appear on the <strong>Help</strong> menu of the application workspace.</td>
</tr>
<tr class="even">
<td>AddToDeveloperHelpMenu</td>
<td>Boolean</td>
<td>Set this property to <strong>Yes</strong> if you want the document set to appear on the <strong>Help</strong> menu of the developer workspace.</td>
</tr>
<tr class="odd">
<td>UserDocumentSet</td>
<td>Boolean</td>
<td>Set this property to <strong>Yes</strong> to associate the document set with the application workspace. If you set this property to <strong>No</strong>, you can't view the context-sensitive (F1) Help that was published by Microsoft.</td>
</tr>
<tr class="even">
<td>DeveloperDocumentSet</td>
<td>Boolean</td>
<td>Set this property to <strong>Yes</strong> to associate the document set with the development workspace. If you set this property to <strong>No</strong>, you can't view the context-sensitive (F1) Help that was published by Microsoft.</td>
</tr>
<tr class="odd">
<td>ContentLocation</td>
<td>Enumeration</td>
<td>An enumeration value that specifies where to retrieve documentation. The following table describes the enumeration.
<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Label</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1</td>
<td>Help server</td>
<td>The documentation is stored on the Help server. This option is used together with the <strong>UserDocumentation</strong> document set and any document set that files have been published for on the Help server.</td>
</tr>
<tr class="even">
<td>2</td>
<td>World Wide Web</td>
<td>The documentation is stored on MSDN or a similar website. This option is required for the <strong>DeveloperDocumentation</strong> documentation set and should not be used with any other document set.</td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

## Menu properties
The following table describes the properties that are available for menus under the **Menus** node in Application Explorer.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Set the configuration key for the menu.</td>
</tr>
<tr class="even">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the menu is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="odd">
<td>DisabledImage</td>
<td>Specify the button image that is used when the menu is disabled. If this property isn't set, the system uses the setting of the <strong>NormalImage</strong> property to generate an image.</td>
</tr>
<tr class="even">
<td>DisabledImageLocation</td>
<td>Specify the location of the image that is used for a disabled control. You can use images from a file, the <strong>Resources</strong> node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the <strong>DisabledImage</strong> property. If the property isn't set, the system uses the setting of the <strong>ImageLocation</strong> property to generate an image.</td>
</tr>
<tr class="odd">
<td>ImageLocation</td>
<td>Specify the location of the image that is used. You can use images from a file, the <strong>Resources</strong> node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the <strong>NormalImage</strong> property.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Set the name of the menu that is shown to the user.</td>
</tr>
<tr class="odd">
<td>MenuItemName</td>
<td>Specify the menu item to include on the menu. The values that are available depend on the value of the <strong>MenuItemType</strong> property.</td>
</tr>
<tr class="even">
<td>MenuItemType</td>
<td>Specify the type of the menu item. There are three categories of menu items:
<ul>
<li>Display</li>
<li>Output</li>
<li>Action</li>
</ul>
The value that you set for this property determines the list of menu item names that appears in the list for the <strong>MenuItemName</strong> property.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the menu is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can be located in exactly one model in a layer. The same element can be located in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>NormalImage</td>
<td>Specify the image that is used when the menu is enabled.</td>
</tr>
<tr class="odd">
<td>Parameters</td>
<td>Specify one or more values that are passed to an object. These values resemble the parameters that are passed to a method. A parameter supplies a value that is then used to perform the task. There is no default value.</td>
</tr>
<tr class="even">
<td>SetCompany</td>
<td>If you set this property to <strong>Yes</strong>, every time that the menu is opened, the company is changed to the company that was specified when the menu was first started.</td>
</tr>
<tr class="odd">
<td>Shortcut</td>
<td>Specify the keyboard shortcut that opens the menu. For example, you can press Ctrl+F3 to open the menu. There is no default value.</td>
</tr>
<tr class="even">
<td>ShowParentModule</td>
<td>Specify whether to update the navigation pane, based on the parent module of the menu item. The following options are available:
<ul>
<li><strong>Yes </strong>– Always update the navigation pane, based on the parent module of the menu item.</li>
<li><strong>No </strong>– Leave the navigation pane unchanged, even if the parent module of the menu item differs from the current module.</li>
</ul>
The default value is <strong>Yes</strong>.</td>
</tr>
</tbody>
</table>

## Menu item properties
The following properties are available for all menu items (display, output, and action), even menu items that are used for web menus.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Select the configuration key that is required in order to enable the menu item. Use the key for the module that the object belongs to.</td>
</tr>
<tr class="even">
<td>CopyCallerQuery</td>
<td>Specify whether to copy the query from the calling form to the target form. This property enables the target form to show the same data that was viewed in the original form. The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>CorrectPermissions</td>
<td>Specify whether correct permission should be available for selection when privileges are assigned to the menu item. The following options are available:
<ul>
<li><strong>Auto </strong>– The permission will be available for selection as a privilege on this menu item's <strong>Privileges</strong> node under the <strong>Entry Points</strong> node.</li>
<li><strong>No </strong>– The permission won't be available for selection as a privilege on the menu item.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>CountryConfigurationKey</td>
<td>Optional: Set a country/region-specific key in addition to or instead of a standard configuration key.</td>
</tr>
<tr class="odd">
<td>CountryRegionCodes</td>
<td>Specify the codes for the countries/regions where the menu item is valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country/region-specific features.</td>
</tr>
<tr class="even">
<td>CreatePermissions</td>
<td>Specify whether create permission should be available for selection when privileges are assigned to the menu item. The following options are available:
<ul>
<li><strong>Auto </strong>– The permission will be available for selection as a privilege on this menu item's <strong>Privileges</strong> node under the <strong>Entry Points</strong> node.</li>
<li><strong>No </strong>– The permission won't be available for selection as a privilege on the menu item.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>DeletePermissions</td>
<td>Specify whether delete permission should be available for selection when privileges are assigned to the menu item. The following options are available:
<ul>
<li><strong>Auto </strong>– The permission will be available for selection as a privilege on this menu item's <strong>Privileges</strong> node under the <strong>Entry Points</strong> node.</li>
<li><strong>No </strong>– The permission won't be available for selection as a privilege on the menu item.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>DisabledImage</td>
<td>Specify the image that is used when the menu item is disabled. If this property isn't set, the system uses the setting of the <strong>NormalImage</strong> property to generate an image.</td>
</tr>
<tr class="odd">
<td>DisabledImageLocation</td>
<td>Specify the location of the image that is used for a disabled control. You can use images from a file, the <strong>Resources</strong> node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the <strong>DisabledImage</strong> property. If the property isn't set, the system uses the setting of the <strong>ImageLocation</strong> property to generate an image.</td>
</tr>
<tr class="even">
<td>EnumTypeParameter and EnumParameter</td>
<td>Optional: Select an enumerated type as a parameter for the object, and then select an enumeration value as the value of the <strong>EnumParameter</strong> property. Typically, these properties are used when one form is used in several situations. You can change the behavior of the form, depending on the <strong>EnumParameter</strong> value. For example, the <strong>PriceDiscGroup</strong> form is used by three display menu items (<strong>PriceDiscGroup_*</strong>), each of which has a different <strong>EnumParameter</strong> value. In the form's <strong>init</strong> method, a switch construct validates the value, and then the form is created.</td>
</tr>
<tr class="odd">
<td>ExtendedDataSecurity</td>
<td>Specify whether the menu item appears under all companies instead of in the context of a single company. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>FormViewOption</td>
<td>Specify the form mode to use. The following options are available:
<ul>
<li>Auto</li>
<li>Grid</li>
<li>Details</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>HelpText</td>
<td>Create a Help string for the menu item. The text appears on the status bar when you select the object that is opened by the menu item (for example, a form). <strong>Note:</strong> To write a Help topic for the menu item, in Application Explorer, in the <strong>Application Documentation/Menu Items</strong> node, find the topic that has the same name as your menu item. This topic will then be shown instead of any Help topic that was written about the object that is opened by the menu item.</td>
</tr>
<tr class="even">
<td>ImageLocation</td>
<td>Specify the location of the image that is used for a control. You can use images from a file, the <strong>Resources</strong> node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the <strong>NormalImage</strong> property.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Select the label to use as the name that appears for the item on menus and buttons.</td>
</tr>
<tr class="even">
<td>LinkedPermissionObject</td>
<td>If the permissions of another object (for example, a form or report) should be applied to this menu item, select the object. Typically, this property is used for action menu items.</td>
</tr>
<tr class="odd">
<td>LinkedPermissionType</td>
<td>Specify the type of the object that is specified by the <strong>LinkedPermissionObject</strong> property.</td>
</tr>
<tr class="even">
<td>MultiSelect</td>
<td>Select whether the menu item can be used on multiple record selections in forms.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can be located in exactly one model in a layer. The same element can be located in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>The name of the menu item.</td>
</tr>
<tr class="odd">
<td>NeededAccessLevel</td>
<td>Define the minimum access that is required for the menu item to appear on a menu or a button. This property is used to set access to the menu item for different user groups.</td>
</tr>
<tr class="even">
<td>NeedsRecord</td>
<td>Specify whether a button that represents the menu item is enabled if no record is present. The default value is <strong>No</strong>. You can use this property to help guarantee that an action can be completed. For example, you have a menu item button that opens a detail form. You might want to disable the button if there are no records on the list page.</td>
</tr>
<tr class="odd">
<td>NormalImage</td>
<td>Specify the image that is used when the menu item is associated with an enabled button control.</td>
</tr>
<tr class="even">
<td>Object</td>
<td>Select an object of the object type that is specified in the <strong>Class</strong> property.</td>
</tr>
<tr class="odd">
<td>ObjectType</td>
<td>Select the type of object that the menu item opens. <strong>Caution:</strong> You should use <strong>SSRSReport</strong> for a menu item for an SSRS report. Don't use <strong>SQLReportLibraryReport</strong> for new menu items. The <strong>SQLReportLibraryReport</strong> option is obsolete and will be removed in a future version.</td>
</tr>
<tr class="even">
<td>OpenMode</td>
<td>Specify the view mode of the target form. You use this property to specify whether the target form opens in edit mode or read-only mode. The following options are available:
<ul>
<li>Auto</li>
<li>View</li>
<li>Edit</li>
<li>New</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>Parameters</td>
<td>Optional: Specify the arguments that are passed to the object.</td>
</tr>
<tr class="even">
<td>Query</td>
<td>Select the query that is passed to the target form for the <strong>IntialQuery</strong> method.</td>
</tr>
<tr class="odd">
<td>ReadPermissions</td>
<td>Specify whether read permission should be available for section when privileges are assigned to the menu item. The following options are available:
<ul>
<li><strong>Auto </strong>– The permission will be available for selection as a privilege on this menu item's <strong>Privileges</strong> node under the <strong>Entry Points</strong> node.</li>
<li><strong>No </strong>– The permission won't be available for selection as a privilege on the menu item.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>ReportDesign</td>
<td>Select the report design to use for a specific SSRS report model.</td>
</tr>
<tr class="odd">
<td>RunOn</td>
<td>Select whether to run the menu item on the client, the server, or the the location that it's called from. This property is mainly used for menu items that open reports. This property determines where the application object is run from only if the <strong>RunOn</strong> property of the object is set to <strong>Called from</strong>.
<ul>
<li>A form is instantiated and run on the client, because the <strong>FormRun</strong> class always runs on the client.</li>
<li>A report is instantiated and run as specified by the menu item's <strong>RunOn</strong> property, because the <strong>ReportRun</strong> class always runs where it was called from. You should set the property to <strong>Called from</strong>. If you set the report to run on the client, and the report is run in a batch, the report will fail. If you set the report to run on the server, and the report is shown on the screen, the report will fail.</li>
<li>A class's <strong>main</strong> method is run as specified by its modifier. The class itself is instantiated as specified by its <strong>RunOn</strong> property. The instantiation might occur in the <strong>main</strong> method.</li>
</ul></td>
</tr>
<tr class="even">
<td>UpdatePermissions</td>
<td>Specify whether update permission should be available for section when privileges are assigned to the menu item. The following options are available:
<ul>
<li><strong>Auto </strong>– The permission will be available for section as a privilege on this menu item's <strong>Privileges</strong> node under the <strong>Entry Points</strong> node.</li>
<li><strong>No </strong>– The permission won't be available for section as a privilege on the menu item.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>Web</td>
<td>Specify the URL that is opened when you run the menu item. The value of this property is no longer used. Don't use this property.</td>
</tr>
<tr class="even">
<td>WebConfigurationKey</td>
<td>Optional: Select a web-specific configuration key in addition to a standard configuration key. This property applies to web menu items only.</td>
</tr>
<tr class="odd">
<td>WebMenuItemName</td>
<td>Specify the menu item to include on a web menu. The available values depend on the setting of the <strong>WebMenuItemType</strong> property.</td>
</tr>
<tr class="even">
<td>WebMenuItemType</td>
<td>Specify the type of the web menu item. There are two categories of web menu items:
<ul>
<li>URL</li>
<li>Action</li>
</ul>
The value that you select determines the web menu item names that are available for the <strong>WebMenuItemName</strong> property.</td>
</tr>
<tr class="odd">
<td>WebPage</td>
<td>Specify the webpage that is linked to the menu item. The value of this property is no longer used. Don't use this property.</td>
</tr>
<tr class="even">
<td>WebSecureTransaction</td>
<td>Select whether the menu item requires secure transactions (SSL). This property applies to web menu items only.</td>
</tr>
</tbody>
</table>

**Note:** When you use the **Parameters** or **EnumParameter** property, errors such as type mismatches can be found only at run time, not at compile time.

## Query properties
Within a query, you can set properties on the query itself, the data sources, the fields that are used for sorting, and the ranges that are used to delimit the query.

### Query properties

Query properties determine the overall behavior of the query. For example, you can specify the form that is shown to users so that they can interact with the query.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AllowCheck</td>
<td>This property is ignored for queries. It's effective on forms and reports.</td>
</tr>
<tr class="even">
<td>AllowCrossCompany</td>
<td>Specify whether data is retrieved for all companies that the user has authority to read from. If the property is set to <strong>false</strong>, which is the default value, data is retrieved only for the current session company.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Optional: Describe the query, what it returns, and so on. This property is useful in Microsoft Office Add-in scenarios.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Specify that query form that MorphX should show when users interact with the query. The default value is <strong>SysQueryForm</strong>.</td>
</tr>
<tr class="odd">
<td>Interactive</td>
<td>Specify whether users can interact with the report by delimiting queries, setting printer options, and so on.</td>
</tr>
<tr class="even">
<td>Literals</td>
<td>Specify how literals are represented in SQL statements. The <strong>forceLiterals</strong> option instructs the kernel to reveal the actual values that are used in <strong>where</strong> clauses to the Microsoft SQL Server database at the time of optimization. The <strong>forcePlaceholders</strong> option instructs the kernel not to reveal the actual values. <strong>Note:</strong> We don't recommend that you use the <strong>forceLiterals</strong> option, because it could expose code to an SQL injection security threat.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the query is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="even">
<td>QueryType</td>
<td>Specify the type of the query. The following options are available:
<ul>
<li>Join</li>
<li>Union</li>
</ul>
The default value is <strong>Join</strong>.</td>
</tr>
<tr class="odd">
<td>Searchable</td>
<td>Specify whether the query can be part of a set of queries that is used to search the Microsoft SharePoint Business Catalog. This property is useful when you use the Enterprise Search feature. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>Title</td>
<td>The heading for the query.</td>
</tr>
<tr class="odd">
<td>UserUpdate</td>
<td>Specify whether the query form should retain its state when it's reopened. If you set this property to <strong>Yes</strong>, the previous settings are restored. If you set it to <strong>No</strong>, the data can be viewed but not edited.</td>
</tr>
<tr class="even">
<td>Version</td>
<td>The version is increased every time that the query is updated. This property is read-only.</td>
</tr>
</tbody>
</table>

### Data source properties

The following properties control the characteristics of a data source. Additional properties are available on embedded data sources and relations between data sources. You can also set one property on fields in the data source.

| Property            | Where it's available                 | Description                                                                                                                                                                                                                                                                                                                        |
|---------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowAdd            | Data source                          | Specify whether users can add fields to sorting and ranges at run time.                                                                                                                                                                                                                                                            |
| Company             | Data source                          | Specify the company to retrieve data from.                                                                                                                                                                                                                                                                                         |
| Dynamic             | Fields node in a data source         | Specify whether all fields in the table in the data source are used. If you set this property to **Yes**, all the fields in the data source are used. If you set it to **No**, you can remove some of the fields. When the data source is a base table, a value of **Yes** means that all fields from the derived tables are used. |
| Enabled             | Data source                          | If you set this property to **No**, the data source (and all embedded data sources) are ignored.                                                                                                                                                                                                                                   |
| FetchMode           | Embedded data source                 | Specify whether the data sources should be related through a 1:1 relation or a 1:n relation. **Note:** For data sources that are used on reports, use a join relation that uses 1:1 fetch mode.                                                                                                                                    |
| Field, RelatedField | Relations on an embedded data source | The name of the fields from the parent data source and related data source that are used in the relation.                                                                                                                                                                                                                          |
| FirstFast           | Data source                          | If you set this property to **Yes**, the database receives a hint that the first record from the query should be retrieved before the other records. This setting enables some database systems to optimize record retrieval and therefore helps improve performance.                                                              |
| FirstOnly           | Data source                          | If you set this property to **Yes**, the database receives a hint that only the first record from the query is required. This setting enables some database systems to optimize record retrieval and therefore helps improve performance.                                                                                          |
| JoinMode            | Embedded data source                 | Specify the strategy that is used to join the output from a data source.                                                                                                                                                                                                                                                           |
| Name                | Data source                          | Specify the name of the data source.                                                                                                                                                                                                                                                                                               |
| Relations           | Embedded data source                 | Specify whether the query system should use the relations that are defined for tables and EDTs. If you set this property to **Yes**, the query is automatically updated if a relation is changed.                                                                                                                                  |
| Table               | Data source                          | Specify the table, map, or view that is used as a data source. This property can't be modified after a sorting order or a range has been defined.                                                                                                                                                                                  |
| Table, RelatedTable | Relations on an embedded data source | The name of the parent data source and the related data source.                                                                                                                                                                                                                                                                    |
| UniqueId            | Data source                          | The unique number of the data source. This property is read-only.                                                                                                                                                                                                                                                                  |
| Update              | Data source                          | Specify whether the query can update records in the database.                                                                                                                                                                                                                                                                      |

### Range properties

The following properties determine the characteristics of the range specification. For example, you can specify whether users are allowed to modify the range at run time.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Enabled</td>
<td>Use this property to disable a field in a range specification.</td>
</tr>
<tr class="even">
<td>Field</td>
<td>Specify the field to define a range on.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Enter a label for the range.</td>
</tr>
<tr class="even">
<td>Status</td>
<td>Specify whether users are allowed to modify the range in the query dialog box at run time. The following options are available:
<ul>
<li><strong>Open</strong> – Users can view and edit the range.</li>
<li><strong>Lock</strong> – Users can only view the range.</li>
<li><strong>Hide</strong> – Users can't view or edit the range.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Value</td>
<td>Specify the range for the records that are retrieved. If you use enumerations, don't use text strings. The enumeration ID must be used.</td>
</tr>
</tbody>
</table>

## Report properties
Most of the properties for a report are set on the design, design section, and control nodes in Application Explorer. For information about system properties that are available on reports, see the "System and common properties" section. The following table describes the properties of a report.

| Property    | Description                                                                                                                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowCheck  | Specify whether a message is shown when users try to run reports that they don't have permission to view. Select **Yes** to specify that a message is shown.                                                                                 |
| AutoJoin    | Specify whether a record that is returned by the **element.args** method is used to set the range on the report query.                                                                                                                       |
| Interactive | Specify whether users can select which records to show by modifying the query that is associated with a report.                                                                                                                              |
| Model       | Specify the model that the report is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in another layer. |

## Report control properties
The following table describes report control properties. For information about additional properties that are available for controls, see the "Form control properties" section.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alignment</td>
<td>Specify the alignment of a value that is shown in a control.</td>
</tr>
<tr class="even">
<td>AllowNegative</td>
<td>Specify whether the control accepts negative values. This property is available only for integer and real controls.</td>
</tr>
<tr class="odd">
<td>ArrayIndex</td>
<td>Specify the array element that is shown in a control. The control is based on an extended data type that has array elements. This property isn't available for text and shape controls.</td>
</tr>
<tr class="even">
<td>AutoDeclaration</td>
<td>Specify whether a variable is created that has the same name as the control. When you set this property to <strong>Yes</strong>, it's easier to access the report controls from X++ code, and you can find errors at compile time.</td>
</tr>
<tr class="odd">
<td>AutoInsSeparator</td>
<td>Specify whether a decimal separator is shown. This property is available only for real controls.</td>
</tr>
<tr class="even">
<td>BackgroundColor</td>
<td>Specify the background color for a control. The setting of this property can be overridden by using the <strong>BackStyle</strong> property.</td>
</tr>
<tr class="odd">
<td>BackStyle</td>
<td>Specify whether the control background is opaque or transparent. When you set this property to <strong>Transparent</strong>, the behavior depends on the type of control:
<ul>
<li>For bitmap controls, pixels that have the same color are transparent.</li>
<li>For all other controls, the foreground color is used as the background color.</li>
</ul></td>
</tr>
<tr class="even">
<td>Bold</td>
<td>Specify bold text formatting.</td>
</tr>
<tr class="odd">
<td>BottomMargin</td>
<td>Specify the margin for a control.</td>
</tr>
<tr class="even">
<td>ChangeCase</td>
<td>Specify the case of text that a user enters. This property is available only for string, enum, text, and prompt controls.</td>
</tr>
<tr class="odd">
<td>ChangeLabelCase</td>
<td>Specify whether the label for the control should be modified when the report is printed. The following options are available:
<ul>
<li>Auto</li>
<li>None</li>
<li>UPPER CASE</li>
<li>lower case</li>
<li>Title Case</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="even">
<td>ColorScheme</td>
<td>Specify the color palette for a control.</td>
</tr>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Specify a configuration key for the control.</td>
</tr>
<tr class="even">
<td>CSSClass</td>
<td>Specify the Cascading Style Sheet (CSS) to use to render the value in HTML.</td>
</tr>
<tr class="odd">
<td>DataField</td>
<td>Specify a table field for the control. This property isn't available for text, shape, box, and bitmap controls.</td>
</tr>
<tr class="even">
<td>DataMethod</td>
<td>Specify a display method that shows data in a control. This property isn't available for text, shape, and box controls.</td>
</tr>
<tr class="odd">
<td>DateDay</td>
<td>Specify the format for the day. This property is available only for date controls.</td>
</tr>
<tr class="even">
<td>DateFormat</td>
<td>Specify the format for a date. This property is available only for date controls.</td>
</tr>
<tr class="odd">
<td>DateMonth</td>
<td>Specify the format for the month. This property is available only for date controls.</td>
</tr>
<tr class="even">
<td>DateSeparator</td>
<td>Specify the separator that appears between the month, day, and year. This property is available only for date controls.</td>
</tr>
<tr class="odd">
<td>DateYear</td>
<td>Specify the format for the year. This property is available only for date controls.</td>
</tr>
<tr class="even">
<td>DecimalSeparator</td>
<td>Specify the symbol that is used to separate decimal values. This property is available only for real controls.</td>
</tr>
<tr class="odd">
<td>DisplaceNegative</td>
<td>Specify a new position for a value in a grid control when the value is a negative number. This property is available only for integer and real controls.</td>
</tr>
<tr class="even">
<td>DynamicHeight</td>
<td>Specify whether the control is resized to show additional lines of text. When you set this property to <strong>Yes</strong>, page headers, page footers, and repeating column headings are automatically added as required. This property is available only for string controls.</td>
</tr>
<tr class="odd">
<td>ExtendedDataType</td>
<td>Specify the EDT that the field that is associated with the control should be based on.</td>
</tr>
<tr class="even">
<td>ExtraSumWidth</td>
<td>Modify the default width that is allowed for sums. This property is available only for integer and real controls.</td>
</tr>
<tr class="odd">
<td>Font</td>
<td>Specify the font.</td>
</tr>
<tr class="even">
<td>FontSize</td>
<td>Specify the font size.</td>
</tr>
<tr class="odd">
<td>ForegroundColor</td>
<td>Specify the foreground color for a control.</td>
</tr>
<tr class="even">
<td>FormatMST</td>
<td>Specify whether values are formatted by using standard currency format. This property is available only for real controls.</td>
</tr>
<tr class="odd">
<td>Height</td>
<td>Specify the height of a control. When a control is associated with an EDT, the <strong>Height</strong> property of the control overrides the <strong>DisplayLength</strong> property of the EDT. If you set the <strong>Height</strong> property to <strong>Auto</strong> for a bitmap control, the size of the control is based on the size of the graphic.</td>
</tr>
<tr class="even">
<td>ImageName</td>
<td>Specify the file name for an image. This property is available only for bitmap controls.</td>
</tr>
<tr class="odd">
<td>ImageResource</td>
<td>Specify the ID for a system resource to show. The resource macro provides a list of these IDs. Macros are located under the <strong>Macros</strong> node in Application Explorer. This property is available only for bitmap controls.</td>
</tr>
<tr class="even">
<td>Italic</td>
<td>Specify italic text formatting.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Specify a title for the control. If a label isn't specified here, it's inherited from the field.</td>
</tr>
<tr class="even">
<td>LabelBold</td>
<td>Set or return a value that indicates the bold setting for the label in the control.</td>
</tr>
<tr class="odd">
<td>LabelCSSClass</td>
<td>Specify the CSS to use to render the label in HTML.</td>
</tr>
<tr class="even">
<td>LabelFont</td>
<td>Set or return a string data type value that indicates the font for the label text in a form combo box control.</td>
</tr>
<tr class="odd">
<td>LabelFontSize</td>
<td>Set or return the font size, in points, for the label text in a form combo box control.</td>
</tr>
<tr class="even">
<td>LabelItalic</td>
<td>Set or return a value that indicates whether the text in the control label should be italic.</td>
</tr>
<tr class="odd">
<td>LabelLineBelow</td>
<td>Specify the format of the underline for the control title.</td>
</tr>
<tr class="even">
<td>LabelLineThickness</td>
<td>Specify the format of the line below column headings.</td>
</tr>
<tr class="odd">
<td>LabelPosition</td>
<td>Set or return the position of the label for the control. Valid values are <strong>Left</strong> and <strong>Above</strong>.</td>
</tr>
<tr class="even">
<td>LabelTabLeader</td>
<td>Specify whether to append a series of dots to control labels. The following options are available:
<ul>
<li>Auto</li>
<li>Do not append</li>
<li>Do append</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>LabelUnderline</td>
<td>Set or return a value that indicates whether the text in the control label should be underlined.</td>
</tr>
<tr class="even">
<td>LabelWidth</td>
<td>Specify the width of the label for the control.</td>
</tr>
<tr class="odd">
<td>Left</td>
<td>Specify the left alignment of a control.</td>
</tr>
<tr class="even">
<td>LeftMargin</td>
<td>Specify the left margin for a control.</td>
</tr>
<tr class="odd">
<td>Line</td>
<td>Specify the appearance of the lines that form a shape. This property is available only for shape controls.</td>
</tr>
<tr class="even">
<td>LineAbove</td>
<td>Specify the type of line for the top border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections.</td>
</tr>
<tr class="odd">
<td>LineBelow</td>
<td>Specify the type of line for the bottom border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections.</td>
</tr>
<tr class="even">
<td>LineLeft</td>
<td>Specify the type of line for the left border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections.</td>
</tr>
<tr class="odd">
<td>LineRight</td>
<td>Specify the type of line for the right border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections.</td>
</tr>
<tr class="even">
<td>MenuItemLabel</td>
<td>Specify the label for a menu item.</td>
</tr>
<tr class="odd">
<td>MenuItemName</td>
<td>Specify the name of the menu item. The available menu items vary, depending on the setting of the <strong>MenuItemType</strong> property.</td>
</tr>
<tr class="even">
<td>MenuItemType</td>
<td>Specify whether the menu item is an action, display, or output menu item. A display menu item is for a form, and an output menu item is for a report. An output menu item is for a class, job, or query.</td>
</tr>
<tr class="odd">
<td>MinNoOfDecimals</td>
<td>Specify the minimum number of decimal places that are shown. Trailing zeros aren't shown.</td>
</tr>
<tr class="even">
<td>ModelFieldName</td>
<td>Specify a field that is used to determine the left alignment and width of a control.</td>
</tr>
<tr class="odd">
<td>NoOfDecimals</td>
<td>Specify the number of decimal places that are shown. The default value is <strong>20</strong>. This property is available only for real controls.</td>
</tr>
<tr class="even">
<td>ResizeBitmap</td>
<td>Specify whether an image can be resized to fit the dimensions of a control. This property is available only for bitmap controls.</td>
</tr>
<tr class="odd">
<td>RightMargin</td>
<td>Specify the margin for a control.</td>
</tr>
<tr class="even">
<td>RotateSign</td>
<td>Specify whether the sign for the control is inverted. This property is available only for integer and real controls.</td>
</tr>
<tr class="odd">
<td>ShowLabel</td>
<td>Set or return a value that indicates whether the label for the control is shown in the form. A value of <strong>True</strong> indicates that the label will be shown.</td>
</tr>
<tr class="even">
<td>ShowPicAsText</td>
<td>Specify whether the file name for an image is shown instead of the image. This property is available only for bitmap controls.</td>
</tr>
<tr class="odd">
<td>ShowZero</td>
<td>Specify whether a 0 (zero) value is shown. This property is available only for integer and real controls.</td>
</tr>
<tr class="even">
<td>SignDisplay</td>
<td>Specify how the sign of a number is shown. This property is available only for integer and real controls.</td>
</tr>
<tr class="odd">
<td>SumAll</td>
<td>Specify whether the sum of all values is calculated. This property is available only for integer and real controls.</td>
</tr>
<tr class="even">
<td>SumNeg</td>
<td>Specify whether the sum of all negative values is calculated. This property is available only for integer and real controls.</td>
</tr>
<tr class="odd">
<td>SumPos</td>
<td>Specify whether the sum of all positive values is calculated. This property is available only for integer and real controls.</td>
</tr>
<tr class="even">
<td>Table</td>
<td>Specify a data source for the control. This property isn't available for text, shape, box, and bitmap controls.</td>
</tr>
<tr class="odd">
<td>Text</td>
<td>Specify the text string that is shown in a control. This property is available only for text controls.</td>
</tr>
<tr class="even">
<td>TimeFormat</td>
<td>Specify whether times are shown in 24-hour format or AM/PM format. This property is available only for time controls.</td>
</tr>
<tr class="odd">
<td>TimeHours</td>
<td>Specify whether hours are shown. This property is available only for time controls.</td>
</tr>
<tr class="even">
<td>TimeMinutes</td>
<td>Specify whether minutes are shown. This property is available only for time controls.</td>
</tr>
<tr class="odd">
<td>TimeSeconds</td>
<td>Specify whether seconds are shown. This property is available only for time controls.</td>
</tr>
<tr class="even">
<td>TimeSeparator</td>
<td>Specify the symbol that is used to separate hours, minutes, and seconds. This property is available only for time controls.</td>
</tr>
<tr class="odd">
<td>Thickness</td>
<td>Specify the thickness of a control border.</td>
</tr>
<tr class="even">
<td>ThousandSeparator</td>
<td>Specify the symbol that is used to separate thousands. This property is available only for real controls.</td>
</tr>
<tr class="odd">
<td>Top</td>
<td>Specify the top alignment of a control.</td>
</tr>
<tr class="even">
<td>TopMargin</td>
<td>Specify the margin for a control.</td>
</tr>
<tr class="odd">
<td>Type</td>
<td>Specify the type of shape that is shown. This property is available only for shape controls.</td>
</tr>
<tr class="even">
<td>TypeHeaderPrompt</td>
<td>Specify whether a line of dots is added to fill the space between the control title and the control value. This property is available only for text and prompt controls.</td>
</tr>
<tr class="odd">
<td>Underline</td>
<td>Specify underline text formatting.</td>
</tr>
<tr class="even">
<td>Visible</td>
<td>Set or return a value that indicates whether the control is visible. A value of <strong>True</strong> indicates that the control is visible.</td>
</tr>
<tr class="odd">
<td>WarnIfMissing</td>
<td>Specify whether a message is shown if an image is missing from the report. This property is available only for bitmap controls.</td>
</tr>
<tr class="even">
<td>WebMenuItemName</td>
<td>Specify the menu item to include on a web menu. The available values depend on the setting of the <strong>WebMenuItemType</strong> property.</td>
</tr>
<tr class="odd">
<td>WebMenuItemType</td>
<td>Specify the type of the menu item. There are two categories of web menu items:
<ul>
<li>URL</li>
<li>Action</li>
</ul>
The value that you select determines the web menu item names that are available for the <strong>WebMenuItemName</strong> property.</td>
</tr>
<tr class="even">
<td>WebTarget</td>
<td>Specify the location of the control on a web report.</td>
</tr>
<tr class="odd">
<td>Width</td>
<td>Specify the width of a control. When a control is associated with an EDT, the <strong>Width</strong> property of the control overrides the <strong>DisplayLength</strong> property of the EDT. If you set the <strong>Width</strong> property to <strong>Auto</strong> for a bitmap control, the size of the control is based on the size of the graphic.</td>
</tr>
</tbody>
</table>

## Report design properties
The following table describes the report design properties.

| Property                                   | Description                                                                                                                                                                              |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ArrangeMethod                              | Specify the layout for the controls in a report section.                                                                                                                                 |
| ArrangeWhen                                | Specify when report controls are arranged.                                                                                                                                               |
| BottomMargin                               | Specify the bottom margin. If you set this property to **Auto**, the default value that is stored in the system table is used.                                                           |
| Caption                                    | Specify the name that is shown for the report in the user interface.                                                                                                                     |
| ColorScheme                                | Specify the color palette.                                                                                                                                                               |
| Columns                                    | Specify the number of columns.                                                                                                                                                           |
| ColumnSpace                                | Specify the space between columns.                                                                                                                                                       |
| Font, FontSize, Italic, Underline and Bold | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you can set by clicking **Options** &gt; **Fonts** on the **Tools** menu. |
| ForegroundColor                            | Specify the foreground color.                                                                                                                                                            |
| Height                                     | Specify the height.                                                                                                                                                                      |
| LeftMargin                                 | Specify the left margin. If you set this property to **Auto**, the default value that is stored in the system table is used.                                                             |
| LineAbove                                  | Specify the type of line for the top border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                       |
| LineBelow                                  | Specify the type of line for the bottom border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                    |
| LineLeft                                   | Specify the type of line for the left border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                      |
| LineRight                                  | Specify the type of line for the right border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                     |
| ResolutionX, ResolutionY                   | Specify the distance between gridlines.                                                                                                                                                  |
| RightMargin                                | Specify the right margin. If you set this property to **Auto**, the default value that is stored in the system table is used.                                                            |
| Ruler                                      | Specify the unit for the ruler that is shown when you edit a design. To edit a design, right-click **AutoDesignSpecs** or **Generated Design**, and then click **Edit**.                 |
| Thickness                                  | Specify the thickness of a section border.                                                                                                                                               |
| TopMargin                                  | Specify the top margin. If you set this property to **Auto**, the default value that is stored in the system table is used.                                                              |

## Report design section properties
The following table describes properties for report design sections. For information about additional properties that are available for report designs, see the "Report design properties" section.

| Property                                  | Description                                                                                                                                                                                                                                                                                                                     |
|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ArrangeMethod                             | Specify the layout for the controls in a report section.                                                                                                                                                                                                                                                                        |
| ArrangeWhen                               | Specify when the controls in the container should be arranged. The available options are **Startup**, **On demand**, and **Never**.                                                                                                                                                                                             |
| Bold                                      | Get or set the weight of the font that was used to show text in the control.                                                                                                                                                                                                                                                    |
| Bottom                                    | Change the position of the bottom of the report.                                                                                                                                                                                                                                                                                |
| BottomMargin                              | Specify the bottom margin. If you set this property to **Auto**, the default value that is stored in the UserInfo system table is used.                                                                                                                                                                                         |
| ColorScheme                               | Specify the color palette.                                                                                                                                                                                                                                                                                                      |
| ColumnHeadingsStrategy                    | Specify the layout of column headings. If you set this property to **WordWrap**, a heading wraps when it's longer than the longest field in the column. Headings can wrap to a maximum of eight lines. Headings that are longer than eight lines are truncated. **Note:** The heading length varies, depending on the language. |
| Columns                                   | Specify the number of columns.                                                                                                                                                                                                                                                                                                  |
| Columnspace                               | Specify the space between columns.                                                                                                                                                                                                                                                                                              |
| Font                                      | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you can set by clicking **Options **&gt; **Fonts** on the **Tools** menu.                                                                                                                                        |
| FontSize                                  | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you can set by clicking **Options **&gt; **Fonts** on the **Tools** menu.                                                                                                                                        |
| ForegroundColor                           | Specify the foreground color.                                                                                                                                                                                                                                                                                                   |
| GrandHeader                               | Specify whether the value of the **HeaderText** property is shown. The **GrandHeader** property is available only when a report has multiple data sources that aren't nested.                                                                                                                                                   |
| GrandTotal                                | Specify whether the value of the **FooterText** property is shown. The **GrandTotal** property is available only when a report has multiple data sources that aren't nested.                                                                                                                                                    |
| HeaderText                                | Specify the text that is shown above the first record in a section when the **GrandHeader** property is set to **Yes**. This property is available only when a report has multiple data sources that aren't nested.                                                                                                             |
| Height                                    | Specify the height.                                                                                                                                                                                                                                                                                                             |
| Italic                                    | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you can set by clicking **Options **&gt; **Fonts** on the **Tools** menu.                                                                                                                                        |
| LabelTopMargin, LabelBottomMargin         | Specify the margins above and below column headings.                                                                                                                                                                                                                                                                            |
| LeftMargin                                | Specify the left margin. If you set this property to **Auto**, the default value that is stored in the UserInfo system table is used.                                                                                                                                                                                           |
| LineAbove, LineBelow, LineLeft, LineRight | Specify the type of line for a section border. If a report has many lines and boxes, consider using the shape control inside a section.                                                                                                                                                                                         |
| Map                                       | Specify the map to use to show data. You can associate a map field with a field in one or more tables. This property lets you use the same field name to access fields that have different names in different tables.                                                                                                           |
| NoOfHeadingLines                          | Specify the number of lines that are used to show column headings. If you set the property to **0** (zero), column headings aren't displayed. For reports that include several fields, increase the number of lines to make sure that all fields are shown.                                                                     |
| RightMargin                               | Specify the right margin. If you set this property to **Auto**, the default value that is stored in the UserInfo system table is used.                                                                                                                                                                                          |
| ResolutionX                               | Specify the distance between gridlines.                                                                                                                                                                                                                                                                                         |
| ResolutionY                               | Specify the distance between gridlines.                                                                                                                                                                                                                                                                                         |
| Ruler                                     | Specify the unit for the ruler that is shown when you edit a design. To edit a design, right-click **AutoDesignSpecs** or **Generated** Design, and then click **Edit**.                                                                                                                                                        |
| Table                                     | Specify the data source for a section.                                                                                                                                                                                                                                                                                          |
| Thickness                                 | Specify the thickness of a section border.                                                                                                                                                                                                                                                                                      |
| Top                                       | Change the position of the top of the report.                                                                                                                                                                                                                                                                                   |
| TopMargin                                 | Specify the top margin. If you set this property to **Auto**, the default value that is stored in the UserInfo system table is used.                                                                                                                                                                                            |
| Underline                                 | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you can set by clicking **Options **&gt; **Fonts** on the **Tools** menu.                                                                                                                                        |

## Report query properties
The following table describes report query properties. For information about additional report properties, see the "Report properties" and "System and common properties" sections.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AllowCheck</td>
<td>Get or set the Allow check flag.</td>
</tr>
<tr class="even">
<td>AllowCrossCompany</td>
<td>Get or set the Allow cross-company flag. This flag indicates whether query execution will be across companies.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>A textual explanation of the query. This optional property is often used in Office Add-ins scenarios.</td>
</tr>
<tr class="even">
<td>Form</td>
<td>Specify the form that is used for user interaction.</td>
</tr>
<tr class="odd">
<td>Interactive</td>
<td>Specify whether users can interact with the report by delimiting queries, setting printer options, and so on.</td>
</tr>
<tr class="even">
<td>Literals</td>
<td>Specify how literals are represented in SQL statements.</td>
</tr>
<tr class="odd">
<td>Model</td>
<td>Specify the model that the report query is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in another layer.</td>
</tr>
<tr class="even">
<td>QueryType</td>
<td>Specify the type of the query. The following options are available:
<ul>
<li>Join</li>
<li>Union</li>
</ul>
The default value is <strong>Join</strong>.</td>
</tr>
<tr class="odd">
<td>Searchable</td>
<td>Specify whether the query can be part of a set of queries that can be used to search the SharePoint Business Catalog. This property is useful when you use the Enterprise Search feature. The default value is <strong>No</strong>.</td>
</tr>
<tr class="even">
<td>Title</td>
<td>Specify the title of the query.</td>
</tr>
<tr class="odd">
<td>UserUpdate</td>
<td>Specify whether users can update a query.</td>
</tr>
<tr class="even">
<td>Version</td>
<td>This is a read-only internal property.</td>
</tr>
</tbody>
</table>

## Security code permission properties
A code permission is a group of permissions that are associated with a menu item or a service operation. When a security role has access to a menu item, it also has access to other Application Explorer items that are mentioned within the code permission for that menu item. The degree of access is controlled by the specific permissions that are defined under the code permission node.

### Securable objects

Code permissions are used to give access to securable objects. The following list shows the hierarchy of code permission nodes in Application Explorer:

-   Security
    -   Code Permissions
        -   YourCodePermission
            -   Tables
            -   Server Methods
            -   Associated Objects
                -   Forms
                -   Web Controls
                -   Reports

Code permissions can also override the access levels to securable objects under the **Associated Objects** node.

### Code permission properties

This following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** in Application Explorer.

| Property | Required | Description                                                                                                                        |
|----------|----------|------------------------------------------------------------------------------------------------------------------------------------|
| Name     | Yes      | The name of the code permission. The code permission lets users run the class method that is specified in the **Method** property. |
| Class    | Optional | The class that is associated with this code permission.                                                                            |
| Method   | Optional | The method that is associated with this code permission.                                                                           |

### Table properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Tables** &gt; **YourTable** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Table</td>
<td>Yes</td>
<td>The name of the table.</td>
</tr>
<tr class="even">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>EffectiveAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the table.</td>
</tr>
<tr class="odd">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Server method properties

The following tables describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Class</td>
<td>Yes</td>
<td>The name of the server class.</td>
</tr>
<tr class="even">
<td>Method</td>
<td>Yes</td>
<td>The secure server method that is tagged with the <strong>SysEntryPointAttribute</strong> attribute.</td>
</tr>
<tr class="odd">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li><strong>Invoke</strong> – The server method can be called.</li>
<li><strong>NoAccess</strong> – The server method can't be called.</li>
</ul></td>
</tr>
<tr class="even">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Form properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Forms** &gt; **YourForm** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Form</td>
<td>Yes</td>
<td>The name of the form.</td>
</tr>
<tr class="even">
<td>AccessLevel</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>EffectiveAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the form.</td>
</tr>
<tr class="odd">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Web control properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Web Controls** &gt; **YourWebControl** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>WebControl</td>
<td>Yes</td>
<td>The name of the web control.</td>
</tr>
<tr class="even">
<td>AccessLevel</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>EffectiveAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the web control.</td>
</tr>
<tr class="odd">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Report properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Reports** &gt; **YourReport** in Application Explorer.

| Property  | Required | Description                                |
|-----------|----------|--------------------------------------------|
| Name      | Yes      | The name of the report design.             |
| Report    | Yes      | The full name of the report.               |
| ManagedBy | Optional | This property is used by automation tools. |

## Security duty properties
Security permissions are combined into privileges, and privileges are combined into duties. Duties are defined as groups of related privileges that provide a user with access to a specific business function. In Application Explorer, these privileges are organized into the nodes of a duty.

### Best practices

This section describes the best practice rules for duties.

-   All duties should be assigned to a role.
-   All duties should be part of a process cycle.
-   Because a duty represents a specific business function, the name of the duty should rarely or never change. For example, your company pays bills. Although the details of how you pay bills might change, the essential function of paying bills won't change. Instead of creating a new duty, you should change the privilege subnodes of the duty.
-   The name of a process cycle should rarely or never change.

### Duty hierarchy in Application Explorer

The following list shows the hierarchy of duty nodes in Application Explorer:

-   Security
    -   Duties
        -   YourDuty
            -   Privileges

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the duty.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Yes</td>
<td>Text that is shown for the duty in the user interface.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Yes</td>
<td>A description of the duty.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the duty.</li>
<li><strong>No</strong> – Disable the duty.</li>
</ul></td>
</tr>
</tbody>
</table>

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Duties** &gt; **YourDuty** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the privilege.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the privilege.</li>
<li><strong>No</strong> – Disable the privilege.</li>
</ul></td>
</tr>
</tbody>
</table>

## Security privilege properties
A privilege is a group of permissions. The nodes that are below each privilege node identify the securable objects that a user can access and set the level of access for each object.

### Best practices

This section describes the best practice rules for privileges.

-   You can use privileges to specify the access that is required in order to perform a job.
-   You can use privileges to group the permissions for related securable objects. For example, menu items and their controls are closely related.
-   You can assign privileges directly to security roles. However, security settings are easier to maintain if you assign duties or process cycles instead of privileges.

### Securable objects

Privileges are used to give access to securable objects. The following list shows the hierarchy under the **Security** &gt; **Privileges** node in Application Explorer:

-   Security
    -   Privileges
        -   YourPrivilege
            -   Entry Points
            -   Permissions
                -   Tables
                -   Server Methods
                -   Forms

Privileges can also override the access levels to securable objects as they are defined elsewhere in Application Explorer. For example, a privilege can override a permission that is defined by the **EffectiveAccess** property under **Forms** &gt; **YourForm** &gt; **Permissions** &gt; **Update** &gt; **Tables** &gt; **YourTable** in Application Explorer.

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the privilege.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Yes</td>
<td>Text that is shown for the privilege in the user interface.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Yes</td>
<td>A description of the privilege.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the privilege.</li>
<li><strong>No</strong> – Disable the privilege.</li>
</ul></td>
</tr>
</tbody>
</table>

### Entry point properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Entry** **Points** &gt; **YourEntryPoint** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the entry point.</td>
</tr>
<tr class="even">
<td>ObjectType</td>
<td>Yes</td>
<td>The object type of the entry point. The following options are available:
<ul>
<li>MenuItemDisplay</li>
<li>MenuItemOutput</li>
<li>MenuItemAction</li>
<li>ServiceOperation</li>
<li>WebActionItem</li>
<li>WebURLItem</li>
<li>WebManagedContent</li>
</ul></td>
</tr>
<tr class="odd">
<td>ObjectName</td>
<td>Yes</td>
<td>The object name of the entry point.</td>
</tr>
<tr class="even">
<td>ObjectChildName</td>
<td>Optional</td>
<td>A value that represents the service method name. <strong>Note:</strong> Specify a value for this property only if the <strong>ObjectType</strong> property is set to <strong>ServiceOperation</strong>.</td>
</tr>
<tr class="odd">
<td>AccessLevel</td>
<td>Yes</td>
<td>The permission value. For all object types except <strong>ServiceOperation</strong>, the following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>AccessLevel</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the entry point. The Correct permission applies only when a time state table is involved. This permission authorizes you to issue update records in a time state table. For the <strong>ServiceOperation</strong> object type, the following options are available:
<ul>
<li><strong>Invoke</strong> – The server method can be called.</li>
<li><strong>NoAccess</strong> – The server method can't be called.</li>
</ul></td>
</tr>
</tbody>
</table>

### Table properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Tables** &gt; **YourTable** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Table</td>
<td>Yes</td>
<td>The name of the table.</td>
</tr>
<tr class="even">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>EffectiveAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. The Correct permission applies only when a time state table is involved. This permission authorizes you to update records in a time state table. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the table.</td>
</tr>
<tr class="odd">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Server method properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Class</td>
<td>Yes</td>
<td>The name of the server class.</td>
</tr>
<tr class="even">
<td>Method</td>
<td>Yes</td>
<td>The name of the secure server method that is tagged with the <strong>SysEntryPointAttribute</strong> attribute.</td>
</tr>
<tr class="odd">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li><strong>Invoke</strong> – The server method can be called.</li>
<li><strong>NoAccess</strong> – The server method can't be called.</li>
</ul></td>
</tr>
<tr class="even">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Form properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Forms** &gt; **YourForm** in Application Explorer.

| Property | Required | Description           |
|----------|----------|-----------------------|
| Form     | Yes      | The name of the form. |

## Security process cycle properties
A process cycle is a group of duties. A process cycle represents a high-level job function. Although the details of how a given job function is run might change over time, the concept and name of that job function probably don't change.

### Best practices

This section describes the best practice rules for process cycles.

-   Each duty should be part of a process cycle.
-   Use a process cycle to organize a group of duties for a job function.

### Process cycle hierarchy in Application Explorer

The following list shows the hierarchy of process cycles nodes in Application Explorer:

-   Security
    -   Process Cycles
        -   YourProcessCycle
            -   Duties

### Process cycle properties

The following table describes the properties for the node at **Security** &gt; **Process** **Cycles** &gt; **YourProcessCycle** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the process cycle.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Yes</td>
<td>Text that is shown for the process cycle in the user interface.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Yes</td>
<td>A description of the process cycle.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the process cycle.</li>
<li><strong>No</strong> – Disable the process cycle.</li>
</ul></td>
</tr>
</tbody>
</table>

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Process Cycles** &gt; **YourProcessCycle** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the duty.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the duty.</li>
<li><strong>No</strong> – Disable the duty.</li>
</ul></td>
</tr>
</tbody>
</table>

## Security policy properties
Developers and system administrators can create security policies to deny access to a subset of data records in tables.

### Constrained tables of a policy

You can add tables and views under the **Constrained Tables** node of a security policy in Application Explorer. These tables and views are related to the data source table of the query that is named in the **Query** property of the policy. The following list shows the hierarchy of security policy nodes in Application Explorer:

-   Security
    -   Policies
        -   YourPolicy
            -   Constrained Tables
                -   YourConstrainedTable
                    -   YourConstrainedSubTable
                -   YourConstrainedView

Each **Constrained Tables** node can contain any number of constrained tables and views. Additionally, each constrained table can contain any number of constrained sub-tables.

### Security policy properties

The following table describes the properties for the node at **Security** &gt; **Policies** &gt; **YourPolicy** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the security policy.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Yes</td>
<td>The text that is shown for the security policy in the user interface.</td>
</tr>
<tr class="odd">
<td>PrimaryTable</td>
<td>Yes</td>
<td>The table that is specified in the data source for the security policy query.</td>
</tr>
<tr class="even">
<td>Query</td>
<td>Yes</td>
<td>The query that the policy uses to filter data from the constrained tables that are specified in the policy.</td>
</tr>
<tr class="odd">
<td>UseNotExistJoin</td>
<td>Yes</td>
<td>A value that indicates whether the security query must be applied as a <strong>not exists</strong> join or an <strong>exists</strong> join.</td>
</tr>
<tr class="even">
<td>PolicyGroup</td>
<td>No</td>
<td>Administrators and developers can use this property to quickly identify groups of related security policies. The available options are the names of the security policy groups that the system administrator or developer has created. The system doesn't use this property at run time.</td>
</tr>
<tr class="odd">
<td>ConstrainedTable</td>
<td>Yes</td>
<td>A value that controls whether the security policy restricts the data values in records that are returned from the primary table. The following options are available:
<ul>
<li><strong>Yes </strong>– The security policy is enforced on the primary table.</li>
<li><strong>No </strong>– The security policy isn't enforced on the primary table.</li>
</ul></td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that controls whether the system enforces the policy at run time. The following options are available:
<ul>
<li><strong>Yes </strong>– Enable the security policy.</li>
<li><strong>No </strong>– Disable the security policy.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Operation</td>
<td>Yes</td>
<td>A value that controls which data operations the policy is enforced for. The following options are available:
<ul>
<li>Select</li>
<li>Insert</li>
<li>Update</li>
<li>Delete</li>
<li>Insert, Update and Delete</li>
<li>All operations</li>
</ul></td>
</tr>
<tr class="even">
<td>ContextType</td>
<td>Yes</td>
<td>A value that controls the context type of the security policy. The following options are available:
<ul>
<li><strong>ContextString </strong>– You must specify a value for the <strong>ContextString</strong> property. The security policy uses a specific application context for the policy.</li>
<li><strong>RoleName </strong>– The security policy is applied only to the application user who is assigned to the value of <strong>RoleName</strong>.</li>
<li><strong>RoleProperty </strong>– This value is used in combination with the <strong>ContextString</strong> property to specify multiple roles context.</li>
</ul></td>
</tr>
<tr class="odd">
<td>ContextString</td>
<td>Yes</td>
<td>This property is used in combination with <strong>ContextType</strong> property. It can be used to specify an application or multiple roles context.</td>
</tr>
</tbody>
</table>

## Security role properties
Roles represent a collection of permissions that can be granted to users. The nodes that are nested below each role node identify various securable objects that a user can access and specify the level of access.

### Role node in Application Explorer

Roles are used to give access to securable objects. The following list shows the hierarchy of role nodes in Application Explorer:

-   Security
    -   Roles
        -   YourRole
            -   Duties
            -   Privileges
            -   Permissions
                -   Tables
                -   Forms
                -   Server Methods
            -   Sub Roles

Roles are typically associated with security duties, and sometimes with security privileges. Access levels to securable objects within a role are derived from the duties, privileges, or both. Roles can also override the access levels to securable objects under the **Permissions** node.

### Role properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **YourRole** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the role.</td>
</tr>
<tr class="even">
<td>Label</td>
<td>Yes</td>
<td>Text that is shown for the role in the user interface.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Yes</td>
<td>A description of the role.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the role.</li>
<li><strong>No</strong> – Disable the role.</li>
</ul></td>
</tr>
<tr class="odd">
<td>PastDataAccess</td>
<td>Yes</td>
<td>The past data access for the tables that have date-effective fields. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>PastDataAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the table.</td>
</tr>
<tr class="even">
<td>CurrentDataAccess</td>
<td>Yes</td>
<td>The current data access for the tables that have date-effective fields.</td>
</tr>
<tr class="odd">
<td>FutureDataAccess</td>
<td>Yes</td>
<td>The future data access for the tables that have date-effective fields.</td>
</tr>
<tr class="even">
<td>ContextString</td>
<td>Optional</td>
<td>A user-defined string that can be used by security policies.</td>
</tr>
</tbody>
</table>

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the duty.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the duty.</li>
<li><strong>No</strong> – Disable the duty.</li>
</ul></td>
</tr>
</tbody>
</table>

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the privilege.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the privilege.</li>
<li><strong>No</strong> – Disable the privilege.</li>
</ul></td>
</tr>
</tbody>
</table>

### Table properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Tables** &gt; **YourTable** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Table</td>
<td>Yes</td>
<td>The name of the table.</td>
</tr>
<tr class="even">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li>Read</li>
<li>Update</li>
<li>Create</li>
<li>Correct</li>
<li>Delete</li>
<li>NoAccess</li>
</ul>
The permission values for the <strong>EffectiveAccess</strong> property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to <strong>NoAccess</strong> to prevent all access to the table.</td>
</tr>
<tr class="odd">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Form properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Form** &gt; **YourForm** in Application Explorer.

| Property | Required | Description           |
|----------|----------|-----------------------|
| Form     | Yes      | The name of the form. |

### Server method properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Class</td>
<td>Yes</td>
<td>The name of the server class.</td>
</tr>
<tr class="even">
<td>Method</td>
<td>Yes</td>
<td>The name of the secure server method that is tagged with the <strong>SysEntryPointAttribute</strong> attribute.</td>
</tr>
<tr class="odd">
<td>EffectiveAccess</td>
<td>Yes</td>
<td>The permission value. The following options are available:
<ul>
<li><strong>Invoke</strong> – The server method can be called.</li>
<li><strong>NoAccess</strong> – The server method can't be called.</li>
</ul></td>
</tr>
<tr class="even">
<td>ManagedBy</td>
<td>Optional</td>
<td>This property is used by automation tools.</td>
</tr>
</tbody>
</table>

### Subrole properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Sub Roles** &gt; **YourSubRole** in Application Explorer.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Name</td>
<td>Yes</td>
<td>The name of the subrole.</td>
</tr>
<tr class="even">
<td>Enabled</td>
<td>Yes</td>
<td>A value that indicates whether the duty is enabled. The following options are available:
<ul>
<li><strong>Yes</strong> – Enable the subrole</li>
<li><strong>No</strong> – Disable the subrole.</li>
</ul></td>
</tr>
</tbody>
</table>

## Web menu properties
The following table describes the properties that are specific to web menus and submenus.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ConfigurationKey</td>
<td>Specify the configuration key that is used to control display of this menu. If a user doesn't have access to the configuration key, the menu won't be visible.</td>
</tr>
<tr class="even">
<td>HighlightSelected</td>
<td>This property isn't supported.</td>
</tr>
<tr class="odd">
<td>Label</td>
<td>Specify the text that is shown for the top-level node of the web menu or submenu. The value can't exceed 250 characters.</td>
</tr>
<tr class="even">
<td>MenuItemName</td>
<td>Specify the menu item to access when the top-level node for the menu or submenu is clicked. The options that are available depend on the setting of the <strong>MenuItemType</strong> property.</td>
</tr>
<tr class="odd">
<td>MenuItemType</td>
<td>Specify the type of menu item that is accessed by the top-level node of the menu or submenu. The available options are <strong>Action</strong> and <strong>URL</strong>.</td>
</tr>
<tr class="even">
<td>Model</td>
<td>Specify the model. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.</td>
</tr>
<tr class="odd">
<td>SetCompany</td>
<td>This property causes the system to change the company when the form receives focus. If the <strong>SaveDataPerCompany</strong> property on a table is set to <strong>Yes</strong>, the <strong>SetCompany</strong> property on a form design that uses the table as a data source must also be set to <strong>Yes</strong>.</td>
</tr>
<tr class="even">
<td>ShowParentModule</td>
<td>Specify whether to update the QuickLaunch, based on the parent module of the menu item. The following options are available:
<ul>
<li><strong>Yes </strong>– Always update the QuickLaunch, based on the parent module of the menu item.</li>
<li><strong>No </strong>– Leave the QuickLaunch unchanged, even if the parent module of the menu item differs from the current module.</li>
</ul>
The default value is <strong>Yes</strong>.</td>
</tr>
</tbody>
</table>

## Web menu item properties
The following table describes the properties that are specific to web menu items.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Big</td>
<td>Specify the size of the button when it's used on an Action Pane. The following options are available:
<ul>
<li><strong>Yes </strong>– The button is shown at full size and is located at the start of the group.</li>
<li><strong>No </strong>– The button is shown at the smaller size and is located on the right side of the group.</li>
</ul></td>
</tr>
<tr class="even">
<td>CloseDialogBehavior</td>
<td>Specify the action that is performed on the parent window when the dialog box closes. The following options are available:
<ul>
<li><strong>Auto </strong>– Depending on how the dialog box was used, the appropriate update actions are performed when the dialog box is closed.</li>
<li><strong>RefreshDataSource </strong>– The read-only data source on the parent form is updated. This option preserves the current selection and performs a <strong>Research()</strong> operation on the data source.</li>
<li><strong>RefreshPage </strong>– Refresh the page.</li>
<li><strong>Submit </strong>– Refresh the parent page.</li>
<li><strong>None </strong>– No action is performed.</li>
</ul>
The default value is <strong>Auto</strong>.</td>
</tr>
<tr class="odd">
<td>HideActionPane</td>
<td>Specify whether the Action Pane is visible on the page that is being opened.</td>
</tr>
<tr class="even">
<td>HomePage</td>
<td>Specify whether the page is a Role Center page and is deployed to the main Enterprise Portal site.</td>
</tr>
<tr class="odd">
<td>NeedsRecord</td>
<td>When you set this property to <strong>Yes</strong>, the menu item is shown when there are no records in the data set.</td>
</tr>
<tr class="even">
<td>PageDefinition</td>
<td>The page that the web menu item points to.</td>
</tr>
<tr class="odd">
<td>Parameters</td>
<td>Specify the arguments that are passed to the page that is being opened. Each parameter must have the following form: <em>name</em>=<em>value</em> If multiple parameters must be passed, they must be separated by an ampersand (&amp;), as shown in the following example: mode=2&amp;category=1</td>
</tr>
<tr class="even">
<td>URL</td>
<td>Specify the URL to navigate to.</td>
</tr>
<tr class="odd">
<td>WebConfigurationKey</td>
<td>Select the configuration key that is required in order to enable the web menu item. Use the key for the module that the object belongs to.</td>
</tr>
<tr class="even">
<td>WindowMode</td>
<td>Specify the type of window to use for the page that is being opened. The following options are available:
<ul>
<li><strong>Inline </strong>– The page that is being opened will replace the existing content in the browser. If the web menu item is being accessed from a dialog box, the page that is being opened will open in a new browser window.</li>
<li><strong>Modal </strong>– If no dialog box is open, a new dialog box will be created. If the web menu item is being accessed from a dialog box, the page that is being opened will replace the content of the current dialog box.</li>
<li><strong>NewModal </strong>– The page that is being opened will always open in a new dialog box.</li>
<li><strong>NewWindow </strong>– The page that is being opened will open in a new browser window.</li>
</ul></td>
</tr>
<tr class="odd">
<td>WindowParameters</td>
<td>Specify additional parameters to control the appearance of the SharePoint dialog box. The parameters must be enclosed in braces ({}) and separated by commas. The following example shows how to set the <strong>WindowParameters</strong> property so that the dialog box has a size of 400 × 300 pixels, and so that it has no <strong>Close</strong> or <strong>Maximize</strong> button: {width:400, height:300, showClose:false, allowMaximize:false}</td>
</tr>
<tr class="even">
<td>WindowSize</td>
<td>Specify the size of the window to use for the page that is being opened. The following options are available:
<ul>
<li><strong>Smallest </strong>– 330 × 200 pixels</li>
<li><strong>Small </strong>– 550 × 450 pixels</li>
<li><strong>Medium </strong>– 800 × 630 pixels</li>
<li><strong>Large </strong>– 930 × 630 pixels</li>
<li><strong>Maximum </strong>– The largest size that will fit in the boundaries of the main browser window</li>
</ul></td>
</tr>
</tbody>
</table>



