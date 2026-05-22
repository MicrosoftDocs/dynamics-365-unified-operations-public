---
title: Application Explorer properties
description: Learn about the properties that appear in the Properties window of Microsoft Visual Studio for items in Application Explorer.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Application Explorer properties

[!include [banner](../includes/banner.md)]

This article describes the properties that appear in the **Properties** window of Microsoft Visual Studio for items in Application Explorer.

Many nodes in Application Explorer represent elements that have associated properties. You can read or modify these properties in the **Properties** window of Microsoft Visual Studio.

## System and common properties

Most application objects in Application Explorer have a standard set of system properties. These system properties are read-only. Use the **Properties** window to view the properties for any item in Application Explorer. To open the **Properties** window, right-click a node in Application Explorer, and then select **Properties**. On the **Categories** tab of the **Properties** window, many system properties appear under the **Statistics** node. This article lists additional common properties that appear on many, but not all, Application Explorer nodes. The following table shows the system properties that appear on almost all Application Explorer nodes. All these system properties are read-only.

| Property     | Description                                                       |
|--------------|-------------------------------------------------------------------|
| ChangedBy    | The user who last changed the object (often the release version). |
| ChangedDate  | The date when the object was last changed.                        |
| ChangedTime  | The time when the object was last changed.                        |
| CreatedBy    | The user who created the object.                                  |
| CreationDate | The date when the object was created.                             |
| CreationTime | The time when the object was created.                             |

The following table shows other common properties that appear on many, but not all, Application Explorer nodes.

| Property          | Description                                                                                                                                                                                                                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ConfigurationKey  | Specify the configuration key that controls access to or display of an element. If a user doesn't have access to the configuration key, the element isn't visible. Elements include pages, controls on pages, tables, and other elements.                                                                            |
| LegacyID          | An identifier element from an earlier version. During upgrade from a previous version, the old identifier is assigned to **LegacyID**. An installation-specific identifier isn't assigned, and business logic remains intact. This property isn't used for new elements.                                             |
| NeededAccessLevel | The minimum access level that a user requires. This property is read-only.                                                                                                                                                                                                                                           |
| Origin            | The globally unique identifier (GUID) of an Application Explorer element. This property is used to identify elements during synchronization and in upgrade scenarios. It's a read-only property, and the value never changes after the system assigns it. No origin GUID value is duplicated anywhere in the system. |
| SecurityKey       | This property is obsolete but is retained for reference in systems that were upgraded from an earlier version.                                                                                                                                                                                                       |

## Base enum properties

The following table describes the properties that are available for enumerations.

| Property | Description |
|---|---|
| AnalysisUsage | Specify the role of the enumeration in a cube. This setting automatically propagates to all table fields that reference the enumeration. However, you can override the setting on a table field. The following options are available:<br><br>- **Attribute** - A field that references the enumeration is a dimension attribute.<br>- **None** - A field that references the enumeration isn't a dimension attribute. |
| ConfigurationKey | Specify the configuration key. |
| CountryRegionCodes | Specify the codes for the countries/regions where the view is applicable or valid. Implement this property as a comma-separated list of International Organization for Standardization (ISO) country/region codes in a single string. The values must match data in the global address book. The client framework and application might use this property to enable or disable country/region-specific features. |
| DisplayLength | Specify the number of characters that are shown. The default value is **Auto**. |
| Help | Create a Help string for the field. The Help string is shown when the field is used on a page. |
| Label | Specify the label that is shown on pages and reports. |
| Model | Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| Name | Specify the enumeration name. An enumeration name must indicate either the possible enumeration values or the type of the enumeration value. Examples of enumerations that are named according to the possible values are **InclExcl** and **NextPrevious**. Examples of enumerations that are named according to the type of the enumeration value are **ArrivalPostingType** and **ListStatus**. |
| Style | Change the default appearance of the enumeration. The following options are available:<br><br>- Combo box<br>- Radio button |
| UseEnumValue | A value of **Yes** indicates that default values of the **EnumValue** property were modified. A value of **No** resets the **EnumValue** property to the default values. |

## Extended data type properties

Extended data type (EDT) properties are divided into the following groups, based on whether they're common to all EDTs or available only for certain base data types.

### Properties that are common to all EDTs

| Property | Description |
|---|---|
| Alignment | Change the alignment of the text. The available options are **Left**, **Right**, and **Center**. |
| AnalysisDefaultSort | Specify the default sort order for a field in a report model that has this EDT. |
| AnalysisDefaultTotal | Specify the aggregate function for a measure. Use this property when the **AnalysisUsage** property is set to **Measure**. The following options are available:<br><br>- **Sum** - Return the sum of all the values in a set.<br>- **Count** - Return the number of non-null items in a set.<br>- **CountDistinct** - Return the number of distinct non-null items in a set.<br>- **Min** - Return the minimum value in a set.<br>- **Max** - Return the maximum value in a set.<br>- **None** - No aggregate function is applied.<br>- **Auto** - This option applies to derived EDTs. The value of the **AnalysisUsage** property for the parent EDT is used.<br><br>You can override the aggregate function at the field level. In other words, you can change the aggregate function for the field by using the **AnalysisDefaultTotal** property for that field. |
| AnalysisGrouping | Specify whether a field that has this EDT is grouped by default when the field is added to a report by using Report Builder for Microsoft SQL Server Reporting Services (SSRS). This property is automatically set to **Discouraged** for currency amounts. For other fields that are unique, set this property to **Discouraged**. |
| AnalysisUsage | Specify the role of the EDT in a cube. This setting automatically propagates to all table fields that reference the EDT. However, you can override the setting on a table field. The following options are available:<br><br>- **Attribute** - A field that references the EDT is a dimension attribute.<br>- **Measure** - A field that references the EDT is a measure.<br>- **Both** - A field that references the EDT is both a dimension attribute and a measure.<br>- **None** - A field that references the EDT is neither a dimension attribute nor a measure.<br>- **Auto** - This option applies to derived EDTs. The value of the **AnalysisUsage** property for the parent EDT is used.<br><br>**Note:** Data types that are based on enumerations can't be measures. |
| ArrayLength | This property is read-only. The default value is **1**. To add array elements to the EDT, right-click the **Array Element** node, and then click **New Array Element**. The value of the **ArrayLength** property is increased to reflect this change. |
| ButtonImage | Specify the image that is shown when the EDT is used for a lookup button on a page. The following options are available:<br><br>- **Arrow**<br>- **Mail** - You can select this option for the **e-mail** type, for example.<br>- **URL** - You can select this option for the **URL** type, for example.<br>- **ThreeDots** (...)<br>- **OpenFile** - You can select this option for the **FilenameOpen** and **FilenameSave** types, for example.<br>- **Calendar** - You can select this option for date types, for example.<br><br>The default value is **Arrow**. |
| CollectionLabel | Specify the label that is used to show the plural name of a field that has this EDT. |
| ConfigurationKey | Specify the configuration key for the EDT. |
| CountryRegionCodes | Specify the codes for the countries or regions where the menu is applicable or valid. Implement this property as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country or region-specific features. |
| DisplayLength | Specify the maximum number of characters that are shown on a page or report. |
| EnumType | Specify an enumerated data type. This property must be set for EDTs of the **enum** type. |
| Extends | Use this property to base the EDT on another EDT. |
| FormHelp | Specify the page to use when you perform a lookup from a field on a page. |
| HelpText | Create a Help string for the EDT. The Help string is shown when the type is used on a page. |
| ID | This property is read-only. |
| Label | Specify the label that is used for the type when the type is used on a page or report. |
| Model | Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| Name | Specify the name of the type. The name is used to refer to the type from X++. |
| PresenceClass | Specify the X++ class that is used together with the **PresenceMethod** property to return an instance of the **PresenceInfo** object. |
| PresenceIndicatorAllowed | Specify whether the control that references the EDT should use presence. The default value is **Yes**. |
| PresenceMethod | For the X++ class that is specified in the **PresenceClass** property, specify the X++ static class method that should be called by using a controls data value. This method returns an instance of the **PresenceInfo** object that contains the data that the Presence indicator requires. |
| ReferenceTable | Specify the table that is referenced by this EDT, and that has the primary key. In other words, this property indicates the primary key table that this EDT references. |
| Style | Change the default appearance of the EDT. The following options are available:<br><br>- Auto<br>- Combo box<br>- Radio button |

### Properties that are available for only some base data types

Unless the following table specifies otherwise, leave all these properties set to **Auto**.

| Property | Type that the property exists for | Description |
|---|---|---|
| Adjustment | String | For strings of fixed length, specify whether the characters that are entered should be stored on the left side or the right side of the padding spaces. The available options are **Left** and **Right**. The default value is **Left**. |
| AllowNegative | IntegerInt64Real | Specify whether the field can accept negative values. |
| AutoInsSeparator | Real | Specify whether the system should automatically insert a decimal separator. For example, if you enter **2222**, the system automatically shows **2222.00**. |
| ChangeCase | String | Specify how text that is entered in a string control should be formatted. For example, the text can be formatted as all uppercase letters, or it can use title capitalization. **Note:** This property isn't supported for Enterprise Portal. |
| DateDay | DateUtcDateTime | Specify how the day should be shown. |
| DateFormat | DateUtcDateTime | Specify the layout of a date. |
| DateMonth | DateUtcDateTime | Specify how the month should be shown. |
| DateSeparator | DateUtcDateTime | Specify the separators between year, month, and day. |
| DateYear | DateUtcDateTime | Specify how the year should be shown. |
| DecimalSeparator | Real | Specify the decimal separator. When the default setting (**Auto**) is used, the decimal separator that is specified in the system setup is used. |
| DisplaceNegative | IntegerInt64Real | Specify whether to align negative numbers to the left. |
| DisplayHeight | String | Specify the number of lines to show at the same time when the EDT is shown on a page. |
| EnumType | Enum | Specify the base enum that is used to create the EDT. |
| FormatMST | Real | Specify master currency values should be formatted. The following options are available: <br><br>- Auto<br>- Yes<br>- No<br>The default value is **Auto**. |
| NoOfDecimals | Real | Specify the number of decimal places when a value is shown on a page or a report. |
| RotateSign | IntegerInt64Real | Select this option to reverse the sign for the number. In other words, change a minus sign (–) to a plus sign (+) or a plus sign to a minus sign. |
| ShowZero | IntegerInt64Real | Specify whether to show a field that has a value of 0 (zero) as an empty field. If a value of 0 in fields of this type means null/nothing, set this property to **No**. |
| SignDisplay | IntegerInt64Real | Specify whether to show the sign of a negative number, and also whether the sign should appear before or after the number. Typically, set this property to **Auto**. However, you can set it to **None** if the **DisplaceNegative** property is used. |
| StringSize | String | Specify the maximum size of the string. |
| ThousandSeparator | Real | Specify the symbol that is used to separate thousands. |
| TimeFormat | TimeUtcDateTime | Specify how times should be formatted. |
| TimeHours | TimeUtcDateTime | Specify whether to include hours. |
| TimeMinute | TimeUtcDateTime | Specify whether to include minutes. |
| TimeSeconds | TimeUtcDateTime | Specify whether to include seconds. |
| TimeSeparator | TimeUtcDateTime | Specify the separator that is used for times. |
| TimezonePreference | UtcDateTime | Specify the time zone to convert the value to from Coordinated Universal Time (UTC). |

## Perspective properties

In Application Explorer, under the **Data Dictionary** node, there's a **Perspectives** node. A perspective is a collection of tables and views that contain the measures and dimensions for a cube. The following table describes the properties that you can set for each perspective. For information about the system properties that are available for a perspective, see the "System and common properties" section. For information about the properties for tables that are associated with a perspective, see the "Table properties" and "Table field properties" sections.

| Property | Description |
|---|---|
| ConfigurationKey | Specify the configuration key that you assign to the perspective. The configuration key determines which configurations of a perspective are included in report models that you generate. |
| HelpText | Create a string to use as a description for the perspective in a report model. |
| ID | Specify the identifier of the perspective. |
| Label | Specify the name that appears for the perspective in a report model. |
| Model | Specify the model that the perspective is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| SharedDimensionContainer | Specify whether to share items in the perspective. When you set this property to **Yes**, the items in the perspective are added to all other perspectives that are in the project, and no cube is created for the perspective. The default value is **No**. |
| Usage | Specify the materialization options for a perspective. The following options are available:<br><br>- **AdHocReporting** - The perspective is used to generate a transactional Semantic Model Definition Language (SMDL) model.<br>- **OLAP** - The perspective is used to generate a cube in a Microsoft SQL Server Analysis Services (SSAS) Business Intelligence project.<br>- **Both** - The perspective is used to generate both a transactional SDML model and a cube in an SSAS Business Intelligence project.<br>- **None** - The perspective isn't materialized.<br><br>The default value is **None**. |

## Table properties

This section describes the properties that appear in the **Properties** window for table elements in Application Explorer. Table elements are located under **Data Dictionary** &gt; **Tables**.

### Table properties

The following table describes the properties of table elements in Application Explorer.

