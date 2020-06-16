---
# required metadata

title: Guidance for workers in production
description: Guidance helps workers in their their tasks across assembly, service, quality assurance and cover as well safety and certification related procedures. 
author: cabeln
manager: sorenand
ms.date: 16/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WorkGuidesManufacturing
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 61943
ms.assetid: a3847f07-fca4-4140-a26f-d83c6ac68dde
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: cabeln
ms.search.validFrom: 2020-08-01
ms.dyn365.ops.version: AX 10.0.13

---
(In preview for release version 10.0.13)

# Guidance for workers in production

Workers in production processes will greatly profit from relevant guidance which must be provided in the context of their work and at the right time.
There are several domains of work where guidance is applicable: Assembly, service, operations, certification, and safety.

Across all of these core business functions, new employees, new equipment, new process and ongoing training guidance will empower workers to achieve more and work better.

## Introduction to Guidance

You can provide guidance in different ways. One very efficient system that ships out of the box uses [Dynamics 365 Guides](https://dynamics.microsoft.com/en-us/mixed-reality/guides/).

With [Dynamics 365 Guides](https://dynamics.microsoft.com/en-us/mixed-reality/guides/) you empower your employees with hands-on learning. You can define standardize processes with step-by-step instructions that guide your employees to the tools and parts they need and how to use them in real work situations. Below are listed a few domains where customer across industries see the biggest value for guidance.

The Dynamics 365 SCM SDK can be used to implement other means of guidance. Please find information on [the data model for guidance here](guidance-datamodel.md).

### Assembly

[![Assembly](./media/work-guides-hero-assembly.png)](./media/work-guides-hero-assembly.png)

Guidance in assembly operations shows workers the tools and parts they need and how to use them in real work situations.

As a production manager you will create and assign guidance for example for [production routes](routes-operations.md), [operation relations](routes-operations.md#operation-relations), or [bill of materials](bill-of-material-bom.md). Workers will find the relevant guidance on the respective operation experience on the shop floor. 

### Service

[![Assembly](./media/work-guides-hero-service.png)](./media/work-guides-hero-service.png)

You can equip technicians with guided instructions at the job site, eliminating the need to schedule additional visits.

As a service manager you can assign guides for example to [products](../../commerce/product.md) that walk through routines of quality assessment.

### Quality

[![Assembly](./media/work-guides-hero-quality.png)](./media/work-guides-hero-quality.png)

Rollout new processes and ensure increased consistency by turning employee knowledge into a repeatable tool.

As a quality assurance manager you can assign guides for example to [products](../../commerce/product.md) that walk through routines of quality assessment.

### Certifications

[![Assembly](./media/work-guides-hero-certification.png)](./media/work-guides-hero-certification.png)

Ensure every employee meets high standards by quickly identifying who needs help where.

### Safety

[![Assembly](./media/work-guides-hero-safety.png)](./media/work-guides-hero-safety.png)

Provide guidance that walks through dangerous procedures virtually before attempting in the physical environment. With a mixed reality approach workers can experience dangerous procedures virtually.

As a production manager you can provide dedicated guidance for hazardous material handling or delicate handling procedures by assigning guidance to [product items](../../commerce/product.md), [routes](routes-operations.md) and [operations](routes-operations.md#operation-relations) while tagging your guidance with a dedicated safety instruction [category](guidance-howto-use-categories.md) which you can create yourself as needed.

## Get started with guidance

To enable guidance in production processes you Dynamics 365 SCM provides an out of the box integration with [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/). A license and installed application instance of Guides is required in order to build, maintain and assign respective mixed reality guidance to production assets and work.
 
This integration is switched off by default and the admin of the F&O organization must enable it once in the License Configuration.  

### Prerequisite steps

Before you can attach guides to Asset management work orders, you must complete these prerequisites:

- [Set up Dynamics 365 Supply Chain Management](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/) version 10.0.13 or later.

- [Turn on dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/enable-dual-write) for Supply Chain Management apps.

- [Turn on flight](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages#features-flighted-in-data-management-and-enabling-flighted-features) for the MRGuidesFeature feature. (For production environments, you must first submit a support ticket to have your tenant added to the flighting group.)

- [Turn on the following configuration keys](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/license-code-and-configuration-key-reference) on the License configuration page:

  - Mixed reality > Mixed reality guide
  - Production management > Production guidance
  - [Set up Dynamics 365 Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup#step-2-create-a-common-data-service-environment-and-install-the-dynamics-365-guides-solution) version 400.0.1.48 or later.

### Use Dynamics 365 Guides

### Managing guidance within Dynamics 365 SCM

### Guidance in the shop floor experience
