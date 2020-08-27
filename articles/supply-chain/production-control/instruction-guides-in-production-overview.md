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
(In private preview for release version 10.0.13)

# Instructions with Dynamics 365 Guides for workers in production

Workers in production processes will greatly profit from relevant instructions which must be provided in the context of their work and at the right time.
There are several domains of work where instructions are applicable: Assembly, service, operations, certification, and safety.

Across all of these core business functions, new employees, new equipment, new process and ongoing training instructions will empower workers to achieve more and work better.

## Introduction

You can provide instructions in different ways. One very efficient system that ships out of the box uses [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/).

With [Dynamics 365 Guides](https://dynamics.microsoft.com/mixed-reality/guides/) you empower your employees with hands-on learning. You can define standardize processes with step-by-step instructions that guide your employees to the tools and parts they need and how to use them in real work situations.

You can attach guides to various aspects of the production control including:

- [Resource groups](#resource-grouptasksdefine-discrete-manufacturing-resource-groupmd)
- [Resources](#resourceoperations-resourcesmd)
- [Released products](#release-productpimtaskscreate-released-product-single-company)
- [BOMs](#bill-of-materialbill-of-material-bommd) and [BOM versions](#bill-of-material-versionbill-of-material-bommdbom-and-formula-versions)
- [Formulas](#formulabill-of-material-bommdformulas-co-products-and-by-products) and [formula versions](#formula-versionbill-of-material-bommdbom-and-formula-versions)
- [Routes](#routeroutes-operationsmd) and [route versions](#route-versionroutes-operationsmdroute-versions)
- [Route operation relations](#route-operation-relationroutes-operationsmdoperation-relations)

> [!NOTE]
> You can use additional options to attach Guides in the **Asset Management** domain.
> [Find more information here.](../asset-management/asset-management-guides-integration.md)

When a first-line worker chooses a job on the shop floor through Supply Chain Management, the worker can see [the resolved guides](#resolving-logic-for-guides) on the job card. When the worker chooses a specific guide a QR renders code on the screen and Guides in HoloLens will then launch the instructions they need to do their work.

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

- [Turn on flight](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages#features-flighted-in-data-management-and-enabling-flighted-features) for the MRGuidesFeature feature. (This is required until public release in Fall 2020. For production environments, you must first submit a support ticket to have your tenant added to the flighting group.)

- [Turn on the following configuration keys](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/license-code-and-configuration-key-reference) on the License configuration page:

  - Mixed reality > Mixed reality guide
  - Production management > Production instructions
  
- [Set up Dynamics 365 Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup#step-2-create-a-common-data-service-environment-and-install-the-dynamics-365-guides-solution) version 400.0.1.48 or later.

### Configure how guides appear on the shop floor

Navigate to Mixed Reality / Dynamics 365 Guides / Configure Guides integration. You should see the field CDS environment subdomain filled in. This field holds the subdomain for the Common Data Service (CDS) environment where you create your Guides. The subdomain is the first part of the CDS URL and is typically named after your organization. For example, if your CDS URL is "contoso.crm4.dynamics.com", you should enter "contoso" here.
The value is used to compose addresses for your guides and will be encoded into the QR codes.

In the  field QR code size allows you can customize the size in which the QR code will be rendered. We recommend to size the QR code to fill as much of the screen estate of your display. Typically 15 is a good value.
> [!TIP]
> Too Large QR codes sizes for your display will take a bit longer to render and will be scaled to display size upon display and therefore do not provide a benefit.
>
> With too small QR code sizes may decrease HoloLens may not read the code properly in all environment situations.

You can use the field QR code error correction level to influence the granularity of the QR code and increase the reliability of the QR code. But the size of the QR code and the error correction level need to be in a good relation.

> [!TIP]
> We recommend to test the settings for your relevant devices that will be used to display QR codes for HoloLens users and choose a settings that provide sufficient readability in your shop floor environment.  

:::image type="content" source="media/instruction-guides-configure-integration.png" alt-text="Configure Guide integration for manufacturing":::

### Managing instructions within Dynamics 365 SCM using Guides

Use the global Guides management form to see the list of all available Guides in your organization and all assignments to your production processes and resources.
Navigate to Mixed reality / Guides / All Guides. In the top list you will see all Guides and you can filter the list of guides. In the list at the bottom you see all assignments and can manage those.

:::image type="content" source="media/instruction-guides-allguides.png" alt-text="Manage Guides":::

You can also assign Guides to the following objects directly to prescribe the instruction that will be automatically attached to the respective production jobs and available on the shop floor.

#### [Resource](operations-resources.md)

You can add  a Guide to a resource so it will be offered in the context of relevant production jobs.

- Typical use case

    For example you could attach a Guide with general machine security or handling instructions to a resource of type machine.
    The Guide will be available on every job that is performed on the machine.
- How to set up

    On the Resource form navigate to the tab Associated Guides and  click the new button.

    :::image type="content" source="media/instruction-guides-Resource.png" alt-text="Adding a Guide to a production resource.":::

    Use the drop down in the Name column to select one of the guides that is available to you. The filter option allows you to better identify Guides.

    :::image type="content" source="media/instruction-guides-Resource-Selector.png" alt-text="Selecting a Guide for a production resource using lookup.":::

#### [Resource Group](tasks/define-discrete-manufacturing-resource-group.md)

If you use resource groups to manage groups of machines, production lines or work cells you can assign relevant guides on this level.

- Typical use cases

    You have defined a resource group for several machines pof the same model. Instead of assigning the relevant handling instruction guide for the machine model to every relevant resource, you would assign the Guide to the resource group that reflect tha machine model.

    You have defined a resource group for a work cell that contains different machines and you have a Guide prepared for general instructions to maintenance of the work cell which applies to any production activity in this work cell.

- How to set up

    Navigate to the Associated Guides tab on the Resource Group form and add the relevant guides using the+Add button and the Guide lookup.

    :::image type="content" source="media/instruction-guides-ResourceGroup.png" alt-text="Adding a Guide to a  resource group.":::

##### [Release Product](../pim/tasks/create-released-product-single-company)

- Typical use cases
  
    Product level Guides are useful to help shop floor workers with instructions relevant to operate or handle a released product or item.

- How to set up

    On the Release product form select the Engineer tab in the action bar and select Assiated Guides in the View action tab.

    :::image type="content" source="media/instruction-guides-releasedProduct.png" alt-text="Associated Guides on a released product.":::

    Use the Associated Guides view to add, remove or manage the associated Guides.
  
    :::image type="content" source="media/instruction-guides-releasedProduct-AddGuides.png" alt-text="Adding Guides to a released product.":::

##### [Formula](bill-of-material-bom.md#formulas-co-products-and-by-products)

- Typical use cases
  
    Formula level Guides are useful to help shop floor workers with guided handling instructions in the context of a formula or recipe. Guides can also be assigned to versions of a formula.

    > [!TIP] You can assign guidance relevant for production process  based on this formula to a route, route version or route operation relations.  

    > [!NOTE] Formula lines cannot be used to attach individual Guides at this point.

- How to set up

    Navigate to Formula form and open the Header section. In Associated Guides tab on header section of the Formula form and add, remove or manage the associated Guides.

  :::image type="content" source="media/instruction-guides-Formula.png" alt-text="Adding a Guide to a Formula.":::

##### [Formula Version](bill-of-material-bom.md#bom-and-formula-versions)

- Typical use cases
  
    Guides can also be attached to individual versions of a Formula. They are useful to help shop floor workers with guides instructions that walk through the production along specific version formula recipe.

    > [!TIP]
    > You can assign guidance relevant for production process based on this formula version to a route, route version or route operation relations.  

    > [!NOTE]
    > Formula lines cannot be used to attach individual Guides at this point.
  
- How to set up

    Navigate to Formula form and open the Header section. In Formula Versions tab on header section of the Formula form select a version.

    :::image type="content" source="media/instruction-guides-FormulaVersion.png" alt-text="Accessing the associated Guides on a Formula version.":::

    The button Associated Guides opens a view where you can add, remove or manage the associated Guides.

    :::image type="content" source="media/instruction-guides-FormulaVersionAddGuide.png" alt-text="Adding a Guide to a Formula version.":::

##### [Bill of material](bill-of-material-bom.md)

- Typical use cases
  
    Bill Of Material (BOM) level Guides are useful to help shop floor workers with guides instructions that walk through preparing and handling material from a BOM. Guides can also be assigned to versions of a BOM.

    > [!NOTE] BOM lines cannot be used to attach individual Guides at this point.

- How to set up

    Navigate to BOM form and open the Header section. In Associated Guides tab on header section of the BOM form and add, remove or manage the associated Guides.

    :::image type="content" source="media/instruction-guides-BOM.png" alt-text="Adding a Guide to a BOM.":::

##### [Bill of material  version](bill-of-material-bom.md#bom-and-formula-versions)

- Typical use cases
  
    Guides can also be attached to individual versions of a Bill Of Material (BOM). They are useful to help shop floor workers with guides instructions for handling a version of a BOM which is different from the generic BOm or other versions.

    > [!NOTE] BOM lines cannot be used to attach individual Guides at this point.

- How to set up

    Navigate to BOM form and open the Header section. In BOM Versions tab on header section of the BOM form select a version.

    :::image type="content" source="media/instruction-guides-BOMVersion.png" alt-text="Accessing the associated  Guides on a BOM version.":::

    The button Associated Guides opens a view where you can add, remove or manage the associated Guides.

    :::image type="content" source="media/instruction-guides-BOMVersionAddGuide.png" alt-text="Adding a Guide to a BOM version.":::

##### [Route](routes-operations.md)

- Typical use cases

    Routes are typically used to specify how a certain release product shall be produced based on a BOM or BOM version and with a set of resources or resource groups.
    You can assign a Guide to a  route in order to provide step by step instructions for the respective production process.

- How to set up

    Navigate to Route form and in the Associated Guides tab add, remove or manage the associated Guides.
  
    :::image type="content" source="media/instruction-guides-Route.png" alt-text="Accessing the associated  Guides on a BOM version.":::

##### [Route Version](routes-operations.md#route-versions)

- Typical use cases

  Routes versions are typically used to specify variants of production processes based on an existing route. You can assign a different Guides to each route version.

- How to set up

  Navigate to Route form and in the Versions tab select a route version.

  :::image type="content" source="media/instruction-guides-RouteVersion.png" alt-text="Accessing the associated  Guides on a BOM version.":::

  The button Associated Guides opens a view where you can add, remove or manage the associated Guides.

  :::image type="content" source="media/instruction-guides-RouteVersionAddGuide.png" alt-text="Adding a Guide to a BOM version.":::

##### [Route Operation Relation](routes-operations.md#operation-relations)

- Typical use cases

  Operation relations are the most specific way to add guidance to a product process and the related operations. You are able to specify guidance for each operation in a route and specify different guidance for any type of relation context that has been specified for a route, like for specific items, configuration and more. You can also specify to which stages in the operation the guidance applies, like setup, queueing, process, transport,...

  > [!NOTE]
  > If you specify guides in several operation relations of a route, among those guides, only the guide from the most specific relation will be show on the shop floor for the generated job.

- How to set up

  Navigate top the route form and in the action bar select the action group Route, under Maintain click on Route details.
  In the route detail form select in the top section the operation you like to provide dedicated guidance for. And in the bottom grid select the specific relation or the generic All relation.

  :::image type="content" source="media/instruction-guides-RouteOperationRelation.png" alt-text="Accessing the associated Guides on a route operation relation.":::

  Use the Associated Guides button to add, remove or manage the associated Guides. You can add one or more guides and specify for each the relevant  stages of the operation.

  :::image type="content" source="media/instruction-guides-RouteOperationRelation-AddGuide.png" alt-text="Adding a Guide to a route operation relation and relevant stages of the operation.":::

### Instructions in the shop floor experience

### Resolving logic for Guides

You can add Guides to the following production data: [Resource groups](#resource-grouptasksdefine-discrete-manufacturing-resource-groupmd), [resources](#resourceoperations-resourcesmd), [released products](#release-productpimtaskscreate-released-product-single-company), [BOMs](#bill-of-materialbill-of-material-bommd) and [BOM versions](#bill-of-material-versionbill-of-material-bommdbom-and-formula-versions), [formulas](#formulabill-of-material-bommdformulas-co-products-and-by-products) and [formula versions](#formula-versionbill-of-material-bommdbom-and-formula-versions), [routes](#routeroutes-operationsmd) and [route versions](#route-versionroutes-operationsmdroute-versions), and [route operation relations](#route-operation-relationroutes-operationsmdoperation-relations).

When Dynamics 365 SCM generates the jobs for the production floor it will collect the relevant Guides from those sources. Please be aware of the following rules:

> [!Important]
> If you attach a BOM/Formula version to a route or production order that any Guide attached to this version and also the Guides attached to the parent BOM/Formula of that version will be shown on the job.

> [!Important]
> If you attach a Route version to a production order that any Guide attached to this version and also the Guides attached to the parent Route of that version will be shown on the job.

> [!IMPORTANT]
> If you define several Route Operation relations, which includes the 'All' relation and assign Guides to those, only the Guides from the most specific relation will be shown for the Job.  

:::image type="content" source="media/instruction-guides-Resolve.png" alt-text="Diagram on resolving the relevant Guides":::