| Property | Description |
|---|---|
| Abstract | Specify whether the table supports inheritance. The default value is **No**. If you set the value to **Yes**, the table can't be a direct target of X++ SQL statements such as **update_recordset** and **select**. **Note:** This property is unavailable when the **SupportInheritance** property is set to **No**. |
| AnalysisDimensionType | Specify the type of dimension that is created, based on the setting of the **IsLookup** property. If the **IsLookup** property is set to **Yes**, the following options are available: <br><br>- **Auto** - The table can contain both factual and dimensional data. The BI Wizard extracts dimensional data, and creates dimensions and attributes. Factual data is extracted to create measures. One child dimension is created that has attributes from the parent table.<br>- **MasterInner** - An inner (full) join is used to create relationships with this table to the child table. Each record combination for this table and the child table are generated in the dimension. One child dimension is created that has attributes from the parent table.<br>- **MasterLeftOuter** - A left outer join is used to create relationships with this table to the child table. Dimensions have additional attributes, based on values in this table that can also be empty. One child dimension is created that has attributes from the parent table.<br>- **Transaction** - The table should be used to generate only factual data (measures). Use this option when a table contains only transactional data. One child dimension is created that contains only enumeration fields from the table.<br>If the **IsLookup** property is set to **No**, the following options are available: <br><br>- **Auto** - Table can contain both factual and dimensional data. The BI Wizard extracts dimensional data, and creates dimensions and attributes. Factual data is extracted to create measures. One parent and child dimension are created.<br>- **MasterInner** - Not applicable. This option is the same as **Auto**.<br>- **MasterLeftOuter** - Not applicable. This option is the same as **Auto**.<br>- **Transaction** - The table should be used to generate only factual data (measures). Use this option when a table contains only transactional data. One child dimension is created that contains only enumeration values from the table.<br> |
| AnalysisIdentifier | Specify the field to use as the identifier for the dimension in an SSAS cube. |
| AOSAuthorization | Specify the type of operation that a user can perform on a table, depending on the user's permissions. When you set this property to **None**, no authorization check is performed. |
| CacheLookup | Specify how to cache the records that are retrieved during a lookup operation. This property exists only on tables that don't inherit from another table. On an inheritance root table, you can't set this property to **EntireTable** by using the Application Explorer **Properties** window. You must not use other techniques to assign this value to inheritance root tables. For example, don't use the **AOTsetProperty** method of the **TreeNode** class to assign this value. |
| ClusterIndex | Specify the cluster index. This property is used only for SQL optimization. |
| ConfigurationKey | Specify the configuration key for the table. Configuration keys let a system administrator enable and disable specific parts of an application. |
| CountryRegionCodes | Specify the codes for the countries/regions where the table is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client framework uses this property to enable or disable country/region-specific features. |
| CountryRegionContextField | Specify the field that is used to identify the country/region context. This property is related to the **CountryRegionCodes** property. |
| CreatedBy | Specify whether the system maintains the **CreatedBy** field for the records in a table. This field contains information about the person who created a record. |
| CreatedDateTime | Specify whether the system maintains the **CreationDate** and **CreationTime** fields for the records in a table. This field contains the date when a record was created. |
| CreatedTransactionId | Specify whether the system maintains the **CreatedTransactionId** field for the records in a table. This field contains information about the transaction that created a record. |
| CreateRecIdIndex | Specify whether an index on the **Record ID** field is created. |
| DeveloperDocumentation | Describe the purpose of a table, and explain how it's used in the program. Typically, a description contains no more than five sentences and is written as a single paragraph. |
| EntityRelationshipType | Classify a table according to common entity relationship (ER) data model notation. A table is classified as either an entity or a relationship. An entity represents an object, whereas a relationship represents an association between two objects. |
| Extends | Derive the table from the specified table. The value of this property is **null** when the **SupportInheritance** property is set to **Yes**. |
| FormRef | Specify the display menu item that is activated when a table is referenced. A display menu item is associated with a page. When you use a primary index field on a report, this page is available as a link in the report. You specify a primary index by using the **PrimaryIndex** property. If you leave this property blank, the system tries to display a page that has the same name as the table. |
| ID | The system-generated table ID. |
| IsLookup | For report models, use this property to specify whether the table information is incorporated into other tables that reference it when a report model is generated. For online analytical processing (OLAP) cubes, use this property to specify whether to generate a consolidated dimension or a distinct dimension. The following options are available: <br><br>- **Yes** - Attributes from the table should be consolidated into the parent dimension (star schema).<br>- **No** - A separate dimension should be generated for the table (snowflake schema).<br> |
| Label | Specify the label for a table. |
| ListPageRef | Specify a display menu item that points to a page that can show a list of this record type. |
| Model | Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table and a class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| ModifiedBy | Specify whether the system maintains the **ModifiedBy** field for the records in a table. This field contains information about the person who last modified a record. |
| ModifiedDateTime | Specify whether the system maintains the **ModifiedDate** field for the records in a table. This field contains the date when a record was last modified. |
| ModifiedTime | Specify whether the system maintains the **ModifiedDateTime** field for the records in a table. This field contains the date and time when a record was last modified. |
| Name | Specify the table name. |
| OccEnabled | Specify whether the optimistic concurrency mode is enabled for a table. When this mode is enabled, data isn't locked from future modification when it's fetched from the database. Data is locked only when the actual update is performed. |
| PreviewPartRef | Specify the info part or form part to use in the enhanced preview. An info part shows a collection of data fields from a specified query. It uses metadata to describe how the data appears. A form part represents a pointer to a page. |
| PrimaryIndex | Specify the primary index. Only a unique index can be selected. This property is used for database optimization and to indicate which unique index should be used as the caching key. If you don't specify a primary index, the unique index that has the lowest ID is used as the caching key. |
| ReplacementKey | Specify the fields to display as the identifier for data in some page controls. |
| ReportRef | Specify the output menu item that is activated when a table is referenced. An output menu item is associated with a report. When you use a primary index field on a report, this report is available as a link in the report. You specify a primary index by using the **PrimaryIndex** property. |
| SaveDataPerCompany | Specify whether the data for the current company is saved. If you set the property to **No**, data is saved without a company identifier (DataAreaId). **Note:** If the **SaveDataPerCompany** property on a table is set to **Yes**, the **SetCompany** property on a page design that uses the table as a data source must also be set to **Yes**. **Tip:** The status line shows the acronym for the company. Double-click the acronym to open a dialog box where you can change the company. |
| SaveDataPerPartition | A value that indicates whether the table has a system field that is named **Partition**. This property is intended to be read-only. If the table has a **Partition** field, each record is assigned to one partition. Each record is hidden from data access operations that are run under the context of other partitions. |
| SearchLinkRefName | Specify the name of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results. If the **SearchLinkRefType** property is set to **URL**, select a menu item that links to a Web Part page that shows the table data. Forms and reports on Web Part pages can display data. |
| SearchLinkRefType | Specify the type of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results. |
| SingularLabel | Specify the label that is used in a report model or a cube to show the singular name of items that are stored in the table. |
| SupportInheritance | When you set this property to **Yes**, you can set a value for other inheritance-related properties, such as **Extends** and **Abstract**. **Caution:** If you set this property to **Yes**, any fields on the table are dropped and must be created again. |
| SystemTable | Indicate whether a table appears as a system table. A table that appears as a system table can be filtered during export and import. System tables are always synchronized when you sign in. Therefore, this property might be useful for tables that you use as soon as you sign in. |
| TableContents | Specify how setup/parameter data can be reused from one customer to another. The following options are available: <br><br>- **Not specified** - Use this option for most tables.<br>- **Default Data** - Use this option for customer-independent data, such as postal codes, units, and time intervals.<br>- **Base Data** - Use this option for customer-dependent data, such as calendars, groups, and parameters.<br>- **Default+Base data** - Use this option for data where the local perception varies. For example, Chart of Accounts is customer-independent in Germany but is customer dependent in most other places.<br> |
| TableGroup | Specify the group that the table belongs to. Table groups provide a method for categorizing tables according to the type of data that they contain. You can use table groups to define whether the system should prompt users when they update or delete data from the table on pages by using the table as the data source. When you export data, you can use table groups to filter records. |
| TableType | This property replaces the **Temporary** property that is found in Microsoft Dynamics AX 2009. |
| TitleField1, TitleField2 | You can use this property in the following ways: <br><br>- Add table field data to a form caption.<br>- Show additional fields on a lookup page. The **TitleField1** property is also used when you activate the lookup list in a field on a page. The fields that you specify for the **TitleField1** and **TitleField2** properties can be merged with the key value.<br>- Show field information in a tooltip.<br> |
| TypicalRowCount | Specify the number of records that typically appear in a table. If the **AnalysisSelection** property isn't set, this property determines how records are selected by using Report Builder for SSRS. The setting of this property affects whether a drop-down list, a list box, or a filtered list box is used to select table records. |
| ValidTimeStateFieldType | Specify the type of date-time field that the system uses when it tracks data within time spans. |
| Visible | Specify the access rights when the table is used as a data source on a page or a report. If the table is used as a data source on a page, the access rights on the page can't exceed the access rights that are defined for the table. |

### Tables and report models

The following properties relate to report models that you use to add information to a report:

- AnalysisSelection
- AnalysisVisibility
- IsLookup
- SingularLabel
- TypicalRowCount

## Table field properties

The following properties relate to report models that you use to add information to a report:

- AnalysisDefaultTotal
- AnalysisLabel
- AnalysisTotaling
- AnalysisUsage
- AnalysisVisibility
- CurrencyCode
- CurrencyCodeField
- CurrencyCodeTable

| Property | Description |
|---|---|
| Adjustment | Specify whether the string field should be left-aligned or right-aligned when it's stored in the database. For example, if the 11-character string "hello world" is stored in a right-aligned field that has a **StringSize** setting of **40**, 29 space characters are stored as the prefix. **Note:** The **Adjustment** setting affects the search results when you search for a value in a table by using the **>**, **<**, **>=**, and **<=** relational operators. It doesn't affect the search results when you use the **==** operator. The **Adjustment** setting is ignored when the **StringSize** property is set to **(Memo)**. |
| AliasFor | Specify the table field that the field is an alias for. |
| AllowEdit | Specify whether users are allowed to modify data in an existing record on a page. |
| AllowEditOnCreate | Specify whether users are allowed to enter data in the field when a new record is created from a page. |
| AnalysisDefaultTotal | For report models, use this property to specify how field data is aggregated when an automatic total for the table is displayed in a report that is built by using SSRS and report models. The default value is **No**, which indicates that the field isn't automatically shown as a total. For OLAP cubes, use this property to specify the aggregate function for a measure. Use this property when the **AnalysisUsage** property is set to **Measure**. The following options are available: <br><br>- **Sum** - Return the sum of all the values in a set.<br>- **Count** - Return the number of non-null items in a set.<br>- **CountDistinct** - Return the number of distinct non-null items in a set.<br>- **Min** - Return the minimum value in a set.<br>- **Max** - Return the maximum value in a set.<br>- **None** - No aggregate function is applied.<br>- **Auto** - This option applies to derived EDTs. The value of the **AnalysisUsage** property for the parent EDT is used.<br> |
| AnalysisLabel | Specify the label to use as the caption in an SSAS cube for the table field. The label is applied to either a dimension attribute or a measure. This property is intended for situations where one of the following conditions is true: <br><br>- The **Label** property isn't defined.<br>- The **Label** property doesn't work as a caption for a dimension attribute or a measure in a SSAS cube.<br> |
| AnalysisUsage | Specify the role of the field in a cube. The following options are available <br><br>- **Attribute** - The field is a dimension attribute.<br>- **Measure** - The field is a measure.<br>- **Both** - The field is both a dimension attribute and a measure.<br>- **None** - The field is neither a dimension attribute nor a measure.<br>- **Auto** - The value of the **AnalysisUsage** property for the EDT or enumeration that the field is based on should be used.<br> |
| ConfigurationKey | Set the configuration key for the field. |
| CountryRegionCodes | Specify the codes for the countries/regions where the table field is applicable or valid. This property is implemented as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client framework and application might use this property to enable or disable country/region-specific features. |
| CountryRegionContextField | Specify the field that identifies the country/region context. See the description of the **CountryRegionCodes** property. |
| ExtendedDataType | Specify the EDT to use for this field. |
| GroupPrompt | Specify a label that is used for the field when it appears in a group. **Tip:** You can use this property to help guarantee that a field label doesn't repeat text that appears in the label for a field group. For example, if a field group on a page is labeled **Customer**, don't include this text in the **GroupPrompt** property for fields that are included in the field group. |
| HelpText | Specify the Help string for the field. The Help string is shown when the field is used on a page. |
| ID | The system-generated field ID. |
| IgnoreEDTRelation | This property is used during the migration of EDT relations. When you migrate relations from an EDT node to a table node, you can skip an invalid relation for a given table field. To skip invalid relations, set this property to **Yes**. The default value is **No**. |
| Label | Specify a label for the field. This label will appear on pages and reports. Also see the description of the **AnalysisLabel** property earlier in this table. |
| Mandatory | Specify whether a user must add data to a field on a page. Set this property to **Yes** to indicate that the default or initialization value for each data type isn't acceptable for persistence into the database. The following list shows some default values that can't be used for mandatory fields on a page: <br><br>- Empty isn't acceptable for a str (string) field.<br>- The minimum date-time isn't acceptable for date-time fields such as date and utcdatetime.<br>- A value of 0 (zero) isn't acceptable for numeric fields such as int, real, and enum.<br>finance and operations doesn't support the semantics for the **null** value that's standard in most SQL database products. Field can't be nulled in the database. Therefore, the **Mandatory** property has nothing to do with the concept of a **null** value. **Caution:** A mandatory table field can have its **EnumType** property set to an enumeration. You might define a field as an enum type that includes an item that has the integer value **0**. In this case, **0** isn't an item that's available for selection on the page. The forms system automatically calls the **validateWrite** method to enforce the setting of the **Mandatory** property. However, the **Mandatory** property has no effect on the behavior of direct X++ SQL that inserts or updates the value of a table field. In your direct X++ SQL, you can include calls to the **validateWrite** method on your table buffer variable. Your buffer variable inherits the method from the **xRecord** class. |
| MinReadAccess | Specify the mode of the automatic authorization feature. Automatic authorization has two modes of operation: surrogate foreign key and lookup. If a table in a query is tagged for surrogate foreign key authorization, and the user doesn't have access to that table but hasn't been explicitly denied, view access is granted to the table. However, not all fields are visible. The visibility is determined by the following rules: <br><br>- If **MinReadAccess** is set to **No**, no access is granted to the field.<br>- If **MinReadAccess** is set to **Yes**, view access is granted to the field.<br>- Otherwise, view access is granted if the field is part of the natural key automatic identification group, if it's a title field, or if it's a system field.<br>If a table in a query is tagged for lookup authorization, access is determined by the following rules: <br><br>- If **MinReadAccess** is set to **No**, no access is granted to the field.<br>- Otherwise, view access is granted to the field.<br> |
| Model | Specify the model that the table field is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| Name | Specify the name of the field. |
| RelationContext | Specify the mapping of a field to a specific table relation. Typically, this property is used in unit-of-measure scenarios to model data that is related to currency codes or quantities. The relation that is associated with the field can then be used to show a lookup of currency codes or quantities. There's no default value. |
| SaveContents | Specify whether the field data is saved in the database or treated as virtual field data. Virtual field data is calculated at run time when the field is displayed. This data has no physical representation in the database. **Tip:** Instead of virtual fields, you can use display and edit methods. |
| StringSize | Set the field length, in the number of characters. The maximum field length depends on the database. A value of **(Memo)** indicates that the field length is unlimited. |
| Type | Specify the base type of a field. |
| Visible | Specify whether the field should be visible in the user interface. |

