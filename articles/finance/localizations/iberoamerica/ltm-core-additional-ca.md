---
title: More authorization code for Latin America
description: Learn about the configuration required to use the additional authorization code feature.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Additional authorization code for Latin America

[!include [banner](../../includes/banner.md)]

[!include [banner](../includes/does-not-apply-to.md)]

This article explains how to configure and use the additional authorization code feature in the LATAM extension. 

This functionality adds a field named **Additional CA** in the **Sales CA** form located in the **Document class sales point** configuration. You can customize the information in this field to meet your requirements.

Learn more in [Document class sales point for Latin America](ltm-core-document-class-sales-point.md) and [Sales authorization code for Latin America](ltm-core-sales-ca.md).

## Prerequisites

Before you can use the additional sales authorization code feature, you must meet these prerequisites:

- The company/region of the legal entity is in a LATAM-supported country/region.
- Both the general LATAM feature and the country/region-specific LATAM feature are enabled.
- Go to **Organization administration > Setup > LATAM > LATAM parameters**, and in the **Functionalities** section, set the **Enable additional authorization code** to **Yes**.
- In the **Document class** configuration, set the **Require CA number** option to **Yes**.
- In the **Document class** configuration, set the entry type of the document mask to **Auto**.

Learn more in [Latin America parameters](ltm-core-latam-parameters.md) and [Document classes for Latin America]( ltm-core-document-class.md).

## Set up additional authorization code

1. Go to **Organization administration > Setup > LATAM > Document class sales point** (you can access this from the **Document class configuration**).
1. On the top menu, select the **Sales CA** button.
1. Complete the **Additional CA** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
