---
title: Commerce Data Exchange troubleshooting
description: This article provides information that helps you troubleshoot CDX in implementations.
author: aneesa
ms.date: 02/12/2026
ms.topic: troubleshooting-general
ms.search.form: RetailTerminalTable, RetailDevice
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: aneesa
ms.search.validFrom: 2020-08-31
ms.custom:  
  - bap-templates
  - firopc-nochange
---

# Commerce Data Exchange troubleshooting

[!include[banner](../includes/banner.md)]

This article is for IT professionals who implement functionality related to data synchronization (Commerce Data Exchange \[CDX\]) in a Microsoft Dynamics 365 Commerce environment. It provides information to help you troubleshoot CDX in implementations.

Data configuration and synchronization are crucial to correct implementation. Regardless of business requirements, IT infrastructure, and overall preparedness, if data isn't correctly synced, the whole environment is effectively useless. Therefore, it's crucial that you understand the process of troubleshooting any issue related to data synchronization, from Commerce headquarters, through the Commerce Scale Unit, to the brick-and-mortar stores that use the Store Commerce app (either with or without an offline database) and other in-store components. This article provides some general guidance about how to mitigate or fix some issues. It also provides information about the best time to create a support request and the most important data to provide if you want to speed up a support request.

Before you go through this article, it's important that you understand the concepts of a channel (store), registers and devices, and the Store Commerce app offline database. Therefore, review some of the resources at the end of this article, such as the CDX implementation guide and the overview of the Commerce architecture.

## Diagnose scenario-based usage problems

In the following known scenarios, some configurations in Commerce headquarters might cause out-of-box CDX functionality not to achieve expected, successful results. This list is updated as more scenarios become known.

- When the [Extensible Data Security (XDS) policies](../../fin-ops-core/dev-itpro/sysadmin/extensible-data-security-policies.md) feature is enabled, CDX might not work correctly. Specifically, users might not be able to see all the Commerce channels in Commerce headquarters. In this scenario, if a user runs a CDX job, it generates only partial data (the data that this user is able to see). Therefore, the channel database data is incomplete, and an error likely occurs.
- The **RetailServiceAccount** user is altered, or XDS policies are assigned to it. The **RetailServiceAccount** user is an important, pregenerated account that's used for various reasons and purposes. Microsoft highly recommends that you don't alter this account in any way. If you're using XDS policies, don't assign any policy to the account that reduces the data that the account can see or access.
- CDX jobs fail with timeout errors when they generate upload packages. This issue most often occurs when custom-created transactional tables are missing an index on the **ReplicationCounterFromOrigin** column in these generated tables.

## Troubleshoot CDX errors

To troubleshoot errors, see [Troubleshoot Commerce Data Exchange (CDX)](/troubleshoot/dynamics-365/commerce/data-synchronization/commerce-data-exchange).

## Additional resources

[Commerce Data Exchange best practices](CDX-Best-Practices.md)

[Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)

[Commerce offline implementation and troubleshooting](implementation-considerations-offline.md)

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Select an in-store topology](retail-in-store-topology.md)

[Device management implementation guidance](../implementation-considerations-devices.md)

[Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)

[Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
