---

# required metadata

title: Fiscal registration service integration sample for Austria
description: This topic provides an overview of the fiscal integration sample for Austria.
author: josaw
manager: annbe
ms.date: 03/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria
ms.search.industry: Retail
ms.author: v-dmpere
ms.search.validFrom: 2019-3-1
ms.dyn365.ops.version: 10.0.1

---

# Fiscal registration service integration sample for Austria

[!include[banner](../includes/banner.md)]

This topic applies to Dynamics 365 for Retail and Dynamics 365 for Finance and Operations. 

The Microsoft Dynamics 365 for Retail functionality for Austria includes a sample of integration of POS with an external fiscal registration service to cover local fiscal requirements to cash registers in Austria. The sample extends the [fiscal integration functionality](fiscal-integration-for-retail-channel.md). It is based on the [EFR (Electronic Fiscal Register)](http://efsta.org/sicherheitsloesungen/) solution from [EFSTA](http://efsta.org/) and enables the communication with the EFR service via the HTTPS protocol. The sample is provided in form of a source code and is a part of the Retail SDK.
Microsoft does not ship any hardware, software or documentation from EFSTA. Please contact [EFSTA](http://efsta.org/kontakt/) for information on how to acquire the EFR solution and operate it.

SAMPLE CODE NOTICE

THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED, OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY. THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.

## Overview

To learn about common POS scenarios and features that are available to customers in all countries or regions, see [Microsoft Dynamics 365 for Retail Documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/index).

### Integration Retail POS with the EFR

Retail includes a sample for integration of POS with Austria-specific certified fiscal registration service. It is assumed that a service is hosted on the mashine inside client's infrastructure and paired with POS Hardware station is able to connect the service via LAN or locally. The sample is implemented as source code of POS, Hardware station, and Commerce runtime extensions, and is available in the Retail software development kit (SDK).


### Austria-specific POS scenarios and features

The following scenarios are covered by the fiscal registration service integration sample for Austria:
   - Registration of cash transactions at the fiscal cash register (EFR):
      - Sending detailed transaction data (sales line information, discounts, payments, taxes) to fiscal register service;
     - Capturing a response from the fiscal register service including a digital sign and link to registered transaction;
      - Printing in the receipt tax group data and reference to registered transaction in fiscal register software as a QR-code
  - Registration of deposits at the fiscal cash register (EFR) as a non-cash transactions:
      - Issue a Gift card;
      - Recording of Customer account’s deposit;
      - Registration of Sales order’s deposit
  - Registration of some POS-related events or transactions at the fiscal cash register (EFR) as a non-cash transactions
      - POS log on/log off;
      - Shift open/close;
      - Start amount / Float entry / Tender removal;
      - Void transaction;
      - Void transaction line;
      - Price override;
      - Tax override;
      - Print copy of receipt;
      - Open drawer;
      - Print X report;
      - Print Z report
  - End of day statements (fiscal X, fiscal Z reports) enhancement by Austria-specific fields  
      - Number of total sold items, products or services delivered to customers;
      - Sales broken down by tax rates;
      - Breakdown of proceeds by cashier/cash register operator;
      - Post-voids postings performed, price discounts, returns, negative sales, by which daily sales are reduced;
      - Zero sales (giveaways).
  - Error handling including following options:
      - Retry fiscal registration if it's possible; for example, if the fiscal registration service is unavailable.
      - Skip fiscal registration, including info codes to capture the reason of failure and additional information.
      - Fiscal registration service health-check before posting transaction data into Dynamics 365 HQ.

## Setting up Retail for Austria

This section describes the Retail settings that are specific to and recommended for Austria. For more information about how to set up Retail, see [Microsoft Dynamics 365 for Retail documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/index).

To use the Austria-specific functionality for Retail, you must complete these tasks:
- Set the **Country/region** field to AUT (Austria) in the primary address of the legal entity.
- Set the **ISO code** field to AT (Austria) in the POS functionality profile of every store that is located in Austria.

Austria-specific settings can be divided into two groups:
- General settings
- EFR–specific settings

### General settings

You must specify the following general settings for Austria:
1. Set up the following parameters for value-added tax (VAT) per Austria requirements:
    - Sales tax codes
    - Sales tax groups
    - Item sales tax groups
    - Sales tax settings in items (item sales tax groups for sales)

For more information about how to set up and use sales tax in Microsoft Dynamics 365 for Finance and Operations and in Retail see [Sales tax overview](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/general-ledger/indirect-taxes-overview).

2. On the **All retail stores** page, update retail store details. Specifically, set the following parameters:
    - In the **Sales tax group** field, set the sales tax group that should be used for sales to the default retail customer.
    - Select the **Prices include sales tax** check box.
    - Set the **Store name** field so that it includes the company name. This change helps guarantee that the company name appears on a sales receipt. Alternatively, you can add the company name to the sales receipt layout as free-format text.
    - Set the **Tax identification number (TIN)** field so that it includes the company identification number. This change helps guarantee that the company identification number appears on a sales receipt. Alternatively, you can add the company identification number to the sales receipt layout as free-format text.

3. Set up POS functionality profiles:
    - On the **Receipt numbering** FastTab, set up receipt numbering. 
    - Create or update records for the **Sale**, **Sales order** and **Return** receipt transaction types.

4. Make the required changes to **Receipt formats**:
    - Change the value of the **Print behavior** field to **Always print** for the receipt format.
    - In the Receipt format designer, make these changes:
        - Add at least the following fields to the **Header** section of the receipt layout:
            - **Store name** and **Tax Identification Number** fields, so that the company name and identity number are printed receipts. Alternatively, you can add the company name and identity number to the layout as free-format text.
            - **Store address**, **Date**, **Time 24H**, **Receipt Number**, and **Register number** fields.
    - Add at least the following field to the **Lines** section of the receipt layout: **Item name**, **Qty**, **Total price with tax**.
    - Add at least the following fields to the **Footer** section of the receipt layout:
        - Tax fields, so that the receipt tax amounts for each tax rate are printed. For example, add the **Tax Id**, **Tax percentage**, and **Tax amounts** fields to one line of the layout.
        - Payment fields, so that the payment amounts for each payment method are printed. For example, add the **Tender name** and **Tender amount** fields to one line of the layout.

### EFR–specific settings

1. Cofigure VAT rates mapping.
The **VAT rates mapping** is included in the **Fiscal connector functional profile** provided as part of the fiscal integration sample:

    A: 20.00; B: 10.00; C: 13.00; D: 0.00; E: 19.00; F: 7.00

    Check default mapping rates values and correct it if is is nessesary.

2. Set up tax group code for printing in receipt. 
For printing tax group code in receipt (for example, “A”, “B”) field **Print code** must be filled for sales taxes in **Sales tax codes** form.

3. Configure custom fields so that they can be used in receipt formats for sales receipts
You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the Language text page, add the following records for the labels of the custom fields for receipt layouts. Note that the Language ID, Text ID, and Text values that are shown in the table are just examples. You can change them to meet to your requirements. However, the Text ID values that you use must be unique, and they must be equal to or higher than 900001.

Add the following POS labels to **Language text** from:

| Language ID | Text Id | Text                      |
|-------------|---------|---------------------------|
| en-US       | 103174  | QR Code                   |
| en-US       | 103175  | Continuous Number         |
| en-US       | 103176  | Tax Retail Print Code     |
| en-US       | 103177  | Total (sales)             |
| en-US       | 103178  | Total Tax (sales)         |
| en-US       | 103179  | Total Include Tax (sales) |
| en-US       | 103180  | Tax Amount (sales)        |
| en-US       | 103181  | Tax Basis (sales)         |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                 | Type    | Caption text Id |
|----------------------|---------|-----------------|
| QRCODE               | Receipt | 103174          |
| CONTINUOUSNUMBER     | Receipt | 103175          |
| RETAILPRINTCODE      | Receipt | 103176          |
| SALESTOTAL           | Receipt | 103177          |
| SALESTOTALTAX        | Receipt | 103178          |
| SALESTOTALINCLUDETAX | Receipt | 103179          |
| SALESTAXAMOUNT       | Receipt | 103180          |
| SALESTAXBASIS        | Receipt | 103181          |

4. Configure receipt formats
In the **Receipt format designer**, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.
   **Header**: Add the following field:
      Continuous Number – This field identifies the number of cash transaction in the fiscal registrator;
   **Lines**:
      Tax Retail Print Code - This field dysplay the code corresponding to tax group 
   **Footer**: Add the following field groups:
      **Sales total**: 
      	Total (sales) - total transaction amount without tax sum;
	Total Include Tax (sales) - total transaction amount with tax sum;
        Total Tax (sales) - transaction tax sum.

      **Tax break down** (should be separate line):
	Tax Basis (sales) - total cash transaction amount (without taxes) excluding deposits, prepayments and gift cards;
	Tax Amount (sales) - total tax amount for cash transactions excluding deposits, prepayments and gift cards;
	Total Include Tax (sales) - total cash transaction amount (with taxes) excluding deposits, prepayments and gift cards;
	Tax Retail Print Code - the code corresponding to tax group.
				
      **QR Code**: 
         QR Code - reference to registered cash transaction in the form of QR-code.
      
5. Update POS permissions groups and individual permission settings for store workers. To allow workers who are assigned to the permission group to skip the fiscal registration, select the Allow skip fiscal registration check box.

### Handling gift cards
The fiscal registration service integration sample implements the following rules in regard to gift cards:
  - Exclude sales lines related to the operations Issue gift card or Add to gift card from the cash transaction registration message, these operations are registered by separate message as a non-cash operation.
  - Do not print a tax group breakdown and a QR-code in a receipt if it consists of gift card lines only.
  - Total amount of gift cards issued or re-charged and a cash transaction amount are printed in the receipt separately.
  - Payment by gift card is considered as a regular payment.

### Handling customer deposits and customer order deposits
The fiscal registration service integration sample implements the following rules in regard to customer account deposits and customer order deposits:
  - Non-cash transaction is registered if a POS transaction is a customer deposit.
  - Non-cash transaction is registered if a POS transaction contains a sales order deposit or a sales order deposit refund only.
  - Print the amount of the previously paid deposit in a fiscal receipt for a customer order pickup operation.
  - Deduct the customer order deposit amount from payment lines when a hybrid customer order is created.
  - Save calculated adjustments of payment lines in the Channel DB with a reference to a fiscal transaction for a hybrid sales order.
