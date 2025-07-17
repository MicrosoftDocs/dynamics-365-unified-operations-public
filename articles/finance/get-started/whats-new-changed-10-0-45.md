---
title: What's new or changed in Dynamics 365 Finance 10.0.45 (September 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.45 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 07/25/2025
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.45 (September 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.45. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Electronic reporting (ER) | In-App PDF conversion for Configurable Business Documents (CBD) | This Electronic Reporting (ER) feature enables in-app PDF conversion of configurable business documents in Word and Excel formats using AOS resources, allowing complete processing within the application and eliminating reliance on external services. | Feature management |
| Electronic reporting (ER) | Suppress forced batch job retries on failure for Electronic Reporting | When the feature enabled, the system deliberately suppresses further batch job retries for failed Electronic Reporting jobs. | Feature management |
| Globalization Studio | Electronic reporting globalization feature JSON import/export | This feature enables the JSON import/export function for Electronic reporting globalization features. It allows users to import new features from JSON files and export their features into JSON files for storage and transfer purposes. | Feature management |
| Electronic reporting (ER) | Validate obsolete elements of Electronic Reporting data sources | Validate obsolete elements of Electronic Reporting data sources during configuration validation so you can adjust the configuration to address that | Default, in Feature management |
| Electronic reporting (ER) | Enhanced access to labels of the ascendent ER data model | This feature enables access to labels of an ascendent ER data model in derived ER format components even when you selected for the derived ER component an ER data model that differs from the one that was used in the base ER component. | Default, in Feature management |
| Electronic reporting (ER) | Enable support of Document Routing Agent running as a service | Enable support of Document Routing Agent running as a service for network printing scenarios of outbound documents. The Document Routing Agent lets you select the mode of execution. The process can run either as a desktop application or as a Windows service. For more information, see [Run the Document Routing Agent as a Windows service](https://learn.microsoft.com/en-gb/dynamics365/fin-ops-core/dev-itpro/analytics/run-document-routing-agent-as-windows-service). | Default, in Feature management |
| Electronic reporting (ER) | Apply the 'Language preference' parameter to the 'File name' expression | Enables ER formats to dynamically compute file names based on the selected language preference, improving localization in outbound file generation. | Default, in Feature management |
| Electronic reporting (ER) | Run ER import of manually uploaded documents in batch | The feature provides the possibility to run the Electronic reporting (ER) framework model mapping for importing manually uploaded documents in batch. | Default, in Feature management |
| Electronic reporting (ER) | Forcing to use for data parsing only cell data types that are defined in an ER format | When you enable this feature, the Electronic reporting (ER) framework uses for data parsing only cell data types that are defined in an ER format. When this feature is disabled, ER tries to recognize cell data types based on values of cells of an inbound file in Excel format. | Default, in Feature management |
| Electronic reporting (ER) | Cache the preferred language of the current user for ER runs | Enable this feature to cache preferred language of the current user for a single run of an Electronic reporting (ER) format to improve execution performance. | Default, in Feature management |
| Electronic reporting (ER) | Accelerate the ER labels storage | This feature introduces a new label storage schema for imported ER configurations to improve performance during editing and execution. Applies to newly added configurations; existing ones require a manual conversion after enabling the feature. | Mandatory, in Feature management |
| Electronic reporting (ER) | Minimize memory consumption by storing datasets at ER reports runtime | Enabling this feature will reduce the size of cached application data by storing the only values of fields that are actually used for report’s generation during an Electronic reporting (ER) format execution. | Mandatory, in Feature management |
| Electronic reporting (ER) | Optimize datasets memory consumption at ER reports runtime | Enabling this feature will reduce the number of cursors for fetching application data by releasing cursors as soon as they become unnecessary, not at the end of the current session of an Electronic reporting (ER) format execution. | Mandatory, in Feature management |
| Globalization Studio | Dataverse repository | This feature enables the Dataverse-based repositories for Electronic reporting configurations and Globalization features. | Mandatory, in Feature management |
| Globalization Studio | Electronic reporting globalization feature Key Vault parameters | This feature enables a new Key vault parameters form which allows you to set up secrets and certificates stored in Microsoft Azure using service application-based authentication in order to connect to it. | Mandatory, in Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|


## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.45.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Extended lookup of ER format configurations allowing to inquire the Global repository | The related functionality is enabled out of the box. | Electronic reporting (ER) |
| Globalization Studio | The related functionality is enabled out of the box. | Globalization Studio |
| E-invoicing service workspace designer | The related functionality is enabled out of the box. | Globalization Studio |
| Utilize application resources to perform CBD documents conversion from Word to PDF format | Disabled in Feature management due to replacement by In-App PDF conversion for Configurable Business Documents (CBD) | Electronic reporting (ER) |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.45 includes platform updates. To learn more, see [Platform updates for version 10.0.45 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle 
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.






This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.
