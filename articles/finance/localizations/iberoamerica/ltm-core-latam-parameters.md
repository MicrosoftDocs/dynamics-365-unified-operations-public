---
title: Latin America parameters 
description: This article provides information about the parameter configuration for Latin America. 
author: Fhernandez0088
ms.date: 04/28/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 	
ms.custom: bap-template
---

# Latin America parameters

This article provides a description of the Latin America (LATAM) parameter configuration. Use these parameters to incorporate the general parameter setup into the local parameters before you start the corresponding configurations.

## Prerequisites

- The Global LATAM taxes feature must be enabled.
- The company must be in a country/region that supports the LATAM localization.

## Set up previous LATAM configurations

1. Go to **Organization administration > Setup > LATAM > LATAM parameters**.
2. On the **General** tab, enter the character length for the prefix field for **Document class types** and **Document class letters**.
3. On the **Functionalities** tab, activate the following options as required.

    | Option                        | Description |
    |-------------------------------|-------------|
    | Enable sales return account   | Activate the alternative ledger account for return sales orders. |
    | Enable project return account | Activate the alternative ledger account for return project sales. |
    | Enable line control           | If the maximum number of lines on a sales order is exceeded, a warning message should be shown. |

3. In the **Max amount of lines** field, enter the maximum number of lines that are allowed before the warning message is shown.
4. On the **Mandatory document class in journal** tab, activate the options for each group as required. When you activate an option, the **Document class** field in the LATAM extended information from journal entries becomes mandatory.
5. On the **Value** tab, update the following fields to configure how payment methods behave with transactions.

    | Field                                               | Description |
    |-----------------------------------------------------|-------------|
    | Save record of bank documents                       | Save information about bank type values. |
    | Save record of cash transactions                    | Save information about movements of cash type values. |
    | Save record of withholding taxes performed          | Save information about the values of withholding taxes that are performed. |
    | Save record of withholding taxes suffered           | Save information about the values of withholding taxes that are suffered. |
    | Save record of other movements                      | Save information about others value types. |
    | Update "Status" field for checks in possession      | Use different statuses for payment method documents, including third-party checks. |
    | Update "Reason" status for conciliated transactions | Use the reason that's selected in the **Reason code for Conciliated Status** field in bank reconciliations. |
    | Reason code for Conciliated Status                  | Select a reason that's configured in **Master of Financial Reasons** for the lines of the **Bank account** type. |
    | Remove IBAN field validation                        | Don't use the native validation of the **IBAN** field in the bank account master. |
    | Show payment transactions                           | Hide value documents while transactions are settled. |

6. On the **Dimension allocations** tab, enable the addition of third-party information as a dimension in transactions.

    | Field                                                         | Description |
    |---------------------------------------------------------------|-------------|
    | Enable value creation in third-party dimension                | Automatically create a third-party dimension code of the country/region tax ID number for the client or vendor that's assigned in a transaction. |
    | Name                                                          | Select the dimension that's used to replicate the third-party country/region tax ID number. |
    | Enable allocation of third-party dimension in customer/vendor | When the vendor or customer LATAM information is completed, the country/region tax ID number is assigned in the selected third-party dimension. |
    | Inherit dimension to journal lines                            | Replicate the third-party dimension information of the client or vendor on the voucher header on the other lines of the journal. Include values, if they're blank. |

7. On the **Concepts and Notes** tab, enter information together with the labels that are required in the following master records: vendors, legal entities, bank groups, contacts, and employees.
