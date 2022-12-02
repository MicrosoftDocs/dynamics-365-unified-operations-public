---
title: Use Customer Lockbox to manage secure access to customer data
description: This article explains how to set up Customer Lockbox and how access requests are initiated, tracked, and stored for later reviews and audits.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/02/2022
ms.custom: bap-template
---

# Use Customer Lockbox to manage secure access to customer data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Most operations, support, and troubleshooting performed by Microsoft personnel (including subprocessors) don't require access to customer data. However, in those rare situations where this access is required, Power Platform Customer Lockbox lets you review and approve (or reject) data access requests. Use it when a Microsoft engineer needs to access customer data, whether in response to a customer-initiated support ticket or a problem identified by Microsoft.

This article explains how to set up Customer Lockbox and how access requests are initiated, tracked, and stored for later reviews and audits.

> [!IMPORTANT]
>
> - Customer Lockbox is provided through Microsoft Power Platform. It applies to environments running one or more finance and operations apps that are integrated with Power Platform, including all environment specific resources (SQL DBs and Storage Account). (See also: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).)
> - The preview version of Customer Lockbox is available at no cost. When Customer Lockbox becomes generally available, there will be a cost associated with environments where it is enabled.
> - Preview features aren’t meant for production use and may have restricted functionality. These features are available before an official release so that Microsoft customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and might not be available yet in your region.

## Summary

You can enable Customer Lockbox as required for the data sources on your tenant. For the duration of the preview, Customer Lockbox will apply to all environments on the respective tenant. Global administrators and Power Platform administrators can enable the Customer Lockbox policy. Once enabled, you'll also be able to use Customer Lockbox for the finance and operations apps running on your tenant.

To enable Customer Lockbox for your finance and operations apps environment, follow these steps:

1. [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).
1. [Enable Customer Lockbox on the Power Platform](/power-platform/admin/about-lockbox).

For more information about how to use Customer Lockbox, see [Securely access customer data using Customer Lockbox in Power Platform](/power-platform/admin/about-lockbox).

### Customer Lockbox support for add-ins

Microsoft Lifecycle Services (LCS) may provide several add-ins for finance and operations apps environments that are integrated with Power Platform. Some add-ins provide only partial support, or no support, for Customer Lockbox. The following table specifies which limitations apply to which add-ins (add-in not listed do support Customer Lockbox).

| Add in | Status |
|---|---|
| Tax calculation | .???. |
| Electronic invoicing | .???. |
| All other add-ins | Support Customer Lockbox |

### Customer Lockbox support across finance and operations apps

Not all finance and operations apps fully support Customer Lockbox in the current preview. The following table specifies the Customer Lockbox support status of each application.

| Application | Status |
|---|---|
| Dynamics 365 Supply Chain Management | Supports Customer Lockbox for all environment-specific resources.|
| Dynamics 365 Human Resources | .???. |
| Dynamics 365 Finance | Supports Customer Lockbox for all environment-specific resources.<br/><br/>.???.<br/><br/>Dynamics 365 Finance environments running the [Regular Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) aren't currently supported by Customer Lockbox. Support for RCS is planned for late 2023.|
|  |  |
