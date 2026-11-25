---
title: Document class sales point for Latin America
description: Learn about the configuration of additional settings for sales points for Latin America, including prerequisites and a process for setting up sales point settings.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: how-to
ms.date: 11/25/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Document class sales point for Latin America

[!INCLUDE [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

On the **Document class sales point** page, define the relationship between **sales point prefixes** and **document classes**.

Use this relationship for transactions across several account types, such as **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, **Bank**, or **Inventory**. Define the **sequence numbers** for document classes when you set their **mask** to **automatic**.

You can also add **print notes** and assign **default financial dimension codes** that are associated with a specific document class and sales point relationship.

## Prerequisites

Before you set up additional settings for sales points in Latin American organizations, ensure you meet the following prerequisites:

- The legal entity has an address in a country/region within the LATAM localization.
- Both the region-specific LATAM feature and the general LATAM feature are enabled.
- Sales point prefixes are created.
  
  Learn more in [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).
- Document classes are configured.
  
  Learn more in [Document classes for Latin America](ltm-core-document-class.md).
- Number sequences are created.

## Set up sales point additional settings for Latin America

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class sales point**.
1. Select **New** to create a record.
1. In the **General** section, update the following fields.

    | Field                | Description                  |
    |----------------------|------------------------------|
    | Document class Id.   | Select a document class.     |
    | Account type         | Select an account type.      |
    | Sales point          | Select a sales point.        |
    | Number sequence code | Select a number sequence.    |

1. The **Printing** section is optional and is used as additional information that's printed on the fiscal document.

> [!NOTE]
> Some of these fields might already be used for specific elements in your base country’s reports. Refer to your country’s overview page for additional details.

## Set up dimensions

Use this section to define default dimension codes for each document class sales point. When you use a document class with an automatic mask in a journal, the system automatically assigns the configured dimensions to the line based on the selected combination of document class, line type, and sales point.

> [!NOTE]
> You can modify these dimensions while posting the transaction if needed.

## Set up a sales authorization code

> [!NOTE]
> To access the sales authorization code configuration through the **Sales CA** field, the following prerequisites must be met:
>
> - Enable both the **Require CA number** option from the selected document class and the **Validate CA** option from the selected sales point.
> - Set the document mask configuration to automatic for the selected document class.

Follow these steps to set up a sales authorization code.

1. On **Document class sales point**, select **Sales CA** on the **Action** pane.
1. Select **New**, and set the following fields.

    | Field                   | Description                                                               |
    |-------------------------|---------------------------------------------------------------------------|
    | Authorization code (CA) | Enter the authorization code that the fiscal authority provides.     |
    | Date from               | Select the first date that the authorization code is valid for.               |
    | Date to                 | Select the last date that the authorization code is valid for.                |
    | From voucher number     | Enter the minimum document number that uses the sales authorization code. |
    | To voucher number       | Enter the maximum document number that uses the sales authorization code. |

1. Select **Save**.

Learn more in [Sales authorization code for Latin America](ltm-core-sales-point-prefixes.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
