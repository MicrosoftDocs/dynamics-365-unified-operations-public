---
title: Tax ID types for Latin America 
description: Learn about the tax ID type configuration for Latin America, including prerequisites and a process for setting up a tax ID type.
author: SandraYamamoto0602
ms.author: v-sandraya 
ms.topic: how-to
ms.date: 06/23/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Tax ID types for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

Use this configuration to enter valid tax ID types for each country or region and identify the entities that the company operates with. These entities can include customers, vendors, contacts, banks, and employees.

## Prerequisites

- The legal entity must have an address in a country or region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature must be enabled.
  
## Set up a tax ID type

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
1. In the **Overview** section, enter the register code in the **Tax ID type** field.
1. Enter a brief description of the tax ID type in the **Description** field.
1. In the **Settings** section, select a validation method in the **Mask validation method** field.

    | Method   | Description |
    |----------|-------------|
    | Basic    | Use a simplified mask to define the number and types of characters. **A** represents alphabetic characters, **9** represents numeric characters, and **X** represents alphanumeric characters. Add symbols such as hyphens (-) and periods (.) to the mask. |
    | Advanced | Use a complete mask with SQL sentences to define each character. The mask can include alphabetic characters (A–Z), numeric characters (0–9), and alphanumeric characters (A–Z, 0–9). Add symbols such as hyphens (-) and slashes (/) to the mask. |
    | None     | The system doesn't validate the mask, and you can't edit the **Mask** and **Length** fields. |

1. Enter the mask format in the **Mask** field. The system automatically sets the **Length** field to the number of characters in the **Mask** value.
1. Select a verification algorithm in the **Verification algorithm** field.

    | Verification algorithm                                                    | Description |
    |---------------------------------------------------------------------------|-------------|
    | No verification                                                           | The system doesn't verify the tax ID. |
    | CUIT verification - Argentina                                             | The verification algorithm verifies that the tax ID is valid for Argentina. |
    | RUT verification - Chile                                                  | The verification algorithm verifies that the tax ID is valid for Chile. |
    | RUC verification - Peru                                                   | The verification algorithm verifies that the tax ID is valid for Peru. |
    | NIT verification - Colombia                                               | The verification algorithm verifies that the tax ID is valid for Colombia. |
    | RUC verification - Ecuador - Legal / Foreign person without identity card | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | Identity card verification - Ecuador                                      | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | RUC verification – Ecuador – Natural person                               | The verification algorithm verifies that the tax ID is valid for Ecuador. |
    | RUT verification – Uruguay                                                | The verification algorithm verifies that the tax ID is valid for Uruguay. |

1. Set the following options according to the characteristics of the tax ID type.

    | Field                 | Description |
    |-----------------------|-------------|
    | Country document type | Set this option to **Yes** to specify that the tax ID type is at the country/region level. |
    | State document type   | Set this option to **Yes** to specify that the tax ID type is at the state level. |
    | Foreign document type | Set this option to **Yes** to specify that the tax ID type can be selected in the countries/regions' address configurations for all foreign countries/regions. |

1. On the Action Pane, select **Save** to finish the configuration and save the record.

## Add the fiscal codification provided by the fiscal authorities

Use the **Tax application** option to add the fiscal codification that the fiscal authorities provide.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
1. On the Action Pane, select **Tax application**.
1. For each Tax ID type that requires fiscal codification:
   1. Select the record, and then go to **Tax application** in the top menu.
   1. Create a new record.
   1. In the **Tax application Id** field, select a value.   
   1. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the Tax ID Type.
   1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
