---
# required metadata

title: Security and data entities
description: This article provides information about security for data entities.
author: peakerbl
ms.date: 03/11/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: a9ede141-56fa-4310-997d-aeef184f7a52
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Security and data entities

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

> [!NOTE]
> Data entities do not support the Extensible Data Security (XDS) concepts.

## Entry points
Data entities support entry point security. This support resembles the support that menu items and pages have. To give you flexibility when you define a security model, data entities allow for a separate security configuration for each integration mode. Currently, two entry points/integration modes are identified for a data entity.

| Entry point     | Description                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------------|
| Data services   | The ability to use OData services (API) for the entity.                                                              |
| Data management | The ability to use asynchronous integration options for the entity, such as import/export and connector integration. |

## Target scenarios
Data entities can support multiple categories of scenarios. Each category might have to be secured separately.

- **Data management (file-based import/export, and so on)** – Typically, a data manager performs these scenarios. These scenarios might provide access to data that isn't usually accessible through the UI for the client. Therefore, you will often want to secure data management scenarios independently of access to the related page, so that a data manager can perform only import/export operations.
- **General integration via OData** – Many integration scenarios require that data entities be exposed as services, so that data can be accessed via OData (for example, from an online storefront or a Process Lifetime Management \[PLM\] system). Often, you will want to control access to data entities that are built for this purpose independently of page access. In other words, you will want to grant access to the service interface without granting access through the client UI.
- **Microsoft Office integration (Edit in Excel, and so on)** – Office integration scenarios also require that data entities be accessed via OData. However, from an end-user perspective, these scenarios can be viewed as a natural extension of the client, where, for example, Microsoft Excel is used to simplify some editing tasks. Therefore, there is usually no reason to secure the Microsoft Office integration independently of page access.

## Privilege/duty mapping
Depending on the target scenarios for a data entity, you should create one or more new privileges, and extend existing duties. Alternatively, you can map the new privileges to duties that are created specifically for the target scenario. This approach helps guarantee that no user is granted more access than the user requires for the scenario.

The following table shows the privileges that you should create. It also explains how you should map these privileges to duties. If your data entity is intended to support more than one scenario, you should create the combined set of privileges and duty mappings.

<table>
<thead>
<tr>
<th>Target scenario</th>
<th>Privileges</th>
<th>Duty mapping</th>
</tr>
</thead>
<tbody>
<tr>
<td>The data entity is intended for data management.</td>
<td>Create the following new privileges:
<ul>
<li><em>&lt;DataEntity&gt;</em><strong>Import</strong>
<ul>
<li>Grant=Create</li>
<li>IntegrationMode=DataManagement</li>
</ul>
</li>
<li><em>&lt;DataEntity&gt;</em><strong>Export</strong>
<ul>
<li>Grant=Read</li>
<li>IntegrationMode=DataManagement</li>
</ul>
</li>
</ul>
</td>
<td>Extend the relevant data management duties with the new privileges. For more information, see the "Data administrator role" section later in this article.</td>
</tr>
<tr>
<td>The data entity is intended for general integration via OData.</td>
<td>Create the following new privileges:
<ul>
<li><em>&lt;DataEntity&gt;</em><strong>View</strong>
<ul>
<li>Grant=Read</li>
<li>IntegrationMode=DataServices</li>
</ul>
</li>
<li><em>&lt;DataEntity&gt;</em><strong>Maintain</strong>
<ul>
<li>Grant=Delete</li>
<li>IntegrationMode=DataServices</li>
</ul>
</li>
</ul>
</td>
<td>Create new duties for the integration scenario, and map the relevant new privileges to these duties. For more information, see the "Duty naming guidelines" section later in this article.</td>
</tr>
<tr>
<td>The data entity is intended for Microsoft Office integration.</td>
<td>Create the following new privileges:
<ul>
<li><em>&lt;DataEntity&gt;</em><strong>View</strong>
<ul>
<li>Grant=Read</li>
<li>IntegrationMode=DataServices</li>
</ul>
</li>
<li><em>&lt;DataEntity&gt;</em><strong>Maintain</strong>
<ul>
<li>Grant=Delete</li>
<li>IntegrationMode=DataServices</li>
</ul>
</li>
</ul>
</td>
<td>Extend the relevant existing duties that provide access to the related pages with the new privileges.</td>
</tr>
</tbody>
</table>

Because the approach that is described in the preceding table complies with the principle of least privilege, we recommend that you use it. Nevertheless, in some situations, you can use the following simpler approach. However, be aware that this approach might be less secure. It might also be slightly harder to maintain and extend.

<table>
<thead>
<tr>
<th>Target scenario</th>
<th>Privileges</th>
<th>Duty mapping</th>
<th>Potential issues</th>
</tr>
</thead>
<tbody>
<tr>
<td>The data entity is intended for data management, general integration via OData, and Microsoft Office integration.</td>
<td>Create the following new privileges:
<ul>
<li><em>&lt;DataEntity&gt;</em><strong>View</strong>
<ul>
<li>Grant=Read</li>
<li>IntegrationMode=All</li>
</ul>
</li>
<li><em>&lt;DataEntity&gt;</em><strong>Maintain</strong>
<ul>
<li>Grant=Delete</li>
<li>IntegrationMode=All</li>
</ul>
</li>
</ul>
</td>
<td>
<ol>
<li>Extend the relevant data management duties with the new privileges.</li>
<li>Create new duties for the integration scenario, and map the relevant new privileges to these duties.</li>
<li>Extend the relevant existing duties that provide access to the related page with the new privileges.</li>
</ol>
</td>
<td>When you use this approach, a data manager who is granted access to import/export data can also access the system from a web service. Likewise, a user who is granted access to the page that is associated with a data entity can also access the system from a web service. This user will be prevented from data import/export only if the user hasn't been granted the related data management duty.</td>
</tr>
</tbody>
</table>

