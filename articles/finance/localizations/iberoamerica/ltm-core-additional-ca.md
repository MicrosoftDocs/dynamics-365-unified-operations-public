---
title: Additional authorization code for Latin America
description: Learn about the configuration required to use the additional authorization code feature.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 10/15/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Additional authorization code for Latin America

This article explains how to configure and use the additional authorization code feature in the LATAM extension. 

This functionality adds a field named **Additional CA** in the in the **Sales CA** form located in the **Document class sales point** configuration, the information in this field is customizable by the user requirements.

To learn more, see [Document class sales point for Latin America](ltm-core-document-class-sales-point.md) and [Sales authorization code for Latin America](ltm-core-sales-ca.md).

## Prerequisites

Before you can use the additional sales authorization code feature the following prerequisites must be met:

- The company/region of the legal entity must be in a LATAM-supported country.
- Both the general LATAM feature and the country/region-specific LATAM feature must be enabled.
- Go to **Organization administration > Setup > LATAM > LATAM parameters**, and in the **Functionalities** section set the **Enable additional authorization code** to **Yes**.
- In the **Document class** configuration, set the **Require CA number** option to **Yes**.
- In the **Document class** configuration, set the entry type of the document mask to **Auto**.

Learn more in [Latin America parameters](ltm-core-latam-parameters.md) and [Document classes for Latin America]( ltm-core-document-class.md).

## Set up additional authorization code

1. Go to **Organization administration > Setup > LATAM > Document class sales point** (you can access from the **Document class configuration**).
1. Select the **Sales CA** button on the top menu.
1. Complete the **Additional CA** field.
