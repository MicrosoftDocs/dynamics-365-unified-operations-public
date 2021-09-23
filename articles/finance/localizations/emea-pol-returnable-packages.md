---
# required metadata

title: Returnable packaging for Poland
description: The topic describes how to set up and use returnable packaging for Poland.
author: ShylaThompson
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PlCustPackageHolder, PlCustPackageReturn, PlInventPackageTable, PlInventPackageTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 273043
ms.assetid: decdb3af-9fc3-4aff-add1-bbb9d2eadc27
ms.search.region: Poland
# ms.search.industry: 
ms.author: ilyako
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Returnable packaging for Poland
[!include [banner](../includes/banner.md)]

The functionality for returnable packaging lets you handle the registration of packages that can be returned by customers. Users can define packaging codes and specify the amount of the deposit that a customer pays for returned packaging materials. This functionality is an extension of the standard functionality for packaging materials.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

| Category                | Prerequisite                                                                                                                                                                                                                                                                                                                                                                                                    |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Setup:** Legal entity | The primary address of the legal entity must be in Poland. On the **Legal entities** page (**Organization administration** &gt; **Organizations** &gt; **Legal entities**), select your legal entity. Then, on the **Addresses** FastTab, create a new address or update an existing address, select **Poland** as the country/region, enter the other address components, and mark the address as **Primary**. |

## Set up returnable packages
This section describes the various settings that you must configure to use the returnable packages functionality.

### Define packaging codes

On the **Return packages** page (**Inventory management** &gt; **Setup** &gt; **Packing material** &gt; **Return packages**), enter values for the following fields.

| Field               | Description                                                                    |
|---------------------|--------------------------------------------------------------------------------|
| Packaging code      | Enter a unique code for a returned package.                                    |
| Package description | Enter the description of the returned package.                                 |
| Deposit             | Enter the amount of the deposit that a customer pays for the returned package. |

### Attach packaging codes to packing units

Use the **Packaging material allocation** page (**Inventory management** &gt; **Setup** &gt; **Packing material** &gt; **Packaging material allocation**) to attach packaging codes to packing units for all items, for specific items, or for specific packing groups. Only the following field is specific for Poland. It extends the standard functionality of the **Packaging material allocation** page.

| Field          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| Packaging code | Select the code for the package that is returned by a customer. |

### Set up a number sequence for package vouchers

On the **Accounts receivable parameters** page (**Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**), on the **Packaging material allocation** FastTab, set up a number sequence for the **Package voucher** reference field.

### Set up a deposit account

When the sales invoice is posted, a special voucher is used to post the customer's fee for the packaging material. All deposit transactions are posted to a separate account, which should already be defined in the related customer posting profiles. On the **Customer posting profile** page (**Accounts receivable** &gt; **Setup** &gt; **Customer posting profile**), enter a value in the **Deposits** field.

## Register and verify returnable packages
Users can register packages for sales orders, post and print packing slips that include the quantity of issued packages, and post and print customer invoices. Users can also inquire about and verify the quantity of the packaged items for sales orders.

### Register packages in a sales order

On the **All sales orders** page (**Accounts receivable** &gt; **Common** &gt; **Sales orders** &gt; **All sales orders**), create a new sales order or open an existing sales order. Switch to the **Lines** view, and create a new sales order line or select an existing sales order line. On the **Line details** FastTab, on the **Packing** tab, in the **Packing unit** field, select the packing unit that is attached to the packaging code that you previously defined for return packages. The number of packages that the customer can return is automatically calculated and is shown in the **Packing unit quantity** Field.

### Verify packages

On the **Sales order lines** FastTab, select a sales order line, and then click **Financials** &gt; **Packages** &gt; **Package issue** to open the **Package issue** page. When this page is opened from a sales order line, users can modify or remove the packages that are automatically calculated for that sales order line. Alternatively, on the Action Pane for the **Sales order** page, on the **General** tab, click **Package issue**. When the **Package issue** page is opened by using this method, users can view the packages that are calculated for all sales order lines. They can also add packages, if additional packages are required.

### Print and post packing slips

On the **Sales order** page, on the Action Pane, on the **Pick and pack** tab, click **Post packing slip**. After packing slips are posted, users can inquire about package issue transactions for each packing slip. Click **Inventory management** &gt; **Setup** &gt; **Packing materials** &gt; **Return packages**, and then, on the **Transactions** tab, click **Transactions** to open the **Return packages transactions** page.

### Print and post invoices

On the **Sales order** page, on the Action Pane, on the **Invoice** tab, click **Generate** &gt; **Invoice**. After invoices are posted, users can inquire about package transactions that have posted deposit amounts for each invoice. Click **Inventory management** &gt; **Setup** &gt; **Packing materials** &gt; **Return packages**, and then, on the **Transactions** tab, click **Transactions** to open the **Return packages transactions** page. Click **Voucher** to open the **Voucher transactions** page. Verify the customer deposit amounts that are posted to the main account. The main account number is specified on the **Customer posting profiles** page. To print the **Deposit packages transactions** report, click **Printout**. Users can also inquire about return package totals for a selected customer. Click **Accounts receivable** &gt; **All customers**, and then, on the **Collect** tab, click **Packages at customer** to open the **Return packages transactions** page.

## Post and print packages returns
To enter information about the packages that customers return, click **Accounts receivable** &gt; **All customers**, and then, on the **Collect** tab, click **Packages return** to open the **Return packages confirmation** page. Enter values in the following fields. **Return packages section**

| Field       | Description                                                                                        |
|-------------|----------------------------------------------------------------------------------------------------|
| Date        | Enter the date of a package return.                                                                |
| Description | Enter the description of a package return.                                                         |
| Posted      | A value that indicates whether the package return was posted. This value is updated automatically. |

**Return packages transactions section**

| Field                         | Description                                                                                                                                                          |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Packaging code                | Select a packaging code to return.                                                                                                                                   |
| Return quantity               | Enter the number of packages to return. The value can't exceed the value in the **This quantity can be returned** field.                                             |
| This quantity can be returned | The maximum number of packages that can be returned. This value is calculated automatically.                                                                         |
| Amount                        | The amount that must be paid to the customer. This value is calculated automatically, based on the deposit amount for the package and the quantity that is returned. |
| Currency                      | The currency for the amount that must be paid to the customer.                                                                                                       |

After you've finished entering information about package returns, click **Post** to post the return transactions. On the posting page, set the **Print** option to **Yes** to print the **Return packages confirmation** report. To reprint the confirmation report later, you can click **Print** on the **Return packages confirmation** page. Users can inquire about return package transactions. Click **Inventory management** &gt; **Setup** &gt; **Packing materials** &gt; **Return packages**, and then, on the **Transactions** tab, click **Transactions** to open the **Return packages transactions** page. Return package transactions will have negative values in the **Package quantity** field. Click **Voucher** to view the details of a selected transaction. Click **Printout** to print the **Return packages confirmation** report.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]