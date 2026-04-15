---
title: Security and data entities
description: Learn about security for data entities, including overviews of entry points, target scenarios, and privileges.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.assetid: a9ede141-56fa-4310-997d-aeef184f7a52
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Security and data entities

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Data entities don't support the Extensible Data Security (XDS) concepts.

## Entry points

Data entities support entry point security. This support resembles the support that menu items and pages have. To give you flexibility when you define a security model, data entities allow for a separate security configuration for each integration mode. Currently, two entry points and integration modes are identified for a data entity.

| Entry point     | Description                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------------|
| Data services   | The ability to use OData services (API) for the entity.                                                              |
| Data management | The ability to use asynchronous integration options for the entity, such as import/export and connector integration. |

## Target scenarios

Data entities can support multiple categories of scenarios. Each category might require separate security.

- **Data management (file-based import/export, and so on)** – Typically, a data manager performs these scenarios. These scenarios might provide access to data that isn't usually accessible through the UI for the client. Therefore, you often want to secure data management scenarios independently of access to the related page, so that a data manager can perform only import/export operations.
- **General integration via OData** – Many integration scenarios require that data entities be exposed as services, so that data can be accessed via OData (for example, from an online storefront or a Process Lifetime Management \[PLM\] system). Often, you want to control access to data entities that are built for this purpose independently of page access. In other words, you want to grant access to the service interface without granting access through the client UI.
- **Microsoft Office integration (Edit in Excel, and so on)** – Office integration scenarios also require that data entities be accessed via OData. However, from an end-user perspective, these scenarios can be viewed as a natural extension of the client, where, for example, Microsoft Excel is used to simplify some editing tasks. Therefore, there's usually no reason to secure the Microsoft Office integration independently of page access.

## Privilege and duty mapping

Depending on the target scenarios for a data entity, create one or more new privileges and extend existing duties. Alternatively, map the new privileges to duties that you create specifically for the target scenario. This approach helps guarantee that no user is granted more access than the user requires for the scenario.

The following table shows the privileges that you should create. It also explains how you should map these privileges to duties. If your data entity is intended to support more than one scenario, create the combined set of privileges and duty mappings.

| Target scenario | Privileges | Duty mapping |
|---|---|---|
| The data entity is intended for data management. | Create the following new privileges: *&lt;DataEntity&gt;***Import** (Grant=Create, IntegrationMode=DataManagement), *&lt;DataEntity&gt;***Export** (Grant=Read, IntegrationMode=DataManagement) | Extend the relevant data management duties with the new privileges. For more information, see the "Data administrator role" section later in this article. |
| The data entity is intended for general integration via OData. | Create the following new privileges: *&lt;DataEntity&gt;***View** (Grant=Read, IntegrationMode=DataServices), *&lt;DataEntity&gt;***Maintain** (Grant=Delete, IntegrationMode=DataServices) | Create new duties for the integration scenario, and map the relevant new privileges to these duties. For more information, see the "Duty naming guidelines" section later in this article. |
| The data entity is intended for Microsoft Office integration. | Create the following new privileges: *&lt;DataEntity&gt;***View** (Grant=Read, IntegrationMode=DataServices), *&lt;DataEntity&gt;***Maintain** (Grant=Delete, IntegrationMode=DataServices) | Extend the relevant existing duties that provide access to the related pages with the new privileges. |

Because the approach described in the preceding table complies with the principle of least privilege, use it. Nevertheless, in some situations, you can use the following simpler approach. However, be aware that this approach might be less secure. It might also be slightly harder to maintain and extend.

| Target scenario | Privileges | Duty mapping | Potential issues |
|---|---|---|---|
| The data entity is intended for data management, general integration via OData, and Microsoft Office integration. | Create the following new privileges: *&lt;DataEntity&gt;***View** (Grant=Read, IntegrationMode=All), *&lt;DataEntity&gt;***Maintain** (Grant=Delete, IntegrationMode=All) | 1. Extend the relevant data management duties with the new privileges. 1. Create new duties for the integration scenario, and map the relevant new privileges to these duties. 1. Extend the relevant existing duties that provide access to the related page with the new privileges. | When you use this approach, a data manager who is granted access to import and export data can also access the system from a web service. Likewise, a user who is granted access to the page that is associated with a data entity can also access the system from a web service. This user is prevented from data import and export only if the user isn't granted the related data management duty. |

