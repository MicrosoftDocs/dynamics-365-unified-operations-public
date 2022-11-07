---
title: Tax Id types for Latin America 
description: This topic provides information about the Tax Id types configuration for Latin America. 
author: Fhernandez0088
ms.date: 11/07/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Tax Id types for Latin America

This configuration will allow you to enter every valid tax ID type in each country, to identify the entities with which the company performs operations (customers, vendors, contacts, banks, employees, etc.).

## Prerequisites

If you want to set up a **Tax Id type** with a fiscal codification the **Tax application** must be previously configured.

## Set up a Tax Id type
1. Go to **Navigation menu > Modules > Organization administration > Setup > LATAM > Tax ID type**

2. In the **Overview** section complete the following fields:
    - In the **Tax ID type** field enter a code to identify the register
    - In the **Description** field enter an extended explanation for the Tax Id type.

3. In the **Settings** section complete the following fields:
    - In the **Mask validation method** field select one of the following:

    | Method   | Description                                                                                                                                                                                                                            |
    |----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Basic    | This method allows use a simplified mask to define the amount and types of characters. The codification is 'X' for alphanumeric characters, 'A' for alphabetic and '9' for numeric. Also, symbols can be added to the mask ('-', '.'). |
    | Advanced | This method allows to complete masks with SQL sentences to define each character. For alphabetic characters: [A-B], for numeric ones [0-9] and for alphanumeric [A-B]. Also, symbols can be added to the mask [-] [/].                 |
    | None     | This option doesn't validate the mask and therefore the fields **Mask** and **Length** won't be editable.                                                                                                                              |

    - In the **Mask** field enter the mask format desired.
    - The **Length** field will be autocompleted with the number of characters that the **Mask** field has.
    - In the **Verification algorithm** field select one of the following options:

    | Verification algorithm                                                    | Description                                                                   |
    |---------------------------------------------------------------------------|-------------------------------------------------------------------------------|
    | No verification                                                           | No verification of the tax ID will be done.                                   |
    | CUIT verification - Argentina                                             | The verification algorithm will check that the tax ID is valid for Argentina. |
    | RUT verification - Chile                                                  | The verification algorithm will check that the tax ID is valid for Chile.     |
    | RUC verification - Peru                                                   | The verification algorithm will check that the tax ID is valid for Peru.      |
    | NIT verification - Colombia                                               | The verification algorithm will check that the Tax ID is valid for Colombia.  |
    | RUC verification - Ecuador - Legal / Foreign person without identity card | The verification algorithm will check that the tax ID is valid for Ecuador.   |
    | Identity card verification - Ecuador                                      | The verification algorithm will check that the tax ID is valid for Ecuador.   |
    | RUC verification – Ecuador – Natural person                               | The verification algorithm will check that the tax ID is valid for Ecuador.   |
    | RUT verification – Uruguay                                                | The verification algorithm will check that the tax ID is valid for Uruguay.   |

    - Enable or disable the following buttons according to the Tax ID type characteristics:

    | Button                | Description                                                                                                                |
    |-----------------------|----------------------------------------------------------------------------------------------------------------------------|
    | Country document type | It allows to identify that the tax ID type is at country level and not at state level.                                     |
    | State document type   | It identifies that the tax ID type belongs at state level.                                                                 |
    | Foreign document type | If it is set to yes, this tax ID type will be selectable in the countries address configurations for all the foreign ones. |

5. Select **Save** from the action pane to finish the configuration and save the record.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Navigation pane > Modules > Organization administration > Setup > LATAM > Taxpayer type**.
2.	Select the **Tax application** button on the action pane.
3.	Select **New** to add a line to the grid.
4.	In the **Tax application Id.** field select a value from the list.
5.	In the **Tax application code field** type the code with which the fiscal authority identifies the **Tax Id type**.
6.	Select **Save**.
