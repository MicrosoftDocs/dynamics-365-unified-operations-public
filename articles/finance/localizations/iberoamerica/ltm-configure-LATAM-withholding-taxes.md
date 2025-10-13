---
title: Configure LATAM Withholding taxes for payments
description: Learn how to configure the LATAM Withholding taxes to apply to vendor payments.
author: Fhernandez0088
ms.date: 10/07/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---


# Configure LATAM Withholding taxes for payments

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and use the Latin American (LATAM) withholding functionality in Dynamics 365 Finance to support scenarios where tax withholdings are calculated at the time of vendor payments.

## Prerequisites

Before you start the LATAM Withholding tax engine configuration, meet the following prerequisites:

- The legal entity's address is in a country/region from the LATAM Globalization expansion.
- Enable both the general LATAM feature and the country/region-specific LATAM feature for the country/region selected in the legal entity address.
- Configure document classes as invoices. Learn more in [Document classes for Latin America](ltm-core-document-class.md).
- Configure sales tax codes. 
- Configure the LATAM section of vendors.

## Configure the LATAM withholding tax engine

To configure the LATAM withholding taxes for vendor payments follow these steps.

1. Enable withholding tax LATAM features and configurations.
1. Configure withholding documents.
1. Configure the payment order document.
1. Configure a vendor payment journal.
1. Configure a set of taxes.
1. Configure withholding tax codes.
1. Configure a withholding tax group.

### Enable withholding tax LATAM features and configurations

Go to **Tax** > **Setup** > **Parameters** > **General ledger parameters**.
In the **Withholding tax** tab, enable the **LATAM Withholdings** slider.

### Configure withholding documents

This section explains all the configurations needed to set up document classes used as withholdings taxes.

#### Configure the document class type

To configure the document class type, follow these steps.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class type** and create a document class type **Withholding**.
1. In the **Payment media** section, select **Yes** in the payment media field.

#### Configure the document class

To configure the document class, follow these steps.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and create a document class as a payment method **Withholding**, for example **Retencion IVA**.
1. In the **Payment media type** section of the **Document class**, select **Calculated withholdings**.
1. In the **Bank account** section of the **Document class**, select a bank account. Create a bank account to help you with withholdings reconciliation.
1. In the **journal name** section of the **Document class**, select a journal, for example **vendor payment journal**.
1. In the **Additional data** section of the **Document class**, you can enable the **Taxable amount**, **Effective tax rate**, and other fields to be shown in the withholding tax transaction.
1. In the **Document mask** section of the **Document class**, you can configure the structure of withholding certificate number (manual or automatic).

### Configure the payment order document

This section explains how to set up document classes as payment orders used in vendor payment journals.

#### Configure the document class type

To configure the document class type, follow these steps.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class type** and create a document class type **payment order**.
1. In the **journal** section, select the appropriate option for this document.

#### Configure the document class

To configure the document class, follow these steps.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and create a document class to be used as a payment order in the vendor type line of the payment journal.
1. In the payment order **Document class**, enable the **Apply withholding calculation** slider. This configuration is important for withholding tax calculation at the moment of the vendor payment.
1. In the **journal name** section of the **Document class**, select a journal, for example **vendor payment journal**. 
1. In the **Document mask** section of the **Document class**, you can configure payment order number (manual or automatic).  

### Configure a vendor payment journal

To configure a vendor payment journal, go to **General ledger** > **Journal setup** > **Journal names** and in the **LATAM** section, enable the **Calculated withholdings** and **Bank** types.

### Configure a set of taxes

To configure a set of taxes, follow these steps.

1. Go to **Tax** > **Indirect taxes** > **LATAM** > **Set of taxes**, create a new record, and enter an ID and a name.
1. In the **Tax detail** section, add the tax codes that you use for defining and calculating the withholding tax base amount.

### Configure withholding tax codes

To configure withholding tax codes, follow these steps.

