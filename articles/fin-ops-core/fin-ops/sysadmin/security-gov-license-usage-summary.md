---
title: User security governance license usage summary
description: Learn about the user security governance license usage summary report.
author: ceian  
ms.author: ceian
ms.topic: concept-article
ms.date: 12/30/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-12-30
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# License Usage Summary Overview

The **Security Governance License Usage Summary** is a tool in Dynamics 365 Finance & Operations that helps system administrators, licensing managers, and compliance officers see exactly which licenses each user needs based on their assigned security roles. Instead of just giving raw license counts, this feature shows how each user's security roles - and the permissions within those roles - translate into licensing requirements.

:::image type="content" source="media/security-governance-license-usage-summary-overview.png" alt-text="License Usage summary overview." lightbox="media/security-governance-license-usage-summary-overview.png":::


This helps your organization: 

- **Confirm that security roles are configured for required licenses** for the tasks users perform. 
- **Identify when a security role is too broad or high-level**, causing a user to need a more expensive license than expected. 
- **Align security roles with internal controls and compliance** by revealing which permissions drive certain license requirements. 
- **Plan and optimize license requirements** by providing a clear view of how security roles drive required licenses. 

Additionally, if your organization has multiple Dynamics 365 Finance & Operations environments (such as multiple production instances), you can get a consolidated view of licensing across all environments in your tenant by using the **User License Consumption report** in the **[Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeAndOperations)**. 

