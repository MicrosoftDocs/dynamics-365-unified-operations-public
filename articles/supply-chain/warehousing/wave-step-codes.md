---
# required metadata

title: Wave step codes
description: This topic provides an overview of wave step codes and how they are used.
author: josaw1
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Wave step codes

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

## About wave step codes

Wave step codes are codes that users can set up and use to link specific instances of wave methods to a corresponding template. The templates include templates for replenishment, containerization, label printing, load building, and sorting.

When wave step codes aren't used, users must enter free text to reference a specific template from the wave method instance. Free text is prone to error, because users must make sure that the wave step text that they add for a specific wave step method in a wave template exactly matches the wave step text in the target template.

Wave step codes for a specific wave step type are set up on a separate page. For every wave step method instance in a wave template that requires a wave step code, the wave step code must be selected in a drop-down list. Selection in a drop-down list replaces free text entry and helps reduce the risk and impact of human error. Setup codes are used to link a wave step method in a wave template to a target template for the method.

> [!NOTE]
> Use of the wave step codes feature is optional, and uptake is per legal entity. Therefore, if a specific legal entity uses the feature, all existing wave step codes in that legal entity are upgraded to the new structure.

## Setup demo 

For this demo, demo data must be installed, and you must use the **USMF** demo data company.

### Enable wave step codes

Follow these steps to turn on the wave step codes feature.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
2. On the **General** tab, on the **Wave processing** FastTab, set the **Enable wave step codes** option to **Yes**.

All existing wave step free texts are upgraded to the new structure. After this upgrade is completed for a legal entity, the **Enable wave step codes** option is no longer available on the **Warehouse management parameters** page.

Validations are done during the upgrade, and if the upgrade fails, you receive an error message. An upgrade might fail because of the following conflicts:

- Duplicate wave step free texts exist.
- Customizations exist.
- A wave step free text that is associated with a wave step method instance doesn't match the expected template type.

After you've resolved any conflicts that are identified during the validations, you can rerun the upgrade process.

When the upgrade succeeds, the **Wave step codes** page (**Warehouse management \> Setup \> Waves \> Wave step codes**) becomes available. This page lists the wave step codes that were upgraded when the wave step codes feature was turned on.

### Create new wave step codes

You can use the **Wave step codes** page to create and delete wave step codes.

Every new wave step code and its associated ID must be unique across all wave step types, and they must be defined for a specific wave step type.

### Apply wave step codes

After you've defined the appropriate wave step codes, they can be applied to the wave process methods.

To apply wave step codes, go to the appropriate target template. Here are the target templates that the wave step codes are designated to point to:

- **Replenishment templates:** Warehouse management \> Setup \> Replenishment \> Replenishment templates
- **Load build templates:** Warehouse management \> Setup \> Load \> Load build templates
- **Sort templates:** Warehouse management \> Setup \> Packing \> Outbound sorting templates
- **Containerization templates:** Warehouse management \> Setup \> Containers \> Container build templates
- **Label printing templates:** Warehouse management \> Setup \> Document routing \> Wave label templates

The templates in this list are applied when they are referenced from a wave process method that is selected in a wave template. When the wave step code on a wave process method in a wave template matches the wave step code in one of the templates types, the template is applied.

### Sample scenario

The following procedure helps guarantee that the replenishment template that you created will be applied for the wave template.

1. Go to **Warehouse management \> Setup \> Waves \> Wave step codes**, and create a wave step code for the **Replenishment** type.
2. Go to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**, and create a replenishment template.
3. In the replenishment template, select the wave step code that you created for the **Replenishment** type.
4. Go to **Warehouse management \> Setup \> Waves \> Wave templates**, and select the wave template that you intend to use.
5. In the template, on the **Methods** FastTab, select the **Replenishment** method.
6. In the **Wave step code** field, select the wave step code that you selected in the replenishment template.
