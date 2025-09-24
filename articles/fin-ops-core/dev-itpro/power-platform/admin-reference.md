---
title: Configure Dataverse virtual entities
description: Learn about how to configure virtual entities for finance and operations apps in Microsoft Dataverse, including overviews on authentication and authorization.
author: pnghub
ms.author: abhijanand
ms.topic: how-to
ms.date: 07/17/2025
ms.custom: NotInToc
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-05-31
ms.dyn365.ops.version: 10.0.12
---

# Configure Dataverse virtual entities

[!include [banner](../includes/banner.md)]



This article explains how to configure virtual entities for finance and operations apps in Microsoft Dataverse.

> [!IMPORTANT]
> For finance and operations apps environments for which the Microsoft Power Platform integration is enabled, the virtual entity configuration is automatically performed as part of the process for enabling the integration. The manual configuration is no longer supported.
> 
> Each Dataverse environment must point to only one finance and operations instance at any time, and each finance and operations environment must point to only one Dataverse environment.
> 
> Virtual entities aren't supported across tenants. The Microsoft Power Platform environment must be on the same Microsoft Entra tenant as the finance and operations apps environment.
> 
> For more information about how to enable the Microsoft Power Platform integration for finance and operations apps environments, see [Enable the Microsoft Power Platform integration](enable-power-platform-integration.md).

## <a name="get-virtual-entity-solution"></a>Getting the virtual entity solution

The Dataverse solution for finance and operations virtual entities must be installed from Microsoft AppSource virtual entity solution. For more information, see [finance and operations virtual entity](https://appsource.microsoft.com/product/dynamics-crm/mscrm.finance_and_operations_virtual_entity).

Ensure the following solutions are installed in Dataverse.

- **Dynamics365Company** - This adds the **Company** entity, which is referenced by all finance and operations entities with a PrimaryCompanyContext metadata value.

- **MicrosoftOperationsVESupport** - This provides the core support for the finance and operations virtual entity feature.

- **MicrosoftOperationsERPCatalog** - This provides a list of available finance and operations entities through the mserp_financeandoperationsentity virtual entity.

- **MicrosoftOperationsERPVE** - This is the API-managed solution that contains the generated virtual entities as they're made visible.

When updates are available for the virtual entity solution, they can be manually applied in the Power Platform admin center. For more information about how to manually install and update the virtual entity solution, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps). 

> [!NOTE]
> For finance and operations apps environments that the Microsoft Power Platform integration is enabled for, available updates to the virtual entity solution are automatically applied.

When the virtual entity configuration is completed, you can enable the virtual entities in Dataverse. For more information, see [Enable Microsoft Dataverse virtual entities](enable-virtual-entities.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