## Table index properties

The following table describes the properties that are available for indexes on tables.

| Property              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowDuplicates       | If you set this property to **Yes**, the index can be nonunique. If you don't create at least one unique index, a unique index is created by combining the first index and the RecId.                                                                                                                                                                                                                                                     |
| AlternateKey          | Specify whether this index is part of an alternate key. The index field must have a unique value in every record.                                                                                                                                                                                                                                                                                                                                                   |
| ConfigurationKey      | Set the configuration key. An index field that is disabled through a configuration key is automatically removed from the index.                                                                                                                                                                                                                                                                                                                                     |
| Enabled               | Use this property to disable the index.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ID                    | The internal identifier of the object.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Model                 | Specify the model that the table index is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer.                                                                                                                                                                   |
| Name                  | Specify the index name.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| UniqueAcrossCompanies | This property is for internal Microsoft use only. The available values are **Yes** and **No**. The default value is **No**. The value of this property is ignored when the **AllowDuplicates** property is set to **No**. However, when **AllowDuplicates** is set to **Yes**, a value of **Yes** for **UniqueAcrossCompanies** can improve the performance of some cross-company queries. The performance improvement is caused by changes to the caching of data. |
| ValidTimeStateKey     | Specify whether this index key is used to determine the valid time state relationship with the parent table. The default value is **No**. **Tip:** To enable this property, set the **AllowDuplicates** property to **No** and the **AlternateKey** property to **Yes**.                                                                                                                                                                                   |
| ValidTimeStateMode    | Specify whether gaps are allowed between two date-effective records. The default value is **NoGap**. **Tip:** To enable this property, set the **AllowDuplicates** property to **No**, the **AlternateKey** property to **Yes**, and the **ValidTimeStateKey** property to **Yes**.                                                                                                                                                                        |

> [!NOTE]
> Pages sort on the first index.

## Table relation properties

### List of properties

The following table describes the properties for a table relation in Application Explorer.

| Property | Description |
|---|---|
| Cardinality | The number of times that each primary key value from the referenced table must occur in the foreign key column of the current table. For example, the **OneMore** value means one or more, but not zero. This value indicates that every parent key value must occur in the child table's foreign key column at least one time. A relation node under a SalesLine table might use the **OneMore** value when the business rule requires that every record in the parent SalesTable table relate to at least one item that's being sold. Currently, the **Cardinality** property isn't used. However, future releases might use this property and the **RelatedTableCardinality** property. |
| CreateNavigationPropertyMethods | A value of **Yes** instructs the system to generate navigation methods on the table buffer class for each foreign key relation node. |
| EDTRelation | If the value is set to **Yes**, a software tool was used to migrate this relation to its current location from an old EDT relation. |
| EntityRelationshipRole | This property clarifies the semantics of a relationship that is defined on a table. A role name should be either a noun or a noun phrase. The role name should indicate the role of the associated table in relation to the associating object. Alternatively, the role name should be a short phrase that starts with a present-tense verb that indicates the role that the table plays in the relationship. Role names aren't required when the relationship is unambiguous. |
| Model | The model that this relation is part of. |
| Name | A descriptive name that you choose for the relation. |
| NavigationPropertyMethodNameOverride | Specify the name of the navigation method. If you don't specify a value, the navigation method uses the value from the **RelatedTableRole** property. |
| RelatedTableCardinality | Specify whether the foreign key field value in the current table can be **null** in some or all records of the current table. The following options are available: <br><br>- **ZeroOne** means zero or one. This value indicates that the foreign key field in a child record can be **null**.<br>- **ExactlyOne** indicates that the foreign key field can't be **null** in any child record.<br> |
| RelatedTableRole | Enter a text value to describe the purpose of the referenced parent table in this relationship. When a table has only one relation that references a given parent table, you can use the name of the parent table. Sometimes, a table has more than one relation to a given referenced parent table. In this case, the value of the **RelatedTableRole** property should describe the relation enough to distinguish the relation's purpose from the other relation to the same parent table. The value of this property can be used as the value of the **JoinRelation** property of a data source relation under an Application Explorer query. In standard cases, this usage is recommended, because it reduces denormalization. This property interacts with the **UseDefaultRoleNames** property. |
| RelationshipType | Select a value that describes the subtle relationship between two tables. For example, the **Composition** value indicates that the child record can't meaningfully exist unless it's related to a specific parent record. The record for the fourth floor in the Floor table can't exist unless it references a record in the parent Building table. **Note:** The DeleteActions should be compatible with this property setting. For a Composition relationship, the DeleteActions should include delete cascade behavior. Currently, the **RelationshipType** property isn't used. However, a future release might use this property. |
| Role | Specify a name that describes the meaning or role of the relation. For example, one relation to a Department table could track the department that the employee currently belongs to. Another relation could track the department that the employee requested a transfer to. Although both these relations are relations to the Department table, they fill different roles. As the value of this property, it's a good idea to join the names of the child table and parent table by using an underscore (_) character. For example, enter **SalesTable_SalesLine**. This property interacts with the **UseDefaultRoleNames** property. |
| Table | The table that the relation refers to. |
| UseDefaultRoleNames | A value of **Yes** indicates that the system must generate default values for the **Role** and **RelatedTableRole** properties. Even when you set this property to **Yes**, the generated values for **Role** and **RelatedTableRole** don't appear in the **Properties** window. Additionally, the **TreeNode** class doesn't use the generated values. However, the **DictRelation** reflection class does use the generated values. |
| Validate | A value of **Yes** indicates that when a page inserts a record into the child table, the insertion is rejected unless the related record exists in the referenced parent table. Additionally, when a page deletes a record from the parent table, the deletion is either rejected or cascades to the related records in the child table. Set the value to **No** when the **RelationshipType** property is set to **Link**. You might also set the value to **No** in special temporary cases, such as during some upgrade scenarios. When you set the value back to **Yes**, no validation occurs for records that were inserted or deleted while the value was **No**. **Caution:** A value of **Yes** for the **Validate** property doesn't prevent direct X++ SQL data operations from deleting parent records or inserting child records that violate the integrity of foreign key data. |

> [!NOTE]
> When you set the **SaveDataPerCompany** property to **Yes** for both tables, the system adds the **DataAreaId** field to each relationship.

### RelatedTableRole and query JoinRelation

This section describes how you can use the **RelatedTableRole** property to simplify the creation of a new query. If you enter an explicit value for the **RelatedTableRole** property on a table relation, you can use that value to populate the **JoinRelation** property on a data source relation under a **Queries** &gt; **MyQuery** node in Application Explorer. Use this method to specify the fields of the join in one location. If the join fields ever change, you must update the join in only one location. Before you can set a value for the **JoinRelation** property, you must delete the values of the **Field** and **RelatedField** properties.

### CreateNavigationPropertyMethods and RelatedTableRole

When you set the **CreateNavigationPropertyMethods** property to **Yes** on a table relation, the system generates navigation methods for the table buffer class. A navigation method links two table buffer instances by using their foreign key relationship. The **UnitOfWork** class is one area where this navigation linkage is used. The name of a navigation method comes from the value of the **RelatedTableRole** property on the table relation. This behavior occurs when you explicitly set the **RelatedTableRole** value in the **Properties** window, and when the system generates the **RelatedTableRole** value because the **UseDefaultRoleNames** property is set to **Yes**. These property values generate the following navigation method on the child CustTable buffer. Most directly, the navigation method name is copied from the value of the **RelatedTableRole** property.

```xpp
public final CustBankAccount BankAccounts([CustBankAccount relatedTable])
```

#### NavigationPropertyMethodNameOverride property

The following list describes cases where you must override the name that the system generates for a navigation method on a table buffer class:

- The table class already has a method name that matches the values of the **RelatedTableRole** property.
- The value of the **RelatedTableRole** property exceeds the maximum length that can be used for a method name.

In these cases, you must choose a valid name for the navigation method and assign that name as the value of the **NavigationPropertyMethodNameOverride** property on the table relation.

## Understanding the RelationshipType enumeration

When you add a node under table relations, you can set the value of the **RelationshipType** property for the new relation. The list of possible values for the **RelationshipType** property is the list of elements in the **RelationshipType** enumeration. This section describes the meaning of each element in the **RelationshipType** enumeration.

### Description of elements

The following table describes the elements of the **RelationshipType** property.

| Element name | Description | Automatic inference |
|---|---|---|
| NotSpecified | This element is often the default value of the **RelationshipType** property. | When the **RelationshipType** property has a value of **NotSpecified**, the system infers an appropriate value. The system infers the value in the following sequence: <br><br>- Specialization<br>- Link<br>- Composition<br>- Aggregation<br>- Association<br>For example, if the criteria for both Composition and Aggregation are met, the system infers Composition, because Composition occurs earlier in the list. |
| Specialization | This element applies only to table inheritance, to relationships between base and derived tables. | The system sets the **RelationshipType** property to **Specialization** whenever table inheritance is involved. |
| Link | This element is a nonrelational relationship. It requires that the **Validate** property be set to **No**. This type of relationship supports navigation between pages that list many records from a table and pages that provide detail fields for one record from the table. | Link is used only to support the migration of EDT link relations during upgrade from earlier versions. Migration tools create this type relationship, but you must not. |
| Composition | This element is a stronger type of Aggregation relation. A table must not have more than one Composition relation. For example, a building is composed of rooms, and a given room can't exist in more than one building. | If the criteria for Composition are met, but you manually assign a value of **Aggregation** or **Association**, the system leaves the value as **Aggregation** or **Association**. |
| Aggregation | This element is appropriate when the child table is considered subordinate to the entity of the parent table. | The system infers Aggregation when one of the following conditions is true: <br><br>- The parent table has a delete action node that is defined to use this relation node.<br>- Any foreign key field for this relation in the child table has the **Mandatory** property set to **Yes**.<br>If the criteria for Aggregation are met, but you manually assign a value of **Association**, the system leaves the value as **Association**. |
| Association | This element is the concept of a standard foreign key. | You must set the **RelationshipType** property to **Association** if the system doesn't set the value of the property to anything, and if both Aggregation and Composition are inappropriate. |

## View properties

The properties for views are the same as the properties for tables. However, because views are read-only, you can't change most of their properties. Some properties have fixed values, and some inherit from the data sources that the query uses to define the view. The following properties for views relate to data analysis when you're using SSRS. You can change all these properties.

- AnalysisVisibility
- AnalysisSelection
- TypicalRowCount
- IsLookup
- SingularLabel

The following table describes the properties that you can set for a view.

| Property | Description |
|---|---|
| AOSAuthorization | Specify which data access operations require verification of user permissions. |
| CacheLookup | The record cache level for the table. |
| ClusterIndex | The cluster index of the table, if there's a cluster index. |
| ConfigurationKey | Set the configuration key for the view. |
| CountryRegionCodes | Specify the codes for the countries or regions where the menu is applicable or valid. Implement this property as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country or region-specific features. |
| CountryRegionContextField | Specify the field that identifies the country/region context. See the description of the **CountryRegionCodes** property. |
| DeveloperDocumentation | Describe the purpose of a view, and explain how it's used in the program. Typically, a description contains no more than five sentences and is written as a single paragraph. |
| EntityRelationshipType | Classify a view according to common entity relationship (ER) data model notation. A view is classified as either an entity or a relationship. An entity represents an object, whereas a relationship represents an association between two objects. |
| FormRef | Specify the default page for the view. The default page is the page that shows when the user activates Jump to Main Table by using the shortcut menu for a field on a page. The page is referenced through a menu item of the **Display** type. If you leave this property blank, MorphX tries to activate a page that has the same name as the table that you're referring to. |
| ID | The internal identifier of the object. |
| Label | Specify a user-friendly name for the view. |
| ListPageRef | Specify a display menu item that points to a page that can show a list of this record type. |
| Model | Specify the model that the view is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| Name | Specify the name of the view. This name is used when you refer to the view from the X++ language. |
| PreviewPartRef | Specify the info part or form part to use in the enhanced preview. An info part shows a collection of data fields from a specified query. It uses metadata to describe how the data appears. A form part represents a pointer to a page. |
| PrimaryIndex | Specify the primary index of the view. Only a unique index can be selected. This property is used for database optimization and to indicate which unique index should be used as the caching key. If you don't specify a primary index, the unique index that has the lowest ID is used as the caching key. |
| Query | Specify the query that is the source of data for the view. You can use this property instead of adding data sources directly to the view. |
| ReportRef | The name of the default report for the table. |
| SaveDataPerCompany | Set this property to **Yes** for company-specific tables. Set it to **No** if the data is related to cross-companies, installation, a database, Application Explorer, tracing, or OLAP. For example, the SysTraceTable or OLAPServerTable table specifies whether data should be saved for that table on a per-company basis, or whether the data should be available without any company affiliation. If the **SaveDataPerCompany** property on a table is set to **Yes**, that table has a **DataAreaId** column that contains the company identifier. If the table property is set to **No**, the **DataAreaId** column is removed from the table. |
| SaveDataPerPartition | A value that indicates whether the view has a system field that is named **Partition**. This property is intended to be read-only. If the view has a **Partition** field, each record is assigned to one partition. Each record is hidden from data access operations that run under the context of other partitions. |
| SearchLinkRefName | The name of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results. |
| SearchLinkRefType | The type of the menu item that links to information on a website about a table record that is listed in the Enterprise Portal search results. |
| SystemTable | A value that indicates whether a table is a system table. System tables can be filtered during export and import, and are always synchronized when you sign in. Therefore, this property might be useful for tables that you use as soon as you sign in. |
| TableContents | Specify how setup/parameter data can be reused from one customer to another. The following options are available: <br><br>- **Not specified** - Use this option for most tables.<br>- **Default Data** - Use this option for customer-independent data, such as postal codes, units, and time intervals.<br>- **Base Data** - Use this option for customer-dependent data, such as calendars, groups, and parameters.<br>- **Default+Base data** - Use this option for data where the local perception varies. For example, Chart of Accounts is customer-independent in Germany but is customer dependent in most other places.<br> |
| TableGroup | Specify the group that the view belongs to. Table groups categorize tables and views according to the type of data that they contain. Views can belong to the same table groups as a table. |
| TitleField1, TitleField2 | The information that is shown in the window caption for the view. The caption is constructed from the following elements: <br><br>- The **TitleField1** label, followed by colon (:) and a space<br>- The value of the current record in the column that is used for **TitleField1**, followed by a comma (,)<br>- The value of the current record in the column that is used for **TitleField2**<br> |
| ValidTimeStateEnabled | Specify whether the view supports the valid time state feature of the underlying table. The default value is **No**. You can set this property to **Yes** only if both the following conditions are true: <br><br>- The underlying table is a valid time state table.<br>- The view has **ValidFrom** and **ValidTo** in its **Fields** list.<br> |
| Visible | Specify the access rights when the table is used as a data source on a page or a report. If the table is used as a data source on a page, the access rights on the page can't exceed the access rights that are defined for the table. |

