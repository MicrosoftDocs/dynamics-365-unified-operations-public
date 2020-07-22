---
# required metadata

title: Instructions for workers in production using Dynamics 365 Guides
description: This topic explains how to integrate the production management module in Microsoft Dynamics 365 Supply Chain Management with Dynamics 365 Guides to take advantage of mixed-reality guides to help production  workers in their their tasks across assembly, quality assurance, safety and certification related procedures.
 
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

# Instructions with Dynamics 365 Guides for workers in production

Workers in production processes will greatly profit from relevant instructions which must be provided in the context of their work and at the right time.
There are several domains of work where instructions are applicable: Assembly, service, operations, certification, and safety.

Across all of these core business functions, new employees, new equipment, new process and ongoing training instructions will empower workers to achieve more and work better.

## Introduction

You can provide instructions in different ways. One very efficient system that ships out of the box uses [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/).

With [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/) you empower your employees with hands-on learning. You can define standardize processes with step-by-step instructions that guide your employees to the tools and parts they need and how to use them in real work situations.

You can attach guides to various aspects of the production control including:

- Resources
- Resource groups
- Released products
- BOMs and BOM versions
- Formulas and formula versions
- Routes and route versions
- Route operation relations

> [!NOTE]
> You can find additional options to attach Guides in the **Asset Management** domain.
>[Find more information here.](../asset-management/asset-management-guides-integration.md)

When a first-line worker chooses a job on the shop floor through Supply Chain Management, the worker can see associated guides on the job card. When the worker chooses a specific guide a QR renders code on the screen and Guides in HoloLens will then launch the instructions they need to do their work.

Below list a few scenarios  where customer across industries see the biggest value for instructions using guides in manufacturing and related scenarios.

### Assembly

[![Assembly](./media/instruction-guides-hero-assembly.png)](./media/work-guides-hero-assembly.png)

Instructions in assembly operations shows workers the tools and parts they need and how to use them in real work situations.

