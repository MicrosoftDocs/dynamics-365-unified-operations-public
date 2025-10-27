---
title: Migrate to unified pricing management
description: Learn how to migrate to unified pricing management in Microsoft Dynamics 365 Commerce to simplify pricing strategies with centralized control and flexible rules.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 10/27/2025
ms.topic: how-to
ms.custom: 
  - bap-template
---

# Migrate to unified pricing management

[!INCLUDE[banner](../includes/banner.md)]

This article explains how to migrate to unified pricing management (UPM) in Microsoft Dynamics 365 Commerce to simplify pricing strategies with centralized control and flexible rules.

UPM migration helps Dynamics 365 Commerce customers transition from the legacy Commerce pricing engine to the unified pricing management framework without heavy configuration or disruption.

This enhancement simplifies adoption, so you can quickly experience the benefits of centralized and flexible pricing management. It lays the groundwork for you to later extend your pricing strategies by incorporating more pricing attributes for greater precision and control.

The migration is structured into three incremental phases from Commerce versions 10.0.46 to 10.0.48, so you can move at your own pace and address various user scenarios and existing Commerce pricing engine configurations.

> [!NOTE]
> This section provides a clearer overview of the contents included in the 10.0.46 migration script.

The following table describes whether or not various rules are supported for pricing features.

|Feature |Current nonattribute rule |New nonattribute rules |New attribute-based rules |
|----------|-----------------------------|--------------------------|----------------------------|
| Trade agreement price | Supported | Can also migrate | Supported |
| Discount | Migrate | Not supported | Supported |
| Shipping discount | Not supported yet | Not supported | Supported |
| Tender discount | Not supported yet | Not supported | Not supported yet |
| Charges | Supported | No migration (In the plan to migrate existing charges rules) | Supported |
| Rebate management | Not supported yet | Not supported yet | Supported |
| Trade agreement discount | Supported | No migration | Not support | Not supported yet |
| Price group | Migrate to attributes | Not supported | Supported |
| Price adjustments | Migration isn't supported until Commerce version 10.0.47. | Not supported | Supported |

## Migration process

To migrate to UPM, follow these steps.

1. In Dynamics 365 Commerce headquarters, go to the **Feature Management** workspace at **System administration** \> **Workspaces** \> **Feature management**.
1. Search for the **Unified pricing management pricing rule performance and enhancement** feature.
1. Select the feature, and then select **Enable**.

    > [!NOTE]
    > When you enable the feature, you unlock the migration options to migrate from the Commerce pricing engine to UPM.

1. Go to **Retail and Commerce \> Migration \> Set up Price group mapping for migration**. You'll see the following:

    - The system automatically converted all existing Commerce price groups to UPM price groups.  
    - Each new group keeps the same price group conditions as its legacy configuration. 

1. If duplicate mappings exist, the system prompts you to resolve them manually. After resolving any duplicates, select **Validate** before proceeding.
1. Go to **Retail and Commerce \> Migration \> Migrate Commerce Pricing Setup**. This page lets you run the migration job that transitions your current Commerce pricing engine data into the UPM framework.

    > [!NOTE]
    > In Commerce version 10.0.46, price adjustments aren't included. Price adjustments migration support is included in Commerce version 10.0.47.

1. Use the **Effective after date** field to select pricing rules that are still active and should be migrated.
1. Choose whether or not to include disabled discounts and skip trade agreements.
1. If you want to continue applying existing trade agreements without attributes, configure the corresponding parameters accordingly.
1. Select X to start the migration.

When the migration completes, your data and configurations are successfully migrated to UPM, providing a foundation for future enhancements to flexible pricing strategy.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
