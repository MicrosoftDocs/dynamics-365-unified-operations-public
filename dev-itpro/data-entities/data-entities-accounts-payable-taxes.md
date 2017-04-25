---
# required metadata

title: Data entities - Accounts payable and taxes
description: This article provides a list of the data entities that are available for the Accounts payable and taxes functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96193
ms.assetid: 9935fcf2-a497-4c19-a3a8-c1ed259a965c
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Accounts payable and taxes

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for the Accounts payable and taxes functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

**10.1.001 AP – AP and AR shared setup**

| Suggested sequence | Entity name            | Area             | Entity type | Dependency       | Comments                                                                                                                                  |
|--------------------|------------------------|------------------|-------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1                  | Payment day lines      | Accounts payable | Setup       | None             |                                                                                                                                           |
| 2                  | Cash discount          | Accounts payable | Setup       | None             | Define cash discounts, which can apply to either customers or vendors.                                                                    |
| 3                  | Payment schedule       | Accounts payable | Setup       | None             | Define payment schedules, which you can use to schedule installment payments from customers and to vendors.                               |
| 4                  | Payment schedule lines | Accounts payable | Setup       | Payment schedule | Define payment schedules, which you can use to schedule installment payments from customers and to vendors.                               |
| 5                  | Terms of payment       | Accounts payable | Setup       | None             | Define default payment terms that can be used for all vendors, and for related purchase agreements, purchase orders, and vendor invoices. |
| 6                  | Delivery charges group | Accounts payable | Setup       | None             | Define charges group for modes of delivery.                                                                                               |
| 7                  | Terms of delivery      | Accounts payable | Setup       | None             | Define the terms of delivery that are used by the company accounts, customers, and vendors.                                               |
| 8                  | Line of business       | Accounts payable | Setup       | None             | Define the line of business codes that you assign to vendors or customers on the Vendors page or the Customers page.                      |

**10.1.002 AP – Vendor payment setup**

| Suggested sequence | Entity name                         | Area             | Entity type | Dependency | Comments                                                                            |
|--------------------|-------------------------------------|------------------|-------------|------------|-------------------------------------------------------------------------------------|
| 9                  | Vendor payment fee                  | Accounts payable | Setup       | None       | Define payment fees that are related to vendors, such as fees for promissory notes. |
| 10                 | Vendor payment method               | Accounts payable | Setup       | None       | Define information about methods of payment for vendors.                            |
| 11                 | Vendor payment method specification | Accounts payable | Setup       | None       | Define payment specification codes for the method of payment.                       |

**10.1.003 AP – Vendor attributes**

| Suggested sequence | Entity name                  | Area             | Entity type | Dependency | Comments                                                                                                                                    |
|--------------------|------------------------------|------------------|-------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| 12                 | Price vendor groups          | Accounts payable | Setup       | None       | Define price groups that can be used to specify a set of prices that should apply to a group of vendors.                                    |
| 13                 | Total discount vendor groups | Accounts payable | Setup       | None       | Define vendor total discount groups that can be used on trade agreements.                                                                   |
| 14                 | Line discount vendor groups  | Accounts payable | Setup       | None       | Define vendor line discount groups that can be used on trade agreements.                                                                    |
| 15                 | Buyer groups                 | Accounts payable | Setup       | None       | Define buyer groups to associate vendors with employees and items.                                                                          |
| 16                 | Purchase pools               | Accounts payable | Setup       | None       | Define purchase order pools. You use purchase pools to group purchase orders, and for filtering and selection purposes.                     |
| 17                 | Destination code             | Accounts payable | Setup       | None       | Define destination codes. You can use destination codes to divide destinations into zones.                                                  |
| 18                 | Reasons                      | Accounts payable | Setup       | None       | Define financial reason codes. Reason codes help explain why some types of transactions were entered or why some field values were changed. |
| 19                 | Vendor exception groups      | Accounts payable | Setup       | None       | Define groups that can be assigned to vendors who are exempt from invoice validation rules.                                                 |
| 20                 | Business segments            | Accounts payable | Setup       | None       | Define general business segments that you can use to categorize prospects.                                                                  |
| 21                 | Business subsegments         | Accounts payable | Setup       | None       | Define precise types, or subsegments, for each business segment.                                                                            |
| 22                 | Vendor charges group         | Accounts payable | Setup       | None       | Define charges groups for vendors.                                                                                                          |
| 23                 | Modes of delivery            | Accounts payable | Setup       | None       |                                                                                                                                             |

**10.1.004 AP – Vendors**

