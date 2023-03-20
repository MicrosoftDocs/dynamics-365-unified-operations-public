---
title: LATAM Parameters 
description: This topic provides information about the LATAM Parameters configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/20/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 	
ms.custom: bap-template
---

# LATAM Parameters
## Overview
This article provides a description of the LATAM Parameters configuration.
It allows to incorporate the general parameterizations to be made to the localization before starting with their respective configurations.

## Prerequisites
The Global LATAM taxes feature must be enabled.
The company must be in a country that supports the LATAM localization.

## Set up previous LATAM configurations
1. In the **General** tab enter the character length for the prefix field for **Document class types** and **Document class letters**.
2. In the **Functionalities** tab activate the desired sliders:

| Slider                        | Description                                                                            |
|-------------------------------|----------------------------------------------------------------------------------------|
| Enable sales return account   | Activate the alternative ledger account for return sales orders.                       |
| Enable project return account | Activate the alternative ledger account for return project sales.                      |
| Enable line control           | Enable the warning when surpassing a defined number of lines entered in a sales order. |
3. Enter the number of lines that triggers the line control warning in the filed **Max amount of lines**.
4. In the **Mandatory document class in journal** tab activate the sliders desired for each group: ledger, project, fixed assets, vendor, customer, and bank.
Activating a slider will make the field **Document class** in the LATAM extended information from journal entries mandatory.
5. In the **Value** tab configure the behavior of payment method related transactions by activating the desired sliders and completing the following fields:

| Slider/Field                                         | Description                                                                                                                    |
|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| Save record of bank documents                       | This allows to save information about bank type values.                                                                        |
| Save record of cash transactions                    | This allows the user to save information about the movements of cash type values.                                              |
| Save record of withholding taxes performed          | This to save information about withholding taxes performed values.                                                             |
| Save record of withholding taxes suffered           | This allows to save information about withholding taxes suffered values.                                                       |
| Save record of other movements                      | This allows to save information about others value types.                                                                      |
| Update “Status” field for checks in possession      | This enables the use of states for payment methods documents: Third-party checks.                                              |
| Update “Reason” status for conciliated transactions | This allows the use of the reason selected in the following field in bank reconciliations.                                     |
| Reason code for Conciliated Status                  | In this field you can select one of the reasons configured in the Master of Financial Reasons for the Bank account type lines. |
| Remove IBAN field validation                        | This allows to disable the native validation of the IBAN field in the bank account master.                                     |
| Show payment transactions                           | This allows to hide value documents while settling transactions.                                                               |
6. In the **Dimension allocations** enable the addition of third-party information as a dimension in transactions.
Complete the following fields/enable the following sliders:

| Slider/Field                                                  | Description                                                                                                                                                                              |
|---------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enable value creation in third-party dimension                | This slider automatically creates as a third-party dimension code of the country tax ID number of the client or vendor assigned in a transaction.                                        |
| Name                                                          | In this field you must select the dimension used to replicate the third-party country tax ID number.                                                                                     |
| Enable allocation of third-party dimension in customer/vendor | When the vendor/customer LATAM information is completed, the country tax ID number will be assigned in the chosen third-party dimension.                                                 |
| Inherit dimension to journal lines                            | This slider replicates the third-party dimension information of the client/vendor in the voucher header on the other lines of the journal, including values (as long as they are empty). |
7. Complete the fields in the **Concepts and Notes** tab with the labels needed in the following master records: vendors, legal entities, bank groups, contacts, and employees.

