---
title: Use Customer Managed Keys to manage secure access to customer data
description: This article explains how to set up Customer managed KeysLockbox and how access requests are initiated, tracked, and stored for later reviews and audits.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/02/2022
ms.custom: bap-template
---

# Manage your encryption keys for data at rest

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Microsoft services adhere data privacy and compliance requirements when securing customer data by encrypting data at-rest. This secures the data from being exposed in an event where a copy of the database is stolen. With data encryption at-rest, the stolen database data is protected from being restored to a different server without the encryption key.

By default, data is encrypted with Microsoft managed keys. For additional control over encryption keys, you can manage your own keys. Customer Managed Keys (CMK) must be stored in Azure Key vault.

This article explains how to set up Customer Managed Keys for Finance and Operations environments.

> [!IMPORTANT]
>
> - Customer Managed Keys is provided through Microsoft Power Platform. It applies to environments running one or more finance and operations apps that are integrated with Power Platform, including all environment specific resources (SQL DBs and Storage Account). (See also: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).)
> - The preview version of Customer Managed Keys is available at no cost. When Customer Managed Keys becomes generally available, there will be a cost associated with environments where it is enabled.
> - Preview features aren’t meant for production use and may have restricted functionality. These features are available before an official release so that Microsoft customers can get early access and provide feedback.
> - This feature is being gradually rolled out across regions and might not be available yet in your region.

## Summary

You can enable Customer Managed Keys (CMK) policy enforcement for Finance and Operations environments where Power Platform Integration is enabled ([Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md)). Finance & Operations environments without Power Platform integration will continue to use the Microsoft Managed key to encrypt its data.

Once enabled the CMK policy will be  will be enabled for environment specific resources (SQL DBs and Storage Account). See table below for details and exceptions across services.

## How to enable CMK for Finance and Operations environments:

1. Login to your LCS project and select the environment details page for the environment where you wish to enable CMK.
1. If you have not setup Power Platform Integration then first please setup that using the instructions: [Enable the Microsoft Power Platform integration](../../dev-itpro/power-platform/enable-power-platform-integration.md). Please note, if you setup integration with existing power platform environment, it should not have CMK enabled on it before integration. (Support for this scenario will be enabled in future).
1. Once you have Power Platform integration setup, in the Power Platform Environment Information on the LCS environment details page, you will see Environment Name. This is the name of your Dataverse Organization. (Please note that name of your Finance and Operations environment might be different than your power platform integration environment, you will need the later for enabling CMK).
1. Go to Power platform admin portal and lookup your Power platform integration environment name.

> [!IMPORTANT]
>
> Follow the instructions from Private Preview July 2022 document to enable CMK on your power platform environment.

### CMK support in Finance and Operation Environment Add-Ins

A number of Add-Ins may be available in LCS for each Finance and Operations environment once the Power Platform integration has been enabled. Add-Ins that have some limitations for CMK are mentioned in the following table (if an Add-In is not in this list, then it supports the CMK policies).

|Add In  |Status  |
|--------|--------|
|Tax Calculation|Tax Calculation uses [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) which doesn’t support CMK policy enforcement as of now, support for this will be enabled in late 2023.|
|Electronic Invoicing|Electronic Invoicing uses [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) which doesn’t support CMK policy enforcement as of now, support for this will be enabled in late 2023.|
|||

### CMK support across Finance and Operations Offers / Applications

Not all applications among Finance and Operations support CMK policies in the preview to the full extent yet. Find more details for individual applications below:

|Offer|Application Status|
|-----|------------------|
|Dynamics 365 Supply Chain Management|Finance and Operations environment provisioned under Dynamics 365 Supply Chain Management offering supports CMK policy enforcement for all environment specific resources.|
|Dynamics 365 Human Resources|Dynamics 365 Human Resources provisioned via Finance and Operations environment will support CMK policy enforcement for all environment specific resources.<br/><br/>Dynamics 365 Human Resources Standalone offering is not CMK compliant; these customers will have to use migration tooling to migrate their environments to Finance and Operations environment and then they can use the CMK policy enforcement.|
|Dynamics 365 Finance|Finance and Operations environment provisioned under Dynamics 365 Finance offering supports CMK policy enforcement for all environment specific resources.<br/><br/>If you use [Regulatory Configuration Service (RCS)](../../../finance/localizations/rcs-overview.md) to compliment your Dynamics 365 Finance environment then please note that data managed under RCS environment, currently doesn’t support CMK policy enforcement. CMK support for RCS will be enabled in late 2023.|
| Microsoft Dynamics 365 Lifecycle Services (LCS) | Any data you store in LCS (such as file assets, methodologies, task recorder data, and any other project metadata) will not be encrypted using Customer Managed Keys.<br/><br/>Customer Managed Key support for LCS metadata is expected to be announced sometime in the future.|