## Duty naming guidelines
When you create data entities for specific integration scenarios, you should also create separate duties. These duties grant the external application or service the required access to the data entities. The duties that you create should follow the same naming guidelines as the corresponding duties that provide access through the client UI. However, you should add a "using services" suffix.

<table>
<thead>
<tr>
<th>Duty type</th>
<th>Duty object name suffix</th>
<th>Duty name template</th>
</tr>
</thead>
<tbody>
<tr>
<td>Enable</td>
<td>…IntegrationEnable</td>
<td>Enable … using services</td>
</tr>
<tr>
<td>Record</td>
<td>…IntegrationMaintain</td>
<td>Maintain … using services</td>
</tr>
<tr>
<td>Authorize</td>
<td>…IntegrationApprove (Release, Confirm, Journalize)</td>
<td>Approve (Release, Confirm, Journalize) … using services</td>
</tr>
<tr>
<td>Inquire</td>
<td>…IntegrationInquire</td>
<td>Inquire into … using services</td>
</tr>
</tbody>
</table>

Here are some examples of duty names that follow these guidelines:

- Maintain route master using service
- Inquire into case progress using services

## Data administrator role
The **DataManagementApplicationAdministrator** security role enables an associated user to have full import/export capabilities in the **Data management** workspace. This security role has two security duties for each of the five data entity categories that are assigned to it. One duty is for importing data via data entities of the associated category, and one for exporting data via data entities of the associated category. Therefore, a total of 10 security duties are assigned to this security role:

- DataManagementApplicationDocumentEntitiesMaintain
- DataManagementApplicationDocumentEntitiesView
- DataManagementApplicationMasterEntitiesMaintain
- DataManagementApplicationMasterEntitiesView
- DataManagementApplicationParametersEntitiesMaintain
- DataManagementApplicationParametersEntitiesView
- DataManagementApplicationReferenceEntitiesMaintain
- DataManagementApplicationReferenceEntitiesView
- DataManagementApplicationTransactionEntitiesMaintain
- DataManagementApplicationTransactionEntitiesView

When you create data entities that can be used in the **Data management** workspace, you must extend these duties with the new security privileges, based on the **Entity Category** property that is specified on the data entity. (For information about how to extend duties with the new security privileges, see the "Privilege/duty mapping" section earlier in this article.) You can also use the duties to create new roles for specific data management scenarios.

## Modeling new entry point security in the Application Explorer
The pattern for modeling security resembles the pattern for modeling security with privileges on an entry point. To model security, follow these steps.

1. Create a new privilege.
2. Create new data entity permissions.
3. Set the **Name** to **Data Entity**.
4. Select the **Access Level**.
5. Select **Integration Mode** (All &gt; Data Services &gt; Data Management). This is specific to Object Type: Data Entity.

    - **All** – Applies same security settings to be applied to both OData and data import/export.
    - **Data Management** – Applies only to data import/export and connector integration.
    - **Data Services** – Only applies to OData Services.

[![RolebasedSecurity.](./media/rolebasedsecurity.png)](./media/rolebasedsecurity.png)

## Sensitive data
The Table Protection Framework (TPF) enables strict access control to data that is stored in finance and operations. This feature is exposed through the AOSAuthorization property on tables and table fields. If you mark a table or field by using AOSAuthorization, the security framework now requires that a user be granted explicit access to that resource. This requirement also applies when the table or field is accessed through data entities. This section describes the guidelines for granting TPF permissions for data entities.

### Data management 
For data entities that are targeted at data migration, you should assign TPF permissions to the corresponding import/export privileges. In this way, you help guarantee that all data can be imported and exported.

### Integration by using OData
For data entities that are targeted at integration scenarios, the TPF permissions that you should assign depend on whether the TPF-protected field is essential for the data entity as a whole to work:

- **If the TPF-protected field is essential**: An essential field is a field that will always be read/written. In this case, TPF permissions should be granted to the same privileges that grant access to the data entity.
- **If the TPF-protected field isn't essential**: Examples of nonessential fields include the field for a worker's Social Security number and the field for a vendor's bank account number. In this case, TPF permissions for accessing the field should be granted through a separate privilege, and that privilege should be assigned directly to the roles that require access to the TPF-protected field. However, if the field is a mapped field on the entity, that access has probably already been granted to the role, if that role also has access to the field through pages in the client UI.

There are several advantages to granting explicit access to TPF-protected fields that aren't considered essential for the entity:

- You can more easily discover who has access to sensitive data.
- You help reduce the risk that someone will gain access to sensitive data by accident, because a role gains access only if you assign both a duty and a privilege to it.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