## Data set properties

This section describes the properties on data set elements in Application Explorer. The **Data Sets** node is a high-level node in Application Explorer. Use data sets to access data in Enterprise Portal.

### Description of properties

The following table describes the properties that are available on data set nodes in Application Explorer.

| Property | Description                   |
|----------|-------------------------------|
| Name     | Set the name of the data set. |

### Data Sources properties

The following table describes the properties for the **Data Sources** node of the data set.

| Property | Description |
|---|---|
| ChangeGroupMode | Specify how changes to the data sources are committed. The following options are available: <br><br>- **None** - The changes to any data source for the data set are committed independently of changes to the other data sources.<br>- **ImplicitInnerOuter** - All the data sources that are inner-joined or outer-joined work as a single unit. All changes are committed successfully, or they're rolled back if an error occurs.<br> |

## Data set data source properties

The following table describes the properties that are available for data set data sources.

| Property | Description |
|---|---|
| AllowCheck | Specify whether security checks occur before the data set is accessed. The following options are available: <br><br>- **Yes** - The user's read permissions are verified before the data set is accessed.<br>- **No** - The user's read permissions are verified only after the data set is accessed. No data is retrieved if the user lacks sufficient permission for the underlying data sources.<br>**Yes** is the default value and is usually recommended. |
| AllowCreate | Specify whether users can create new records in the data source (that is, in the table for the data source). |
| AllowDelete | Specify whether users can delete records in the data source (that is, in the table for the data source). |
| AllowEdit | Specify whether users can modify the data. **Tip:** You can set the **AllowEdit** property for the whole data source here. The same property also exists on each field in the data source, so that you can prohibit modifications for individual fields. |
| AutoNotify | This property isn't used for data sets. |
| AutoQuery | This property isn't used for data sets. |
| AutoSearch | This property isn't used for data sets. |
| CounterField | Specify one of the fields in the data source as a counter for the data set. The field must be an index on the underlying table for the data source, and it must be of the **real** type. This property helps guarantee that a record that is inserted in a data set has a line number that corresponds to the actual sequential position in the data. For example, if a new line is inserted between lines 3 and 4, the new line becomes line number 3.5. |
| CrossCompanyAutoQuery | Specify whether the data source retrieves data from more than one company database. |
| DelayActive | Use this property to delay execution of the active method for the data source. If you set this property to **Yes**, the active method is activated only after a delay of 20 milliseconds. When a user scrolls through a data source, the active method isn't called on every record. Instead. it's called only on the final record that the user selects. **Tip:** The **DelayActive **property is useful when two data sources are linked (that is, when the **LinkType** property is set to **Delayed**). This property is part of the AutoJoin system. |
| Index | Set the index that is used to specify a sorting order. You can choose any of the indexes on the table. If you specify an index in this manner, it's used as an index hint on each query to the database. The index specifies both an access path and a sort order for the records in the data set, based on this data source. The initial sort order for the records is prioritized in this manner: <br><br>- If sort fields are added to the data source query, the sort specification is used.<br>- If an index is specified in the **Index** property on the data source, the sort order that is implicitly specified in that index is used.<br>- If the data source is autojoined with another data source, the system finds the most appropriate index for this join and then sorts the data according to that index.<br>- If nothing else is specified, the sort order that is implicitly specified in the first index (the index that has the lowest ID) on the table that is used in the page data source is used.<br>When no index hints are specified, the database management system locates an applicable access path. This access path is based on the information in the query that is supplied. The user can change the sort order for a page by using the query dialog box. |
| InsertAtEnd | Specify whether a new record is created when the user moves focus past the last record in the table. |
| InsertIfEmpty | Specify whether a blank record is inserted if there are no records in the table. If you set this property to **No**, you must manually create a new record. |
| JoinSource | Use this property to join two data sources. Set this property when two or more tables are used as the data source, and you want to join them. |
| LinkType | Use this property to maintain an active link between two data sources. When focus changes in the first data source, the corresponding record or records in the second data source are selected. For example, a customer table and a table of transactions is used for each customer. When the user scroll from one customer to the next, the transaction list is automatically updated to show transactions for the current customer. Set this property to **Delayed** for the outer (externally linked) data source. The linked data source is updated only after a delay of 100 milliseconds. This delay helps guarantee that the linked data source isn't updated while the user is scrolling through a data source. The update occurs only after the user finally focuses on a record. This property is part of the AutoJoin system. |
| Name | Set the name of the data source. This name should be the same as the name of the underlying table. |
| OnlyFetchActive | Specify whether to fetch all fields in the data source or only those fields that are used by the data set. When this property is set to **Yes**, records can't be deleted from the data set. This restriction helps preserve data integrity, because it helps guarantee that a delete operation is never tried on incomplete records. |
| OptionalRecordMode | Specify the create and delete behavior for records on an outer-joined table. The following options are available: <br><br>- **ImplicitCreate** - When no record is saved in the database, create an outer-joined record and joined tables as soon as the parent record becomes active. If the outer-joined record or its children aren't changed, they'll be deleted when the parent record is no longer active.<br>- **ExplicitCreate** - When no record is saved in the database, treat this record as disabled until the user explicitly triggers creation by using the **Optional Record** check box. When the record exists, clearing the check box deletes this record.<br>- **None** - No special create or delete behavior occurs for an outer-joined record.<br> |
| StartPosition | Specify whether the first record or the last record should be the current record when the data set is accessed. |
| Table | Set the table that is used as the data source. |
| ValidTimeStateAutoQuery | Specify the types of queries for date effectivity (**AsOfDate** or **DateRange**). |
| ValidTimeStateUpdate | Specify the types of updates for an existing date-effective record. The following options are available: <br><br>- **CreateNewTimePeriod** - On the record that's becoming the previous record, the **ValidTo** date field is set to a date that is no later than the current date. In the same transaction, the new current record has its **ValidFrom** field set to immediately after **ValidTo** date of the previous record.<br>- **Correction** - The **ValidFrom** or **ValidTo** value of existing rows must be modified to keep the date-effective data valid after the record set is updated.<br>- **EffectiveBased** - Records in the past can't be edited. Records that are currently active are edited in a manner that resembles CreateNewTimePeriod mode. Future records are edited in a manner that resembles Correction mode.<br>The default value is **CreateNewTimePeriod**. |

## Form properties

This section describes the properties that you set on forms in Application Explorer. To provide a uniform application interface, many properties have **Auto** values. You can create forms by using a drag-and-drop operation and then manually set several properties. To specify the name of a form, set the **Name** property in the **Properties** window for the form. All other properties on the top-level node for the form are system properties and are read-only.

## Form design properties

Most properties on the **Design** node for a form also exist on the individual controls. Examples include the **Width** and **Height** properties. However, when you set a property on the **Design** node instead of setting it on a control, the setting affects the whole form. A few properties exist only on the **Design** node. The following table describes these properties.

| Property | Description |
|---|---|
| AlignChild | Specify whether a control within a group follows the **AlignChildren** property setting for the group or for the overall form design. For example, **AlignChildren** is set to **Yes** on the **Design** node for the form, but you don't want a particular group to be arranged together with the other groups. In this case, set **AlignChild** to **No** for that group. |
| AlignChildren | Align the child controls within a container. |
| AllowDocking | Specify whether a form can be attached to the client workspace. The default value is **No**. |
| AllowFormCompanyChange | Specify whether the form supports company changes when it's used as a child form with a cross-company dynamic-link library (DLL). The default value is **No**. |
| AllowUserSetUp | Specify whether a user can move controls on a form and can change the value of control properties. This property is also found on the design of a form. The following options are available: <br><br>- **No** - Users can't customize any controls in this container.<br>- **Restricted** - Users can change properties of individual controls, but they can't move controls.<br>- **Yes** - There are no restrictions on the user setup.<br>The default value is **Yes**. **Caution:** Full user setup isn't allowed if any of the parent containers for the control have restrictions on the user setup level. The **AllowAdd** property on form data sources determines whether a user can add a field to a form. |
| AlwaysOnTop | Specify whether the form always appears on top of other windows in the z-order. The default value is **No**. |
| ArrangeMethod | Specify whether to arrange child field groups in columns or in rows. |
| ArrangeWhen | Specify when the controls in the container should be arranged. The following options are available: <br><br>- Startup<br>- On demand<br>- Never<br>- Default<br>- Auto<br>The default value is **Startup**. |
| BackgroundColor | Specify the color that is used for the background of the control. To make the background opaque or transparent, use the **BackStyle** property. |
| BottomMargin | Set the bottom margin of the form in pixels. The default value is **Auto**. |
| Caption | Specify the heading for grouped controls. Use a label for this property. |
| ColorScheme | Specify the color palette for the control. To change the color palette for the whole form, set the **ColorScheme** property for the largest container, and keep the default values for the individual controls. |
| Columns | Specify the number of columns that show the information. **Caution:** Field groups on the underlying table are never split into more than one column. |
| ColumnSpace | Set the amount of space between columns in container controls. |
| DataSource | Specify the table that data in the control comes from. To set a particular field within the table, use the **DataField** property. If the control opens another form, relations between the data source for the control, as specified by this property, and the data source on the other form help guarantee that records in the second form are dynamically selected. For example, a customer is selected in one form, and the control opens a form that shows customer transactions. In this case, the second form shows a range of customer transactions that apply to the current customer. **Caution:** If you set the **DataSource** and **DataField** properties, their settings override any settings for the **DataMethod** or **ExtendedDataType** properties. |
| Font | Change the font properties for the control by using the **Font** dialog box. Use the dialog font to specify the font, font style, and font size. |
| Frame | Specify the frame style that the form uses. |
| Height | Specify the height of the form or control in pixels. |
| HideIfEmpty | Use this property to hide a container control if it's empty. This property has no effect if the **Width** and **Height** properties of the container are set to **Auto**, because the size of the control is 0 (zero) in this case. |
| HideToolBar | Hide form-specific buttons on the toolbar. |
| ImageMode | Define how the bitmap that is specified by the **ImageName** property appears in a control. The following options are available: <br><br>- Normal<br>- Size to fit<br>- Side by side<br>- Center<br>The default value is **Normal**. |
| ImageName | Specify the image that is shown for a control. You can select only .bmp files. To use one of the resource files, use the **ImageResource** property instead. |
| ImageResource | Use one of the images from the image resource file as the image for a control. Specify the ID of the image. You can select only an image from the integrated resource file. To use another file type, use the **ImageName** property. |
| LabelFont | Change the font for the text that is supplied in the **Label** property. |
| Left | Change the position of the upper-left corner of the form. There are several predefined settings. You can also specify an exact position in pixels. The following predefined settings are available: <br><br>- Auto (left)<br>- Auto (right)<br>- Left edge<br>- Right edge<br>- Center<br>The default value is **Auto (left)**. |
| LeftMargin | Change the default left margin of the form. The margin is specified in pixels. |
| MaximizeBox | Specify whether to include the maximize box in the upper-right corner of the enclosing window. The default value is **Yes**. |
| MinimizeBox | Specify whether to include the minimize box in the upper-right corner of the enclosing window. The default value is **Yes**. |
| Mode | Specify the data entry mode for the form. |
| Model | Specify the model that the form is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| RightMargin | Change the default right margin of the form. The margin is specified in pixels. |
| SaveSize | Set this property to **Yes** to save the size of the form. |
| ScrollBars | Specify whether scroll bars are enabled in the form. |
| SetCompany | Cause the system to change the company when the form receives focus. **Note:** If the **SaveDataPerCompany** property on a table is set to **Yes**, the **SetCompany** property on a form design that uses the table as a data source must also be set to **Yes**. |
| StatusBarStyle | Specify how the status bar appears in a form. Use this property to hide the status bar, show only Help information, show status bar elements according to the **WindowType** setting, or always show the full status bar. **Note:** Forms that have a WindowType setting of **ListPage**, **ContentPage**, or **Workspace** ignore this property. |
| Style | Specify the style of the form. This property controls the form design pattern that is used for the form. The following options are available: <br><br>- Auto<br>- DetailsFormMaster<br>- DetailsFormTransaction<br>- Dialog<br>- DropDialog<br>- FormPart<br>- ListPage<br>- Lookup<br>- SimpleList<br>- SimpleListDetails<br>- TableOfContents<br>The default value is **Auto**. |
| TitleDataSource | Specify the data source to use in the form caption. |
| Top | Change the position of the top of the form. There are several predefined settings. You can also specify an exact position in pixels. The following predefined settings are available: <br><br>- Auto<br>- Top edge<br>- Bottom edge<br>- Center<br>The default value is **Auto**. |
| TopMargin | Set the top margin of the form in pixels. The default value is **Auto**. |
| UseCaptionFromMenuItem | Specify whether to replace the form caption with the label from the calling menu item. This property enables the caption of the form to be changed when the form is opened. The default value is **No**. |
| ViewEditMode | Specify whether the form opens in read-only mode or as a form that allows you to change fields. The following options are available: <br><br>- **View** - Open the form as read-only.<br>- **Edit** - Open the form in edit mode.<br>- **Auto** - Open the form in the appropriate mode.<br>The default value is **Auto**. |
| Visible | Use this property to hide the form. **Caution:** You can't use the **Visible** property to enforce access restrictions. The user can change the visibility for the controls in the **Form Setup** dialog box. To enforce access restrictions, use the **Enabled** and **NeededAccessLevel** properties instead. |
| Width | Change the width of the form in pixels. |
| WindowResize | Specify whether the form can be resized. |
| WindowType | Specify the type of window. |
| WorkflowDataSource | Set the root data source for the workflow on a form. The root data source that you specify should be the same root data source that is specified in the query that used for the **Document** property on the workflow template. |
| WorkflowEnabled | Set this property to **Yes** to enable the workflow menu bar on the form. The default value is **No**. |
| WorkflowType | Specify the workflow type, which determines the following items and behaviors: <br><br>- The workflow document to use. The workflow document exposes calculated fields and identifies the query that exposes data fields for the workflow.<br>- Whether the user can configure tasks and approvals.<br>- The workflow categories to use when a workflow type is assigned to a specific module.<br>- Menu items and event handlers.<br> |

