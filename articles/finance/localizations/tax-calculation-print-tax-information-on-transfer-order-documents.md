---
# required metadata

title: Print tax information on transfer order documents
description: This topic explains how the tax information determined by the tax calculation service is printed on transfer order documents.
author: Kai-Cloud
ms.date: 10/15/2021
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
[!include [banner](../../includes/preview-banner.md)]

This topic exlains how to print tax information on transfer order documents. You can print the proforma invoice document of a transfer order for stock transfers which are considered intra-community supply and intra-community acquisitions under European Union (EU) value-added tax (VAT) regulations. 

The following tax relevant data is added to the transfer order documents.

- The names and the ship-from and ship-to addresses for the stock transfer.
- The tax identification numbers of the supplier and the recipient.
- The unit price and the taxable amount of the supplied goods.
- The tax code/rate, tax amount, and tax directives.

To configure these data, you must complete the following main steps:

1. [Enable and set up the tax feature for transfer orders](Tax-feature-support-for-transfer-order.md).
2. [Create and set up multiple tax registration numbers for a legal entity](emea-multiple-vat-registration-numbers.md).
3. Set up the exempt code, description, tax directives, and print code in tax codes. For this example, three tax codes are created and synchronized in Microsoft Dynamics 365 Finance: **NL-Exempt**, **BE-RC-21**, and **BE-RC+21**.

   1. In Finance, go to **Tax** > **Setup** > **Sales tax** > **Sales tax exempt codes**.
   2. Select **Edit**, and enter a description for the **EC** exempt code. For example, Tax-free EC shipments with tax registration number.
   3. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
   4. Select the tax code, **BE-RC-21** and then select **Tax directives**.
   5. Select **New**.
   6. In the **Language** field, select **EN-US** and in the **Text** field, enter "Document laying down the transfer of goods in the sense of article 138. 2. c) of EU VAT Directive 2006/112/EC".
   7. Close the page, and on the **General** FastTab, in the **Print** field, select **Sales tax rate**.
   8. Select the tax code **NL-Exempt**, and on the **General** FastTab, in the **Print** field, select **Sales tax rate**.

      > [!NOTE] 
      > The tax code, tax rate, and tax exempt description aren't printed on the transfer order documents when there is no exempt code description or tax directives maintained for the tax code.

## Print transfer order - shipment document

After a transfer is shipped, complete the following steps to print the transfer order - shipment document.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Shipment**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On **Records to include** tab, select **Filter**, select the transfer order number and then select **OK**.
4. Select **OK** to print the transfer order - shipment document.


## Print transfer order - receipt document

After a transfer is received, complete the following steps to print the transfer order - receipt document.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Receive**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
4. Select **OK** to print the transfer order - receipt document.


## Print transfer overview document

Follow these steps to print the transfer overview document.

> [!NOTE]
> Tax information is only available when the transfer order has been shipped or received.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Transfer overview**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
4. Select **OK** to print the transfer overview document.

  [!INCLUDE [footer-include](../../../includes/footer-banner.md)]
