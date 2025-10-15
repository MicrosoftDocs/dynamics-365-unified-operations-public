---
title: Control code feature for Bolivia
description: Learn about the configuration required to use the additional authorization code feature for Bolivia.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 10/15/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Control code feature for Bolivia

This feature adds a field named **Control code** to the **Additional data** section in the **LATAM** information when posting a document.
This entry can be set manually or automatically by using the additional authorization code.
The automatic entry of this field responds to the Bolivian requirement of **Control code** in computerized documents.

Learn more in [Sales authorization code for Latin America](ltm-core-sales-ca.md) and [Additional authorization code for Latin America](ltm-core-additional-ca.md).

## Prerequisites

Before you can use the control code feature manually the following prerequisites must be met:

- The company/region of the legal entity must be in Bolivia.
- Both the general LATAM feature and the country/region-specific Bolivia LATAM feature must be enabled.

To use the control code feature for Bolivia with an automatic entry the following prerequisites must be met:

- The company/region of the legal entity must be in Bolivia.
- Both the general LATAM feature and the country/region-specific Bolivia LATAM feature must be enabled.
- Go to **Organization administration > Setup > LATAM > LATAM parameters**, and in the **Functionalities** section set the **Enable additional authorization code** to **Yes**.
- In the **Document class** configuration, set the **Require CA number** option to **Yes**.
- In the **Document class** configuration, in the **Document mask** section set the entry type of the document mask to **Auto**.

## Set up Control code feature for Bolivia

To enable the Control code field, follow these steps:

- In the **Document class** configuration, set the **Require control code** option to **Yes**.
- In the **Document class** configuration, set the **Type of control code** to **Automatic - Bolivia** or **Manual**.

To use the automatic control code entry for Bolivia, follow these steps:

1. Go to **Organization administration > Setup > LATAM > Document class sales point** (you can access from the **Document class configuration**).
1. Select the **Sales CA** button on the top menu.
1. Complete the **Additional CA** field with the digital key for Bolivia.

## Use Control code feature for Bolivia

To use the Control code feature manually follow these steps:

1. When posting a transaction go to the **LATAM** section.
1. If the setup is done correctly a field named **Control code** will appear in the **Additional data** section, enter a value manually.
1. Post the transaction.

To use the Control code feature with automatic entry for Bolivia follow these steps:

1. When posting a transaction go to the **LATAM** section.
1. If the setup is done correctly a field named **Control code** with a value will appear in the **Additional data** section.
1. Post the transaction.