## Duty naming guidelines

When you create data entities for specific integration scenarios, also create separate duties. These duties grant the external application or service the required access to the data entities. Follow the same naming guidelines as the corresponding duties that provide access through the client UI. However, add a "using services" suffix.

| Duty type | Duty object name suffix | Duty name template |
|---|---|---|
| Enable | …IntegrationEnable | Enable … using services |
| Record | …IntegrationMaintain | Maintain … using services |
| Authorize | …IntegrationApprove (Release, Confirm, Journalize) | Approve (Release, Confirm, Journalize) … using services |
| Inquire | …IntegrationInquire | Inquire into … using services |

Here are some examples of duty names that follow these guidelines:

- Maintain route master using service
- Inquire into case progress using services

## Data administrator role

The **DataManagementApplicationAdministrator** security role grants full import and export capabilities in the **Data management** workspace. This security role includes two security duties for each of the five data entity categories that you assign to it. One duty handles importing data through data entities of the associated category, and the other duty handles exporting data through data entities of the associated category. As a result, this security role has 10 security duties in total:

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

When you create data entities for use in the **Data management** workspace, extend these duties with the new security privileges, based on the **Entity Category** property that you specify on the data entity. For more information about how to extend duties with new security privileges, see the "Privilege/duty mapping" section earlier in this article. You can also use these duties to create new roles for specific data management scenarios.

## Modeling new entry point security in the Application Explorer

The pattern for modeling security resembles the pattern for modeling security with privileges on an entry point. To model security, follow these steps:

1. Create a new privilege.
1. Create new data entity permissions.
1. Set the **Name** to **Data Entity**.
1. Select the **Access Level**.
1. Select **Integration Mode** (All &gt; Data Services &gt; Data Management). This setting is specific to Object Type: Data Entity.

    - **All** – Applies the same security settings to both OData and data import/export.
    - **Data Management** – Applies only to data import/export and connector integration.
    - **Data Services** – Applies only to OData Services.

:::image type="content" source="./media/rolebasedsecurity.png" alt-text="Screenshot of the role-based security configuration for data entity entry points." lightbox="./media/rolebasedsecurity.png":::

## Sensitive data

The Table Protection Framework (TPF) enables strict access control to data that is stored in finance and operations. This feature is exposed through the AOSAuthorization property on tables and table fields. If you mark a table or field by using AOSAuthorization, the security framework now requires that a user be granted explicit access to that resource. This requirement also applies when the table or field is accessed through data entities. This section describes the guidelines for granting TPF permissions for data entities.

### Data management

For data entities that are targeted at data migration, assign TPF permissions to the corresponding import/export privileges. This approach helps guarantee that all data can be imported and exported.

### Integration by using OData

For data entities that target integration scenarios, assign TPF permissions based on whether the TPF-protected field is essential for the data entity to work:

- **If the TPF-protected field is essential**: An essential field is a field that the system always reads or writes. In this case, grant TPF permissions to the same privileges that grant access to the data entity.
- **If the TPF-protected field isn't essential**: Examples of nonessential fields include the field for a worker's Social Security number and the field for a vendor's bank account number. In this case, grant TPF permissions for accessing the field through a separate privilege. Assign that privilege directly to the roles that require access to the TPF-protected field. However, if the field is a mapped field on the entity, the role probably already has access, if that role also has access to the field through pages in the client UI.

Granting explicit access to TPF-protected fields that aren't essential for the entity has several advantages:

- You can more easily discover who has access to sensitive data.
- You help reduce the risk that someone gains access to sensitive data by accident, because a role gains access only if you assign both a duty and a privilege to it.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
