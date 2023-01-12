---
title: Use Customer Managed keys to control encryption keys for data at rest
description: This article explains how to set up Customer Managed Keys for Finance and Operations environments to to control encryption keys for data at rest.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/01/2023
ms.custom: bap-template
---

# Use Customer Managed keys to control encryption keys for data at rest

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Microsoft services adhere data privacy and compliance requirements when securing customer data by encrypting data at-rest. This secures the data from being exposed in an event where a copy of the database is stolen. With data encryption at-rest, the stolen database data is protected from being restored to a different server without the encryption key.

By default, data is encrypted with Microsoft managed keys. For additional control over encryption keys, you can manage your own keys. Customer Managed Keys (CMK) must be stored in Azure Key vault.

This article explains how to set up Customer Managed Keys for Finance and Operations environments to to control encryption keys for data at rest.

> [!IMPORTANT]
>
> - Customer Managed Keys is provided through Microsoft Power Platform. It applies to environments running one or more finance and operations apps that are integrated with Power Platform, including all environment specific resources (SQL DBs and Storage Account). (See also: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).)
> - The preview version of Customer Managed Keys is available at no cost. When Customer Managed Keys becomes generally available, there will be a cost associated with environments where it is enabled.
> - Preview features aren’t meant for production use and may have restricted functionality. These features are available before an official release so that Microsoft customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and might not be available yet in your region.

## Enable Customer Managed Keys

You can enable Customer Managed Keys (CMK) policy enforcement for Finance and Operations environments where Power Platform Integration is enabled ([Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md)). Finance & Operations environments without Power Platform integration will continue to use the Microsoft Managed key to encrypt its data.

Once enabled the CMK policy will be  will be enabled for environment specific resources (SQL DBs and Storage Account). See table below for details and exceptions across services.

To enable Customer Lockbox for your finance and operations apps environment, follow these steps:

1. [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).

    > [!NOTE]
    >
    > If you setup integration with existing power platform environment, it should not have CMK enabled on it before integration. (Support for this scenario will be enabled in future).

1. Once Power Platform integration is enabled, you will see environment name in the Power Platform Environment Information on the LCS environment details page. This is also the name of your Dataverse Organization.

    > [!NOTE]
    >
    > - Please note the environment name for the next steps to enable Customer managed Keys.
    > - The name of your Finance and Operations environment might be different.

1. [Enable Customer Managed Keys in the Power Platform and create an enterprise policy](/power-platform/admin/customer-managed-key). [**Review link**](
<https://review.learn.microsoft.com/en-us/power-platform/admin/customer-managed-key?branch=matp-3069441>)

1. [Add your environment with above name to the enterprise policy.](/power-platform/admin/customer-managed-key#add-an-environment-to-the-enterprise-policy-to-encrypt-data). [**Review link**](
<https://review.learn.microsoft.com/en-us/power-platform/admin/customer-managed-key?branch=matp-3069441#add-an-environment-to-the-enterprise-policy-to-encrypt-data>)

## Customer Managed Keys support for add-ins

Microsoft Dynamics Lifecycle Services might provide several add-ins for finance and operations apps environments that are integrated with Microsoft Power Platform. Some add-ins provide only partial support, or no support, for Customer managed Keys. The following table describes the limitations that apply to different add-ins.

|Add In  |Status  |
|--------|--------|
|Tax Calculation|Deployments of the Tax Calculation add-in that use stand-alone [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) don't support Customer Managed Keys for encryption of related resources. Support for Customer Managed Keys will be enabled in late 2023 when RCS functionality is added to the finance and operations platform.|
|Electronic Invoicing|Deployments of the Electronic Invoicing add-in that use use stand-alone [RCS](../../../finance/localizations/rcs-overview.md) don't support Customer Managed Keys for encryption of related resources. Support for Customer Managed Keys will be enabled in late 2023 when RCS functionality is added to the finance and operations platform.|
|All other add-ins|All other add-ins support Customer Managed Key policies|

## Customer Managed Keys support across finance and operations apps

Not all applications among Finance and Operations support Customer Managed Key policies in the preview. The following table describes the Customer Lockbox support status of each app.

|App  |Status  |
|-----|------------------|
|Dynamics 365 Supply Chain Management|Finance and operations environments that are provisioned under Dynamics 365 Supply Chain Management support Customer Managed Keys for encryption of all environment-specific resources at rest.|
|Dynamics 365 Human Resources|Dynamics 365 Human Resources that's provisioned via a finance and operations environment supports Customer Managed Keys for all environment-specific resources.<br/><br/>The Human Resources stand-alone app doesn't support Customer Managed Keys. To enable us of Customer Managed Keys, you must first use migration tooling to migrate your stand-alone Human Resources environment to a finance and operations environment.|
|Dynamics 365 Finance|Finance and Operations environment provisioned under Dynamics 365 Finance support use of Customer Managed Keys for all environment specific resources.<br/><br/>Note: If you use [RCS](../../../finance/localizations/rcs-overview.md) to compliment your Dynamics 365 Finance environment, that data that's managed under RCS environment doesn’t currently support use of Customer Managed Keys. Support for Customer Managed Keys will be enabled in late 2023 when RCS functionality is added to the finance and operations platform.|
| Microsoft Dynamics 365 Lifecycle Services (LCS) | Any data you store in LCS (such as file assets, methodologies, task recorder data, and any other project metadata) will not be encrypted using Customer Managed Keys.<br/><br/>Customer Managed Key support for LCS metadata is expected to be announced sometime in the future.|
