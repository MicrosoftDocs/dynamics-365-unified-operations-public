---
title: Configure LATAM Withholding taxes for payments
description: Learn how to configure the LATAM Withholding taxes to apply to vendor payments.
author: Fhernandez0088
ms.date: 10/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---


# Configure LATAM Withholding taxes for payments

This article describes how to configure and use the Latin American (LATAM) withholding functionality in Dynamics 365 Finance to support scenarios where tax withholdings must be calculated at the time of vendor payments.

## Prerequisites

Before you start the LATAM Withholding tax engine configuration, the following prerequisites must be met:

- The legal entity's address must be in a country from the LATAM Globalization expansion.
- You must enable both the general LATAM feature and the country/region-specific LATAM feature for the country selected in the legal entity address.
- You must have document classes configured as invoices. Learn more in [Document classes for Latin America](ltm-core-document-class.md).
- You must have sales tax codes configured. 
- You must have the LATAM section of vendors configured.

## LATAM Withholding tax engine configurations

### Enable withholding tax LATAM feature/configurations

Go to **Tax > Setup > Parameters > General ledger parameters**.
In the **Withholding tax** tab enables the **LATAM Withholdings** slider.

### Withholding document configuration

#### Document class type

1. Go to **Organization administration > Setup > LATAM > Document class type** and create a document class type ** Withholding**.
2. In the **Payment media** section select yes in payment media field

#### Document class

1.  Go to **Organization administration > Setup > LATAM > Document class** and create a document class as a payment method ** Withholding**, for example **Retencion IVA**
1.  In the **Payment media type** section of the **Document class** select **Calculated withholdings**.
1.  In the **Bank account** section of the **Document class** select a bank account. You must create a bank account to help you with withholdings reconciliation.
1. In the **journal name** section of the **Document class** select a journal, for example **vendor payment journal**. 
1. In the **Additional data** section of the **Document class** you can enable the **Taxable amount**, **Effective tax rate** and other fields to be shown in the withholding tax transaction.
1. In the **Document mask** section of the **Document class** you can configure the structure of withholding certificate number (manual or automatic) .

### Payment order document configuration

#### Document class type

1. Go to **Organization administration > Setup > LATAM > Document class type** and create a document class type ** payment order**.
2. In the **journal** section select the appropriate option for this document.

#### Document class

1. Go to **Organization administration > Setup > LATAM > Document class** and create a document class to be used as a payment order in the vendor type line of the payment journal.
2. In the payment order **Document class** enable the **Apply withholding calculation** slider. This configuration is important for withholding tax calculation at the moment of the vendor payment.
3. In the **journal name** section of the **Document class** select a journal, for example **vendor payment journal**. 
4. In the **Document mask** section of the **Document class** you can configure payment order number (manual or automatic)  

### Vendor payment journal configuration

Go to **General ledger > Journal setup > Journal names** and in the **LATAM** section enable the **Calculated withholdings** and **Bank** types.

### Set of taxes configuration

1. Go to **Tax > Indirect taxes > LATAM > Set of taxes** create a new record and enter an ID and a name.
1.  In the **Tax detail** section add the tax codes that will be used for defining and calculating the withholding tax base amount.

### Withholding tax codes configuration

1.  Go to **Tax > Indirect taxes > Withholding tax > Withholding tax codes** and create a new record and enter a new code and a new name for the record.
1. Add a **Document class id** configured as a **Calculated withholding**.

   > [!NOTE]
   > The Id entered for the Withholding tax code must be the same as the Document class Id selected.

1. In the **Calculation basis** section configure the following:

   |        Field       |                                   Description                                  |
   |:------------------:|:------------------------------------------------------------------------------:|
   |         +/-        | Select if this set of taxes will increase or decrease the taxable base amount. |
   | Type of the amount | Select what part of the invoice total will be considered taxable base amount.  |
   | Set of taxes id    | Select a set of taxes that will be considered for the taxable base amount.     |

1. In the **Calculation accumulated base** section configure the following when the accumulated calculation es enabled:

   |        Field       |                                   Description                                  |
   |:------------------:|:------------------------------------------------------------------------------:|
   |         +/-        | Select if this set of taxes will increase or decrease the taxable base amount. |
   | Type of the amount | Select what part of the invoice total will be considered taxable base amount.  |
   | Set of taxes id    | Select a set of taxes that will be considered for the taxable base amount.     |

1. In the **Calculation method** section configure the following:

   |                        Field                        |                                                                Description                                                                |
   |:---------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------:|
   | Calculated on first payment                        |                            Enable this option if the total withholding must be calculate on the first payment.                            |
   | Calculated over                                     | Select if one withholding is calculated per invoice paid in the journal or one withholding is calculated for all the invoices in payment. |
   | Subtract minimum subject amount                     | Enable this to subtract an mount before calculating the withholding tax.                                                                  |
   | Minimum subject amount                              | Set the minimum amount to be subtracted.                                                                                                  |
   | Minimum Withholding                                 | Set the minimum withholding tax that has to be calculated to be shown.                                                                    |
   | Calculate Accumulated                               | Select if the accumulated amount comes from the withholding taxable amounts or from the invoice/credit notes amounts.                     |
   | Minimum accumulated amount to calculate withholding | The minimum accumulated amount to start calculating withholding taxes.                                                                    |
   | Number of units                                     | Number of units of time measurement selected as interval of period.                                                                        |
   | Interval of period                                  | Select the measurement of time where the accumulated amount will be calculated.                                                          |

1. In the **Values** section you can configure scales that affect how the withholding taxes are calculated:
     |     Field    |                                                                         Description                                                                         |
   |:------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------:|
   | From date    | Set the starting date of the withholding tax validity.                                                                                                      |
   | To date      | Set the ending date of the withholding tax validity.                                                                                                        |
   | From Amount  | Set the taxable amount from which the percentage configured will be calculated.                                                                             |
   | To Amount    | Set the taxable amount to which the percentage configured will be calculated.                                                                               |
   | Fixed Amount | Set the amount that will be deducted from each line of the scale. The withholding will be calculated on the excess between the base amount and this amount. |
   | Percentage   | Set the withholding tax rate.                                                                                                                               |
   | Over amount  | Set the minimum amount to be calculated. It will be deducted from the base amount.                                                                          |

1. The **Document class** section will allow you to determine the document classes on which withholding taxes will be calculated. Make sure you add the document classes that should calculate withholding taxes on. Those not listed here will not be included in the calculation.

### Withholding tax group configuration

The **Withholding tax group** will define the withholding tax codes that will be calculated in a determined vendor transaction.

1. Go to **Tax > Indirect taxes > Withholding tax > Withholding tax groups** and create a new record, enter a group ID and a description. 
1. In the **Configuring** section add the withholding tax codes for the group.
1. In the LATAM section enter the role, country/region, state and taxpayer type that the group will apply.
1. Go to **Accounts payable > Vendors > All vendors** and assign a group in the **Withholding tax group** field from the **Invoice and delivery** section (this will predetermine the withholding tax group for each vendor transaction).
