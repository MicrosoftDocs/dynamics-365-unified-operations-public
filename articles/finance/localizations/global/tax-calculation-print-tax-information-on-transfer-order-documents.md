---
title: Print tax information on transfer order documents
description: Learn how the tax information that is determined by the tax calculation service can be printed on transfer order documents.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-10-12
ms.custom: 
  - bap-template
---

# Print tax information on transfer order documents

[!include [banner](../../includes/banner.md)]

This article explains how to print tax information on transfer order documents. You can print the pro-forma invoice document of a transfer order for stock transfers that are considered intra-community supply and intra-community acquisitions under European Union (EU) value-added tax (VAT) regulations. 

The following tax-relevant data is added to the transfer order documents:

- The names and the ship-from and ship-to addresses for the stock transfer
- The tax identification numbers of the supplier and the recipient
- The unit price and the taxable amount of the supplied goods
- The tax code, tax rate, tax amount, and tax directives

To configure this data, complete the following main steps.

1. [Enable and set up the tax feature for transfer orders](Tax-feature-support-for-transfer-order.md).
1. [Create and set up multiple tax registration numbers for a legal entity](emea-multiple-vat-registration-numbers.md).
1. Set up the exempt code, description, tax directives, and print code in tax codes. For this example, create and synchronize three tax codes in Microsoft Dynamics 365 Finance: **NL-Exempt**, **BE-RC-21**, and **BE-RC+21**.

    1. In Finance, go to **Tax** > **Setup** > **Sales tax** > **Sales tax exempt codes**.
    1. Select **Edit**, and enter a description for the **EC** exempt code. For example, enter **Tax-free EC shipments with tax registration number**.
    1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
    1. Select the **BE-RC-21** tax code, and then select **Tax directives**.
    1. Select **New**.
    1. In the **Language** field, select **EN-US**. Then, in the **Text** field, enter **Document laying down the transfer of goods in the sense of article 138. 2. c) of EU VAT Directive 2006/112/EC**.
    1. Close the page.
    1. On the **General** tab, in the **Print** field, select **Sales tax rate**.
    1. Select the **NL-Exempt** tax code, and then, on the **General** tab, in the **Print** field, select **Sales tax rate**.

    > [!NOTE] 
    > The tax code, tax rate, and tax-exempt description don't print on transfer order documents if you don't maintain an exempt code description or tax directives for the tax code.

## Print the transfer order - shipment document

After you ship a transfer, follow these steps to print the transfer order - shipment document.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Shipment**.
1. On the **Parameters** tab, in the **Print** group, select **Tax information**.
1. On **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
1. Select **OK** to print the transfer order - shipment document.

## Print the transfer order - receipt document

After you receive a transfer, follow these steps to print the transfer order - receipt document.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Receive**.
1. On the **Parameters** tab, in the **Print** group, select **Tax information**.
1. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
1. Select **OK** to print the transfer order - receipt document.

## Print the transfer overview document

Follow these steps to print the transfer overview document.

> [!NOTE]
> Tax information is available only when the transfer order is shipped or received.

1. Go to **Inventory management** > **Inquiries and reports** > **Transfer orders** > **Transfer overview**.
1. On the **Parameters** tab, in the **Print** group, select **Tax information**.
1. On the **Records to include** tab, select **Filter**, select the transfer order number, and then select **OK**.
1. Select **OK** to print the transfer overview document.

[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
