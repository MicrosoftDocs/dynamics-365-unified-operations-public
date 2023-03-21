---
title: Latin America parameters 
description: This article provides information about the parameter configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/20/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 	
ms.custom: bap-template
---

# Lating America parameters

This article provides a description of the Latin America (LATAM) parameters configuration. Use these parameters to incorporate the general parameters setup with the local parameters before you start with the respective configurations.

## Prerequisites

- Global LATAM taxes feature must be enabled.
- The company must be in a country that supports the LATAM localization.

## Set up previous LATAM configurations

1. On the **General** tab enter the character length for the prefix field for **Document class types** and **Document class letters**.
2. In the **Functionalities** tab activate the sliders as needed:

    | Slider                        | Description                                                                            |
    |-------------------------------|----------------------------------------------------------------------------------------|
    | Enable sales return account   | Activate the alternative ledger account for return sales orders.                       |
    | Enable project return account | Activate the alternative ledger account for return project sales.                      |
    | Enable line control           | When the maximum number of lines on a sales order has been exceeded, a warning will occur. |
    
3. In the **Max amount of lines** field, enter the maximum number of lines allowed before the warning message occurs.
4. On the **Mandatory document class in journal** tab, activate the sliders for each group as needed. Activating a slider will make the field **Document class** in the LATAM extended information from journal entries mandatory.
5. On the **Value** tab, update the following sliders and fields to configure how payment methods behaviour with transactions.

    | Slider/Field           | Description                |
    |------------------------|----------------------------|
    | Save record of bank documents                       | Save information about bank type values.      |
    | Save record of cash transactions                    | Save information about the movements of cash type values.    |
    | Save record of withholding taxes performed          | Save information about the performed values of withholding taxes.   |
    | Save record of withholding taxes suffered           | Save information about withholding taxes suffered values.   |
    | Save record of other movements                      | Save information about others value types.      |
    | Update “Status” field for checks in possession      | Use different statuses for payment method documents including third-party checks.    |
    | Update “Reason” status for conciliated transactions | Use the reason selected in the **Reason code for Conciliated Status** field in bank reconciliations.   |
    | Reason code for Conciliated Status                  | Select a reason configured in the **Master of Financial Reasons** for the Bank account type lines. |
    | Remove IBAN field validation                        | Select to not use the native validation of the IBAN field in the bank account master.     |
    | Show payment transactions                           | Hide value documents while settling transactions.    |

6. On the **Dimension allocations** tab, enable the addition of third-party information as a dimension in transactions.

    | Slider/Field                            | Description              |
    |-----------------------------------------|--------------------------|
    | Enable value creation in third-party dimension     | Automatically create a third-party dimension code of the country tax ID number for the client or vendor assigned in a transaction.   |
    | Name              | Select the dimension used to replicate the third-party country tax ID number.     |
    | Enable allocation of third-party dimension in customer/vendor | When the vendor/customer LATAM information is completed, the country tax ID number is assigned in the chosen third-party dimension.      |
    | Inherit dimension to journal lines     | Replicate the third-party dimension information of the client or vendor in the voucher header on the other lines of the journal, including values, as long as they are empty. |

7. Enter information on the **Concepts and Notes** tab with the labels needed in the following master records: vendors, legal entities, bank groups, contacts, and employees.
