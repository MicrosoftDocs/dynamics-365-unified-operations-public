---
title: Use Customer Lockbox to manage secure access to customer data
description: This article explains how to set up Customer Lockbox, and how access requests are initiated, tracked, and stored for later reviews and audits.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/17/2023
audience: IT Pro
ms.search.region: Global
ms.custom: bap-template
---

# Use Customer Lockbox to manage secure access to customer data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Most operations, support, and troubleshooting that Microsoft personnel (including subprocessors) perform don't require access to your data. However, in those rare situations where this access is required, Microsoft Power Platform Customer Lockbox lets you review and approve (or reject) data access requests. Use it when a Microsoft engineer must access your data in response to either a support ticket that you've raised or a problem that Microsoft has identified.

This article explains how to set up Customer Lockbox, and how access requests are initiated, tracked, and stored for later reviews and audits.

> [!IMPORTANT]
>
> - Customer Lockbox is provided through Microsoft Power Platform. It applies to environments that run one or more finance and operations apps that are integrated with Microsoft Power Platform, including all environment-specific resources (SQL databases and storage accounts). For more information, see [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).
> - The preview version of Customer Lockbox is available at no cost. When Customer Lockbox becomes generally available, a cost will be associated with environments where it's enabled.
> - Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that Microsoft customers can get early access and provide feedback.
> - This feature is gradually being rolled out across regions and might not yet be available in your region.
> - Customer Lockbox policy enforcement doesn't include cloud-hosted environments because these environments are deployed in customer-managed subscriptions. For more information on best practices for securing cloud-hosted environment, see [Secure one-box development environments](../../dev-itpro/dev-tools/secure-developer-vm.md).

## Enable Customer Lockbox

You can enable Customer Lockbox as required for the data sources on your tenant. For the duration of the preview, Customer Lockbox will apply to all environments on the tenant. Global administrators and Microsoft Power Platform administrators can enable the Customer Lockbox policy. After it's enabled, you'll also be able to use Customer Lockbox for other finance and operations apps that run on your tenant.

To enable Customer Lockbox for your finance and operations apps environment, follow these steps.

1. [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).
1. [Enable Customer Lockbox on Microsoft Power Platform](/power-platform/admin/about-lockbox).

For more information about how to use Customer Lockbox, see [Securely access customer data using Customer Lockbox in Power Platform](/power-platform/admin/about-lockbox).

## Customer Lockbox support for add-ins

Microsoft Dynamics Lifecycle Services might provide several add-ins for finance and operations apps environments that are integrated with Microsoft Power Platform. Some add-ins provide only partial support, or no support, for Customer Lockbox. The following table describes the limitations that apply to different add-ins.

| Add-in | Status |
|---|---|
| Tax Calculation | Deployments of the Tax Calculation add-in that use stand-alone [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) don't support Customer Lockbox for related resources. Support for Customer Lockbox will be enabled in late 2023 when RCS functionality is added to the finance and operations platform. |
| Electronic Invoicing | Deployments of the Electronic Invoicing add-in that use stand-alone [RCS](../../../finance/localizations/rcs-overview.md) don't support Customer Lockbox for related resources. Support for Customer Lockbox will be enabled in late 2023 when RCS functionality is added to the finance and operations platform. |
| All other add-ins | All other add-ins support Customer Lockbox. |

## Customer Lockbox support across finance and operations apps

Not all finance and operations apps fully support Customer Lockbox in the current preview. The following table describes the Customer Lockbox support status of each app.

| App | Status |
|---|---|
| Dynamics 365 Supply Chain Management | Finance and operations environments that are provisioned under Dynamics 365 Supply Chain Management support Customer Lockbox for all environment-specific resources. |
| Dynamics 365 Human Resources | <p>Dynamics 365 Human Resources installations that are provisioned via a finance and operations environment support Customer Lockbox for all environment-specific resources.</p><p>The Human Resources stand-alone app doesn't support Customer Lockbox. To enable Customer Lockbox, you must first use migration tooling to migrate your stand-alone Human Resources environment to a finance and operations environment.</p> |
| Dynamics 365 Finance | <p>Finance and operations environments that are provisioned under Dynamics 365 Finance support Customer Lockbox for all environment-specific resources.</p><p>**Note:** If you use [RCS](../../../finance/localizations/rcs-overview.md) to complement your Finance environment, data that's managed under RCS environments doesn't currently support Customer Lockbox. Support for Customer Lockbox is expected in late 2023, when RCS functionality is added to the finance and operations platform.</p> |
| Dynamics 365 Commerce | <p>Dynamics 365 Commerce environments support Customer Lockbox for all environment-specific resources except the content management system in e-commerce. Customer Lockbox support for the content management system in e-commerce is expected to be enabled in the future.</p>|
| Microsoft Dynamics Lifecycle Services | <p>Data that you store in Lifecycle Services (such as file assets, methodologies, task recorder data, and any other project metadata) isn't part of the Customer Lockbox policy enforcement.</p><p>Customer Lockbox support for Lifecycle Services metadata is expected sometime in the future.</p> |
