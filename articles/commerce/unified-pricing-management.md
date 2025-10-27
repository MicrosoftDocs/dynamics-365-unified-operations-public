---
title: Migrate to Unified Pricing Management in Dynamics 365
description: Learn how to migrate to Dynamics 365 Unified Pricing Management seamlessly. Simplify pricing strategies with centralized control and flexible rules.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 10/27/2025
ms.topic: concept-article
---

# Dynamics 365 Commerce pricing migration to Unified Pricing Management

[!INCLUDE[banner](../includes/banner.md)]

Dynamics 365 Unified Pricing Management (UPM) migration helps Dynamics 365 Commerce customers transition from the legacy Commerce Pricing Engine to the new Unified Pricing Management framework without heavy configuration or disruption.

This enhancement simplifies adoption, so you can quickly experience the benefits of centralized and flexible pricing management. It lays the groundwork for you to later extend your pricing strategies by incorporating more pricing attributes for greater precision and control.

The migration is structured into three incremental phases (from version 10.0.46 to 10.0.48), so you can move at your own pace and address various user scenarios and existing Commerce Pricing Engine configurations.

> [!NOTE]
> This section provides a clearer overview of the contents included in the 10.0.46 migration script.

---

### Sections

| Feature | Current nonattribute rule | New nonattribute rules | New attribute-based rules |
|----------|-----------------------------|--------------------------|----------------------------|
| Trade agreement price | Support | Can also migrate | Support |
| Discount | Migrate | Not support | Support |
| Shipping discount | Not support Yet | Not support | Support |
| Tender discount | Not support yet | Not support | Not support yet |
| Charges | Support | No migration (In the plan to migrate existing charges rules) | Support |
| Rebate management | Not support yet | Not support yet | Support |
| Trade agreement discount | Support | No migration | Not support | Not support yet |
| Price group | Migrate to attributes | Not support | Support |
| Price adjustments | Migration doesn't support till 10.0.47 | Not support | Support |

---

## Migration process

### Step 1: Enable the feature
In **Feature Management**, enable the feature:

> **Unified pricing management pricing rule performance and enhancement**

When you enable this feature, you unlock the migration options to migrate from Commerce Pricing Engine to Unified Pricing Management.

---

### Step 2: Set Up Price Group Mapping for Migration
After you enable the feature, go to:

**Retail and Commerce > Migration > Setup Price group mapping for migration**

- The system automatically converts all existing Commerce Price Groups to Unified Pricing Management Price Groups.  
- Each new group keeps the same price group conditions as its legacy configuration.  
- If duplicate mappings exist, the system prompts you to resolve them manually.  
- After resolving any duplicates, select **Validate** before proceeding.

---

### Step 3: Migrate Commerce Pricing Setup
Next, open:

**Retail and Commerce > Migration > Migrate Commerce Pricing Setup**

This screen lets you run the migration job that transitions your current Commerce Pricing Engine data into the Unified Pricing Management framework.

> [!NOTE]
> In version 10.0.46, Price Adjustments aren't yet included. Their migration support is coming in version 10.0.47.

---

### Step 4: Configure migration parameters
When you run the migration job:

- Use the **Effective after date** field to select pricing rules that are still active and should be migrated.  
- Choose whether to:  
  - Include disabled discounts  
  - Skip trade agreements  

If you want to continue applying existing trade agreements (without attributes), configure the corresponding parameters accordingly.

When the migration completes, your data and configurations are successfully migrated to Unified Pricing Management, providing a foundation for future enhancements to flexible pricing strategy.
