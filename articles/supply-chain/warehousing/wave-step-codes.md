---
# required metadata

title: Wave step codes
description: This topic provides an overview of wave step codes and how they are used.
author: josaw1
manager: AnnBe
ms.date: 08/05/2019
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
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Wave step codes

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

## About wave step codes

Wave step codes allow users to set up codes that will be used to link
specific wave method instances with their corresponding template. This covers
templates for replenishment, containerization, label printing, load building,
and sorting. 

Without wave step codes, users must reference a specific
template from the wave process method using only free text. Free text is is error prone, as it requires a user to manually ensure that the wave step text
added for a specific wave step process method in a wave template matches the
exact wave step text in the target template. 

Wave step codes are set up for a
specific wave step type in a separate form. Each wave step method in a wave
template that needs a wave step code requires the wave step code to be
selected from a dropdown list, instead of a free text entry. Linking a wave step method
in a wave template to a target template for the method is based on setup codes, reducing the risk and impact of human
errors.

> [!NOTES]
> The use of wave step codes is optional. 

> Uptake for wave step codes is per legal entity. As such, all
existing wave steps codes in the specific legal entity will be upgraded into the
new structure.

## Setup demo 

For this demo, you will need to have demo data installed, and use demo data company USMF.

### Enable step codes

To enable wave step codes, go to **Warehouse management > Setup > Warehouse
management parameters.** On the **General** tab, on the **Wave processing** FastTab, select **Yes* for **Enable wave step codes**.

All existing wave step free texts will be upgraded into the new
structure. Once this is complete for a legal entity, the item **Enable wave step
codes** will no longer be available in the form. Validations are performed during the upgrade,
and if the upgrade fails, an error message will appear. An upgrade may fail for the following reasons; duplicate wave step code free texts, customizations, or a wave step
free text associated with a wave step method does not match the expected
template type. Once the conflicts identified during the
validations are resolved, the upgrade process can be re-run.

When the upgrade succeeds, the **Wave step codes** page will be available. The **Warehouse management > Setup > Waves > Wave step codes** page lists the wave step codes upgraded during the enabling
process. 

### Create new step codes

You can use the **Warehouse management > Setup > Waves > Wave step codes** page to create and delete wave step codes. 

Any new wave step code and its associated ID must be unique across all wave step types, and must be 
defined for a specific wave step type.

### Apply step codes

Once the appropriate wave step codes have been defined, they can be applied for
the wave processing methods. 

To apply step codes, go to the appropriate target template. The target templates for which the wave step codes are
designated to point to are:

- **Replenishment templates**. **Warehouse management > Setup > Replenishment > Replenishment templates**

- **Load build templates**: **Warehouse management > Setup > Load > Load build templates**

- **Sort templates**: **Warehouse management > Setup > Packing > Outbound sorting templates**

- **Containerization templates**: **Warehouse management > Setup > Containers > Container build templates**

- **Label printing templates**: **Warehouse management > Setup > Document routing > Wave label templates**

The templates above will be applied when referenced from a wave processing
method selected in a wave template. When the wave step code on a wave
processing method in a wave template matches the wave step code on a one of the
templates types, then the template will be applied.

### Sample scenario

1. Go to **Warehouse management > Setup > Waves > Wave step codes**. Create a wave step code for the type **Replenishment**. 
1. Go to **Warehouse management > Setup > Replenishment > Replenishment templates.** Create a replenishment template. 
1. On the replenishment template, select the wave step code created for the type.
1. Go to **Warehouse management > Setup > Waves > Wave templates**. Select the wave template
that you intent to use. 
1. On the template, on the **Methods** FastTab, select the method **Replenishment**. 
1. In the **Wave step code** field, select the wave step code you also selected for the replenishment template.

By following these steps, you ensured that the replenishment template you created
will be the replenishment template that will be applied for the wave template
when used as the wave step codes selected match.