1.  Go to **Tax** > **Indirect taxes** > **Withholding tax** > **Withholding tax codes** and create a new record. Enter a new code and a new name for the record.
1. Add a **Document class ID** configured as a **Calculated withholding**.

   > [!NOTE]
   > The ID you enter for the Withholding tax code must match the Document class ID you select.

1. In the **Calculation basis** section, configure the following fields:

   |        Field       |                                   Description                                  |
   |:------------------:|:------------------------------------------------------------------------------:|
   |         +/-        | Select if this set of taxes increases or decreases the taxable base amount. |
   | Type of the amount | Select what part of the invoice total is the taxable base amount.  |
   | Set of taxes ID    | Select a set of taxes that are considered for the taxable base amount.     |

1. In the **Calculation accumulated base** section, configure the following fields when the accumulated calculation is enabled:

   |        Field       |                                   Description                                  |
   |:------------------:|:------------------------------------------------------------------------------:|
   |         +/-        | Select if this set of taxes increases or decreases the taxable base amount. |
   | Type of the amount | Select what part of the invoice total is the taxable base amount.  |
   | Set of taxes ID    | Select a set of taxes that are considered for the taxable base amount.     |

1. In the **Calculation method** section, configure the following fields:

   |                        Field                        |                                                                Description                                                                |
   |:---------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------:|
   | Calculated on first payment                        |                            Enable this option if the total withholding must be calculated on the first payment.                            |
   | Calculated over                                     | Select if one withholding is calculated per invoice paid in the journal or one withholding is calculated for all the invoices in payment. |
   | Subtract minimum subject amount                     | Enable this to subtract an amount before calculating the withholding tax.                                                                  |
   | Minimum subject amount                              | Set the minimum amount to subtract.                                                                                                  |
   | Minimum Withholding                                 | Set the minimum withholding tax that must be calculated and shown.                                                                    |
   | Calculate Accumulated                               | Select if the accumulated amount comes from the withholding taxable amounts or from the invoice/credit notes amounts.                     |
   | Minimum accumulated amount to calculate withholding | The minimum accumulated amount to start calculating withholding taxes.                                                                    |
   | Number of units                                     | Number of units of time measurement selected as interval of period.                                                                        |
   | Interval of period                                  | Select the measurement of time where the accumulated amount is calculated.                                                          |

1. In the **Values** section, configure scales that affect how the withholding taxes are calculated:
     |     Field    |                                                                         Description                                                                         |
   |:------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------:|
   | From date    | Set the starting date of the withholding tax validity.                                                                                                      |
   | To date      | Set the ending date of the withholding tax validity.                                                                                                        |
   | From Amount  | Set the taxable amount from which the percentage configured is calculated.                                                                             |
   | To Amount    | Set the taxable amount to which the percentage configured is calculated.                                                                               |
   | Fixed Amount | Set the amount that is deducted from each line of the scale. The withholding is calculated on the excess between the base amount and this amount. |
   | Percentage   | Set the withholding tax rate.                                                                                                                               |
   | Over amount  | Set the minimum amount to be calculated. It is deducted from the base amount.                                                                          |

1. In the **Document class** section, determine the document classes on which withholding taxes are calculated. Add the document classes that calculate withholding taxes. If you don't list a document class here, it isn't included in the calculation.

### Configure a withholding tax group

The **Withholding tax group** defines the withholding tax codes that the system calculates in a vendor transaction.

To configure a withholding tax group, follow these steps.

1. Go to **Tax** > **Indirect taxes** > **Withholding tax** > **Withholding tax groups** and create a new record. Enter a group ID and a description. 
1. In the **Configuring** section, add the withholding tax codes for the group.
1. In the LATAM section, enter the role, country/region, state, and taxpayer type that the group applies to.
1. Go to **Accounts payable** > **Vendors** > **All vendors** and assign a group in the **Withholding tax group** field from the **Invoice and delivery** section. This step sets the withholding tax group for each vendor transaction.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