## Help document set properties

A document set is a collection of Help documentation that you associate with a workspace. When you publish a content element, use metadata to add your content element or table of contents information to a document set. To manage the relationship between a workspace and a document set, Application Explorer includes a node named **Help Document Sets**. Each document set in the **Help Document Sets** node includes a collection of properties. You edit these properties when you add a new document set or change the relationship between a document set and a workspace. **Caution:** A workspace can be associated with only one document set. Although Application Explorer lets you add a new document set and associate it with a workspace, you no longer see documentation from the document set that you replaced. Typically, you use **UserDocumentation** as the document set for any content element or table of contents entries that you publish to the Help server. The following table describes the properties for a document set in the **Help Document Sets** node of Application Explorer.

| Property | Type | Description |
|---|---|---|
| DocumentSetName | String | A name that uniquely identifies the document set. The name is limited to 40 characters and must not contain whitespace. Use the value of this property when you set the value of the **DocumentSets** metadata element in a content element or table of contents file. |
| DocumentSetDescription | String | The text or label to display for the document set. This value appears in the **Search content from** list of the **Options** menu of the Help viewer. |
| AddToApplicationHelpMenu | Boolean | Set this property to **Yes** if you want the document set to appear on the **Help** menu of the application workspace. |
| AddToDeveloperHelpMenu | Boolean | Set this property to **Yes** if you want the document set to appear on the **Help** menu of the developer workspace. |
| UserDocumentSet | Boolean | Set this property to **Yes** to associate the document set with the application workspace. If you set this property to **No**, you can't view the context-sensitive (F1) Help that Microsoft published. |
| DeveloperDocumentSet | Boolean | Set this property to **Yes** to associate the document set with the development workspace. If you set this property to **No**, you can't view the context-sensitive (F1) Help that Microsoft published. |
| 1 | Help server | The documentation is stored on the Help server. This option is used together with the **UserDocumentation** document set and any document set that files are published for on the Help server. |
| 2 | World Wide Web | The documentation is stored on MSDN or a similar website. This option is required for the **DeveloperDocumentation** documentation set and shouldn't be used with any other document set. |

## Menu properties

The following table describes the properties that are available for menus under the **Menus** node in Application Explorer.

| Property | Description |
|---|---|
| ConfigurationKey | Set the configuration key for the menu. |
| CountryRegionCodes | Specify the codes for the countries or regions where the menu is applicable or valid. Implement this property as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country or region-specific features. |
| DisabledImage | Specify the button image that is used when the menu is disabled. If you don't set this property, the system uses the setting of the **NormalImage** property to generate an image. |
| DisabledImageLocation | Specify the location of the image that is used for a disabled control. You can use images from a file, the **Resources** node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the **DisabledImage** property. If you don't set this property, the system uses the setting of the **ImageLocation** property to generate an image. |
| ImageLocation | Specify the location of the image that is used. You can use images from a file, the **Resources** node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the **NormalImage** property. |
| Label | Set the name of the menu that is shown to the user. |
| MenuItemName | Specify the menu item to include on the menu. The values that are available depend on the value of the **MenuItemType** property. |
| MenuItemType | Specify the type of the menu item. There are three categories of menu items: <br><br>- Display<br>- Output<br>- Action<br>The value that you set for this property determines the list of menu item names that appears in the list for the **MenuItemName** property. |
| Model | Specify the model that the menu is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can be located in exactly one model in a layer. The same element can be located in a customized version in a model that is in a higher layer. |
| NormalImage | Specify the image that is used when the menu is enabled. |
| Parameters | Specify one or more values that are passed to an object. These values resemble the parameters that are passed to a method. A parameter supplies a value that is then used to perform the task. There's no default value. |
| SetCompany | If you set this property to **Yes**, every time that the menu opens, the company changes to the company that you specified when the menu first started. |
| Shortcut | Specify the keyboard shortcut that opens the menu. For example, you can press Ctrl+F3 to open the menu. There's no default value. |
| ShowParentModule | Specify whether to update the navigation pane, based on the parent module of the menu item. The following options are available: <br><br>- **Yes** - Always update the navigation pane, based on the parent module of the menu item.<br>- **No** - Leave the navigation pane unchanged, even if the parent module of the menu item differs from the current module.<br>The default value is **Yes**. |

## Menu item properties

All menu items (display, output, and action), including menu items for web menus, have the following properties.

| Property | Description |
|---|---|
| ConfigurationKey | Select the configuration key that enables the menu item. Use the key for the module that the object belongs to. |
| CopyCallerQuery | Specify whether to copy the query from the calling form to the target form. This property enables the target form to show the same data that you viewed in the original form. The default value is **Auto**. |
| CorrectPermissions | Specify whether correct permission should be available for selection when assigning privileges to the menu item. The following options are available: <br><br>- **Auto** - The permission is available for selection as a privilege on this menu item's **Privileges** node under the **Entry Points** node.<br>- **No** - The permission isn't available for selection as a privilege on the menu item.<br>The default value is **Auto**. |
| CountryConfigurationKey | Optional: Set a country/region-specific key in addition to or instead of a standard configuration key. |
| CountryRegionCodes | Specify the codes for the countries/regions where the menu item is valid. Implement this property as a comma-separated list of ISO country codes in a single string. The values must match data in the global address book. The client uses this property to enable or disable country/region-specific features. |
| CreatePermissions | Specify whether create permission should be available for selection when assigning privileges to the menu item. The following options are available: <br><br>- **Auto** - The permission is available for selection as a privilege on this menu item's **Privileges** node under the **Entry Points** node.<br>- **No** - The permission isn't available for selection as a privilege on the menu item.<br>The default value is **Auto**. |
| DeletePermissions | Specify whether delete permission should be available for selection when assigning privileges to the menu item. The following options are available: <br><br>- **Auto** - The permission is available for selection as a privilege on this menu item's **Privileges** node under the **Entry Points** node.<br>- **No** - The permission isn't available for selection as a privilege on the menu item.<br>The default value is **Auto**. |
| DisabledImage | Specify the image that is used when the menu item is disabled. If you don't set this property, the system uses the setting of the **NormalImage** property to generate an image. |
| DisabledImageLocation | Specify the location of the image that is used for a disabled control. You can use images from a file, the **Resources** node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the **DisabledImage** property. If you don't set this property, the system uses the setting of the **ImageLocation** property to generate an image. |
| EnumTypeParameter and EnumParameter | Optional: Select an enumerated type as a parameter for the object, and then select an enumeration value as the value of the **EnumParameter** property. Typically, use these properties when one form is used in several situations. You can change the behavior of the form, depending on the **EnumParameter** value. For example, the **PriceDiscGroup** form is used by three display menu items (**PriceDiscGroup_***), each of which has a different **EnumParameter** value. In the form's **init** method, a switch construct validates the value, and then the form is created. |
| ExtendedDataSecurity | Specify whether the menu item appears under all companies instead of in the context of a single company. The default value is **No**. |
| FormViewOption | Specify the form mode to use. The following options are available: <br><br>- Auto<br>- Grid<br>- Details<br>The default value is **Auto**. |
| HelpText | Create a Help string for the menu item. The text appears on the status bar when you select the object that the menu item opens (for example, a form). **Note:** To write a Help article for the menu item, in Application Explorer, in the **Application Documentation/Menu Items** node, find the article that has the same name as your menu item. This article appears instead of any Help article that was written about the object that the menu item opens. |
| ImageLocation | Specify the location of the image that is used for a control. You can use images from a file, the **Resources** node in Application Explorer, or an embedded resource. The value that you select for this property determines the values that are available for the **NormalImage** property. |
| Label | Select the label to use as the name that appears for the item on menus and buttons. |
| LinkedPermissionObject | If the permissions of another object (for example, a form or report) should be applied to this menu item, select the object. Typically, use this property for action menu items. |
| LinkedPermissionType | Specify the type of the object that is specified by the **LinkedPermissionObject** property. |
| MultiSelect | Select whether the menu item can be used on multiple record selections in forms. |
| Model | Specify the model that the table is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can be located in exactly one model in a layer. The same element can be located in a customized version in a model that is in a higher layer. |
| Name | The name of the menu item. |
| NeededAccessLevel | Define the minimum access that is required for the menu item to appear on a menu or a button. Use this property to set access to the menu item for different user groups. |
| NeedsRecord | Specify whether a button that represents the menu item is enabled if no record is present. The default value is **No**. Use this property to help guarantee that an action can be completed. For example, you have a menu item button that opens a detail form. You might want to disable the button if there are no records on the list page. |
| NormalImage | Specify the image that is used when the menu item is associated with an enabled button control. |
| Object | Select an object of the object type that is specified in the **Class** property. |
| ObjectType | Select the type of object that the menu item opens. **Caution:** Use **SSRSReport** for a menu item for an SSRS report. Don't use **SQLReportLibraryReport** for new menu items. The **SQLReportLibraryReport** option is obsolete and will be removed in a future version. |
| OpenMode | Specify the view mode of the target form. Use this property to specify whether the target form opens in edit mode or read-only mode. The following options are available: <br><br>- Auto<br>- View<br>- Edit<br>- New<br>The default value is **Auto**. |
| Parameters | Optional: Specify the arguments that are passed to the object. |
| Query | Select the query that is passed to the target form for the **InitialQuery** method. |
| ReadPermissions | Specify whether read permission should be available for section when assigning privileges to the menu item. The following options are available: <br><br>- **Auto** - The permission is available for selection as a privilege on this menu item's **Privileges** node under the **Entry Points** node.<br>- **No** - The permission isn't available for selection as a privilege on the menu item.<br>The default value is **Auto**. |
| ReportDesign | Select the report design to use for a specific SSRS report model. |
| RunOn | Select whether to run the menu item on the client, the server, or the location that it's called from. This property is used for menu items that open reports. This property determines where the application object runs from only if the **RunOn** property of the object is set to **Called from**. <br><br>- A form is instantiated and run on the client, because the **FormRun** class always runs on the client.<br>- A report is instantiated and run as specified by the menu item's **RunOn** property, because the **ReportRun** class always runs where it was called from. Set the property to **Called from**. If you set the report to run on the client, and the report is run in a batch, the report fails. If you set the report to run on the server, and the report is shown on the screen, the report fails.<br>- A class's **main** method is run as specified by its modifier. The class itself is instantiated as specified by its **RunOn** property. The instantiation might occur in the **main** method.<br> |
| UpdatePermissions | Specify whether update permission should be available for section when assigning privileges to the menu item. The following options are available: <br><br>- **Auto** - The permission is available for section as a privilege on this menu item's **Privileges** node under the **Entry Points** node.<br>- **No** - The permission isn't available for section as a privilege on the menu item.<br>The default value is **Auto**. |
| Web | Specify the URL that opens when you run the menu item. The value of this property is no longer used. Don't use this property. |
| WebConfigurationKey | Optional: Select a web-specific configuration key in addition to a standard configuration key. This property applies to web menu items only. |
| WebMenuItemName | Specify the menu item to include on a web menu. The available values depend on the setting of the **WebMenuItemType** property. |
| WebMenuItemType | Specify the type of the web menu item. There are two categories of web menu items: <br><br>- URL<br>- Action<br>The value that you select determines the web menu item names that are available for the **WebMenuItemName** property. |
| WebPage | Specify the webpage that is linked to the menu item. The value of this property is no longer used. Don't use this property. |
| WebSecureTransaction | Select whether the menu item requires secure transactions (SSL). This property applies to web menu items only. |

