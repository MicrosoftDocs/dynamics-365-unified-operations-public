---
# required metadata

title: Report 340 for Spain
description: This topic provides information about how to set up and generate Report 340 for Spain.
author: ShylaThompson
manager: AnnBe
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Spain
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Report 340

[!include[banner](../includes/banner.md)]

Report 340 replaced two earlier reports (Sales Statutory Books and Purchases Statutory Books) that all Spanish companies submitted as hard copies to the Spanish tax authorities. The new report can be uploaded to the tax authorities' website, or it can be submitted by using a software package that is available free of cost from the tax authorities.

Report 340 contains information about all invoices and taxes that are related to invoices that a company issued or received during a specific period. Report 340 should be submitted to the tax authorities during the first 20 days after the reporting period. The reporting period can be a month or a quarter, depending on the size of the company.

## Entries that are included in Report 340

Report 340 includes the following entries:

- **Sales entries** – Entries of value-added tax (VAT) report lines that correspond to sales invoices and project invoices. These records are **Type 2** issued invoices.
- **Sales credit memos (corrective invoices)** – Entries of VAT report lines that correspond to corrective invoices.
- **Purchase entries** – Entries of VAT report lines that correspond to purchase invoices. These records are **Type 2** received invoices.
- **Purchase credit memos** – Entries of VAT report lines that correspond to corrective invoices.
- **Auto-invoices and auto-credit memos** – Entries of VAT report lines that correspond to invoices and credit memos that are automatically created when goods or services are delivered by a vendor in the European Union (EU).
- **Invoices that include equivalence charge** – Equivalence charge is a type of Spanish sales tax.
- **Invoices including different VAT% or equivalence charge percentage (EC%)** – Entries of invoices that have more than one VAT percentage or equivalence charge (EC) percentage.

## Generate a Spanish VAT book and export the Report 340 ASCII file

1. Select **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Spanish VAT books**.
2. In the **VAT book** and **Description** fields, enter a name and description for the VAT book.
3. In the **Number sequence code** field, select a number sequence code.
4. On the **Setup** FstTab, select the **Add** button, and then follow these steps to set up sales tax codes on the sales tax transactions that should be included on the report:

    1. In the **Sales tax code** field, select a sales tax code.
    2. In the **Equivalence charge code** field, select the EC, if it's required.
    3. Set the **Non-Deductible VAT** option to **Yes** to activate non-deductible VAT for a sales tax code.

        > [!NOTE]
        > Purchasers aren't allowed to deduct non-deductible VAT from their own VAT liability.

    4. Set the **Reverse Charge** option to **Yes** to activate reverse charges for a sales tax code.

        > [!NOTE]
        > Reverse charges are part of the VAT law. In some cases, goods or services are delivered by a foreign company. When reverse charges are activated, the VAT on these goods and services is payable by the recipient company, not by the foreign company.

5. Select the **Spanish VAT reports** button to open the **Spanish VAT reports** page.
6. Select the **Create new** button to create a new report. On the **Spanish VAT list** page, fill in the **VAT book**, **Description**, **Settlement period**, **From date**, and **Start numbering** fields, and follow these steps:

    1. In the **Method of numbering** field, select a value.
    2. Set the **Replacement declaration** option to **Yes** to replace the previous declaration.
    3. In the **Previous declaration number** field, enter the 13-digit number of the previous declaration.

        > [!NOTE]
        > The **Previous declaration number** field can be edited only if the **Replacement declaration** option has **Yes**.

7. Select **OK** to return to the **Spanish VAT reports** page. The system enters information from the **Spanish VAT list** page on the **Spanish VAT reports** page. You can't modify the values in the **Settlement period**, **Method of numbering**, and **From date** fields on the **Spanish VAT reports** page.
8. On the **General** tab, follow these steps:

    1. In the **Presentation type** field, select the type of media to use to export the file:

         - **Telematic** – Upload the report to the tax authorities' website, or submit the report by using the free software that is provided by the tax authorities.
        - **CD-R** – Send the report to the tax authorities on a CD-ROM.
        - **Report**

        > [!NOTE]
        > Select either **Telematic** or **CD-R**. If you select **Report**, you receive an error message.

    2. Set the **Reported** option to **Yes** to generate the final report.
    3. In the **Contact person** field, enter the name of the contact person.
    4. In the **Telephone** field, enter the telephone number of the contact person.
    5. In the **Document** field, enter the four-digit document number. If you enter a number that contains fewer than four digits, leading zeros are added to create a four-digit number. For example, if you enter **1**, the system automatically converts the value to **0001** and stores the new value.
    6. In the **Electronic** field, enter the 16-digit electronic code. This number is mandatory and is provided by the tax authorities.

9. Select the **Totals** button to open the **Totals** page. On this page, you can view the following values:

    - **Number of operations** – The total number of sales or receivables in the **Deliveries** field group, and the total number of purchases or payables in the **Acquisitions** field group.
    - **Amount** – The total amount of the sales or receivables in the **Deliveries** field group, and the total number of purchases or payables in the **Acquisitions** field group.

10. Select the **VAT report lines** button to open the **VAT report lines** page. On this page, you can view the details of VAT transactions. You can delete or exclude lines from the report if they don't have be reported when you export the report.
11. Select the **Output** button, and then select either **Print** or **Export to ASCII file**. If you selected **Export to ASCII file** then complete the following steps: 

    > [!NOTE]
    > If the VAT report contains no transactions, you receive an error message.
    > Before execution these step, please, check information on **General** tab. You should fill in information in **Contact information** and **Document number** field groups. Otherwise you would get error message. 
    
    1. On the **Export to ASCII** page, select the file to export, and then select **OK**. Tax law forbids the export of ASCII files for years before 2009. However, you can print records for years before 2009.
    2. On the **Spanish VAT register book** page, in the **Format mapping** field, select the format.

    The information is retrieved from the **VAT report lines** page.

## File format

The format of the Report 340 text file complies with the regulatory requirements and contains the following record types:

- **Type 1** – The **Type 1** record contains information about the company that submits Report 340. This company is known as the *deponent*. The information is retrieved from the Company Information table and the **Spanish VAT books** page.
- **Type 2** – The report should include at least one **Type 2** record. **Type 2** records contain information about the goods and services that were purchased and sold during the specified period. Customer and vendor information is retrieved from the Customer and Vendor records.

> [!NOTE]
> If there are no **Type 2** records, the file isn't generated.

## Validate the file format and submit the Report 340 file to the tax authorities

You can validate the file format by using one of the following methods:

- Upload the file to the [tax authorities' website](https://www5.aeat.es/es13/h/iemodelk.html?mod=9340). You can test the file on a specific page of the site. However, you must have a valid e-certificate.

    > [!NOTE]
    > E-certificates are issued only to Spanish citizens.

- Upload the file by using the free software that is provided by the tax authorities.
