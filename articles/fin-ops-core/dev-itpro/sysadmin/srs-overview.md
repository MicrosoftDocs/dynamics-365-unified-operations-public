---
title: Cross-company data sharing overview
description: Learn about cross-company data sharing. This is a mechanism for sharing reference and group data among companies in a deployment.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: concept-article
ms.date: 01/21/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-01-27
ms.search.form: SysDataSharingConfiguration
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
---

# Cross-company data sharing overview

[!include [banner](../includes/banner.md)]

Cross-company data sharing enables you to share company-specific master, reference, and setup data across companies within a finance and operations deployment.

Two data sharing concepts are available:

> [!NOTE]
> Master company data sharing is generally available in version 10.0.43.

- Duplicate record sharing (DRS) is a concept where creating, updating, or deleting records for any company in the policy copies or replicates those changes across all companies in the policy. Updates of fields replicate if you select them for sharing in the policy. DRS was the first sharing type made available.
- Master company sharing, also known as single record sharing (SRS), is a concept where a single physical record belonging to a master company is virtually shared across child companies. Create, update, or delete in any company in the policy updates the single record used across all companies.

## Why should you consider cross-company data sharing?

Consider cross-company data sharing if you need consistent data across more than one company in a deployment. There might be hundreds of companies in a deployment and the business requires that at any time, these companies can rely on a single version of truth for critical data.

Here are some examples of business scenarios for cross-company data sharing:

- All customers should always be available to service and have the same terms across all companies.
- Terms for payment and delivery should always be aligned across all companies per region.
- Configuration for cash and bank management parameters must be aligned to secure consistent processing across all companies.

By using roles and security configuration, you can centralize maintenance of shared tables by only providing permissions to selected users in selected companies.

## Data sharing policies

Data sharing is based on the configuration of data sharing policies. By using policies, you can control the following aspects of data sharing:

- Data sharing concept.
- Tables that are shared.
- Fields that are shared.
- Companies that participate in the sharing.

:::image type="content" source="media/SRS-image1.png" alt-text="Screenshot of single record sharing example showing data sharing policy configuration.":::

The same company and table can only be in one enabled policy. However, you can share the same table in more than one policy. You might need to create more than one policy when you reach the limits of records or companies for DRS, or when you need to create policies for tables that need to be shared differently per country or region.

## When to consider duplicate record versus master company sharing

Duplicate record sharing has several advantages. Always select this option whenever possible. This consideration is important because once you enable master company sharing, you can't reduce the scope or stop sharing.

Consider master company sharing only if you need to share:

- More than 300 companies in the same policy.
  - In a policy, the number of transactions for any table exceeds 2 million records.
  - The limit is calculated as number of records per company multiplied by number of companies in a policy.
  - The table is supported for master company sharing.