> [!NOTE]
> When you use the **Parameters** or **EnumParameter** property, errors such as type mismatches can be found only at run time, not at compile time.

## Query properties

Within a query, you can set properties on the query itself, the data sources, the fields that you use for sorting, and the ranges that you use to delimit the query.

### Query properties

Query properties determine the overall behavior of the query. For example, you can specify the form that users see so they can interact with the query.

| Property | Description |
|---|---|
| AllowCheck | The system ignores this property for queries. It's effective on forms and reports. |
| AllowCrossCompany | Specify whether to retrieve data for all companies that the user has authority to read from. If you set the property to **false**, which is the default value, the system retrieves data only for the current session company. |
| Description | Optional: Describe the query, what it returns, and so on. This property is useful in Microsoft Office Add-in scenarios. |
| Form | Specify the query form that MorphX shows when users interact with the query. The default value is **SysQueryForm**. |
| Interactive | Specify whether users can interact with the report by delimiting queries, setting printer options, and so on. |
| Literals | Specify how literals are represented in SQL statements. The **forceLiterals** option instructs the kernel to reveal the actual values that are used in **where** clauses to the Microsoft SQL Server database at the time of optimization. The **forcePlaceholders** option instructs the kernel not to reveal the actual values. **Note:** Don't use the **forceLiterals** option, because it could expose code to an SQL injection security threat. |
| Model | Specify the model that the query is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| QueryType | Specify the type of the query. The following options are available: <br><br>- Join<br>- Union<br>The default value is **Join**. |
| Searchable | Specify whether the query can be part of a set of queries that is used to search the Microsoft SharePoint Business Catalog. This property is useful when you use the Enterprise Search feature. The default value is **No**. |
| Title | The heading for the query. |
| UserUpdate | Specify whether the query form should retain its state when it's reopened. If you set this property to **Yes**, the previous settings are restored. If you set it to **No**, the data can be viewed but not edited. |
| Version | The version is increased every time that the query is updated. This property is read-only. |

### Data source properties

The following properties control the characteristics of a data source. Embedded data sources and relations between data sources offer additional properties. You can also set one property on fields in the data source.

| Property            | Where it's available                 | Description                                                                                                                                                                                                                                                                                                                        |
|---------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowAdd            | Data source                          | Specify whether users can add fields to sorting and ranges at run time.                                                                                                                                                                                                                                                            |
| Company             | Data source                          | Specify the company to retrieve data from.                                                                                                                                                                                                                                                                                         |
| Dynamic             | Fields node in a data source         | Specify whether all fields in the table in the data source are used. If you set this property to **Yes**, all the fields in the data source are used. If you set it to **No**, you can remove some of the fields. When the data source is a base table, a value of **Yes** means that all fields from the derived tables are used. |
| Enabled             | Data source                          | If you set this property to **No**, the query system ignores the data source and all embedded data sources.                                                                                                                                                                                                                                   |
| FetchMode           | Embedded data source                 | Specify whether the data sources should be related through a 1:1 relation or a 1:n relation. **Note:** For data sources that are used on reports, use a join relation that uses 1:1 fetch mode.                                                                                                                                    |
| Field, RelatedField | Relations on an embedded data source | The name of the fields from the parent data source and related data source that are used in the relation.                                                                                                                                                                                                                          |
| FirstFast           | Data source                          | If you set this property to **Yes**, the database receives a hint that the first record from the query should be retrieved before the other records. This setting enables some database systems to optimize record retrieval and therefore helps improve performance.                                                              |
| FirstOnly           | Data source                          | If you set this property to **Yes**, the database receives a hint that only the first record from the query is required. This setting enables some database systems to optimize record retrieval and therefore helps improve performance.                                                                                          |
| JoinMode            | Embedded data source                 | Specify the strategy that is used to join the output from a data source.                                                                                                                                                                                                                                                           |
| Name                | Data source                          | Specify the name of the data source.                                                                                                                                                                                                                                                                                               |
| Relations           | Embedded data source                 | Specify whether the query system should use the relations that are defined for tables and EDTs. If you set this property to **Yes**, the query is automatically updated if a relation is changed.                                                                                                                                  |
| Table               | Data source                          | Specify the table, map, or view that is used as a data source. You can't modify this property after you define a sorting order or a range.                                                                                                                                                                                  |
| Table, RelatedTable | Relations on an embedded data source | The name of the parent data source and the related data source.                                                                                                                                                                                                                                                                    |
| UniqueId            | Data source                          | The unique number of the data source. This property is read-only.                                                                                                                                                                                                                                                                  |
| Update              | Data source                          | Specify whether the query can update records in the database.                                                                                                                                                                                                                                                                      |

### Range properties

The following properties determine the characteristics of the range specification. For example, you can specify whether users can modify the range at run time.

| Property | Description |
|---|---|
| Enabled | Use this property to disable a field in a range specification. |
| Field | Specify the field to define a range on. |
| Label | Enter a label for the range. |
| Status | Specify whether users can modify the range in the query dialog box at run time. The following options are available: <br><br>- **Open** - Users can view and edit the range.<br>- **Lock** - Users can only view the range.<br>- **Hide** - Users can't view or edit the range.<br> |
| Value | Specify the range for the records that are retrieved. If you use enumerations, don't use text strings. Use the enumeration ID. |

## Report properties

Set most of the properties for a report on the design, design section, and control nodes in Application Explorer. For information about system properties that are available on reports, see the "System and common properties" section. The following table describes the properties of a report.

| Property    | Description                                                                                                                                                                                                                                  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowCheck  | Specify whether a message is shown when users try to run reports that they don't have permission to view. Select **Yes** to specify that a message is shown.                                                                                 |
| AutoJoin    | Specify whether a record that the **element.args** method returns is used to set the range on the report query.                                                                                                                       |
| Interactive | Specify whether users can select which records to show by modifying the query that is associated with a report.                                                                                                                              |
| Model       | Specify the model that the report is in. A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in another layer. |

## Report control properties

The following table describes report control properties. For information about additional properties that are available for controls, see the "Form control properties" section.

| Property | Description |
|---|---|
| Alignment | Specify the alignment of a value that is shown in a control. |
| AllowNegative | Specify whether the control accepts negative values. This property is available only for integer and real controls. |
| ArrayIndex | Specify the array element that is shown in a control. The control is based on an extended data type that has array elements. This property isn't available for text and shape controls. |
| AutoDeclaration | Specify whether a variable is created that has the same name as the control. When you set this property to **Yes**, it's easier to access the report controls from X++ code, and you can find errors at compile time. |
| AutoInsSeparator | Specify whether a decimal separator is shown. This property is available only for real controls. |
| BackgroundColor | Specify the background color for a control. The setting of this property can be overridden by using the **BackStyle** property. |
| BackStyle | Specify whether the control background is opaque or transparent. When you set this property to **Transparent**, the behavior depends on the type of control: <br><br>- For bitmap controls, pixels that have the same color are transparent.<br>- For all other controls, the foreground color is used as the background color.<br> |
| Bold | Specify bold text formatting. |
| BottomMargin | Specify the margin for a control. |
| ChangeCase | Specify the case of text that a user enters. This property is available only for string, enum, text, and prompt controls. |
| ChangeLabelCase | Specify whether the label for the control should be modified when the report is printed. The following options are available: <br><br>- Auto<br>- None<br>- UPPER CASE<br>- lower case<br>- Title Case<br>The default value is **Auto**. |
| ColorScheme | Specify the color palette for a control. |
| ConfigurationKey | Specify a configuration key for the control. |
| CSSClass | Specify the Cascading Style Sheet (CSS) to use to render the value in HTML. |
| DataField | Specify a table field for the control. This property isn't available for text, shape, box, and bitmap controls. |
| DataMethod | Specify a display method that shows data in a control. This property isn't available for text, shape, and box controls. |
| DateDay | Specify the format for the day. This property is available only for date controls. |
| DateFormat | Specify the format for a date. This property is available only for date controls. |
| DateMonth | Specify the format for the month. This property is available only for date controls. |
| DateSeparator | Specify the separator that appears between the month, day, and year. This property is available only for date controls. |
| DateYear | Specify the format for the year. This property is available only for date controls. |
| DecimalSeparator | Specify the symbol that is used to separate decimal values. This property is available only for real controls. |
| DisplaceNegative | Specify a new position for a value in a grid control when the value is a negative number. This property is available only for integer and real controls. |
| DynamicHeight | Specify whether the control is resized to show additional lines of text. When you set this property to **Yes**, page headers, page footers, and repeating column headings are automatically added as required. This property is available only for string controls. |
| ExtendedDataType | Specify the EDT that the field that is associated with the control should be based on. |
| ExtraSumWidth | Modify the default width that is allowed for sums. This property is available only for integer and real controls. |
| Font | Specify the font. |
| FontSize | Specify the font size. |
| ForegroundColor | Specify the foreground color for a control. |
| FormatMST | Specify whether values are formatted by using standard currency format. This property is available only for real controls. |
| Height | Specify the height of a control. When a control is associated with an EDT, the **Height** property of the control overrides the **DisplayLength** property of the EDT. If you set the **Height** property to **Auto** for a bitmap control, the size of the control is based on the size of the graphic. |
| ImageName | Specify the file name for an image. This property is available only for bitmap controls. |
| ImageResource | Specify the ID for a system resource to show. The resource macro provides a list of these IDs. Macros are located under the **Macros** node in Application Explorer. This property is available only for bitmap controls. |
| Italic | Specify italic text formatting. |
| Label | Specify a title for the control. If a label isn't specified here, it's inherited from the field. |
| LabelBold | Set or return a value that indicates the bold setting for the label in the control. |
| LabelCSSClass | Specify the CSS to use to render the label in HTML. |
| LabelFont | Set or return a string data type value that indicates the font for the label text in a form combo box control. |
| LabelFontSize | Set or return the font size, in points, for the label text in a form combo box control. |
| LabelItalic | Set or return a value that indicates whether the text in the control label should be italic. |
| LabelLineBelow | Specify the format of the underline for the control title. |
| LabelLineThickness | Specify the format of the line below column headings. |
| LabelPosition | Set or return the position of the label for the control. Valid values are **Left** and **Above**. |
| LabelTabLeader | Specify whether to append a series of dots to control labels. The following options are available: <br><br>- Auto<br>- Don't append<br>- Do append<br>The default value is **Auto**. |
| LabelUnderline | Set or return a value that indicates whether the text in the control label should be underlined. |
| LabelWidth | Specify the width of the label for the control. |
| Left | Specify the left alignment of a control. |
| LeftMargin | Specify the left margin for a control. |
| Line | Specify the appearance of the lines that form a shape. This property is available only for shape controls. |
| LineAbove | Specify the type of line for the top border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections. |
| LineBelow | Specify the type of line for the bottom border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections. |
| LineLeft | Specify the type of line for the left border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections. |
| LineRight | Specify the type of line for the right border of a control. If your report has many lines or boxes, consider using a shape control inside the individual sections. |
| MenuItemLabel | Specify the label for a menu item. |
| MenuItemName | Specify the name of the menu item. The available menu items vary, depending on the setting of the **MenuItemType** property. |
| MenuItemType | Specify whether the menu item is an action, display, or output menu item. A display menu item is for a form, and an output menu item is for a report. An output menu item is for a class, job, or query. |
| MinNoOfDecimals | Specify the minimum number of decimal places that are shown. Trailing zeros aren't shown. |
| ModelFieldName | Specify a field that is used to determine the left alignment and width of a control. |
| NoOfDecimals | Specify the number of decimal places that are shown. The default value is **20**. This property is available only for real controls. |
| ResizeBitmap | Specify whether an image can be resized to fit the dimensions of a control. This property is available only for bitmap controls. |
| RightMargin | Specify the margin for a control. |
| RotateSign | Specify whether the sign for the control is inverted. This property is available only for integer and real controls. |
| ShowLabel | Set or return a value that indicates whether the label for the control is shown in the form. A value of **True** indicates that the label is shown. |
| ShowPicAsText | Specify whether the file name for an image is shown instead of the image. This property is available only for bitmap controls. |
| ShowZero | Specify whether a 0 (zero) value is shown. This property is available only for integer and real controls. |
| SignDisplay | Specify how the sign of a number is shown. This property is available only for integer and real controls. |
| SumAll | Specify whether the sum of all values is calculated. This property is available only for integer and real controls. |
| SumNeg | Specify whether the sum of all negative values is calculated. This property is available only for integer and real controls. |
| SumPos | Specify whether the sum of all positive values is calculated. This property is available only for integer and real controls. |
| Table | Specify a data source for the control. This property isn't available for text, shape, box, and bitmap controls. |
| Text | Specify the text string that is shown in a control. This property is available only for text controls. |
| TimeFormat | Specify whether times are shown in 24-hour format or AM/PM format. This property is available only for time controls. |
| TimeHours | Specify whether hours are shown. This property is available only for time controls. |
| TimeMinutes | Specify whether minutes are shown. This property is available only for time controls. |
| TimeSeconds | Specify whether seconds are shown. This property is available only for time controls. |
| TimeSeparator | Specify the symbol that is used to separate hours, minutes, and seconds. This property is available only for time controls. |
| Thickness | Specify the thickness of a control border. |
| ThousandSeparator | Specify the symbol that is used to separate thousands. This property is available only for real controls. |
| Top | Specify the top alignment of a control. |
| TopMargin | Specify the margin for a control. |
| Type | Specify the type of shape that is shown. This property is available only for shape controls. |
| TypeHeaderPrompt | Specify whether a line of dots is added to fill the space between the control title and the control value. This property is available only for text and prompt controls. |
| Underline | Specify underline text formatting. |
| Visible | Set or return a value that indicates whether the control is visible. A value of **True** indicates that the control is visible. |
| WarnIfMissing | Specify whether a message is shown if an image is missing from the report. This property is available only for bitmap controls. |
| WebMenuItemName | Specify the menu item to include on a web menu. The available values depend on the setting of the **WebMenuItemType** property. |
| WebMenuItemType | Specify the type of the menu item. There are two categories of web menu items: <br><br>- URL<br>- Action<br>The value that you select determines the web menu item names that are available for the **WebMenuItemName** property. |
| WebTarget | Specify the location of the control on a web report. |
| Width | Specify the width of a control. When a control is associated with an EDT, the **Width** property of the control overrides the **DisplayLength** property of the EDT. If you set the **Width** property to **Auto** for a bitmap control, the size of the control is based on the size of the graphic. |

