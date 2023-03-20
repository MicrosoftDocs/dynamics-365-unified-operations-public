---
title: Document class sales point for Latin America
description: This article provides information about the sales point additional settings configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/17/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Document class sales point for Latin America

[!include [banner](../includes/banner.md)]

You can add a configuration with sales point, account typem and sequence number to any document class in this form.

## Prerequisites

The following prerequisites must be met before you can set up additional settings for sales points in Latin America organizations:

- Sales point prefixes must be created 
- Document classes must be configured
- Number sequences must be created

## Set up sales point additional settings for Latin America

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class sales point**.
2. Select **New** to create a record.
3. In the **General** section, update the following fields:

    | Field                | Description                  |
    |----------------------|------------------------------|
    | Document class Id.   | Select a document class.     |
    | Account type         | Select an account type.      |
    | Sales point prefix   | Select a sales point prefix. |
    | Number sequence code | Select a number sequence.    |

   The **Printing** section is optional and is used as additional information to be printed in the fiscal document.

## Setup a sales authorization code

Select **Sales CA** to access the sales authorization code configuration for the sales point.

- The sales point assigned to the **Document class sales point** configuration must have the **Validate AC** option enabled.
- The document class assigned to the **Document class sales point** must have the **Require CA number** option enabled.
- The document mask configuration for the document class selected must be automatic.

1. On the **Document class sales point** page, on the Action Pane, select **Sales CA**.
2. Select **New** and enter information in the following fields.

    | Field                   | Description                                                                   |
    |-------------------------|-------------------------------------------------------------------------------|
    | Authorization code (CA) | Enter the authorization code provided by the fiscal authority.                |
    | Date from               | Select the date from which the authorization code is valid.                   |
    | Date to                 | Select the date until which the authorization code will be valid.             |
    | From voucher number     | Enter the minimum document number that uses the sales authorization code.     |
    | To voucher number       | Enter the maximum document number that uses the sales authorization code.     |

3. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
