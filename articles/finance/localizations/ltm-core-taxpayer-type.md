---
title: Taxpayer types for Latin America 
description: This topic provides information about the taxpayer type configuration for Latin America. 
author: Fhernandez0088
ms.date: 10/27/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Taxpayer types for Latin America 

You can set up a type of tax responsible entity with which the company operates. Entities can include customers, vendors, employees, and even the company itself.
 
## Prerequisites

The following prerequisites must be met before you can set up taxpayer types for organizations in Latin America:

- **Tax ID types** must be configured.
- **Document class letters** must be configured.

## Set up a Taxpayer type for Latin America

1. Go to **Navigation pane > Organization administration > Setup > LATAM > Taxpayer type**.

1. In the **General** section complete the following fields:

  - In the **Taxpayer type** field enter the code that identifies the register.

  - In the **Description** field enter an extended explanation of the taxpayer type.

> [!NOTE]
> These fields are mandatory.

2. In the **Settings** section complete the configuration according to the taxpayer type characteristics:

Enable or disable the buttons as required:

| Button                                  | Description                                                                                                                                                                                                                                  |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Foreign taxpayer                        | This verification field should be selected if the entity registered is foreign.                                                                                                                                                              |
| Validate vendor AC                      | This verification field should be selected if the authorization code issued by the vendors is required to be validated.                                                                                                                      |
| Internal taxpayer                       | This field of verification should be selected if the taxpayer being created is internal. This means it doesn't represent a real entity. All transactions made by entities possessing this taxpayer type will not be informed in tax reports. |
| Mandatory country of residence          | If this button is set to yes, the field “Country of residence” in the entity configuration will be mandatory.                                                                                                                                |
| Mandatory registered jurisdiction       | If this button is set to yes, the field "Registered jurisdiction” in the entity configuration will be mandatory.                                                                                                                             |
| Mandatory country identification number | If this button is set to yes, the “Country identification number” field in the entity configuration will be mandatory.                                                                                                                       |
| Mandatory state identification number   | If this button is set to yes, the field “State identification number” will be mandatory.                                                                                                                                                     |

3. In the **Document types** grid add the **Tax Id types** associated to the taxpayer type according to the country legislation.

> [!NOTE]
> This configuration, together with the tax ID type configuration in the country address master, allows filtering or directly assign the Tax ID type in the customer/vendor master record.

4. In the **Document class letter** grid select the Ids that the taxpayer type will use in their transactions.

5. Select **Save**.

## Add the fiscal codification provided by the fiscal authorities

You can use **Tax application** option to add this codification.

1.	Go to **Navigation pane > Organization administration > Setup > LATAM > Taxpayer type**.
2.	Select the **Tax application** button on the action pane.
3.	Slect **New** to add a line to the grid.
4.	In the **Tax application Id.** field select a value from the list.
5.	In the **Tax application code field** type the code with wich the fiscal authority identifies the tax payer type.
6.	Select **Save**.


