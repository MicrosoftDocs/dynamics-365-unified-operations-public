---
# required metadata

title: Wave step codes
description: This article provides an overview of wave step codes and how they are used.
author: Mirzaab
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSWaveTableListPage, WHSWaveStepCode, WHSReplenishmentTemplates, WHSWaveTemplateTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# Wave step codes

[!include [banner](../includes/banner.md)]

Wave step codes are codes that users can set up and use to link specific instances of wave methods to a corresponding template. The templates include templates for replenishment, containerization, label printing, load building, and sorting.

When wave step codes aren't used, users must enter free text to reference a specific template from the wave method instance. Free text is prone to errors because users must make sure that the wave step text that they add for a specific wave step method in a wave template exactly matches the wave step text in the target template.

Wave step codes for a specific wave step type are set up on a separate page. For every wave step method instance in a wave template that requires a wave step code, the wave step code must be selected in a drop-down list. Selection in a drop-down list replaces free text entry and helps reduce the risk and impact of human error. Setup codes are used to link a wave step method in a wave template to a target template for the method.

> [!NOTE]
> Use of the wave step codes feature is optional. It is enabled organization-wide for all legal entities.

## Setup demo 

For this demo, demo data must be installed, and you must use the **USMF** demo data company.

### Enable wave step codes

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you are running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Organization wide wave step code* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

When you first enable this feature, all existing wave step free texts in all legal entities are upgraded to the new structure. After this upgrade is completed for all legal entities, then the feature is enabled. If the feature cannot be enabled for one or more legal entities, then the feature is not enabled for any legal entities.

During the enablement, validations are done during the data upgrade. If the upgrade fails, you receive an error message. An upgrade might fail because of the following conflicts:

- Duplicate wave step free texts exist.
- Customizations exist.
- A wave step free text that is associated with a wave step method instance doesn't match the expected template type.

After you've resolved any conflicts that are identified during the validations, you can retry to enable the feature.

When the feature has been enabled, the **Wave step codes** page (**Warehouse management \> Setup \> Waves \> Wave step codes**) becomes available. This page lists the wave step codes that were upgraded when the *Organization wide wave step code* feature was enabled.

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

You perform these steps for each legal entity.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]