## Report design properties

The following table describes the report design properties.

| Property                                   | Description                                                                                                                                                                              |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ArrangeMethod                              | Specify the layout for the controls in a report section.                                                                                                                                 |
| ArrangeWhen                                | Specify when report controls are arranged.                                                                                                                                               |
| BottomMargin                               | Specify the bottom margin. If you set this property to **Auto**, the default value that the system table stores is used.                                                           |
| Caption                                    | Specify the name that appears for the report in the user interface.                                                                                                                     |
| ColorScheme                                | Specify the color palette.                                                                                                                                                               |
| Columns                                    | Specify the number of columns.                                                                                                                                                           |
| ColumnSpace                                | Specify the space between columns.                                                                                                                                                       |
| Font, FontSize, Italic, Underline, and Bold | Specify the text formatting. The settings of the **Font** and **FontSize** properties override the values that you set by clicking **Options** &gt; **Fonts** on the **Tools** menu. |
| ForegroundColor                            | Specify the foreground color.                                                                                                                                                            |
| Height                                     | Specify the height.                                                                                                                                                                      |
| LeftMargin                                 | Specify the left margin. If you set this property to **Auto**, the default value that the system table stores is used.                                                             |
| LineAbove                                  | Specify the type of line for the top border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                       |
| LineBelow                                  | Specify the type of line for the bottom border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                    |
| LineLeft                                   | Specify the type of line for the left border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                      |
| LineRight                                  | Specify the type of line for the right border of a section. If a report has many lines and boxes, consider using the shape control inside a section.                                     |
| ResolutionX, ResolutionY                   | Specify the distance between gridlines.                                                                                                                                                  |
| RightMargin                                | Specify the right margin. If you set this property to **Auto**, the default value that the system table stores is used.                                                            |
| Ruler                                      | Specify the unit for the ruler that appears when you edit a design. To edit a design, right-click **AutoDesignSpecs** or **Generated Design**, and then select **Edit**.                 |
| Thickness                                  | Specify the thickness of a section border.                                                                                                                                               |
| TopMargin                                  | Specify the top margin. If you set this property to **Auto**, the default value that the system table stores is used.                                                              |

## Report design section properties

The following table describes properties for report design sections. For information about other properties that are available for report designs, see the "Report design properties" section.

|                 Property                  |                                                                                                                                                                        Description                                                                                                                                                                        |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               ArrangeMethod               |                                                                                                                                                 Specify the layout for the controls in a report section.                                                                                                                                                  |
|                ArrangeWhen                |                                                                                        Specify when the controls in the container should be arranged. The available options are <strong>Startup</strong>, <strong>On demand</strong>, and <strong>Never</strong>.                                                                                         |
|                   Bold                    |                                                                                                                                       Get or set the weight of the font that was used to show text in the control.                                                                                                                                        |
|                  Bottom                   |                                                                                                                                                     Change the position of the bottom of the report.                                                                                                                                                      |
|               BottomMargin                |                                                                                                   Specify the bottom margin. If you set this property to <strong>Auto</strong>, the default value that is stored in the UserInfo system table is used.                                                                                                    |
|                ColorScheme                |                                                                                                                                                                Specify the color palette.                                                                                                                                                                 |
|          ColumnHeadingsStrategy           | Specify the layout of column headings. If you set this property to <strong>WordWrap</strong>, a heading wraps when it's longer than the longest field in the column. Headings can wrap to a maximum of eight lines. Headings that are longer than eight lines are truncated. <strong>Note:</strong> The heading length varies, depending on the language. |
|                  Columns                  |                                                                                                                                                              Specify the number of columns.                                                                                                                                                               |
|                Columnspace                |                                                                                                                                                            Specify the space between columns.                                                                                                                                                             |
|                   Font                    |                                                       Specify the text formatting. The settings of the <strong>Font</strong> and <strong>FontSize</strong> properties override the values that you can set by clicking <strong>Options &gt; Fonts</strong> on the <strong>Tools</strong> menu.                                                        |
|                 FontSize                  |                                                       Specify the text formatting. The settings of the <strong>Font</strong> and <strong>FontSize</strong> properties override the values that you can set by clicking <strong>Options &gt; Fonts</strong> on the <strong>Tools</strong> menu.                                                        |
|              ForegroundColor              |                                                                                                                                                               Specify the foreground color.                                                                                                                                                               |
|                GrandHeader                |                                                                          Specify whether the value of the <strong>HeaderText</strong> property is shown. The <strong>GrandHeader</strong> property is available only when a report has multiple data sources that aren't nested.                                                                          |
|                GrandTotal                 |                                                                          Specify whether the value of the <strong>FooterText</strong> property is shown. The <strong>GrandTotal</strong> property is available only when a report has multiple data sources that aren't nested.                                                                           |
|                HeaderText                 |                                                       Specify the text that is shown above the first record in a section when the <strong>GrandHeader</strong> property is set to <strong>Yes</strong>. This property is available only when a report has multiple data sources that aren't nested.                                                       |
|                  Height                   |                                                                                                                                                                    Specify the height.                                                                                                                                                                    |
|                  Italic                   |                                                       Specify the text formatting. The settings of the <strong>Font</strong> and <strong>FontSize</strong> properties override the values that you can set by clicking <strong>Options &gt; Fonts</strong> on the <strong>Tools</strong> menu.                                                        |
|     LabelTopMargin, LabelBottomMargin     |                                                                                                                                                   Specify the margins above and below column headings.                                                                                                                                                    |
|                LeftMargin                 |                                                                                                    Specify the left margin. If you set this property to <strong>Auto</strong>, the default value that is stored in the UserInfo system table is used.                                                                                                     |
| LineAbove, LineBelow, LineLeft, LineRight |                                                                                                          Specify the type of line for a section border. If a report has many lines and boxes, consider using the shape control inside a section.                                                                                                          |
|                    Map                    |                                                                   Specify the map to use to show data. You can associate a map field with a field in one or more tables. This property lets you use the same field name to access fields that have different names in different tables.                                                                   |
|             NoOfHeadingLines              |                                         Specify the number of lines that are used to show column headings. If you set the property to <strong>0</strong> (zero), column headings aren't displayed. For reports that include several fields, increase the number of lines to make sure that all fields are shown.                                          |
|                RightMargin                |                                                                                                    Specify the right margin. If you set this property to <strong>Auto</strong>, the default value that is stored in the UserInfo system table is used.                                                                                                    |
|                ResolutionX                |                                                                                                                                                          Specify the distance between gridlines.                                                                                                                                                          |
|                ResolutionY                |                                                                                                                                                          Specify the distance between gridlines.                                                                                                                                                          |
|                   Ruler                   |                                                                      Specify the unit for the ruler that is shown when you edit a design. To edit a design, right-click <strong>AutoDesignSpecs</strong> or <strong>Generated</strong> Design, and then select <strong>Edit</strong>.                                                                      |
|                   Table                   |                                                                                                                                                          Specify the data source for a section.                                                                                                                                                           |
|                 Thickness                 |                                                                                                                                                        Specify the thickness of a section border.                                                                                                                                                         |
|                    Top                    |                                                                                                                                                       Change the position of the top of the report.                                                                                                                                                       |
|                 TopMargin                 |                                                                                                     Specify the top margin. If you set this property to <strong>Auto</strong>, the default value that is stored in the UserInfo system table is used.                                                                                                     |
|                 Underline                 |                                                       Specify the text formatting. The settings of the <strong>Font</strong> and <strong>FontSize</strong> properties override the values that you can set by clicking <strong>Options &gt; Fonts</strong> on the <strong>Tools</strong> menu.                                                        |

## Report query properties

The following table describes report query properties. For information about other report properties, see the "Report properties" and "System and common properties" sections.

| Property | Description |
|---|---|
| AllowCheck | Get or set the Allow check flag. |
| AllowCrossCompany | Get or set the Allow cross-company flag. This flag indicates whether query execution is across companies. |
| Description | A textual explanation of the query. This optional property is often used in Office Add-ins scenarios. |
| Form | Specify the form that is used for user interaction. |
| Interactive | Specify whether users can interact with the report by delimiting queries, setting printer options, and so on. |
| Literals | Specify how literals are represented in SQL statements. |
| Model | Specify the model that the report query is in. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in another layer. |
| QueryType | Specify the type of the query. The following options are available: <br><br>- Join<br>- Union<br>The default value is **Join**. |
| Searchable | Specify whether the query can be part of a set of queries that can be used to search the SharePoint Business Catalog. This property is useful when you use the Enterprise Search feature. The default value is **No**. |
| Title | Specify the title of the query. |
| UserUpdate | Specify whether users can update a query. |
| Version | This is a read-only internal property. |

## Security code permission properties

A code permission is a group of permissions that are associated with a menu item or a service operation. When a security role has access to a menu item, it also has access to other Application Explorer items that the code permission for that menu item mentions. The specific permissions that are defined under the code permission node control the degree of access.

### Securable objects

Use code permissions to grant access to securable objects. The following list shows the hierarchy of code permission nodes in Application Explorer:

- Security
  - Code Permissions
    - YourCodePermission
      - Tables
      - Server Methods
      - Associated Objects
        - Forms
        - Web Controls
        - Reports

Code permissions can also override the access levels to securable objects under the **Associated Objects** node.

### Code permission properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** in Application Explorer.

| Property | Required | Description                                                                                                                        |
|----------|----------|------------------------------------------------------------------------------------------------------------------------------------|
| Name     | Yes      | The name of the code permission. The code permission lets users run the class method that you specify in the **Method** property. |
| Class    | Optional | The class that is associated with this code permission.                                                                            |
| Method   | Optional | The method that is associated with this code permission.                                                                           |

### Table properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Tables** &gt; **YourTable** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Table | Yes | The name of the table. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **EffectiveAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. Set the permission value to **NoAccess** to prevent all access to the table. |
| ManagedBy | Optional | Automation tools use this property. |

### Server method properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Class | Yes | The name of the server class. |
| Method | Yes | The secure server method that's tagged with the **SysEntryPointAttribute** attribute. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- **Invoke** - The server method can be called.<br>- **NoAccess** - The server method can't be called.<br> |
| ManagedBy | Optional | Automation tools use this property. |

### Form properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Forms** &gt; **YourForm** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Form | Yes | The name of the form. |
| AccessLevel | Yes | The permission value. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **EffectiveAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. Set the permission value to **NoAccess** to prevent all access to the form. |
| ManagedBy | Optional | Automation tools use this property. |

### Web control properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Web Controls** &gt; **YourWebControl** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| WebControl | Yes | The name of the web control. |
| AccessLevel | Yes | The permission value. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **EffectiveAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. Set the permission value to **NoAccess** to prevent all access to the web control. |
| ManagedBy | Optional | Automation tools use this property. |

### Report properties

The following table describes the properties for the node at **Security** &gt; **Code Permissions** &gt; **YourCodePermission** &gt; **Associated Objects** &gt; **Reports** &gt; **YourReport** in Application Explorer.

| Property  | Required | Description                                |
|-----------|----------|--------------------------------------------|
| Name      | Yes      | The name of the report design.             |
| Report    | Yes      | The full name of the report.               |
| ManagedBy | Optional | Automation tools use this property. |

## Security duty properties

Security permissions combine into privileges, and privileges combine into duties. Define duties as groups of related privileges that provide a user with access to a specific business function. In Application Explorer, organize these privileges into the nodes of a duty.

### Best practices

Follow these best practice rules for duties:

- Assign all duties to a role.
- Include all duties as part of a process cycle.
- Because a duty represents a specific business function, rarely or never change the name of the duty. For example, your company pays bills. Although the details of how you pay bills might change, the essential function of paying bills doesn't change. Instead of creating a new duty, change the privilege subnodes of the duty.
- Rarely or never change the name of a process cycle.

### Duty hierarchy in Application Explorer

The following list shows the hierarchy of duty nodes in Application Explorer:

- Security
  - Duties
    - YourDuty
      - Privileges

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the duty. |
| Label | Yes | Text that the user interface shows for the duty. |
| Description | Yes | A description of the duty. |
| Enabled | Yes | A value that indicates whether the duty is enabled. The following options are available: <br><br>- **Yes** - Enable the duty.<br>- **No** - Disable the duty.<br> |

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Duties** &gt; **YourDuty** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the privilege. |
| Enabled | Yes | A value that indicates whether the privilege is enabled. The following options are available: <br><br>- **Yes** - Enable the privilege.<br>- **No** - Disable the privilege.<br> |

## Security privilege properties

A privilege is a group of permissions. The nodes that are below each privilege node identify the securable objects that a user can access and set the level of access for each object.

### Best practices

This section describes the best practice rules for privileges.

- Use privileges to specify the access that is required to perform a job.
- Use privileges to group the permissions for related securable objects. For example, menu items and their controls are closely related.
- Assign privileges directly to security roles. However, it's easier to maintain security settings if you assign duties or process cycles instead of privileges.

### Securable objects

Use privileges to give access to securable objects. The following list shows the hierarchy under the **Security** &gt; **Privileges** node in Application Explorer:

- Security
  - Privileges
    - YourPrivilege
      - Entry Points
      - Permissions
        - Tables
        - Server Methods
        - Forms

