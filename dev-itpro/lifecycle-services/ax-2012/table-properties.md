---
# required metadata

title: Table properties | Microsoft Docs
description: This topic describes the properties that are in the<strong> Properties</strong> window for table elements in the Application Object Tree (AOT). Table elements are located under <strong>Data Dictionary</strong> &gt; <strong>Tables</strong>.
author: kfend
manager: AnnBe
ms.date: 2015-12-04 23:16:47
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18141
ms.assetid: fca27850-7ca8-45f1-aae1-fb1312e1a481
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Table properties

This topic describes the properties that are in the<strong> Properties</strong> window for table elements in the Application Object Tree (AOT). Table elements are located under <strong>Data Dictionary</strong> &gt; <strong>Tables</strong>.

For information about system properties available for tables, see [System and Common Properties](http://ax.help.dynamics.com/en/wiki/system-and-common-properties/). For guidelines about setting property values, see [Best Practices for Table Properties](http://msdn.microsoft.com/library/5def498e-107d-4a2b-a621-fbbe0243e399(AX.60).aspx). Next is a list of topics about the properties of AOT elements that are sub-elements under a table element.

## Table Properties
The following table describes the properties of table elements in the AOT.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
<th>New in this version of Microsoft Dynamics AX</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong><span class="ui">Abstract</span></strong></td>
<td>Specifies whether or not the table supports inheritance.The default value is <span class="ui">No</span>. If the value is <span class="ui">Yes</span>, the table cannot be a direct target of X++ SQL statements such as <span class="code">update_recordset</span> and <span class="code">select</span>. This property is unavailable when the <span class="ui">SupportInheritance</span> property is set to <span class="ui">No</span>. For more information, see <a href="http://msdn.microsoft.com/library/cb4803e7-9a29-4c54-be43-63722557dac6(AX.60).aspx">Table Inheritance Overview</a>.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">AnalysisDimensionType</span></strong></td>
<td>Determines the type of dimension created based on the <span class="ui">IsLookup</span> property setting. You can specify one of the following values.<strong><span class="ui">IsLookup</span></strong> property set to <strong><span class="ui">Yes</span></strong>
<ul>
<li><strong><span class="ui">Auto</span></strong> - Specifies that the table may contain factual as well as dimensional data. The <strong>BI Wizard</strong> will extract dimensional data and create dimensions and attributes while factual data will be extracted to create measures. One child dimension is created with attributes from the parent table.</li>
<li><strong><span class="ui">MasterInner</span></strong> - Specifies an inner (full) join to create relationships with this table to the child table. Each record combination for this table and the child table are generated in the dimension. One child dimension is created with attributes from the parent table.</li>
<li><strong><span class="ui">MasterLeftOuter</span></strong> - Specifies a left outer join to create relationships with this table to the child table. Dimensions will have additional attributes based on values in this table that can also be empty. One child dimension is created with attributes from the parent table.</li>
<li><strong><span class="ui">Transaction</span></strong> - Specifies that the table should strictly be used to generate factual data (measures). This setting should be used when a table only contains transactional data. One child dimension is created containing only enumeration fields from the table.</li>
</ul>
<strong><span class="ui">IsLookup</span></strong> property set to <strong><span class="ui">No</span></strong>
<ul>
<li><strong><span class="ui">Auto</span></strong> - Specifies that the table may contain factual as well as dimensional data. The <strong>BI Wizard</strong> will extract dimensional data and create dimensions and attributes while factual data will be extracted to create measures. One parent and child dimension is created.</li>
<li><strong><span class="ui">MasterInner</span></strong> - Not applicable. Same as <span class="ui">Auto</span>.</li>
<li><strong><span class="ui">MasterLeftOuter</span></strong> - Not applicable. Same as <span class="ui">Auto</span>.</li>
<li><strong><span class="ui">Transaction</span></strong> - Specifies that the table should strictly be used to generate factual data (measures). This setting should be used when a table only contains transactional data. One child dimension is created containing only enumeration values from the table.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">AnalysisIdentifier</span></strong></td>
<td>Specifies the field to be used as the identifier for the dimension in a SQL Server Analysis Services (SSAS) cube.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">AOSAuthorization</span></strong></td>
<td>Specifies the type of operation that a user can perform on a table, depending on the user's permissions.When the property is set to <strong><span class="ui">None</span></strong>, an authorization check is not performed.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">CacheLookup</span></strong></td>
<td>Determines how to cache the records retrieved during a lookup operation.This <strong><span class="ui">CacheLookup</span></strong> property exists only on tables that do not inherit from another table. On an inheritance root table, this property cannot be set to <strong><span class="ui">EntireTable</span></strong> by using the AOT <span class="ui">Properties</span> window. You must not use other techniques to assign this value to inheritance root tables. For example, do not use the <strong><span class="code">AOTsetProperty</span></strong> method of the <strong><span class="code">TreeNode</span></strong> class to assign this value.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">ClusterIndex</span></strong></td>
<td>Specifies the cluster index.This property is used only for SQL optimization purposes.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">ConfigurationKey</span></strong></td>
<td>Specifies the configuration key for the table.Configuration keys allow a system administrator to enable and disable certain parts of an application.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">CountryRegionCodes</span></strong></td>
<td>Specifies the country region codes where the table is applicable or valid. The client framework and application may make use of this property to enable or disable country or region specific features. This is implemented as a comma-separated list of ISO country codes in a single string. The values must match data contained in the global address book.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">CountryRegionContextField</span></strong></td>
<td>Specifies the field that will be used to identify the country context. This relates to the <strong><span class="ui">CountryRegionCodes</span></strong> property.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">CreatedBy</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">CreatedBy</span></strong> field for the records in a table. This field contains information about who created a particular record.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">CreatedDateTime</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">CreationDate</span></strong> and <strong><span class="ui">CreationTime</span></strong> fields for the records in a table. This field contains the date when a record was created.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">CreatedTransactionId</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">CreatedTransactionId</span></strong> field for the records in a table. This field contains information about which transaction created the record.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">CreateRecIdIndex</span></strong></td>
<td>Indicates whether an index on the <strong>Record ID</strong> field is created.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">DeveloperDocumentation</span></strong></td>
<td>Describes the purpose of a table and explains how it is used in the application. A description is typically no more than five sentences long and is written as a single paragraph.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">EntityRelationshipType</span></strong></td>
<td>Classifies a table according to common entity relationship (ER) data model notation. A table is classified as an entity or a relationship. An entity represents an object. A relationship represents an association between two objects.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Extends</span></strong></td>
<td>Derives the table from another table that is chosen as the property value.The value is null when the <span class="ui">SupportInheritance</span> property is set to <span class="ui">Yes</span>. For more information, see <a href="http://msdn.microsoft.com/library/cb4803e7-9a29-4c54-be43-63722557dac6(AX.60).aspx">Table Inheritance Overview</a>.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">FormRef</span></strong></td>
<td>Specifies the display menu item that is activated when a table is referenced. A display menu item is associated with a form.When you use a primary index field on a report, this form is available as a link in the report. A primary index is specified by using the <strong><span class="code">PrimaryIndex</span></strong> property. If you leave this field blank, the system attempts to display a form that has the same name as the table.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">ID</span></strong></td>
<td>Specifies the table <span class="code">ID</span> generated by the system. For more information, see <a href="http://msdn.microsoft.com/library/2951f194-4362-460e-8607-7f9fc0022449(AX.60).aspx">Application Object IDs</a>.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">IsLookup</span></strong></td>
<td>For report models, it specifies whether the table information is incorporated into other tables that reference it when a report model is generated.For OLAP cubes, it determines whether to generate a consolidated dimension or a distinct dimension. You can specify one of the following values.
<ul>
<li><strong><span class="ui">Yes</span></strong> - Indicates that attributes from the table are to be consolidated into the parent dimension (star schema).</li>
<li><strong><span class="ui">No</span></strong> - Indicates that a separate dimension is to be generated for the table (snowflake schema).</li>
</ul>
For more information about dimensions and star and snowflake schemas, see <a href="http://go.microsoft.com/fwlink/?LinkId=115450">Introduction to Dimensions (SQL Server 2005 Books Online)</a>.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Label</span></strong></td>
<td>Specifies the label for a table.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">ListPageRef</span></strong></td>
<td>Specifies a display menu item that points to a form that can show a list of this record type.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">Model</span></strong></td>
<td>Specifies which model the table is in.A model is a logical grouping of elements in a layer. An element can exist in exactly one model in a layer. Examples of elements are a table or class. The same element can exist in a customized version in a model in a higher layer.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">ModifiedBy</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">ModifiedBy</span></strong> field for the records in a table. This field records the person who performed the last modification to a record.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">ModifiedDateTime</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">ModifiedDate</span></strong> field for the records in a table. This field records the date of the last modification of a record.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">ModifiedTime</span></strong></td>
<td>Indicates whether the system maintains the <strong><span class="code">ModifiedDateTime</span></strong> field for the records in a table. This field records the date and time when a record was last modified.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">Name</span></strong></td>
<td>Specifies the table name.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">OccEnabled</span></strong></td>
<td>Specifies whether the optimistic concurrency mode is enabled for a table.When this mode is enabled, data is not locked from future modification when it is fetched from the database. Data is locked only when the actual update is performed.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">PreviewPartRef</span></strong></td>
<td>Specifies the <span class="ui">Info Part</span> or <span class="ui">Form Part</span> to be used in the enhanced preview.An info part shows a collection of data fields from a specified query. An info part uses metadata to describe how the data appears. A form part represents a pointer to a form.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">PrimaryIndex</span></strong></td>
<td>Specifies the primary index.Only a unique index can be selected. The property is used for database optimization purposes and to indicate which unique index to use as the caching key. If a primary index is not specified, the unique index with the lowest ID is used as the caching key.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">ReplacementKey</span></strong></td>
<td>Specifies the fields to display as the identifier for data in some form controls.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">ReportRef</span></strong></td>
<td>Specifies the output menu item that is activated when a table is referenced. An output menu item is associated with a report.When you use a primary index field on a report, this report is available as a link in the report. A primary index is specified using the <span class="code">PrimaryIndex</span> property.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">SaveDataPerCompany</span></strong></td>
<td>Indicates whether the data for the current company is saved.If you set the property to<strong><span class="ui"> No</span></strong>, data is saved without a company identifier (<span class="code">DataAreaId</span>).
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>If the <strong><span class="code">SaveDataPerCompany</span></strong> property on a table is set to <strong>Yes</strong>, the <strong><span class="code">SetCompany</span></strong> property on a form design that uses the table as a data source must also be set to Yes.</td>
</tr>
</tbody>
</table>
</div>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The company acronym can be seen in the status line. Double-clicking the acronym opens a dialog box to change to another company.</td>
</tr>
</tbody>
</table>
</div></td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">SaveDataPerPartition</span></strong></td>
<td>Shows whether the table has a system field named <strong><span class="code">Partition</span></strong>. This is meant to be a read-only system field.If the table has a <strong><span class="code">Partition</span></strong> field, each record is assigned to one partition. Each record is kept hidden from data access operations that are run under the context of other partitions.</td>
<td>AX 2012 R2</td>
</tr>
<tr class="even">
<td><strong><span class="ui">SearchLinkRefName</span></strong></td>
<td>Specifies the name of the menu item that links to information on a Web site about a table record listed in the Enterprise Portal search results.If the <strong><span class="code">SearchLinkRefType</span></strong> property is set to URL, select a menu item from the <strong><span class="code">SearchLinkRefName</span></strong> property list that links to a Web part page that displays the table data. Forms and reports on Web part pages can display data.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">SearchLinkRefType</span></strong></td>
<td>Specifies the type of the menu item that links to information on a Web site about a table record listed in the Enterprise Portal search results.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">SingularLabel</span></strong></td>
<td>Specifies the label that is used in a report model or a cube to display the singular name of items stored in the table.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">SupportInheritance</span></strong></td>
<td>Setting this property to <strong><span class="ui">Yes</span></strong> enables you to set a value for other inheritance related properties such as <strong><span class="ui">Extends</span></strong> and <strong><span class="ui">Abstract</span></strong>.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>When you set the value to <strong><span class="ui">Yes</span></strong>, any fields on the table are dropped and must be created again.</td>
</tr>
</tbody>
</table>
</div>
For more information, see <a href="http://msdn.microsoft.com/library/cb4803e7-9a29-4c54-be43-63722557dac6(AX.60).aspx">Table Inheritance Overview</a>.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">SystemTable</span></strong></td>
<td>Indicates if a table appears as a System table. It can then be filtered during export and import.System tables are always synchronized when you log in. This may be useful for tables that you use as soon as you log in.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">TableContents</span></strong></td>
<td>Specifies how setup/parameter data can be reused from one customer to another. The following values are possible:
<ul>
<li><strong><span class="ui">Not specified</span></strong> – For most tables.</li>
<li><strong><span class="ui">Default Data</span></strong> – Use for customer-independent data such as ZIP/Postal Codes, units, and time intervals.</li>
<li><strong><span class="ui">Base Data</span></strong> – Use for customer-dependent data such as calendars, groups, and parameters.</li>
<li><strong><span class="ui">Default+Base data</span></strong> – Use for data where the local perception varies. For example, Chart of Accounts is not customer-dependent in Germany, but is most other places in the world.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">TableGroup</span></strong></td>
<td>Determines which group the table belongs to.<a href="http://msdn.microsoft.com/library/3330d438-ab53-44db-9a9b-a044ed19608d(AX.60).aspx">Table Groups</a> provide a method for categorizing tables according to the type of data they contain. Table groups can be used to define whether the system should prompt users when they update or delete from the table in forms by using the table as the data source. When exporting data, you can use table groups to filter records.</td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">TableType</span></strong></td>
<td>Replaces the <strong><span class="ui">Temporary</span></strong> property found in Microsoft Dynamics AX 2009. For more information, see <a href="http://msdn.microsoft.com/library/9986b514-6079-499a-b491-9a95589f8229(AX.60).aspx">Temporary Tables and the TableType Property</a>.</td>
<td>AX 2012</td>
</tr>
<tr class="even">
<td><strong><span class="ui">TitleField1</span></strong>, <strong><span class="ui">TitleField2</span></strong></td>
<td>Enables you to do the following:
<ul>
<li>Add table field data to a form caption.</li>
<li>Display additional fields in a lookup form. For more information, see <a href="http://msdn.microsoft.com/library/2e365e4b-842a-44eb-b0fa-6fa4c8c1e0fe(AX.60).aspx">How to: Add a Control with a Lookup Form</a>. The <strong><span class="code">TitleField1</span></strong> property is also used when activating the lookup list in a field on a form. The fields you specify for <strong><span class="code">TitleField1</span></strong> and <strong><span class="code">TitleField2</span></strong> properties can be merged with the key value.</li>
<li>Display field information in a tooltip.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td><strong><span class="ui">TypicalRowCount</span></strong></td>
<td>Specifies the number of records that typically appear in a table.If the <strong><span class="code">AnalysisSelection</span></strong> property is not set, the <strong><span class="code">TypicalRowCount</span></strong> property determines how records are selected by using Report Builder for Microsoft SQL Server Reporting Services. The <strong><span class="code">TypicalRowCount</span></strong> property setting affects whether a drop-down list, list box, or a filtered list box is used to select table records. For more information, see <a href="http://msdn.microsoft.com/library/5def498e-107d-4a2b-a621-fbbe0243e399(AX.60).aspx">Best Practices for Table Properties</a>.</td>
<td></td>
</tr>
<tr class="even">
<td><strong><span class="ui">ValidTimeStateFieldType</span></strong></td>
<td>Specifies the type of date-time field for the system to use when it tracks data within time spans.</td>
<td>AX 2012</td>
</tr>
<tr class="odd">
<td><strong><span class="ui">Visible</span></strong></td>
<td>Specifies the access rights when the table is used as a data source in a form or a report.If the table is used as a data source in a form, then the access rights in the form cannot exceed the access rights defined for the table.</td>
<td></td>
</tr>
</tbody>
</table>

## Tables and Report Models
The following properties are related to report models that are used to add information to a report.
-   AnalysisSelection
-   AnalysisVisibility
-   IsLookup
-   SingularLabel
-   TypicalRowCount



See also
--------

[Data Dictionary Node in the AOT](http://msdn.microsoft.com/library/4d7d1f77-11b8-4d8a-a44c-85e7d288c368(AX.60).aspx)