**License Usage Summary** in the Security Governance workspace focuses on one environment at a time, while the **[Power Platform admin center](https://admin.powerplatform.microsoft.com/billing/licenses/financeAndOperations)** provides a tenant-wide perspective. 

>[!Note]
> The **License Usage Summary** is informational only. It does not assign licenses or change any user's access. It provides reporting on what licenses are required for the access each user and security role configuration. Ensure that users have the required license assigned in **[Microsoft 365 admin center](https://admin.microsoft.com)**

> [!IMPORTANT]
> If you’re not familiar with the Dynamics 365 licensing model or license types (for example, what's included in a **Finance** vs. an **Operations - Activity** license, or attach license requirements), review the latest [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [Dynamics 365 Licensing Deck](https://go.microsoft.com/fwlink/?linkid=2279233). Customers must acquire and assign appropriate subscription licenses for its users per [Microsoft's product terms](https://go.microsoft.com/fwlink/?linkid=2339737). Microsoft provides these reports to help customers monitor required licenses based on their users' configured access to Dynamics 365 finance and operations apps. User license reporting may vary based on user security role assignment and may be periodically enhanced to reflect Microsoft's current licensing requirements. [Learn more](https://go.microsoft.com/fwlink/?linkid=2323873).

> [!IMPORTANT]
> Updates to assigned security roles, customizations to security role's security objects typically take **2 to 8 hours** to appear in security governance reporting. Allow time for changes to be processed and reflected in the reports.

## Getting Started: Enabling the Feature 

Before you access the **User security governance** workspace, you must activate it in **Feature management**:

1. Sign in to your Dynamics 365 F&O environment with System Administrator rights.
2. Go to **System administration > Feature management**. Select and enable the following features.
   - *User security governance*
   - *User security governance license usage summary report*

:::image type="content" source="media/security-governance-license-usage-summary-feature-enable.png" alt-text="Security governance in the system admin user experience." lightbox="media/security-governance-license-usage-summary-feature-enable.png":::

:::image type="content" source="media/security-governance-license-usage-summary-feature-enabled.png" alt-text="Security governance features enabled in the system admin user experience." lightbox="media/security-governance-license-usage-summary-feature-enabled.png":::

> [!IMPORTANT]
> The **Security Governance** feature and **User Security Governance License Usage Summary** report are available only in versions [10.0.44](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) and above.

:::image type="content" source="media/security-governance-version-info.png" alt-text="Security governance version info." lightbox="media/security-governance-version-info.png":::

## Accessing License Usage Summary 

Once the feature is enabled, access the **License Usage Summary** page: 

Sign in to your Dynamics 365 F&O environment with **System Administrator** rights.

Go to **System administration > Security > Security Governance > License usage summary**. 

Within this workspace, you'll find multiple tabs that provide different views on licensing data: 

- **User Role Licenses**: User and the license(s) required based on their roles. 
- **Role Licenses**: Security role and the minimum license required for the role, plus details on covered security objects. 
- **Duty Licenses**: Shows license requirements for individual duties (groupings of privileges), if you need to examine license impacts at the duty level. 
- **Privilege Licenses**: Shows license requirements for individual privileges or menu items, for the most detailed analysis. 

Each of these views helps you analyze license usage from a different angle. 

For most day-to-day checks, focus on the **User Licenses** and **Role Licenses** tabs. 

## Understanding the User License Summary

:::image type="content" source="media/security-governance-license-usage-summary-user-role-licenses-overview.png" alt-text="User Role Licenses Overview screen with multiple finance and commcer licenses." lightbox="media/security-governance-license-usage-summary-user-role-licenses-overview.png":::

In the **User Licenses** view, each row corresponds to a user and displays the highest level of license that the user requires, given all the security roles assigned to them. Key columns in this view: 

- **User** - The user's ID whose license requirements you are examining. 

- **License** - The license needed for that user's assigned security role. The system looks at all the security objects in the assigned role and determines which license covers the most security objects in the role. 

- **License quantity** - How many licenses the user needs. Typically this is 1 (one base license). A number higher than 1 means the user needs one or more additional attach licenses. For example, 2 would mean the user needs their base license plus one attach license, 3 would mean the user needs their base license plus two attach licenses. 

>[!Tip] 
> For more **detailed analysis**, select **Open in Microsoft Office** to download a detailed view in Excel.

### How to use the User License Summary view: 

- **Verify expected licenses** : Check that each user's License matches what you expect for their assigned security role. If a user's license requirement is exactly what you'd anticipate (e.g. a finance clerk shows a **Finance** license), then you know their roles and associated security objects are appropriately configured. Then ensure that the user has the required license assigned in **[Microsoft 365 admin center](https://admin.microsoft.com)**. 

- **Investigate higher-than-expected licenses**: Pay special attention to users who require a higher license than seems appropriate. For instance, if a Warehouse clerk is shown needing a Finance license, it could mean they were inadvertently given a role with permissions that only a Finance user should have. Identify which roles that user has, then use the **Role Licenses** view for those roles to see what might be causing the increased requirement. 

>[!Tip]
> Duplicate the security role or duty using the [Duplicate a security role or duty with a license filter](/dynamics365/fin-ops-core/dev-itpro/sysadmin/security-role-duplicate-with-license-filter) feature to see which permissions are excluded when evaluating license requirements.

- **Address multiple license needs**: When the License quantity for a user is 2 or more, that uses's role and associated security objects span multiple product licenses. The highest-priority license is counted as the base license, and the remaining lower priority licenses would be attach licenses. Make sure the user is assigned all necessary license types in **[Microsoft 365 admin center](https://admin.microsoft.com)**. Also consider if those extra security priveleges (and the attach licenses they require) are truly needed, or if the user's access could be simplified to reduce the number of different licenses required. 

## Understanding the the Role Licenses View

The **Role Licenses** view highlights the license requirements for each security role in the system. Each row in this view is a security role, showing the minimum license level a user would need if they were assigned that role. You can filter by role to see how many security objects are entitled, not entitled, or not required for each license level. This breakdown helps explain why a particular license is indicated for that role.

:::image type="content" source="media/security-governance-license-usage-role-filter.png" alt-text="Role Licenses filtered for showing multiple license entitled values" lightbox="media/security-governance-license-usage-role-filter.png":::

Key columns in the **Role Licenses** view: 

- **Security Role** - Name of the security role (for example, Accounts payable clerk). 

- **License** - The lowest-level Dynamics 365 license that covers all permissions in the role. If the role’s permissions include any function that requires a higher license, that higher license will be shown here. 

- **Priority** - When a role's permissions cross multiple license levels, the **Priority** column indicates which license is considered primary. The licenses are ranked by how many security objects they cover. The highest priority license is listed as the Required License for the role. Any lower-priority licenses are also included as attach licenses in combination with other base licenses can also cover these security objects. 

:::image type="content" source="media/security-governance-license-usage-role-filter-priority.png" alt-text="Role Licenses filtered with priority column included." lightbox="media/security-governance-license-usage-role-filter-priority.png":::

**Entitlement counts** - For the required license, the role's permissions are broken down into three categories: 

- **Entitled** - Included security objects within the mapped license
- **Not entitled** - Not included in the mapped license (requires different license)
- **Not Required** - Security obects or privilege inherited in system user, not included in license computation

This breakdown helps you understand why a role requires the license it does. 

## Securable Object License Classification 

Each security object in a role has one of three classifications regarding required license: 

| Securable Object Status | Details |
|------------------------|---------|
| **Entitled** | The included security object's are **included** in the scope of the role's required license. No different license is required. |
| **Not Entitled** | These security object's are **not covered** by the role's required license. A different license is required, which can cause the role's overall requirement to a different license. |
| **Not Required** | The security object is not counted toward license requirement. For example, the included security objects may be inherited in system user and therefore not included in license computation

## Drilling Down into Specific Security Objects 

The **License Usage Summary** also lets you inspect exactly which security objects are contributing to a role or user's license requirements: 

**Detailed panel**: When you select a particular user (on the **User Licenses** tab) or a role (on the **Role Licenses** tab), a detailed panel appears at the bottom of the page -listing individual security objects related to that selection. 

- **Information provided**: For each listed security object, you'll see details such as: 
- **SecurableType** - The type of object (e.g. a form, report, menu item, button, api, etc.). 
- **AOT Name / Child Name** - The internal name of the object (from the Application Object Tree) and any sub-component. 
- **Access Level** - The level of access granted (Read, Update, Create, Invoke, Delete, etc.). 
- **License** - Which license is required by that security object. 
- **Entitled** / **Not Entitled** / **Not Required** - Whether that object is covered by the current license context, requires a different license, or may be inherited in system user and therefore not included in license computation 

Examining this detailed breakdown allows you to pinpoint the exact privileges or duties causing a higher license requirement. For example, you might discover that the **Retail Store Manager** role includes a privilege that is marked as **Not Entitled** under the **Operations - Activity** license. This implies that the functionality requires a higher license (perhaps a Supply Chain Management or Commerce license), which may drive the requirement for an attach license or a higher base license for users in that role. 

With this information, you can make informed decisions-such as removing that privilege from the role for users who don't need it, or knowing that anyone with that role should also be assigned the requisite attach license. 

>[!Tip]
> You can also use [Security analysis](/dynamics365/fin-ops-core/fin-ops/sysadmin/security-reports) to find where specific privileged entry points are introduced into roles, and Security configuration to adjust security roles.

## Example: A User with Multiple Roles 

Suppose a user has been assigned three roles: **Accountant**, **Retail Store Manager**, and **System User**. 

:::image type="content" source="media/security-governance-license-usage-summary-example.png" alt-text="License Usage summary example." lightbox="media/security-governance-license-usage-summary-example.png":::

The License Usage Summary shows the following for this user: 

| Role Name              | License                 | License Quantity | Notes |
|------------------------|-------------------------|------------------|-------|
| Accountant              | Finance                 | 1                | This security role has the highest priority license requirement |
| Retail Store Manager    | Operations - Activity   | 0                | No additional license requirement for this role, for this user, if the user has been assigned a Finance license |
| System User             | None                    | 0                | No additional license requirement for this role, for this user, if the user has been assigned a Finance license |

For this user, the **Finance license** is the necessary base license due to the high-level permissions of the Accountant role. Even though the user also has the **Retail Store Manager role** (which by itself requires an **Operations - Activity** license), the **Finance license** covers that role's requirements too, so no second license is required. 

Select the **Role License** tab, and select **Accountant** role to inspect specific objects (*3362*) Entitled security objects contributing to the requirement of a **Finance** license. For more detailed analysis, select **Open in Microsoft Office** to download a detailed view in Excel.

**Role License** tab:

| SKU Name | Securable Object Count | Entitlement | Notes |
|----------|------------------------|--------------------|-------|
| Finance  | 3,362                  | **Entitled** | Included in the mapped license scope |
| Finance  | 1,557                  | **Not Entitled** | Not included in the mapped license (requires different license) |

:::image type="content" source="media/security-governance-license-usage-summary-example-role-license.png" alt-text="License Usage Summary Role License detailed." lightbox="media/security-governance-license-usage-summary-example-role-license.png":::

From this example, we can draw a few conclusions: 

- The user must be assigned a **Finance** license in [Microsoft 365 admin portal](https://admin.microsoft.com) to ensure their access to the system. 
- If the user's job doesn't actually require full Finance capabilities, you might consider removing the **Accountant role** (and perhaps assigning a more appropriate role) so that the user could be fully served by a lower license like **Operations - Activity**. This would reduce licensing requirements and would limit the user's access to only what they need. 
- If the user truly needs both roles, ensure they have the Finance license. In this case, a **Operations - Activity** license is not needed because the Finance license supersedes it for this user's roles. 


## Ongoing Management and Best Practices 

Making the License Usage Summary part of your regular governance routine will help maintain both compliance and cost efficiency. Here are some best practices: 

- **Regular license reviews**: Periodically review the user license summary to catch any unexpected changes in license needs. For example, if someone's required license increases (perhaps due to a customization to the security role), you'll want to know and address it. 
- **Role audits**: Use the Role Licenses view to audit custom roles and even standard roles. If a role is causing users to need a higher license level, decide if that's required. It may be better to adjust the role's content or split responsibilities between roles to avoid over-privileging users. 
- **Support compliance audits**: When preparing for a compliance audit, export the License Usage Summary data to excel. This provides to auditors that your organization is properly managing license requirements. 
- **Cost management**: Keep an eye out for users who have high-level licenses but might not be using all their features. If the License Usage Summary indicates that certain users could operate under a less expensive license, consider adjusting their roles (and their license assignments) to optimize licensing costs. 
-  **Segregation of duties (SoD)**: While analyzing roles and user access, be mindful of SoD conflicts. The License Usage Summary, together with other security tools in Dynamics 365, can highlight if a user or role has permissions that should be segregated. Use this insight to refine roles and ensure critical processes have proper checks and balances. 

By leveraging the **Security Governance License Usage Summary** on a regular basis, you can keep your Dynamics 365 Finance & Operations environment **secure**, **compliant**, and **cost-effective**. This tool allows you to adjust security roles and license allocations proactively, ensuring that each user has the access they need while your organization only pays for the licenses that are truly required.


## Related information

- [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409)  
- [Finance and Operations Apps Security Role FAQ](https://go.microsoft.com/fwlink/?linkid=2319108)
- [Security governance FAQ](https://go.microsoft.com/fwlink/?linkid=2319108)
- [User security governance overview](/dynamics365/fin-ops-core/fin-ops/sysadmin/security-gov-overview)
- [Security governance FAQ](https://go.microsoft.com/fwlink/?linkid=2319108)  
- [Prepare for finance and operations apps user license validation](/dynamics365/fin-ops-core/dev-itpro/sysadmin/prepare-for-user-validation)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]