---
# required metadata

title: Regulatory Configuration Service
description: This topic provides an overview of the capabilities of Regulatory Configuration Service (RCS) and explains how to access the service.
author: JaneA07
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RCS, Regulatory Configuration Services, Localization
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9

---
# Regulatory Configuration Service

[!include [banner](../includes/banner.md)]

Regulatory Configuration Service (RCS) is a standalone designer and lifecycle management service for no-code/low-code globalization functionality. RCS lets globalization stakeholders extend and customize key globalization areas of tax, e-invoicing, regulatory reporting, banking, and business documents without having to involve developers. This no-code/low-code globalization approach makes globalization easier, faster, and more cost effective to create or extend.

RCS provides the following capabilities:

- Support for all functionality that is provided by Electronic reporting (ER).
- A prerequisite to configure new globalization microservices.
- Support for Electronic Invoicing. For more information, see [Electronic Invoicing](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-add-on-dynamics-365-ga).
- Supports for Tax Calculation. For more information, see [Tax service](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/tax-service-preview).
- Support for new globalization feature functionality that simplifies the lifecycle management of multi-component features and provides extra capability to configure actions and set up feature parameters. For more information, see [Regulatory Configuration Service – simplified globalization feature management for globalization services](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/regulatory-configuration-service-simplified-globalization-feature-management-globalization-services).
- Support for centralized publication, storage, and sharing of custom configurations in the Global repository to simplify configuration management without requiring the use of Microsoft Dynamics Lifecycle Services (LCS).

## Access RCS

You can sign up for or sign in to RCS from the [Regulatory Configuration Service page](https://marketing.configure.global.dynamics.com/).

![RCS sign-up/sign-in](media/202103_RCS%20Marketing%20page_updated_1.jpg)

On the **Regulatory Configuration Service** page, review and accept the supplemental terms and conditions for use of the service, and then select one of the following buttons:

- **Sign up** if you're a first-time user of the service, and you're using a business email address to provision your organization a service environment
- **Sign in** if you've previously signed up for the service, and you want to access your organization environment

## Regional availability

RCS is generally available in the following regions:

- United States
- India
- France
- Europe

For a complete list of regions, see [Dynamics 365 and Power Platform: Availability, data location, language, and localization](https://aka.ms/dynamics_365_international_availability_deck).

## RCS default company

Design time functionality used in RCS is shared across all companies and therefore they do not contain company-specific functionality, for this reason we recommend using single company 'DAT' with your RCS environment.

However, there are some scenarios where the user may want to make Electronic Reporting (ER) formats use parameters that are related to a specific legal entity, the default company switcher should be utilized in these instances only. For example, see [Configure ER format to use parameters that are specified per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-configure-format).

## Related RCS documentation

For more information about related components, see the following documentation:

- **RCS:**

    - [Create ER configuration & upload to Global repo](rcs-global-repo-upload.md)
   
- **Global repository:**

    - [Create ER configuration & upload to Global repo](rcs-global-repo-upload.md)
    - [Share configuration in Global repo](rcs-global-repo-share-configuration.md)
    - [Enhanced filtering in Global repo](enhanced-filtering-global-repo.md)
    - [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md)
    - [Discontinuing configurations in Global repo](discontinuing-configurations-rcs-global-repo.md)
    - [Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation](rcs-lcs-repo-dep-faq.md)

- **Globalization feature:**

    - [Regulatory Configuration Service (RCS) - Globalization feature](/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/regulatory-configuration-service-simplified-globalization-feature-management-globalization-services)


## Troubleshooting RCS sign up:

When you sign up for RCS from the service page, you might encounter an issue related to Azure Active Directory (AAD) and receive the following error message:

![RCS sign-up error](media/01_RCSSignUpError.jpg)

The cause of the issue is that the user is blocked from signing up for ad-hoc subscriptions & need to enable this property [`AllowAdHocSubscriptions`] in their tenant. 
- If your IT department manages your organization Azure tenants, you should contact them to report the issue. 
- If you are responsible for managing your Azure tenants you can fix the issues by following the steps in this guidance, see [What is self-service sign-up for Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/enterprise-users/directory-self-service-signup#how-do-i-control-self-service-settings)


