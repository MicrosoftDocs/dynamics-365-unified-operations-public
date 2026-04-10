---
title: Returnable packaging for Poland
description: Learn how to set up and use returnable packaging for Poland in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: PlCustPackageHolder, PlCustPackageReturn, PlInventPackageTable, PlInventPackageTrans
ms.assetid: decdb3af-9fc3-4aff-add1-bbb9d2eadc27
---

# Returnable packaging for Poland

[!include [banner](../../includes/banner.md)]

This article explains how to set up and use returnable packaging for Poland in Microsoft Dynamics 365 Finance.

The functionality for returnable packaging lets you handle the registration of packages that customers can return. Users can define packaging codes and specify the amount of the deposit that a customer pays for returned packaging materials. This functionality is an extension of the standard functionality for packaging materials.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category                | Prerequisite |
|-------------------------|--------------|
| **Setup:** Legal entity | The primary address of the legal entity must be in Poland. On the **Legal entities** page (**Organization administration** \> **Organizations** \> **Legal entities**), select your legal entity. Then, on the **Addresses** FastTab, create a new address or update an existing address, select **Poland** as the country/region, enter the other address components, and mark the address as **Primary**. |

## Set up returnable packages

This section describes the various settings that you must configure to use the returnable packages functionality.

### Define packaging codes

On the **Return packages** page (**Inventory management** \> **Setup** \> **Packing material** \> **Return packages**), enter values for the following fields.

| Field               | Description                                                                    |
|---------------------|--------------------------------------------------------------------------------|
| Packaging code      | Enter a unique code for a returned package.                                    |
| Package description | Enter the description of the returned package.                                 |
| Deposit             | Enter the amount of the deposit that a customer pays for the returned package. |

### Attach packaging codes to packing units

Use the **Packaging material allocation** page (**Inventory management** \> **Setup** \> **Packing material** \> **Packaging material allocation**) to attach packaging codes to packing units for all items, for specific items, or for specific packing groups. Only the following field is specific for Poland. It extends the standard functionality of the **Packaging material allocation** page.

| Field          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| Packaging code | Select the code for the package that a customer returns. |

### Set up a number sequence for package vouchers

To set up a number sequence for package vouchers, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Packaging material allocation** FastTab, set up a number sequence for the **Package voucher** reference field.

### Set up a deposit account

When you post the sales invoice, use a special voucher to post the customer's fee for the packaging material. All deposit transactions post to a separate account, which you define in the related customer posting profiles. On the **Customer posting profile** page (**Accounts receivable** \> **Setup** \> **Customer posting profile**), enter a value in the **Deposits** field.

## Register and verify returnable packages

Users can register packages for sales orders, post and print packing slips that include the quantity of issued packages, and post and print customer invoices. Users can also inquire about and verify the quantity of the packaged items for sales orders.

### Register packages in a sales order

To register packages in a sales order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.
1. Create a new sales order or open an existing sales order.
1. Switch to the **Lines** view, and then create a new sales order line or select an existing sales order line.
1. On the **Line details** FastTab, on the **Packing** tab, in the **Packing unit** field, select the packing unit that's attached to the packaging code that you previously defined for return packages. The number of packages that the customer can return is automatically calculated and is shown in the **Packing unit quantity** field.

### Verify packages

To verify packages, follow these steps:

1. On the **Sales order lines** FastTab, select a sales order line.
1. Go to **Financials** \> **Packages** \> **Package issue**. When the page is opened from a sales order line, you can modify or remove the packages that are automatically calculated for that sales order line.
1. Alternatively, on the Action Pane for the **Sales order** page, on the **General** tab, select **Package issue**. When the **Package issue** page is opened by using this method, you can view the packages that are calculated for all sales order lines. You can also add packages if extra packages are required.

### Print and post packing slips

To print and post packing slips, follow these steps:

1. In Dynamics 365 Finance, go to the **Sales order** page.
1. On the Action Pane, on the **Pick and pack** tab, select **Post packing slip**. After packing slips are posted, you can inquire about package issue transactions for each packing slip.
1. Go to **Inventory management** > **Setup** > **Packing materials** > **Return packages**.
1. On the **Transactions** tab, select **Transactions** to open the **Return packages transactions** page.

### Print and post invoices

To print and post invoices, follow these steps:

1. In Dynamics 365 Finance, go to the **Sales order** page.
1. On the action pane, on the **Invoice** tab, select **Generate** > **Invoice**. After you post invoices, you can view package transactions that have posted deposit amounts for each invoice.
1. Go to **Inventory management** > **Setup** > **Packing materials** > **Return packages**.
1. On the **Transactions** tab, select **Transactions** to open the **Return packages transactions** page.
1. Select **Voucher** to open the **Voucher transactions** page.
1. Verify the customer deposit amounts that you post to the main account. You specify the main account number on the **Customer posting profiles** page.
1. To print the **Deposit packages transactions** report, select **Printout**. You can also view return package totals for a selected customer.
1. Go to **Accounts receivable** > **All customers**.
1. On the **Collect** tab, select **Packages at customer** to open the **Return packages transactions** page.

## Post and print packages returns

To enter information about the packages that customers return, select **Accounts receivable** \> **All customers**. On the **Collect** tab, select **Packages return** to open the **Return packages confirmation** page. Enter values in the following fields. **Return packages section**

| Field       | Description                                                                                        |
|-------------|----------------------------------------------------------------------------------------------------|
| Date        | Enter the date of a package return.                                                                |
| Description | Enter the description of a package return.                                                         |
| Posted      | A value that indicates whether the package return was posted. This value updates automatically. |

**Return packages transactions section**

| Field                         | Description                                                                                                                                                          |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Packaging code                | Select a packaging code to return.                                                                                                                                   |
| Return quantity               | Enter the number of packages to return. The value can't exceed the value in the **This quantity can be returned** field.                                             |
| This quantity can be returned | The maximum number of packages that can be returned. This value calculates automatically.                                                                         |
| Amount                        | The amount that you must pay to the customer. This value calculates automatically, based on the deposit amount for the package and the quantity that is returned. |
| Currency                      | The currency for the amount that you must pay to the customer.                                                                                                       |

After you finish entering information about package returns, follow these steps:

1. Select **Post** to post the return transactions.
1. On the posting page, set the **Print** option to **Yes** to print the **Return packages confirmation** report. To reprint the confirmation report later, you can select **Print** on the **Return packages confirmation** page. You can also inquire about return package transactions.
1. Go to **Inventory management** > **Setup** > **Packing materials** > **Return packages**.
1. On the **Transactions** tab, select **Transactions** to open the **Return packages transactions** page. Return package transactions have negative values in the **Package quantity** field.
1. Select **Voucher** to view the details of a selected transaction.
1. Select **Printout** to print the **Return packages confirmation** report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