Privileges can also override the access levels to securable objects as they're defined elsewhere in Application Explorer. For example, a privilege can override a permission that the **EffectiveAccess** property defines under **Forms** &gt; **YourForm** &gt; **Permissions** &gt; **Update** &gt; **Tables** &gt; **YourTable** in Application Explorer.

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the privilege. |
| Label | Yes | Text that is shown for the privilege in the user interface. |
| Description | Yes | A description of the privilege. |
| Enabled | Yes | A value that indicates whether the privilege is enabled. The following options are available: <br><br>- **Yes** - Enable the privilege.<br>- **No** - Disable the privilege.<br> |

### Entry point properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Entry** **Points** &gt; **YourEntryPoint** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the entry point. |
| ObjectType | Yes | The object type of the entry point. The following options are available: <br><br>- MenuItemDisplay<br>- MenuItemOutput<br>- MenuItemAction<br>- ServiceOperation<br>- WebActionItem<br>- WebURLItem<br>- WebManagedContent<br> |
| ObjectName | Yes | The object name of the entry point. |
| ObjectChildName | Optional | A value that represents the service method name. **Note:** Specify a value for this property only if the **ObjectType** property is set to **ServiceOperation**. |
| AccessLevel | Yes | The permission value. For all object types except **ServiceOperation**, the following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **AccessLevel** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. You can set the permission value to **NoAccess** to prevent all access to the entry point. The Correct permission applies only when a time state table is involved. This permission authorizes you to issue update records in a time state table. For the **ServiceOperation** object type, the following options are available: <br><br>- **Invoke** - The server method can be called.<br>- **NoAccess** - The server method can't be called.<br> |

### Table properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Tables** &gt; **YourTable** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Table | Yes | The name of the table. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **EffectiveAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. The Correct permission applies only when a time state table is involved. This permission authorizes you to update records in a time state table. Set the permission value to **NoAccess** to prevent all access to the table. |
| ManagedBy | Optional | Automation tools use this property. |

### Server method properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Class | Yes | The name of the server class. |
| Method | Yes | The name of the secure server method that's tagged with the **SysEntryPointAttribute** attribute. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- **Invoke** - The server method can be called.<br>- **NoAccess** - The server method can't be called.<br> |
| ManagedBy | Optional | Automation tools use this property. |

### Form properties

The following table describes the properties for the node at **Security** &gt; **Privileges** &gt; **YourPrivilege** &gt; **Permissions** &gt; **Forms** &gt; **YourForm** in Application Explorer.

| Property | Required | Description           |
|----------|----------|-----------------------|
| Form     | Yes      | The name of the form. |

## Security process cycle properties

A process cycle is a group of duties. A process cycle represents a high-level job function. Although the details of how a given job function runs might change over time, the concept and name of that job function probably don't change.

### Best practices

This section describes the best practice rules for process cycles.

- Each duty should be part of a process cycle.
- Use a process cycle to organize a group of duties for a job function.

### Process cycle hierarchy in Application Explorer

The following list shows the hierarchy of process cycle nodes in Application Explorer:

- Security
  - Process Cycles
    - YourProcessCycle
      - Duties

### Process cycle properties

The following table describes the properties for the node at **Security** &gt; **Process** **Cycles** &gt; **YourProcessCycle** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the process cycle. |
| Label | Yes | Text that appears for the process cycle in the user interface. |
| Description | Yes | A description of the process cycle. |
| Enabled | Yes | A value that indicates whether the duty is enabled. The following options are available: <br><br>- **Yes** - Enable the process cycle.<br>- **No** - Disable the process cycle.<br> |

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Process Cycles** &gt; **YourProcessCycle** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the duty. |
| Enabled | Yes | A value that indicates whether the duty is enabled. The following options are available: <br><br>- **Yes** - Enable the duty.<br>- **No** - Disable the duty.<br> |

## Security policy properties

Developers and system administrators can create security policies to deny access to a subset of data records in tables.

### Constrained tables of a policy

In Application Explorer, under the **Constrained Tables** node of a security policy, you can add tables and views. These tables and views relate to the data source table of the query that you name in the **Query** property of the policy. The following list shows the hierarchy of security policy nodes in Application Explorer:

- Security
  - Policies
    - YourPolicy
      - Constrained Tables
        - YourConstrainedTable
          - YourConstrainedSubTable
        - YourConstrainedView

Each **Constrained Tables** node can contain any number of constrained tables and views. Additionally, each constrained table can contain any number of constrained sub-tables.

### Security policy properties

The following table describes the properties for the node at **Security** &gt; **Policies** &gt; **YourPolicy** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the security policy. |
| Label | Yes | The text that appears for the security policy in the user interface. |
| PrimaryTable | Yes | The table specified in the data source for the security policy query. |
| Query | Yes | The query that the policy uses to filter data from the constrained tables that the policy specifies. |
| UseNotExistJoin | Yes | A value that indicates whether the security query must be applied as a **not exists** join or an **exists** join. |
| PolicyGroup | No | Administrators and developers can use this property to quickly identify groups of related security policies. The available options are the names of the security policy groups that the system administrator or developer creates. The system doesn't use this property at run time. |
| ConstrainedTable | Yes | A value that controls whether the security policy restricts the data values in records that are returned from the primary table. The following options are available: <br><br>- **Yes** - The security policy is enforced on the primary table.<br>- **No** - The security policy isn't enforced on the primary table.<br> |
| Enabled | Yes | A value that controls whether the system enforces the policy at run time. The following options are available: <br><br>- **Yes** - Enable the security policy.<br>- **No** - Disable the security policy.<br> |
| Operation | Yes | A value that controls which data operations the policy is enforced for. The following options are available: <br><br>- Select<br>- Insert<br>- Update<br>- Delete<br>- Insert, Update and Delete<br>- All operations<br> |
| ContextType | Yes | A value that controls the context type of the security policy. The following options are available: <br><br>- **ContextString** - You must specify a value for the **ContextString** property. The security policy uses a specific application context for the policy.<br>- **RoleName** - The security policy is applied only to the application user who is assigned to the value of **RoleName**.<br>- **RoleProperty** - This value is used in combination with the **ContextString** property to specify multiple roles context.<br> |
| ContextString | Yes | This property is used in combination with **ContextType** property. It can be used to specify an application or multiple roles context. |

## Security role properties

Roles represent a collection of permissions that you can grant to users. The nodes that are nested below each role node identify various securable objects that a user can access and specify the level of access.

### Role node in Application Explorer

Use roles to grant access to securable objects. The following list shows the hierarchy of role nodes in Application Explorer:

- Security
  - Roles
    - YourRole
      - Duties
      - Privileges
      - Permissions
        - Tables
        - Forms
        - Server Methods
      - Sub Roles

Typically, associate roles with security duties, and sometimes with security privileges. The access levels to securable objects within a role come from the duties, privileges, or both. Roles can also override the access levels to securable objects under the **Permissions** node.

### Role properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **YourRole** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the role. |
| Label | Yes | Text that the user interface shows for the role. |
| Description | Yes | A description of the role. |
| Enabled | Yes | A value that indicates whether the role is enabled. The following options are available: <br><br>- **Yes** - Enable the role.<br>- **No** - Disable the role.<br> |
| PastDataAccess | Yes | The past data access for the tables that have date-effective fields. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **PastDataAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. Set the permission value to **NoAccess** to prevent all access to the table. |
| CurrentDataAccess | Yes | The current data access for the tables that have date-effective fields. |
| FutureDataAccess | Yes | The future data access for the tables that have date-effective fields. |
| ContextString | Optional | A user-defined string that security policies can use. |

### Duty properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Duties** &gt; **YourDuty** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the duty. |
| Enabled | Yes | A value that indicates whether the duty is enabled. The following options are available: <br><br>- **Yes** - Enable the duty.<br>- **No** - Disable the duty.<br> |

### Privilege properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Privileges** &gt; **YourPrivilege** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the privilege. |
| Enabled | Yes | A value that indicates whether the privilege is enabled. The following options are available: <br><br>- **Yes** - Enable the privilege.<br>- **No** - Disable the privilege.<br> |

### Table properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Tables** &gt; **YourTable** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Table | Yes | The name of the table. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- Read<br>- Update<br>- Create<br>- Correct<br>- Delete<br>- NoAccess<br>The permission values for the **EffectiveAccess** property represent a hierarchy. Read is the weakest permission, and Delete is the strongest. Delete permission includes every other permission. Create permission includes Update and Read. Set the permission value to **NoAccess** to prevent all access to the table. |
| ManagedBy | Optional | Automation tools use this property. |

### Form properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Form** &gt; **YourForm** in Application Explorer.

| Property | Required | Description           |
|----------|----------|-----------------------|
| Form     | Yes      | The name of the form. |

### Server method properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Permissions** &gt; **Server Methods** &gt; **YourServerMethod** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Class | Yes | The name of the server class. |
| Method | Yes | The name of the secure server method that's tagged with the **SysEntryPointAttribute** attribute. |
| EffectiveAccess | Yes | The permission value. The following options are available: <br><br>- **Invoke** - The server method can be called.<br>- **NoAccess** - The server method can't be called.<br> |
| ManagedBy | Optional | Automation tools use this property. |

### Subrole properties

The following table describes the properties for the node at **Security** &gt; **Roles** &gt; **Sub Roles** &gt; **YourSubRole** in Application Explorer.

| Property | Required | Description |
|---|---|---|
| Name | Yes | The name of the subrole. |
| Enabled | Yes | A value that indicates whether the duty is enabled. The following options are available: <br><br>- **Yes** - Enable the subrole<br>- **No** - Disable the subrole.<br> |

## Web menu properties

The following table describes the properties that are specific to web menus and submenus.

| Property | Description |
|---|---|
| ConfigurationKey | Specify the configuration key that controls the display of this menu. If a user doesn't have access to the configuration key, the menu isn't visible. |
| HighlightSelected | This property isn't supported. |
| Label | Specify the text that appears for the top-level node of the web menu or submenu. The value can't exceed 250 characters. |
| MenuItemName | Specify the menu item to access when the top-level node for the menu or submenu is clicked. The available options depend on the setting of the **MenuItemType** property. |
| MenuItemType | Specify the type of menu item that the top-level node of the menu or submenu accesses. The available options are **Action** and **URL**. |
| Model | Specify the model. A model is a logical grouping of elements in a layer. Examples of elements include a table or class. An element can exist in exactly one model in a layer. The same element can exist in a customized version in a model that is in a higher layer. |
| SetCompany | This property causes the system to change the company when the form receives focus. If the **SaveDataPerCompany** property on a table is set to **Yes**, the **SetCompany** property on a form design that uses the table as a data source must also be set to **Yes**. |
| ShowParentModule | Specify whether to update the QuickLaunch, based on the parent module of the menu item. The following options are available: <br><br>- **Yes** - Always update the QuickLaunch, based on the parent module of the menu item.<br>- **No** - Leave the QuickLaunch unchanged, even if the parent module of the menu item differs from the current module.<br>The default value is **Yes**. |

## Web menu item properties

The following table describes the properties that are specific to web menu items.

| Property | Description |
|---|---|
| Big | Specify the size of the button when it's used on an Action Pane. The following options are available: <br><br>- **Yes** - The button is shown at full size and is located at the start of the group.<br>- **No** - The button is shown at the smaller size and is located on the right side of the group.<br> |
| CloseDialogBehavior | Specify the action that is performed on the parent window when the dialog box closes. The following options are available: <br><br>- **Auto** - Depending on how the dialog box was used, the appropriate update actions are performed when the dialog box is closed.<br>- **RefreshDataSource** - The read-only data source on the parent form is updated. This option preserves the current selection and performs a **Research()** operation on the data source.<br>- **RefreshPage** - Refresh the page.<br>- **Submit** - Refresh the parent page.<br>- **None** - No action is performed.<br>The default value is **Auto**. |
| HideActionPane | Specify whether the Action Pane is visible on the page that's being opened. |
| HomePage | Specify whether the page is a Role Center page and is deployed to the main Enterprise Portal site. |
| NeedsRecord | When you set this property to **Yes**, the menu item is shown when there are no records in the data set. |
| PageDefinition | The page that the web menu item points to. |
| Parameters | Specify the arguments that are passed to the page that's being opened. Each parameter must have the following form: *name*=*value* If multiple parameters must be passed, they must be separated by an ampersand (&), as shown in the following example: mode=2&category=1 |
| URL | Specify the URL to navigate to. |
| WebConfigurationKey | Select the configuration key that is required in order to enable the web menu item. Use the key for the module that the object belongs to. |
| WindowMode | Specify the type of window to use for the page that's being opened. The following options are available: <br><br>- **Inline** - The page that's being opened replaces the existing content in the browser. If the web menu item is accessed from a dialog box, the page that's being opened opens in a new browser window.<br>- **Modal** - If no dialog box is open, a new dialog box is created. If the web menu item is accessed from a dialog box, the page that's being opened replaces the content of the current dialog box.<br>- **NewModal** - The page that's being opened always opens in a new dialog box.<br>- **NewWindow** - The page that's being opened opens in a new browser window.<br> |
| WindowParameters | Specify other parameters to control the appearance of the SharePoint dialog box. The parameters must be enclosed in braces ({}) and separated by commas. The following example shows how to set the **WindowParameters** property so that the dialog box has a size of 400 × 300 pixels, and so that it has no **Close** or **Maximize** button: {width:400, height:300, showClose:false, allowMaximize:false} |
| WindowSize | Specify the size of the window to use for the page that's being opened. The following options are available: <br><br>- **Smallest** - 330 × 200 pixels<br>- **Small** - 550 × 450 pixels<br>- **Medium** - 800 × 630 pixels<br>- **Large** - 930 × 630 pixels<br>- **Maximum** - The largest size that fits in the boundaries of the main browser window<br> |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]