|  Considerations  | Duplicate record sharing | Master company sharing |
|----|-----|-----|
| Can you remove tables, fields, or companies after enabling or updating a policy? | Yes   | No   |
| Can you disable a policy? |  Yes  |  No  |
| Can you add tables, fields, or companies after enabling a policy? | Yes   | Yes  |
| Can you exclude or unselect mandatory foreign key relations for sharing? | No   | No   |
| Can you manually manage sharing of nonmandatory foreign key fields? | Yes   | No   |
| Can fields that you don't select for sharing still be maintained in each company? | Yes   | No   |
| Max number of companies in a policy |  300  | No limit   |
| Max number of records per table and policy | 2 million    |  No limit  |
| Can you share tables without a unique index? |  No  |  Yes  |
| What table data sharing types are supported? | Duplicate   | Duplicate and single   |
| Can companies have existing records in a table before sharing is enabled? | Yes   | Only master company   |
| Is it required to select copy data and to validate sharing issues after enabling or updating a policy? |  Yes  |  No  |
| List of officially supported tables |  [Supported tables](/dynamics365/fin-ops-core/dev-itpro/sysadmin/drs-srs-tables)  | [Supported tables](/dynamics365/fin-ops-core/dev-itpro/sysadmin/drs-srs-tables#tables-supported-for-master-company-data-sharing)   |
| Are Microsoft-provided policy templates available?  |  Yes  |  No  |

You can combine duplicate record sharing and master company sharing for the same set of companies by using different policies. Always select all applicable tables and optional foreign key fields in the duplicate record policy and enable the policy before the master company sharing policy is enabled. This way you can share, for example, the customer groups and terms of payment tables, using duplicate record sharing and the customer table using master company sharing for scenarios where it's only the number of customer records that exceeds the limit and the number of companies don't exceed 300 for the policy.

## Specific considerations for successful data sharing

### Automatically added tables based on selected foreign key fields

Foreign key fields are selected automatically or manually. The system automatically adds tables that these foreign key fields reference when you enable or update a policy, if the reference table isn't already added.

In the example shown in the following image, the system automatically adds the terms of payment table unless you add it manually. The system adds this table because the PaymTermId foreign key field is selected for sharing in the Customer groups table.

:::image type="content" source="media/SRS-image2.png" alt-text="Screenshot of single record sharing showing foreign key field selection for customer groups table.":::

> [!NOTE]
> The system automatically adds only one level of child foreign key relationships.

The system doesn't display tables that it automatically adds when you enable or update a policy in the **Configure cross-company data sharing** form until you disable the policy. Manually add tables based on the selected foreign key fields before you enable or update the policy. By manually adding tables, you can understand the tables and fields that are shared. This approach also provides the option for DRS policies to select fields for these tables, including optional foreign key fields that in turn might add more tables.

### Country/region specific considerations for successful data sharing

Carefully consider tables that include country/region specific fields and logic. You might need to use sharing policies per country/region for certain tables to avoid configuration conflicts. Country/region specific fields are only viable and editable for companies in that country/region, but updates for these fields might trigger conflicts with companies in other country regions.

### Cross company data sharing consistency check
In Platform update 61, Microsoft added functionality for a consistency check. Run the consistency check when setting up data sharing to resolve configuration issues. The consistency check drops "orphaned" fields in a table that don't have a corresponding configuration. The consistency check enables quick detection and fixes any inconsistencies in the policy.

To enable the cross company data sharing consistency check, follow these steps:

1.	Go to **System administration** > **Setup** > **Configure cross-company data sharing**.
1.	On the **Configure cross-company data sharing** page, select **Consistency check**.

:::image type="content" source="media/configure-cross-company-data.png" alt-text="A screenshot of the Configure cross company data sharing page."::: 

### More considerations

- You must share composite tables in the same policy. If you don't, users see a message that prompts them to add more tables during enable and update to secure this.  
- For tables that use number sequences, all companies in a sharing policy for those entities must use the same number sequence types.
  - You can also align number sequences during enable and update.

## Limitations

- You can't share foreign key fields that reference financial dimensions, such as ledger or default dimension. Dimensions hold a loose foreign key reference to the backing dimension data, which can reference both company-specific and noncompany specific data. Determining the appropriate action to take for each dimension value has inherent complexity and would require a change from the current implementation, which could dramatically impact performance.
- You can't use sharing with dual-write.
- Deletion of shared records isn't yet fully supported and shouldn't be used. When you delete a shared record, any references (lookup or reference fields) on transactions might become blank. The same condition currently applies to the Rename action that renames the unique record key.

## Duplicate record sharing

The sharing logic for DRS is based on unique keys for records, such as Account for Customers or Name for Terms of Payment. Therefore, a table must have a unique index to be part of a DRS policy. After you enable or update a policy, copy data across companies to process the initial synchronization. Because the volumes can be large, perform this action during nonbusiness hours.

Only required foreign key fields are selected by default when you add a table to a policy. You need to manually select optional foreign keys to include them.

### Conflict resolution

Validation rules run when you enable or update a sharing policy. Always use **Find sharing issues** to view and resolve any inconsistencies between companies. Inconsistencies occur when attribute values differ between companies based on unique record keys. For example, the same name for terms of payment. Examples can be differences in description or payment method. In data sharing issues, you can select the company values that should be used for all other companies in the policy - either field by field or the full record.  

### Customer and vendor master data sharing feature

Customer and vendor master data sharing allows you to share customer and vendor data across multiple companies. You can enable it by using the customer and vendor master data sharing feature in Feature management. Consider the limits in the maximum number of records and companies stated earlier. Tables that are part of the party concept might require more preparations before sharing can be enabled. You have to resolve any scenario where the party relations differ across companies for the same unique record key. For example, customer account number 1000 might be related to different party IDs across companies. In this case, you must align party relationships if the customers use the rename function to keep them as separate customers. For more information, see [Party and global address book](../data-entities/dual-write/party-gab.md).

### Stop or reduce sharing scope

You can stop sharing by removing one or more companies before you update the policy. This approach also works for deselecting fields from sharing.

To stop sharing tables, you must disable the policy and then remove the tables. The same process applies when deleting an entire policy. In all these scenarios, synchronization stops for the excluded scope, but existing records remain. Sharing stops automatically at enable or update when the number of records for a table or number of companies exceed the maximum limits.  

## Master company sharing

Enable master company sharing by using the master company data sharing feature in the Feature management module. Enable the feature while in Maintenance mode.

> [!NOTE]
> Because you can't stop or reduce the sharing scope, test thoroughly and validate master company data sharing policies before enabling the same configuration in a production environment.

When you add a table to a master company sharing policy, all possible fields are selected by default. This selection includes all foreign key fields for all tables that support master company sharing. You can't disable master company policies, so it's especially important to manually add all tables that the default foreign key fields would otherwise add automatically. This manual addition is the only way to fully understand the table and field sharing scope that are enabled. The Configure cross-company data sharing form doesn't show automatically added tables. For example, the Vendors table is added when you add the Customer table based on foreign key relation, unless the Vendors table is already shared by using DRS.

You can use the DRS policy configuration as a workaround when you need to exclude a table from being automatically added based on foreign key relation. The workaround is to create and enable a DRS policy for the table by adding the master company and a nonoperational company to this policy. If you don't share a foreign key table, the foreign key field has no value.  

### Limitations

The following limitations exist:

- Change tracking for child company tables isn't supported. For example, you must use full export in data management.
- You can't use sharing in combination with Retail Channel Databases.
- Sharing is based on kernel logic. This means that no actual records exist in SQL for child companies.
