---
# required metadata

title: Print tax information on transfer order documents
description: This topic explains how the tax information determined by the tax calculation service is printed on the transfer order documents.
author: Kai-Cloud
ms.date: 10/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-10-12
ms.dyn365.ops.version: 10.0.23
---

# Print tax information on transfer order documents

[!include [banner](../../includes/banner.md)]

This topic provides information about printing the tax information on transfer order documents. This functionality lets you print the proforma invoice document of the transfer order for stock transfers which are considered intra-community supply and intra-community acquisitions under European Union (EU) value-added tax (VAT) regulations. 

The following tax relevant data are added to the transfer order documents.

- The names and the ship-from, ship-to addresses for the stock transfer.
- The tax identification numbers of the supplier and the recipient.
- The unit price and the taxable amount of the supplied goods.
- The tax code/rate, tax amount and tax directives.

To configure these data, you must complete the following main steps:

1. [Enable and set up the tax feature for transfer orders](Tax-feature-support-for-transfer-order.md).

2. [Create and set up multiple tax registration numbers for a legal entity](emea-multiple-vat-registration-numbers.md).

3. Set up exempt code, description, tax directives and print code in tax codes. For this example, three tax codes are created and synchronized in Microsoft Dynamics 365 Finance: **NL-Exempt**, **BE-RC-21**, and **BE-RC+21**.

   1. In Finance, go to **Tax > Setup > Sales tax > Sales tax exempt codes**.

   2. Click Edit, Input the description for the "EC" exempt code. For example: "Tax-free EC shipments with tax registration number".

   3. In Finance, go to **Tax > Indirect taxes > Sales tax > Sales tax codes**.

   4. Select tax code **BE-RC-21**, on the header menu click **Tax directives**.

   5. Click **New**, select **Language** and input **Text** for the tax directives. For example: "en-us" and "Document laying down the transfer of goods in the sense of article 138. 2. c) of EU VAT Directive 2006/112/EC".

   6. Close page, in the **General** FastTab, in the **Print** option, select "Sales tax rate".

   7. Select tax code **NL-Exempt**, in the **General** FastTab, in the **Print** option, select "Sales tax rate".

      > [!Note] 
      >
      > The tax code, tax rate and tax exempt description will not be printed on the transfer order documents when there is no exempt code description or tax directives maintained for the tax code.

## Print transfer order - shipment document

After shipped a transfer, follow these steps to print the transfer order - shipment document.

1. In Finance, go to **Inventory management > Inquiries and reports > Transfer orders > Shipment**.
2. In **Parameters**, under **Print**, switch on option **Tax information**.
3. In **Records to include**, click **Filter**, select the transfer order number, click **OK**.
4. Click **OK** to print the transfer order - shipment document.


## Print transfer order - receipt document

After received a transfer, follow these steps to print the transfer order - receipt document.

1. In Finance, go to **Inventory management > Inquiries and reports > Transfer orders > Receive**.
2. In **Parameters**, under **Print**, switch on option **Tax information**.
3. In **Records to include**, click **Filter**, select the transfer order number, click **OK**.
4. Click **OK** to print the transfer order - receipt document.


## Print transfer overview document

Follow these steps to print the transfer overview document.

> [!Note]
>
> Tax information is only available when the transfer order has been shipped or received.

1. In Finance, go to **Inventory management > Inquiries and reports > Transfer orders > Transfer overview**.
2. In **Parameters**, under **Print**, switch on option **Tax information**.
3. In **Records to include**, click **Filter**, select the transfer order number, click **OK**.
4. Click **OK** to print the transfer overview document.

  [!INCLUDE [footer-include](../../../includes/footer-banner.md)]