---
title: LATAM Taxpayer type 
description: This topic provides information about the taxpayer type configuration for LATAM. 
author: Fhernandez0088
ms.date: 10/27/2022
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# LATAM Taxpayer type

## **Overview**

This form allows to create any type of tax responsible entity with which the company operates (customers, vendors, employees, and even the company itself).
To make the corresponding settings enter go to: **Organization administration > Setup > LATAM > Taxpayer type**.
 
 
## **General panel**

To modify an existing taxpayer type access the browser list and select or create a new register.

The fields to complete are:

**Taxpayer type:** this field should be completed manually, identifying with a code the taxpayer type that is being registered.

**Description:** this field should be completed manually, extending in a detail the taxpayer type that is being created.

## **Settings panel**

| Field                                   | Description                                                                                                                                                                                                                                  |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Foreign taxpayer                        | This verification field should be selected if the entity registered is foreign.                                                                                                                                                              |
| Validate vendor AC                      | This verification field should be selected if the authorization code issued by the vendors is required to be validated.                                                                                                                      |
| Internal taxpayer                       | This field of verification should be selected if the taxpayer being created is internal. This means it doesn't represent a real entity. All transactions made by entities possessing this taxpayer type will not be informed in tax reports. |
| Mandatory country of residence          | If this button is set to yes, the field “Country of residence” in the entity configuration will be mandatory.                                                                                                                                |
| Mandatory registered jurisdiction       | If this button is set to yes, the field "Registered jurisdiction” in the entity configuration will be mandatory.                                                                                                                             |
| Mandatory country identification number | If this button is set to yes, the “Country identification number” field in the entity configuration will be mandatory.                                                                                                                       |
| Mandatory state identification number   | If this button is set to yes, the field “State identification number” will be mandatory.                                                                                                                                                     |

Depending on the taxpayer type selected, the verification fields will vary.

The options are as follows:

- If the taxpayer is set up as a national (i.e., it doesn’t have the foreign taxpayer and internal contributor buttons set to yes):

  - Every option can be enabled or disabled according to the national taxpayer type configuration.

- If the taxpayer is configured as foreign:

  - **Internal taxpayer:** this field will be set to no by default and cannot be edited.

  - **Validate vendor AC:** this field will be set to no by default and cannot be edited.

  - **Mandatory country of residence/Mandatory registered jurisdiction/Mandatory country identification number:** can be enabled or disabled.

  - **Mandatory state identification number:** If this option is enabled, the field corresponding to the mandatory country identification number should also be enabled.

- If the taxpayer is configured as an internal:

  - **Foreign taxpayer/Validate vendor CA:** this fields will come disabled by default and cannot be edited.

  - **Mandatory country of residence/Mandatory registered jurisdiction/Mandatory country identification number/Mandatory state identification number:** can be enabled or disabled according to the configuration desired.

## **Document types panel**

In this panel, the tax ID types created in the master record will be linked with the taxpayer type.

The fields to complete are:

| Field          | Description                                                                                    |
|----------------|------------------------------------------------------------------------------------------------|
| Document types | In this field you must select one or more of the Tax ID types configured in the master record. |
| Description    | This field will expand the information of the tax ID type.                                     |

> [!NOTE]
> This configuration, together with the tax ID type configuration in the country address master, allows filtering or directly assign the Tax ID type in the customer/vendor master record.

## Document class letter panel

In this tab the document class letters will be associated with the taxpayer.

The fields to complete are:

| Field                    | Description                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------|
| Document class letter Id | In this field you must select one of document class letter ID created in the master record. |
| Description              | This field will expand the information document class letter.                               |


## Tax application button

You can use Tax application option to add the codification provided by the fiscal autorities.

1.	Go to Organization administration > Setup > LATAM > Taxpayer type.
2.	Click Tax application.
3.	Click New.
4.	In the Tax application Id. field, enter or select a value.
5.	In the Tax application code field, type a value.
6.	Click Save.

## Prerequisites:

- Tax ID type configured
- Document class letter configured


