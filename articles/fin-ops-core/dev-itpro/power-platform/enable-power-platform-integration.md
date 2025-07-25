---
title: Enable Power Platform integration
description: Learn about how to enable the Microsoft Power Platform integration by using Microsoft Dynamics Lifecycle Services for finance and operations apps and Dataverse.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/24/2025
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Enable Power Platform integration

[!include[banner](../includes/banner.md)]

> [!IMPORTANT]
> Beginning **May 1, 2025**, all environments for finance and operations apps are required to have the Power Platform integration enabled. Before this date, environment administrators should enable Power Platform integration by following the steps in this article, and selecting the Power Platform environment to which the environment for your finance and operations apps should be linked. Any finance and operations apps environments that aren't linked to a Power Platform environment through the Power Platform integration after this date will have the Power Platform integration automatically enabled for the environment. During automated enablement, the environment will either be linked to a newly provisioned Power Platform environment, or linked to an existing Power Platform environment if either [dual-write](../data-entities/dual-write/dual-write-home-page.md) or [virtual entities for finance and operations apps](../power-platform/virtual-entities-overview.md) has already been enabled for the environment.
> Learn more in [Microsoft Power Platform integration with finance and operations apps](overview.md#tools-and-services-unlocked-with-microsoft-power-platform-integration) that includes which features are enabled by the Power Platform integration.

As part of the One Dynamics, One Platform effort, a growing number of customers get value out of integrating their finance and operations apps with Microsoft Dataverse and the Microsoft Power Platform ecosystem. Whether it's used to build low-code applications, or to fully integrate front-office and back-office processes and applications, the integration of these two systems is a common requirement for many customers.

Power Platform Integration is a feature you can enable in Microsoft Dynamics Lifecycle Services. It lets administrators link their finance and operations environments with new or existing Microsoft Power Platform–based environments. 

After Power Platform integration is established, your organization can perform these actions:

* Create low-code apps and flows by using the Power Platform environment that link to finance and operations apps.
* Integrate finance and operations apps data with the Dataverse platform by using virtual tables, business events, and dual-write features.
* Install and connect other Dynamics 365 applications with your finance and operations apps.
* Install add-ins and connect them with your finance and operations apps.

To learn more about Power Platform integration, watch our TechTalk on the [Microsoft Dynamics 365 Community](https://www.youtube.com/@MSD365Community) YouTube channel.

> [!VIDEO https://www.youtube.com/embed/HmJIuHhx3Hg]

## Initial Power Platform environment

By default, all finance and operations apps environments (sandbox and production) that are managed by Lifecycle Services receives an initial Power Platform environment **without** Dataverse. This environment is linked to your finance and operations environment, as shown in the following illustration. The relationship is one to one. Over time, your finance and operations apps is migrated to this location in Power Platform admin center. You can determine whether an environment in Power Platform admin center is linked to an environment from Lifecycle Services by looking at the finance and operations apps URL on the environment details page in Power Platform admin center.

![A Power Platform environment in Power Platform admin center is created with the same name as the finance and operations environment from Lifecycle Services. The finance and operations URL is populated with the URL of the finance and operations instance.](media/LinkedPowerPlatformEnvironment.png)

The Power Platform environment that's connected to your environment in Lifecycle Services enables finance and operations apps customers to take advantage of Microsoft Power Platform. This Power Platform environment can't be deleted or reset, and a Dataverse database can't be manually added to it in Power Platform admin center. To add Dataverse and fully enable Microsoft Power Platform integration capabilities, follow the instructions in [Connect finance and operations apps with a new Microsoft Dataverse instance](./environment-lifecycle-connect-finops-new-dv.md).

Alternatively, your organization might already have a Power Platform environment with Dataverse that you want to connect to your finance and operations environment. To reuse an existing Dataverse instance, follow the instructions in [Connect finance and operations apps with an existing Microsoft Dataverse instance](./environment-lifecycle-connect-finops-existing-dv.md). In this case, the initial Power Platform environment that was created when your finance and operations environment was created is disconnected and no longer shows the finance and operations apps URL. At that point, the initial environment can be deleted or used for another purpose.

## Licensing and capacity considerations

When you purchase a license for any finance and operations app, such as Dynamics 365 Finance or Dynamics 365 Supply Chain Management, your tenant is entitled to an additional 10 gigabytes (GB) of Dataverse database capacity. In addition, for each user license that you purchased, you receive an incremental amount of database capacity, as shown in the following illustration from Power Portal admin center.

![Capacity view in Power Platform admin center.](media/PPI-Capacity.png)

The same purchase of licenses entitles you to one self-service sandbox environment and production environment in Lifecycle Services. Because of this, an initial Power Platform environment can automatically be created for every finance and operations apps environment. Every initial environment in Power Platform admin center is without Dataverse. Therefore, it uses only 1 GB of database capacity to provision apps that are created by using Power Apps and flows that are created by using Power Automate. When you set up Power Platform integration, a Dataverse database is added to the same environment. This database often consumes 3 GB or more.

Add-on sandbox environments that customers purchase to use in Lifecycle Services don't entitle them to more Dataverse database capacity. Customers who require Power Platform integration capabilities should purchase add-on Dataverse database storage. For more information about how to manage capacity in Power Platform admin center, see [Free up storage space](/power-platform/admin/free-storage-space).

## Scenarios and core concepts

To learn the core concepts of Power Platform Integration and view a detailed list of supported scenarios, see [Environment lifecycle operations - Core concepts](./environment-lifecycle-core-concepts.md).

## Power Platform connection isn't reversible

Connecting, or linking as it's also referred, a finance and operations apps environment to a Microsoft Dataverse instance isn't reversible. The integration between the two systems is done via the infrastructure and disconnecting them would result in data loss. If you wish to delete the Microsoft Dataverse instance, follow this guide: [Delete environments when Power Platform Integration is enabled](./environment-lifecycle-delete-env.md).

## Troubleshooting the setup

Setup can fail at various stages of the deployment of the Dataverse-based environment.

Anytime that the setup fails, an error message is shown. The following illustration shows an example of the error message for a dual-write setup failure.

![Error message for a dual-write setup failure.](media/Error.png)

Based on the error message, you might have to address licensing or capacity issues. After these issues are fixed, you can select **Resume** in the **Power Platform integration** section of the **Environment details** page in Lifecycle Services to finish the setup.

## Enable the integration for cloud-hosted development environments

> [!NOTE]
> Power Platform integration for cloud-hosted development environments is a deprecated feature and is no longer supported. While the option may still appear during environment deployment, it's not recommended for use. 
> For testing and development scenarios, we recommend using a Sandbox environment and/or a Unified Developer Environment (UDE), which are fully supported and better suited for integration with Power Platform.
> For more information about UDE, see [Unified developer experience for finance and operations apps](/power-platform/developer/unified-experience/finance-operations-dev-overview).

## Verify Power Platform integration status at runtime

The `RetrieveFinanceAndOperationsIntegrationDetails` API is available in Dataverse to validate the status of the Power Platform integration for the Power Platform environment. If the Power Platform environment is linked to a finance and operations apps environment through the Power Platform integration, the API returns the Microsoft Entra tenant and environment details of the finance and operations apps environment.


The API can be used during troubleshooting to verify that the Power Platform integration is enabled for an environment. We recommend that you also use the API when you code plug-ins, client forms, or other applications that must be aware of the finance and operations apps environment that's linked to the Power Platform environment.

**Request**
```http
GET [Organization URI]/api/data/v9.1/RetrieveFinanceAndOperationsIntegrationDetails
```

**Response**
```json
{
    "Url": "https://contoso.operations.dynamics.com",
    "TenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
    "Id": "b2106f5c-e218-4aac-841a-a59da4738eb4"
}
```

**Properties**

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| Environment URL<br>**Url**<br>***String*** | Read-only<br>Required | The URL of the finance and operations apps environment linked to the Power Platform environment through the Power Platform integration. |
| Tenant ID<br>**TenantId**<br>***GUID*** | Read-only<br>Required | The ID of the Microsoft Entra tenant on which both the finance and operations apps environment and Power Platform environment are located. |
| Environment ID<br>**Id**<br>***GUID*** | Read-only<br>Required | The ID of the finance and operations apps environment linked to the Power Platform environment through the Power Platform integration. |

If the environment isn't linked to a finance and operations apps environment through the Power Platform integration, the following error is returned in the API response:

| Error code | Message |
| --- | --- |
| 0x80048d0b | Dataverse instance isn't integrated with finance and operations. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
