---
title: License Usage Summary Security Object Licenses view (Preview)
description: Learn about the user security governance Security object licenses view (Preview).
author: ianceicys-msft
ms.author: ceian
ms.topic: concept-article
ms.date: 06/29/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2025-12-30
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# License usage summary security object licenses view (Preview)

[!INCLUDE [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Security object licenses view (Preview)**, part of user security governance, gives system administrators an object-by-object breakdown of every security object in a finance and operations environment, along with the license each object requires. Use this view to understand why a role maps to specific duties, which security objects are included in those duties, and which license each security object requires. You can also use this view to identify the objects that drive license requirements from end to end.

## Prerequisites

Before you open the Security object licenses view, confirm the following prerequisites are met:

- **[System administrator](/dynamics365/fin-ops-core/fin-ops/sysadmin/assign-users-security-roles) access** in finance and operations apps.
- Upgrade to the **[latest quality update (10.0.47 or 10.0.48)](https://go.microsoft.com/fwlink/?linkid=2095900)**.
- Enable **(Preview) User security governance security object license view** in Feature management.

### Upgrade to the latest quality update (10.0.47 or 10.0.48)

To use this feature, upgrade to the latest quality update (10.0.47 or 10.0.48).

:::image type="content" source="media/security-governance-security-object-license-preview-version-info.png" alt-text="Screenshot of the version information page for upgrading to the latest product quality update." lightbox="media/security-governance-security-object-license-preview-version-info.png":::

The preview requires upgrading the **Application** and **Platform** versions to one of the following minimum versions:

| Service release | 10.0.47 | 10.0.48 |
|---|---|---|
| Application version | **10.0.47 (10.0.2527.152+)** | **10.0.48 (10.0.2645.32+)** |
| Product update | **PU71** | **PU72** |
| Platform release | **7.0.7858.132** | **10.0.2645.72** |

To upgrade to the latest quality update and enable the features, follow these steps:

1. Go to [Microsoft Dynamics 365 Lifecycle Services](https://lcs.dynamics.com/v2).
1. Select your application and update your platform to one of the minimum versions.
1. Apply the latest **[Proactive Quality Update](https://go.microsoft.com/fwlink/?linkid=2095900)**.
1. Go to **System administration > Feature management > Check for updates**.
1. Search for and enable the following features:

   - **User security governance license usage summary report**
   - **(Preview) User security governance security object license view**

   :::image type="content" source="media/security-governance-license-object-preview-feature-enabled.png" alt-text="Screenshot of enabling the User security governance and Preview User security governance security object license view feature." lightbox="media/security-governance-license-object-preview-feature-enabled.png":::

   First enable User security governance license usage summary report, followed by enabling User security governance security object license view.

   :::image type="content" source="media/security-governance-license-usage-summary-feature-enabled.png" alt-text="Screenshot of security governance features enabled in the System administration user experience." lightbox="media/security-governance-license-usage-summary-feature-enabled.png":::

1. Go to **System administration > Security > Security governance** to confirm that the **License usage summary** report is available. From there, open the **Security object licenses** view.

   :::image type="content" source="media/security-governance-security-object-license-license-view-default-preview.png" alt-text="Screenshot of the Security governance Security object licenses view." lightbox="media/security-governance-security-object-license-license-view-default-preview.png":::

## Understand the Security object licenses view

The **Security object licenses view** displays every securable object across every role, with one row per object. This structure helps you trace permissions and configuration from the security role down to the specific menu items and data entities that the security role is configured to allow permission to.

The columns move from the security hierarchy, such as role, subrole, duty, and privilege, to the object itself, including securable type and Application Object Tree (AOT) names. The view then shows the individual permission grants: **Read**, **Update**, **Create**, **Delete**, and **Invoke**.

The final two columns show the mapped effective **Access level** and the eligible **License** that is required.

:::image type="content" source="media/security-governance-security-object-license-default-view-preview.png" alt-text="Screenshot of the default view for the Security object licenses view." lightbox="media/security-governance-security-object-license-default-view-preview.png":::

### Column reference

Each row represents one securable object and shows how that object maps from role to license. The grid includes the following columns.

| Term | Description |
|---|---|
| **Role name** | Name of the security role. Users get access through roles rather than by assigning permissions directly to each user. |
| **Subrole name** | Name of the subrole, or child role, of the security role. |
| **Duty name** | Name of the security duty. A duty is a grouping of privileges that represents a business process, such as maintaining bank transactions. |
| **Privilege name** | Name of the privilege. A privilege is a grouping of permissions that represents the access needed to perform a specific task or complete an assignment. |
| **Securable type** | Type of object that you can secure, such as a menu item, table, form, report, button, or API. Reporting can show **Menu item action**, **Menu item display**, and **DataEntity**. |
| **AOT name** | Name of the Application Object Tree object. |
| **AOT child name** | Name of the child Application Object Tree object, or subcomponent of the AOT object. |
| **Read** | Grant setting for the **Read** permission on the securable object. If only Read is granted, the resulting access level is Read. |
| **Update** | Grant setting for the **Update** permission: **Grant**, **Deny**, or **Unset**. Update access allows a user to modify existing records. Granting Update, or any permission beyond Read, elevates the access level to Write. |
| **Create** | Grant setting for the **Create** permission: **Grant**, **Deny**, or **Unset**. Create access allows a user to add new records. Granting Create elevates the access level to Write. |
| **Delete** | Grant setting for the **Delete** permission: **Grant**, **Deny**, or **Unset**. Delete access allows a user to remove records. Granting Delete elevates the access level to Write. |
| **Invoke** | Grant setting for the **Invoke** permission: **Grant**, **Deny**, or **Unset**. Invoke access allows a user to execute or run an operation and is the only applicable permission for ServiceOperation and DataEntityMethod object types. Granting Invoke implies Execute, a write-class operation, so it elevates the access level to Write. |
| **Access level** | Effective access level that is rolled up from the permission grants. Access level is identified as **Read** when only Read is granted, or **Write** when any permission beyond Read is granted. If **Read** is denied, access is denied. If all permissions are **Unset**, the access level is **NotSpecified**. |
| **License** | Associated license requirement that maps to the securable object. When multiple license SKUs satisfy the requirement, they appear as a string separated by **or**. When **Access level** is **Read**, the applicable license is no higher than Team Members or Human Resources Self-Service. |

> [!IMPORTANT]
> Many out-of-the-box securable objects include read-only entry points. Read access to these standard security objects requires at least a **[Dynamics 365 Team Members](https://admin.cloud.microsoft/?#/licensedetailpage/8e7a3d30-d97d-43ab-837c-d7701cef83dc)** license. For more information, see the latest [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## Use the Security object licenses view

The **Security object licenses** view helps explain each security role, its included securable objects, and the applicable license requirement for each object.

A common pattern is a securable object that grants **Write** access when only **Read** access is needed. This configuration can increase the required license from Team Members to a full user license.

1. In **License usage summary**, open the **Security object licenses view (Preview)**.
1. Filter to the role that you want to inspect.
1. Review the associated columns and note the **License** column, which is the last column in the grid.
1. If the securable object appears to require a higher license than expected, review whether the object includes **Write** access that isn't needed.

   :::image type="content" source="media/security-governance-security-object-license-license-view-preview.png" alt-text="Screenshot of specific security objects displayed with the License column." lightbox="media/security-governance-security-object-license-license-view-preview.png":::

### Find objects with multiple eligible licenses

To identify securable objects that can map to multiple applicable licenses, filter the **License** column by using **contains** and the value **or**.

This filter helps you confirm whether an existing license already covers an object before you make changes to a **role**, **permission**, or **access level**.

:::image type="content" source="media/security-governance-security-object-license-filtered-license-or-view-preview.png" alt-text="Screenshot of filtering the License column by or when multiple licenses satisfy the requirement." lightbox="media/security-governance-security-object-license-filtered-license-or-view-preview.png":::

### Export to Excel for deeper analysis

For more detailed analysis, select **Open in Microsoft Office** to export the complete detailed object-to-license inventory to Microsoft Excel.

:::image type="content" source="media/security-governance-security-object-license-export-office-preview.png" alt-text="Screenshot of exporting the Security object licenses view to Microsoft Office." lightbox="media/security-governance-security-object-license-export-office-preview.png":::

:::image type="content" source="media/security-governance-security-object-license-export-office-example-preview.png" alt-text="Screenshot of the Excel export of the complete security object inventory to Microsoft Office." lightbox="media/security-governance-security-object-license-export-office-example-preview.png":::

> [!NOTE]
> If you need to export more than 50,000 rows, a system administrator can adjust the maximum export limit. To adjust the maximum export limit, follow these steps:
>
> 1. Go to **System administration > Setup > Client performance options**.
> 1. Locate the **Maximum number of rows to export to Excel** field.
> 1. Change the value from **0**, the default value that allows up to 50,000 rows, to a higher number, up to 1,000,000 rows.
> 1. Save the configuration.
>
> Users can now export larger datasets in a single session.

## Related information

- [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409)  
- [Finance and Operations Apps Security Role FAQ](https://go.microsoft.com/fwlink/?linkid=2319108)
- [Security governance FAQ](https://go.microsoft.com/fwlink/?linkid=2319108)
- [User security governance overview](/dynamics365/fin-ops-core/fin-ops/sysadmin/security-gov-overview)
- [Prepare for finance and operations apps user license validation](/dynamics365/fin-ops-core/dev-itpro/sysadmin/prepare-for-user-validation)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
