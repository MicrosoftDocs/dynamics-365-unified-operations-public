---
title: Tax ID types for Latin America 
description: This article provides information about the tax ID type configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/07/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Tax ID types for Latin America

USe this configuration to enter valid tax ID types in each country and to identify the entities with which the company performs operations including customers, vendors, contacts, banks, and employees.

## Prerequisites

Before you can set up a tax ID Type with a fiscal codification, the tax application must already be configured.

## Set up a Tax ID type

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
2. In the **Overview** section, in the **Tax ID type** field, enter the register code.
3. In the **Description** field, enter a brief description of the tax ID type.
4. In the **Settings** section, in the **Mast validation method** field, select one of the following methods:

    | Method   | Description  |
    |----------|--------------|
    | Basic    | Use a simplified mask to define the amount and types of characters. The codification is **X** for alphanumeric characters, **A** for alphabetic and **9** for numeric. Symbols can also be added to the mask. For example, **-** or **.**. |
    | Advanced | Complete masks with SQL sentences to define each character. For alphabetic characters: [A-B], numeric characters [0-9], and alphanumeric characters [A-B]. Symbols can also be added to the mask [-] [/].  |
    | None     | This option doesn't validate the mask and the fields **Mask** and **Length** aren't editable.  |

5. In the **Mask** field, enter the mask format. The **Length** field is filled automatically with the number of characters that the **Mask** field has.
6. In the **Verification algorithm** field, select one of the following options:

    | Verification algorithm                                                    | Description                                                                   |
    |---------------------------------------------------------------------------|-------------------------------------------------------------------------------|
    | No verification                                                           | No verification of the tax ID is done.                                   |
    | CUIT verification - Argentina                                             | The verification algorithm verifies that the tax ID is valid for Argentina. |
    | RUT verification - Chile                                                  | The verification algorithm verifies that the tax ID is valid for Chile.     |
    | RUC verification - Peru                                                   | The verification algorithm verifies that the tax ID is valid for Peru.      |
    | NIT verification - Colombia                                               | The verification algorithm verifies that the Tax ID is valid for Colombia.  |
    | RUC verification - Ecuador - Legal / Foreign person without identity card | The verification algorithm verifies that the tax ID is valid for Ecuador.   |
    | Identity card verification - Ecuador                                      | The verification algorithm verifies that the tax ID is valid for Ecuador.   |
    | RUC verification – Ecuador – Natural person                               | The verification algorithm verifies that the tax ID is valid for Ecuador.   |
    | RUT verification – Uruguay                                                | The verification algorithm verifies that the tax ID is valid for Uruguay.   |

7. Set the following fields to **Yes** according to the tax ID type characteristics:

    | Field                | Description                                                                                                                |
    |-----------------------|----------------------------------------------------------------------------------------------------------------------------|
    | Country document type | Identify that the tax ID type is at the country level and not at the state level.                                     |
    | State document type   | Identify that the tax ID type belongs at the state level.                                                                 |
    | Foreign document type | If set to **Yes**, this tax ID type can be selected in the countries' address configurations for all the foreign ones. |

9. On the Action Pane, select **Save** to finish the configuration and save the record.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type**.
2.	On the Action Pane, select **Tax application**.
3.	Select **New** to add a line to the grid, and in the **Tax application Id** field, select a value from the list.
5.	In the **Tax application code** field, enter the code with which the fiscal authority identifies the **Tax Id type**.
6.	Select **Save**.
