---
# required metadata

title: Dual-write home page
description: This topic provides links to information about dual-write.
author: robinarh
manager: AnnBe
ms.date: 02/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-01-08
ms.dyn365.ops.version: AX 7.0.0

---

# Dual-write home page

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

These topics describe dual-write integration.

+ [What is dual-write?](dual-write-overview.md)

    - [Top reasons to use dual-write](dual-write-overview.md#top-reasons-to-use-dual-write)
    - [What does dual-write mean for developers and architects of customer engagement app?](dual-write-overview.md#developer-architect)

+ [What's new or changed in dual-write](whats-new-dual-write.md)
+ [Frequently asked questions](dual-write-faq.md)    

## Dual-write setup

+ [System requirements for dual-write](dual-write-system-req.md)
+ [Guidance for how to set up dual-write](connection-setup.md)
+ [Considerations for initial synchronization](initial-sync-guidance.md)
+ [Dual-write setup from Lifecycle Services](lcs-setup.md)
+ Enable dual-write for existing Finance and Operations apps

    + [Enable dual-write for existing Finance and Operations apps](enable-dual-write.md)
    + [System requirements and prerequisites](requirements-and-prerequisites.md)
    + [How to use the dual-write wizard to link your environments](link-your-environment.md)
    + [Enable table map for dual-write](enable-entity-map.md)

+ [Currency data-type migration for dual-write](currrency-decimal-places.md)
+ [Set up the mapping for the sales order status columns](sales-status-map.md)
+ [Filter intercompany orders to avoid synchronizing Orders and OrderLines](filtering-intercompany-orders.md)

## Managing dual-write after setup

+ [Customize table and column mappings](customizing-mappings.md)
+ [Handling multiple table maps](multiple-entity-maps.md)
+ [Edit a legal table after dual-write setup](edit-legal-entity.md)
+ [Error management and alert notifications](errors-and-alerts.md)
+ [Application lifecycle management](app-lifecycle-management.md)

## Mapping concepts between apps

These topics describe mapping between concepts in Finance and Operations applications and concepts in model-driven apps in Microsoft Dynamics 365.

+ [Integrated customer master](customer-mapping.md)
+ [Integrated vendor master](vendor-mapping.md)

    + [Switch between vendor designs](vendor-switch.md)

+ [Customer loyalty cards and reward points](loyalty-mapping.md)
+ [Unified product experience](product-mapping.md)

    + [Integrated sites and warehouses](sites-warehouses-mapping.md)

+ [Company concept in Dataverse](company-data.md)

    + [Initialize company data](bootstrap-company-data.md)

+ [Organization hierarchy awareness](organization-mapping.md)
+ [Access to finance and tax reference data](finance-tax-reference.md)

    + [Integrated ledger](ledger-mapping.md)
    + [Integrated tax master](tax-mapping.md)

+ [Integrate procurement in Supply Chain Management with Field Service](scm-field-service-procurement.md)
+ [Synchronizing on-demand with the Dynamics 365 Supply Chain Management price engine](pricing-engine.md)
+ [Prospect to cash in dual-write](dual-write-prospect-to-cash.md)
+ [In-house assets for servicing](in-house-assets.md)
+ [Integrated worker, job, and position](integrated-hr.md)

## Support

+ [Support for Field Service solutions and Project Service Automation solutions](field-service-project-service-automation.md)

## Troubleshooting

+ [Verify that dual-write is configured in Finance and Operations apps and Dataverse](dual-write-troubleshooting-verify-config.md)
+ [Troubleshoot issues during initial setup](dual-write-troubleshooting-initial-setup.md)
+ [Troubleshoot issues during initial synchronization](dual-write-troubleshooting-initial-sync.md)
+ [Troubleshoot issues with the Dual-write module in Finance and Operations apps](dual-write-troubleshooting-dual-write-module.md)
+ [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md)
+ [Troubleshoot issues related to solution awareness](dual-write-troubleshooting-solution-awareness.md)
+ [Troubleshoot issues related to upgrades of Finance and Operations apps](dual-write-troubleshooting-finops-upgrades.md)
+ [General troubleshooting](dual-write-troubleshooting.md)
