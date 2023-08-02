---
# required metadata

title: Enable quality and nonconformance management
description: This article provides an overview of the process for setting up and configuring quality and nonconformance management features in Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestAssociationTable, InventTestGroup, InventTestItemQualityGroup, InventTestTable, InventTestVariable, InventTestVariableOutcome, InventParameters, InventProblemType, InventProblemTypeSetup, InventQuarantineZone, InventTestDiagnosticType, InventTestReportSetup, SysUserManagement, InventTestRelatedOperations
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Enable quality and nonconformance management

[!include [banner](../includes/banner.md)]

This article provides an overview of the process for setting up and configuring quality and nonconformance management features in Microsoft Dynamics 365 Supply Chain Management.

## <a name="enable-qm"></a>Enable quality and nonconformance management

Follow these steps to enable quality management on your system.

1. Go to **Inventory management \> Setup \> Inventory and warehouse management parameters**.
1. On the **Quality management** tab, set the **Use quality management** option to *Yes*.
1. In the **Hourly rate** field, enter an hourly labor rate in the local currency. The hourly rate is used to calculate costs for operations that are related to a nonconformance. The hourly rate and calculated costs provide reference information for a nonconformance. They don't interact with other functionality.
1. Select **Report setup**.
1. Add new lines for the various report types, and select the type of document to use for each report.
1. Close the page.
1. Close the page.

## Quality management configuration process

Before you can start to use the quality management features and generate quality orders, you must configure the system and prerequisites. Here is a list of the steps that are required to configure quality management.

1. [Enable quality and nonconformance management](#enable-qm).
1. Optional: [Configure test instruments](quality-test-instruments.md).
1. [Configure tests](quality-tests.md).
1. [Configure test variables and outcomes](quality-test-variables.md).
1. [Configure test groups](quality-test-groups.md).
1. Optional: [Configure quality groups, and link to products](quality-groups.md).
1. Optional: [Configure quality associations](quality-associations.md).

After the configuration is completed, you can start to create and process quality orders. For more information about how to create and work with quality orders, see [Quality orders](quality-orders.md).

## Nonconformance management configuration process

Before you can start to use the nonconformance management features and generate nonconformances, you must configure the system and prerequisites. Here is a list of the steps that are required to configure nonconformance management.

1. [Enable quality and nonconformance management](#enable-qm).
1. [Configure workers who are responsible for approving nonconformances](quality-responsible-workers.md).
1. [Configure problem types](quality-problem-types.md).
1. [Configure quarantine zones](quality-quarantine-zones.md).
1. [Configure diagnostic types](quality-diagnostic-types.md).
1. [Configure operations](quality-operations.md).
1. Optional: [Configure quality charges](quality-charges.md).

After the configuration is completed, you can start to create and process nonconformances. For more information about how to create and work with nonconformances, see [Create and process nonconformances](tasks/create-process-non-conformance.md).

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