As a production manager you will create and assign instructions for example for [production routes](routes-operations.md), [operation relations](routes-operations.md#operation-relations), or [bill of materials](bill-of-material-bom.md). Workers will find the relevant instructions on the respective operation experience on the shop floor.

### Service

[![Assembly](./media/instruction-guides-hero-service.png)](./media/work-guides-hero-service.png)

You can equip technicians with guided instructions at the job site, eliminating the need to schedule additional visits.

As a service manager you can assign guides for example to [products](../../commerce/product.md) that walk through routines of quality assessment.

### Quality

[![Use Guides in quality assurance tasks](./media/instruction-guides-hero-quality.png)](./media/work-guides-hero-quality.png)

Rollout new processes and ensure increased consistency by turning employee knowledge into a repeatable tool.

As a quality assurance manager you can assign guides for example to [products](../../commerce/product.md) that walk through routines of quality assessment.

### Certifications

[![Use Guides for certification related tasks](./media/instruction-guides-hero-certification.png)](./media/work-guides-hero-certification.png)

Ensure every employee meets high standards by quickly identifying who needs help where.

### Safety

[![Use Guides in work safety instructions](./media/instruction-guides-hero-safety.png)](./media/work-guides-hero-safety.png)

Provide instructions that walks through dangerous procedures virtually before attempting in the physical environment. With a mixed reality approach workers can experience dangerous procedures virtually.

As a production manager you can provide dedicated handling instructions for hazardous material handling or delicate handling procedures by assigning instructions to [product items](../../commerce/product.md), [routes](routes-operations.md) and [operations](routes-operations.md#operation-relations).

## Get started with instructions

To enable instructions in production processes you Dynamics 365 SCM provides an out of the box integration with [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/). A license and installed application instance of Guides is required in order to build, maintain and assign respective mixed reality instructions to production assets and work.

This integration is switched off by default and the admin of the F&O organization must enable it once in the License Configuration.  

### Prerequisite steps

Before you can attach guides to Asset management work orders, you must complete these prerequisites:

- [Set up Dynamics 365 Supply Chain Management](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/) version 10.0.13 or later.

- [Turn on dual-write](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/enable-dual-write) for Supply Chain Management apps.

- [Turn on flight](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages#features-flighted-in-data-management-and-enabling-flighted-features) for the MRGuidesFeature feature. (For production environments, you must first submit a support ticket to have your tenant added to the flighting group.)

- [Turn on the following configuration keys](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/license-code-and-configuration-key-reference) on the License configuration page:

  - Mixed reality > Mixed reality guide
  - Production management > Production instructions
  - [Set up Dynamics 365 Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup#step-2-create-a-common-data-service-environment-and-install-the-dynamics-365-guides-solution) version 400.0.1.48 or later.

#### Configure how guides appear on the shop floor

Navigate to Mixed Reality / Dynamics 365 Guides / Configure Guides integration. You should see the field Environment URL filled in. This is the address of your Dynamics 365 Guides environment in CDS without the web protocol,like 'https://'. The value is used to compose addresses for your guides and will be encoded into the QR codes.

In the  field QR code size allows you can customize the size in which the QR code will be rendered. We recommend to size the QR code to fill as much of the screen estate of your display. Typically 15 is a good value. 
> [!TIP]
> Too Large QR codes sizes for your display will take a bit longer to render and will be scaled to display size upon display and therefore do not provide a benefit.
>
> With too small QR code sizes may decrease HoloLense may not read the code properly in all environment situations. 

You can use the field QR code error correction level to influence the granularity of the QR code and increase the reliability of the QR code. But the size of the QR code and the error correction level need to be in a good relation.

> [!TIP]
> We recommend to test the settings for your relevant devices that will be used to display QR codes for HoloLens users and choose a settings that provide sufficient readability in your shop floor environment.  

:::image type="content" source="media/instruction-guides-configure-integration.png" alt-text="Configure Guide integration for manufacturing":::

### Use Dynamics 365 Guides

### Managing instructions within Dynamics 365 SCM using Guides

Use the global Guides management form to see the list of all available Guides in your organization and all assignments to your production processes and resources.
Navigate to Mixed reality / Guides / All Guides. In the top list you will see all Guides and you can filter the list of guides. In the list at the bottom you see all assignments and can manage those.

:::image type="content" source="media/instruction-guides-allguides.png" alt-text="Manage Guides":::

You can also assign Guides to the following objects directly to prescribe the instruction that will be automatically attached to the respective production jobs and available on the shop floor.

- [Resource](operations-resources.md)

    You can add  a Guide to a resource so it will be offered in the context of relevant production jobs. On the Recource form navigate to the tab Associated Guides and  click the new button. Use the drop down in the Name column to select one of the guides that is available to you.

    :::image type="content" source="media/instruction-guides-Resource.png" alt-text="Addign a Guide to a production resource.":::

- [Resource Group](tasks/define-discrete-manufacturing-resource-group.md)

    If you use resource groups to manage groups of machines, production lines or work cells and you want to make available relevant guides on this level, you would navigate to the Associated Guides tab on the Resource Group form and add the relevant guides.

- [Release Product](../pim/tasks/create-released-product-single-company)

    Product level Guides are useful to help shop floor workers with instructions relevant to operate or handle a released product or item. Navigate to the Associated Guides tab on the Release product form and add, remove or manage the associated Guides.

- [Formula](bill-of-material-bom.md#formulas-co-products-and-by-products)
- [Formula Version](bill-of-material-bom.md#bom-and-formula-versions)
- [Bill of material](bill-of-material-bom.md)
- [Bill of material  version](bill-of-material-bom.md#bom-and-formula-versions)
- [Route](routes-operations.md)
- [Route Version](routes-operations.md#route-versions)
- [Route Operation Relation](routes-operations.md#operation-relations)

### Instructions in the shop floor experience
