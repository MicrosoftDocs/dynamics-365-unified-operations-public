---
title: What's new or changed in Dynamics 365 Finance and Operations version 8.0 (April 2018)
description: Learn about new or changed features in Dynamics 365 Finance and Operations version 8.0. This version was released in April 2018.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-09-30
ms.dyn365.ops.version: Release 8.0
ms.assetid: b265d51c-52d1-45c5-b578-64c5242c592a
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 Finance and Operations version 8.0 (April 2018)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 8.0 (April 2018). This version was released in April 2018 and has build numbers 8.0.30 and 8.0.35.

To discover the latest updates to our business applications, as well as a host of new capabilities for building your own applications and extensions on top of our platform, download the [Dynamics 365 Spring '18 release plans](/business-applications-release-notes/April18/release-overview). The release plans provide details about the features that are either new or changed in Dynamics 365 Finance and Operations.

### Introducing Dynamics 365 Finance and Operations

Users and developers will see an updated product name, "Microsoft Dynamics 365 Finance and Operations." With version 8.0, Microsoft is further simplifying our Dynamics 365 offerings and increasing ease of selection for our customers and ecosystem. Going forward, Microsoft is no longer offering separate editions (Business edition and Enterprise edition), so the product name for this Dynamics 365 application is Microsoft Dynamics 365 Finance and Operations.

## Business productivity

### Alerts

Client-based alert functionality enables a user to define alert rules based on business events, such as when an invoice is paid or a customer changes an address. For more information about alerts and how to create them, see [Alerts overview](../../fin-ops/get-started/alerts-overview.md).

### Optimization advisor

Uses telemetry to analyze customers' business processes, finds optimization opportunities, uses application data to quantify the opportunities, and then recommends solutions.

### Project timesheet mobile

Employees can create and submit project timesheets. The use of saved favorites and the ability to copy from a previous timesheet facilitates rapid, accurate time entry.

### Edit default project fulfillment hours

Project resource managers can edit the default hours as part of the project booking fulfillment process.

### Reserve project resources past the task end date

Project resource managers can fulfill resources on tasks past the current planned end date for the task.

### Person search report

You can find a person and their personal data in Finance and Operations.

### Data sharing for customer and vendor tables

Data can be shared across customer and vendor tables and many related tables across multiple legal entities.

### One voucher deprecation

The existing functionality for financial journals (general journal, fixed asset journal, vendor payment journal, and so on) lets you enter multiple subledger transactions in the context of a single voucher. This functionality is referred to as "One voucher." The One voucher functionality causes issues during settlement, tax calculation, reconciliation of a subledger to the general ledger, financial reporting, and more. Because of these issues, the One voucher functionality will be made obsolete. However, because there are functional gaps that depend on this functionality, the functionality won't become obsolete all at once. Instead, we will use the following schedule:

- **Spring '18 release** – The functionality will be turned off by default, through a General ledger parameter. However, you can turn the functionality on if your organization has a scenario that falls in the business scenario gaps that are listed in the One voucher documentation.

    - If a customer has a business scenario that doesn't require One voucher, don't turn the functionality on. We won't fix "bugs" in the areas that are identified in the One voucher documentation if this functionality is used.
    - Stop using One voucher for integrations into Microsoft Dynamics 365 Finance and Operations, unless the functionality is required for one of the functional gaps.

- **Fall '18 and later releases** – The functional gaps will be filled. After the functional gaps are filled, the One voucher functionality will be permanently turned off.

See the [One voucher documentation](../../../finance/general-ledger/one-voucher.md) for detailed information about the use and deprecation of this functionality.

## Extensibility and customization

### Customizations through extensions only

Migrating customizations from one release to the next has been simplified by moving away from over-layering to the use of extensions.

### Extensibility requests

Customers can submit a request to Microsoft for extension support to be added to the product for a needed scenario. In this release, this feature is moved to Lifecycle Services (LCS).

### Embedding Microsoft Power Apps in workspaces and forms

Use Microsoft Power Apps to embed data from external sources into Finance and Operations data. For information about how to embed a PowerApp on a Finance and Operations page, see [Embed PowerApps](embed-power-apps.md).

### Custom fields

Organizations can add custom fields to tailor their application to their business requirements, using a no-code extensibility experience. For information about how to add a custom field, see [Create and work with custom fields](../../fin-ops/get-started/user-defined-fields.md).

## Integration 

### Integration with Dataverse

Dynamics 365 Finance and Operations has enabled cross-application business processes between finance and operations and Dynamics 365 for Field Service and between Finance and Operations and Dynamics 365 for Project Service Automation. These scenarios are configured using extensible Data integrator templates and Dataverse to enable the cross-application scenarios.

### Integration with Dynamics 365 for Field Service

Provides data integration to support scenarios where Field Service activities are done outside Finance and Operations, leveraging the data integrator.

### Integration with Dynamics 365 for Project Service Automation

Supports scenarios where project and resource management activities are done outside Finance and Operations, and the project accounting activities are done in Finance and Operations, leveraging the data integrator.

## Improved support experiences

### Telemetry-based KB recommendation

Telemetry from a production environment can be used to identify the application hotfixes that apply to a tenant.

### KB recommendations when entering a support case

LCS provides telemetry-driven KB recommendations.

### Report production outage

Provides a quick and effective channel to escalate issues to Microsoft Support if the services in a production environment are degraded or become unavailable.

## Supply chain management

### Vendor collaboration – RFQ process

Enhancements make it easy to tell who entered a bid (a vendor or a procurement department). For more information, see [Requests for quotation (RFQs)](../../../supply-chain/procurement/request-quotations.md).

### Partial shipment of a load (split load)

Allows single loads or multiple loads to be fully or partially loaded.

### Immediate replenishment of locations

Used during wave execution if allocation fails for a location directive line that has a replenishment template. For more information about immediate replenishment, see [Immediate replenishment](../../../supply-chain/warehousing/immediate-replenishment.md).

### Reason codes added to warehouse counting and adjustment

Users can add a reason code when performing counts and when making an adjustment. For more information about reason codes, see [Reason codes for inventory counting](../../../supply-chain/warehousing/reason-codes-for-counting-journals.md).

### Batch balancing enabled for advanced warehousing processes

The batch balancing process is now available for products that are set up for warehouse management processes (in earlier releases, the batch balancing process was enabled only for products that were not set up for warehouse management processes). This enhancement makes it possible for the user to release ingredients to picking after the batch balancing process has been completed. For more information about batch balancing, see [Batch balancing](../../../supply-chain/production-control/batch-balancing.md).

### Analytical workspaces with embedded Power BI for Cost management

New Analytical workspaces for Cost management are embedded in the Cost administration and Cost Analysis workspaces. The content pack includes measures such as beginning balance, ending balance, net sourcing and net usage. A set of calculated measures, such as inventory turn ratio, days inventory on-hand, and inventory accuracy are also included. The **Cost management** Power BI content is shown in the **Cost administration** and **Cost analysis** workspaces. For more information, see [Cost management Power BI content](../analytics/cost-management-content-pack.md).

## Globalization

### India localization – project and upgrade

Users can manage India Goods and Services Tax (GST) for the Project management and accounting module, and AX 2012 customers can upgrade to Dynamics 365 Finance and Operations.

### Enhanced configurability

New features include import and testing scenarios, and also broader support for configurability without coding.

## Servicing, performance, and deployment

### Improved delivery of platform and financial reporting updates

Platform and financial reporting updates will be continual updates managed by Microsoft rather than optional updates. This change is intended to improve service reliability and availability, and also to ensure that customers have the latest improvements and fixes. Platform and financial reporting updates are backward-compatible. For more information, see [One Version service updates FAQ](one-version.md).

### Upgrade automation

Upgrade automation makes major version upgrades a self-service operation for the customer, using LCS for non-production environments.

### Service hardening

Added service monitoring and alerting for core business processes, and improved form load performance of the most commonly used forms.

### Lifecycle Services sandbox self-service automation and RDP lockdown

Sandbox self-service automation supports data movement, debugging operations, monitoring, and diagnostics without requiring access to the sandbox environments through Remote Desktop. Remote Desktop capabilities for sandbox environments will be deprecated. This means that customers won't be required to use Remote Desktop to access the VM, which improves reliability and security.

## Compliance

### General Data Protection Regulation (GDPR)

Investments address the European privacy law's requirements. Go to the [Trust Center](https://www.microsoft.com/trustcenter/compliance/accessibility) to learn more and find resources to help you comply.

### Accessibility enhancements

Go to the [Trust Center](https://www.microsoft.com/trustcenter/compliance/accessibility) to learn about our industry-leading accessibility standards.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

