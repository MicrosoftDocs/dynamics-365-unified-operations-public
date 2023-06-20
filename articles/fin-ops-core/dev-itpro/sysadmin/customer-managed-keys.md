---
title: Use customer-managed keys to control encryption keys for data at rest
description: This article explains how to set up customer-managed keys for finance and operations environments to control encryption keys for data at rest.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/01/2023
ms.custom: bap-template
---

# Use customer-managed keys to control encryption keys for data at rest

[!include [banner](../includes/banner.md)]

Microsoft services adhere to data privacy and compliance requirements when they secure customer data by encrypting data at rest. This practice secures the data from being exposed if a copy of the database is stolen. When data encryption at rest is used, any stolen database data is protected from being restored to a different server without the encryption key.

By default, data is encrypted by using *Microsoft-managed keys*. However, if you want more control over your encryption keys, you can manage your own keys by using *customer-managed keys* (CMKs) instead. CMKs must be stored in Microsoft Azure Key Vault.

This article explains how to set up CMKs to control encryption keys for data at rest in finance and operations environments.

> [!IMPORTANT]
>
> - The CMK feature is provided through Microsoft Power Platform. It applies to environments that run one or more finance and operations apps that are integrated with Microsoft Power Platform. It also applies to all environment-specific resources, including SQL databases and Azure storage accounts. (For more information, see [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).)
> - This feature is being gradually rolled out across regions and might not yet be available in your region.
> - CMK policy enforcement doesn't include cloud-hosted environments because these environments are deployed in customer-managed subscriptions. For more information on best practices for securing cloud-hosted environment, see [Secure one-box development environments](../../dev-itpro/dev-tools/secure-developer-vm.md).
> - Refer to [Licensing requirements for customer managed key](/power-platform/admin/customer-managed-key#licensing-requirements-for-customer-managed-key).

## Enable CMKs

You can enable enforcement of the CMK policy for finance and operations environments where [Microsoft Power Platform integration is enabled](../../dev-itpro/power-platform/enable-power-platform-integration.md)). Finance and operations environments without Microsoft Power Platform integration will continue to use Microsoft-managed keys to encrypt their data.

After the CMK policy is enabled, it also applies to environment-specific resources, including SQL databases and Azure storage accounts. For details and exceptions across services, see the [CMK support across finance and operations apps](#cmk-support-across-finance-and-operations-apps) section later in this article.

To enable customer-managed keys for your finance and operations apps environment, follow these steps:

1. [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).

    > [!NOTE]
    > If you set up integration with an existing Power Platform environment, CMKs shouldn't be enabled in that environment before integration. (Support for that scenario will be enabled in future.)

1. After Microsoft Power Platform integration is enabled, the environment name will be shown in the Power Platform environment information on the environment details page in Microsoft Dynamics Lifecycle Services. This name is also the name of your Dataverse organization. Make a note of the environment name, because you'll need it for the next steps.

    > [!NOTE]
    > The name of your finance and operations environment might differ.

1. [Enable CMKs in Microsoft Power Platform, and create an enterprise policy](/power-platform/admin/customer-managed-key).
1. [Add the environment that has the previously noted name to the enterprise policy](/power-platform/admin/customer-managed-key#add-an-environment-to-the-enterprise-policy-to-encrypt-data).

## CMK support for add-ins

Lifecycle Services might provide several add-ins for finance and operations environments that are integrated with Microsoft Power Platform. However, some add-ins provide only partial support, or no support, for CMKs. The following table describes the limitations that apply to various add-ins.

| Add In | Status |
| --- | --- |
| Tax Calculation | Deployments of the Tax Calculation add-in that use the stand-alone [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) don't support CMKs for the encryption of related resources. Support for CMKs is expected in late 2023, when RCS functionality is added to the finance and operations platform. |
| Electronic Invoicing | Deployments of the Electronic Invoicing add-in that use stand-alone [RCS](../../../finance/localizations/rcs-overview.md) don't support CMKs for the encryption of related resources. Support for CMKs is expected in late 2023, when RCS functionality is added to the finance and operations platform. |
| All other add-ins | All other add-ins support CMK policies. |

## CMK support across finance and operations apps

Not all finance and operations apps support CMK policies. The following table describes the CMK support status of each app.

| App | Status |
| --- | --- |
| Dynamics 365 Supply Chain Management | Finance and operations environments that are provisioned under Dynamics 365 Supply Chain Management support CMKs for the encryption of all environment-specific resources at rest. |
| Dynamics 365 Human Resources | <p>Dynamics 365 Human Resources installations that are provisioned via a finance and operations environment support CMKs for all environment-specific resources.</p><p>The Human Resources stand-alone app doesn't support CMKs. To enable the use of CMKs, you must first use migration tooling to migrate your stand-alone Human Resources environment to a finance and operations environment.</p> |
| Dynamics 365 Finance | <p>Finance and operations environments that are provisioned under Dynamics 365 Finance support CMKs for all environment-specific resources.</p><p>**Note:** If you use [RCS](../../../finance/localizations/rcs-overview.md) to complement your Dynamics 365 Finance environment, data that's managed under RCS environments doesn't currently support CMKs. Support for CMKs is expected in late 2023, when RCS functionality becomes available for finance and operations apps.</p> |
| Dynamics 365 Commerce | <p>Dynamics 365 Commerce environments support CMKs for all environment-specific resources except the content management system in e-commerce and recommendations. CMK support for the content management system in e-commerce and recommendations is expected to be enabled in the future.</p>|
| Microsoft Dynamics Lifecycle Services | <p>Data that you store in Lifecycle Services (such as file assets, methodologies, task recorder data, and any other project metadata) won't be encrypted by using CMKs.</p><p>CMK support for Lifecycle Services metadata is expected sometime in the future.</p> |
