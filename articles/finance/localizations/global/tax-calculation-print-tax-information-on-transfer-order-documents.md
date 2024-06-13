---
title: Print tax information on transfer order documents
description: Learn how the tax information that is determined by the tax calculation service can be printed on transfer order documents.
author: Kai-Cloud
ms.author: kailiang
ms.topic: article
ms.date: 10/15/2021
ms.custom: 
ms.reviewer: johnmichalak
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2021-10-12
ms.search.form:
ms.dyn365.ops.version: 10.0.23
---

# Print tax information on transfer order documents

[!include [banner](../../includes/banner.md)]

This article explains how to print tax information on transfer order documents. You can print the pro-forma invoice document of a transfer order for stock transfers that are considered intra-community supply and intra-community acquisitions under European Union (EU) value-added tax (VAT) regulations. 

The following tax-relevant data is added to the transfer order documents:

- The names and the ship-from and ship-to addresses for the stock transfer
- The tax identification numbers of the supplier and the recipient
- The unit price and the taxable amount of the supplied goods
- The tax code, tax rate, tax amount, and tax directives

To configure this data, you must complete the following main steps.

1. [Enable and set up the tax feature for transfer orders](Tax-feature-support-for-transfer-order.md).
2. [Create and set up multiple tax registration numbers for a legal entity](emea-multiple-vat-registration-numbers.md).
3. Set up the exempt code, description, tax directives, and print code in tax codes. For this example, three tax codes are created and synchronized in Microsoft Dynamics 365 Finance: **NL-Exempt**, **BE-RC-21**, and **BE-RC+21**.

    1. In Finance, go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**.
    2. Select **Edit**, and enter a description for the **EC** exempt code. For example, enter **Tax-free EC shipments with tax registration number**.
    3. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
    4. Select the **BE-RC-21** tax code, and then select **Tax directives**.
    5. Select **New**.
    6. In the **Language** field, select **EN-US**. Then, in the **Text** field, enter **Document laying down the transfer of goods in the sense of article 138. 2. c) of EU VAT Directive 2006/112/EC**.
    7. Close the page.
    8. On the **General** FastTab, in the **Print** field, select **Sales tax rate**.
    8. Select the **NL-Exempt** tax code, and then, on the **General** FastTab, in the **Print** field, select **Sales tax rate**.

    > [!NOTE] 
    > The tax code, tax rate, and tax-exempt description aren't printed on transfer order documents if no exempt code description or tax directives are maintained for the tax code.

## Print the transfer order - shipment document

After a transfer is shipped, follow these steps to print the transfer order - shipment document.

1. Go to **Inventory management** \> **Inquiries and reports** \> **Transfer orders** \> **Shipment**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
4. Select **OK** to print the transfer order - shipment document.

## Print the transfer order - receipt document

After a transfer is received, follow these steps to print the transfer order - receipt document.

1. Go to **Inventory management** \> **Inquiries and reports** \> **Transfer orders** \> **Receive**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
4. Select **OK** to print the transfer order - receipt document.

## Print the transfer overview document

Follow these steps to print the transfer overview document.

> [!NOTE]
> Tax information is available only when the transfer order has been shipped or received.

1. Go to **Inventory management** \> **Inquiries and reports** \> **Transfer orders** \> **Transfer overview**.
2. On the **Parameters** tab, in the **Print** group, enable **Tax information**.
3. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
4. Select **OK** to print the transfer overview document.

[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