**Note:** To complete the import, you might have to unmap some fields or attributes that are set on the vendor file. All these fields might not be imported yet. Otherwise, those entities can be added to **Vendor attributes** package. Some of the fields and attributes might include **SalesTaxGroupCode**, **DefaultPurchaseSite**, **DefaultProcurementWarehouseID**, and **MultiLineDiscountVendorGroupCode**. If the invoice account is set on the vendors source file, you should unmap the **InvoiceVendorAccountNumber** field the first time that it's imported. Because of the order of the records in the file, the invoice vendor account might not exist at the time of import. After all the vendors are imported, you can map and import the field again. If the **1099** field is set for vendors, open the **1099** page (**Accounts payable** &gt; **Tax 1099** &gt; **1099 fields**) before you import.

| Suggested sequence | Entity name   | Area             | Entity type | Dependency | Comments                                                |
|--------------------|---------------|------------------|-------------|------------|---------------------------------------------------------|
| 24                 | Vendor groups | Accounts payable | Setup       | None       | Define groups of vendors that share parameters.         |
| 25                 | Vendors       | Accounts payable | Setup       | None       | Define vendors that do business with your organization. |

**10.1.005 AP – AP parameters**

| Suggested sequence | Entity name            | Area             | Entity type | Dependency | Comments                                                                                       |
|--------------------|------------------------|------------------|-------------|------------|------------------------------------------------------------------------------------------------|
| 26                 | Vendor posting profile | Accounts payable | Setup       | None       | Define posting profiles that control the posting of vendor transactions to the general ledger. |
| 27                 | Vendor ledger accounts | Accounts payable | Setup       | None       |                                                                                                |
| 28                 | Vendor parameters      | Accounts payable | Setup       | None       | Define parameters for Accounts payable.                                                        |

**10.1.006 Tax – Sales tax setup**

| Suggested sequence | Entity name                     | Area | Entity type | Dependency | Comments                                                                           |
|--------------------|---------------------------------|------|-------------|------------|------------------------------------------------------------------------------------|
| 29                 | Sales tax ledger posting groups | Tax  | Setup       | None       | Define ledger posting groups for sales taxes.                                      |
| 30                 | Sales tax authorities           | Tax  | Setup       | None       | Define the governmental units that sales tax is reported and paid to.              |
| 31                 | Sales tax period setup          | Tax  | Setup       | None       | Define the sales tax settlement periods that your legal entity uses for reporting. |

**10.1.007 Tax – Sales tax code groups**

Some sales tax codes might fail during import, if their marginal base set to **Net amount per line**. To work around this issue, on the **General ledger parameters** page, on the **Sales tax** tab, in the **Calculation method** field, select **Line** before you import.

| Suggested sequence | Entity name               | Area | Entity type | Dependency | Comments                                                                                                                                             |
|--------------------|---------------------------|------|-------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| 32                 | Sales tax codes           | Tax  | Setup       | None       | Define the sales tax codes for the sales taxes and duties that your legal entity is obliged to calculate, collect, and pay to sales tax authorities. |
| 33                 | Sales tax code values     | Tax  | Setup       | None       | Define the sales tax code values or percentage for the sales tax calculation of a sales tax code.                                                    |
| 34                 | Sales tax code limits     | Tax  | Setup       | None       |                                                                                                                                                      |
| 35                 | Sales tax groups          | Tax  | Setup       | None       | Define the sales tax groups that determine the sales tax and duty calculation for customers, vendors, or ledger accounts.                            |
| 36                 | Sales tax group details   | Tax  | Setup       | None       |                                                                                                                                                      |
| 37                 | Sales tax item groups     | Tax  | Setup       | None       | Define item sales tax groups.                                                                                                                        |
| 38                 | Sales tax exempt numbers  | Tax  | Setup       | None       | Define the legal entity’s tax exempt numbers by country/region.                                                                                      |
| 39                 | Sales tax exempt code     | Tax  | Setup       | None       | Define the sales tax exempt codes that should be printed on external documents.                                                                      |
| 40                 | Sales tax reporting codes | Tax  | Setup       | None       | Define sales tax reporting codes. The codes refer to a field number on the sale report.                                                              |

**10.1.008 Tax – Sales tax parameters**

| Suggested sequence | Entity name          | Area | Entity type | Dependency | Comments                         |
|--------------------|----------------------|------|-------------|------------|----------------------------------|
| 41                 | Sales tax parameters | Tax  | Setup       | None       | Define parameters for sales tax. |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)


