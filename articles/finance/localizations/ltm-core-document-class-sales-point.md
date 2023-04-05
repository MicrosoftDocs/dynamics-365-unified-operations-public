---
title: Document class sales point for Latin America
description: This article provides information about the configuration of additional settings for sales points for Latin America.
author: Fhernandez0088
ms.date: 04/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document class sales point for Latin America

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

On the **Document class sales point** page, you can add a configuration that has a sales point, account type, and sequence number to any document class.

## Prerequisites

The following prerequisites must be met before you can set up additional settings for sales points in Latin American organizations:

- Sales point prefixes must be created.
- Document classes must be configured.
- Number sequences must be created.

## Set up sales point additional settings for Latin America

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**.
2. Select **New** to create a record.
3. In the **General** section, update the following fields.

    | Field                | Description                  |
    |----------------------|------------------------------|
    | Document class Id.   | Select a document class.     |
    | Account type         | Select an account type.      |
    | Sales point prefix   | Select a sales point prefix. |
    | Number sequence code | Select a number sequence.    |

    The **Printing** section is optional and is used as additional information that's printed on the fiscal document.

## Set up a sales authorization code

Select **Sales CA** to access the sales authorization code configuration for the sales point.

- For the sales point that's assigned to the **Document class sales point** configuration, the **Validate AC** option must be enabled.
- For the document class that's assigned to the **Document class sales point** configuration, the **Require CA number** option must be enabled.
- For the selected document class, the document mask configuration must be automatic.

Follow these steps to set up a sales authorization code.

1. On the **Document class sales point** page, on the Action Pane, select **Sales CA**.
2. Select **New**, and set the following fields.

    | Field                   | Description                                                               |
    |-------------------------|---------------------------------------------------------------------------|
    | Authorization code (CA) | Enter the authorization code that's provided by the fiscal authority.     |
    | Date from               | Select the first date that the authorization code is valid.               |
    | Date to                 | Select the last date that the authorization code is valid.                |
    | From voucher number     | Enter the minimum document number that uses the sales authorization code. |
    | To voucher number       | Enter the maximum document number that uses the sales authorization code. |

3. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
