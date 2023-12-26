---
title: Plan for one-time vendors in the public sector
description: This article explains how organizations in the public sector can prepare to import and create multiple one-time vendors and invoices.
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: v-kiarnd
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 936570cb-932f-4027-b3c7-2235ad79bc1c
ms.search.industry: Public sector
ms.search.form: LedgerTransVoucher, SysConfiguration, Tax1099Summary, VendTableListPage
---

# Plan for one-time vendors in the public sector

[!include [banner](../includes/banner.md)]

This article explains how to prepare to import and create multiple one-time vendors and invoices. 

Typically, if you plan to mass-import vendor and invoice information, you first create a data file in spreadsheet format and save it in CSV (comma-separated values) format.

-   Because commas are used to separate the fields in a CSV file, don't use commas in the text of an entry. For example, to specify a company name of “Smith, Smith, and Jones,” enter it as **Smith Smith and Jones**.
-   If you don't set values for fields on this page, the newly created vendor accounts use values from the one-time vendor profile that is referenced on the **Accounts payable parameters** page. For example, if the method of payment is set to **Check** for the one-time vendor profile on the **Accounts payable parameters** page, that method of payment will also be set for the one-time vendors that you're adding.
-   The **One-time supplier** Accounts payable number sequence is used to assign the one-time vendor accounts and must not be set to **Continuous** for this service. Invoices are generated in a draft state. Before you create payment proposals for payment, you must post the invoices.

The following table show the fields that the import file must contain. Each field label is equivalent to a column heading in a spreadsheet, and each spreadsheet row contains the data for each applicable column.

**Vendor section**

| Field                                          | Details                                                 |
|------------------------------------------------|---------------------------------------------------------|
|Record type                                     | **Person** or **Organization**                          |
| First name                                     | (If the record type value is **Person**)                |
| Middle name (Optional)                         | (If the record type is **Person**)                      |
| Last name                                      | (If the record type is **Person**)                      |
| Vendor name                                    | (If the record type is **Organization**)                |
| Group                                          | Ten-character limit                                     |
| Country/region                                 | Ten-character limit                                     |
| ZIP/postal code                                |                                                         |
| Street                                         |                                                         |
| City                                           |                                                         |
| City                                           |                                                         |
|Federal tax ID (Optional)                       | (U.S. only) 1099 number                                 |
| Tax ID type                                    | (U.S. only) Values can be **Unknown**, **Employer Identification Number**, **Social Security Number**, **Individual Taxpayer Identification Number**, or **Adopted Tax Payer Identification Number**.  **Note:** If no federal tax ID is provided, this field should be set to **Unknown**.                                               |
| Bank account (Optional)                        | Bank account name                                       |
| Bank account number                            |                                                         |
| Routing number (Optional)                      |                                                         |
| SWIFT code (Optional)                          | Also known as BIC (Bank identifier code)                |
|IBAN (Optional)                                 | International bank account number, 34-character limit   |



**Invoice section**

| Field                                                | Details                                           |
|------------------------------------------------------|---------------------------------------------------|
| Invoice number                                       | Invoice number, 20-character limit                |
| Invoice description (Optional)                       |                                                   |
| Posting date (Optional)                              | Date format                                       |
| Invoice date                                         | Date format                                       |
| Due date (Optional)                                  | Date format                                       |
| Line number                                          |                                                   |
|Item number (Optional)                                | 20-character limit   **Note:** If no item number is provided, you must provide values in the **Procurement category** and **Procurement category hierarchy** fields. If no procurement category and procurement category hierarchy are provided, you must provide a value in the **Item number** field.                    |
| Item name (Optional)                                 |  60-character limit                               |
| Procurement category hierarchy (Optional)            |    **Note:** If you provide a value for this field, the **Procurement category** field is also required.                                                                         |
| Procurement category (Optional)                      | **Note:** If you provide a value for this field, the **Procurement category hierarchy** field is also required.                                                                        |
| Quantity (Optional)                                  |                                                   |
| Unit (Optional)                                      | Ten-character limit                               |
|Line net amount                                       | Decimal values are allowed.                       |
| Unit price (Optional)                                | Decimal values are allowed.                       |


**Distributions section**

| Field                                                | Details                                  |
|------------------------------------------------------|------------------------------------------|
| Number                                               | Accounting distribution line number      |
| Financial dimensions                                 | If the file you import has financial dimensions, you need to include all of the financial dimensions with the proper naming, otherwise an error message will appear stating that the ledger dimension is invalid. You’ll then need to either correct the financial dimensions or remove the columns from the file.                                         |
| Percent                                              | Decimal values are allowed.              |




## What do I do next?
After you’ve set up the prerequisites that you require, see [One-time vendors in the public sector](one-time-vendors-public-sector.md).

## Additional resources

[One-time vendors in the public sector](one-time-vendors-public-sector.md)

[Accounts payable in the public sector overview](accounts-payable-public-sector.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
