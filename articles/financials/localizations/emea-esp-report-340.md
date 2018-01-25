---
# required metadata

title: Report 340 for Spain
description: This topic provides information about setting up and generating the Report 340 for Spain.  
author: ShylaThompson
manager: AnnBe
ms.date: 01/24/2018
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

Report 340 is a report that replaced two reports (Sales and Purchases Statutory Books) that all Spanish companies submited as hard copy to the Spanish tax authorities. 
The new report may be uploaded to the tax authority Web site or submitted using a software package that is available free of cost from the tax authority. Report 340 contains information of all invoices and taxes pertaining to invoices that were issued or received by a company during a specific period. Report 340 should be submitted to the tax authorities during the first 20 days following the reporting period (month or quarter, depending on the size of the company). 

## Entries included in Report 340
Report 340 includes the following entries: 
- Sales entries: Entries of VAT report lines corresponding to sales invoices and project invoices. These records are **Type 2** issued invoices.
- Sales credit memos (corrective invoices): Entries of VAT report lines corresponding to corrective invoices. 
- Purchase entries: Entries of VAT report lines corresponding to purchase invoices. These records are **Type 2** received invoices.
- Purchase credit memos: Entries of VAT report lines corresponding to corrective invoices. 
- Auto-invoices and auto-credit memos: Entries of VAT report lines corresponding to auto-invoices and auto-credit memos, which are created when goods or services are delivered by a vendor in the European Union.
- Invoices that include equivalence charge. Equivalence charge is a Spanish sales tax type.
- Invoices including different VAT% or equivalence charge percentage (EC%) – Entries of invoices that have more than one VAT% or EC%.

## Generate a Spanish VAT book and export the Report 340 ASCII file
1. Click *Tax > Setup > Sales tax > Spanish VAT books*. 
2. In the **VAT book** and **Description** fields, enter the name and the description for the VAT book. 
3. In the **Number sequence code** field, select a number sequence code. 
4. In **Setup** area click **Add** button to setup sales tax codes on which sales tax transactions should be included in the report: 
   - in the **Sales tax code** field, select a sales tax code.  
   - in the **Equivalence charge code** field, select the equivalence charge if needed.  
   - select the **Non-Deductible VAT** check box to activate non-deductible VAT for a sales tax code. Note: A purchaser is not allowed to deduct non-deductible VAT from his own VAT liability. 
   - Select the **Reverse Charge** check box to activate reverse charge for a sales tax code. Note: in some cases, goods or services are delivered by a foreign company. Reverse charge is a component of the VAT law whereby the VAT on such goods and services is payable by the recipient company and not the foreign company. 
5. Click the **Spanish VAT reports** button to open the **Spanish VAT reports** form. 
6. Click **Create new** button to create a new report and fill in the fields in the **Spanish VAT list** form (**VAT book**, **Description**, **Settlement period**, **From date**, **Start numbering**): 
   - Select the value in the **Method of numbering** field 
   - Select the **Replacement declaration** check box to replace the previous declaration. 
   - in the **Previous declaration number** field, enter the 13-digit number of the previous declaration. Note:  The **Previous declaration number** field is editable only if the **Replacement declaration** check box is selected. 
7. Click **OK** button to return to the **Spanish VAT reports** form. The system inserts information to the **Spanish VAT reports** form from the **Spanish VAT list** form. You cannot modify the values in the **Settlement period**, **Method of numbering**, **From date** fields in the **Spanish VAT reports** form.
8. Fill in the fields on **General** tab:
  - in the **Presentation type field**, select the type of media to be used to export the file: **Telematic** – upload the report to the tax authority Web site or submit the report using software provided by the tax authority. **CD-R** – send the report to the tax authority on a CD-ROM. Report  Note: select either **Telematic** or **CD-R**. If you select **Report**, an error message is displayed. 
  - Select the **Reported** check box to generate the final report. 
  - In the **Contact person** field, enter the name of the contact person. 
  - In the **Telephone** field, enter the telephone number of the contact person. 
  - In the **Document** field, enter the four-digit document number. If you enter a number containing fewer than four digits, preceding zeros are appended to create a four-digit number. For example, if you enter 1, AX will automatically convert it to 0001 and store it. 
  - In the **Electronic** field, enter the 16-digit electronic code. This number is provided by the authorities and it is mandatory. 
9. Click the **Totals** button to open the **Totals** form. In the form, you can view:  
  - **Number of operations** – the total number of sales or receivables under the **Deliveries** field group, the total number of purchases or payables under the **Acquisitions** field group. 
  - **Amount** – the total amount of the sales or receivables under the **Deliveries** field group and the total number of purchases or payables under the **Acquisitions** field group. 
10. Click the **VAT report lines** button to open the **VAT report lines** form. In the form, you can view the details of VAT transactions. You can delete or Exclude lines from report if they are not required to be reported at the time of exporting the report. 
11. Click the **Output** button and select from the following: **Print** or **Export to ASCII file**. Note: if the VAT report contains no transactions, an error message is displayed. 
    - In the **Export to ASCII** form, select the file to be exported and click **OK**. Tax law forbids the export of ASCII files for years prior to 2009. However, you can print pre-2009 records.
    - In the **Spanish VAT register book** form select format in the **Format mapping** field.
    The information is retrieved from the **VAT report lines** form.  

## File format
The Report 340 text file format complies with the regulatory requirements and contains the following record types: **Type 1** – the **Type 1** record contains information about the company which submit the Report 340 (the deponent). The information is retrieved from the **Company Information** table and from the **Spanish VAT Books** form. At least one **Type 2** record should be in the report. **Type 2** records contain information on goods and services purchased and sold during the specific period. Customer and vendor information is retrieved from the Customer and Vendor cards. Note:  if there are no **Type 2** records, the file is not generated. 

## Validate the file format and submit the Report 340 file to the tax authorities
You can validate the file format by using either of the following two methods: 

- You can upload the file to the [tax authority Web site] (https://www5.aeat.es/es13/h/iemodelk.html?mod=9340). You can test the file on a specific page of the site. To do this, however, you require a valid E-certificate. 

  > [!NOTE]
  > E-certificates are issued to Spanish citizens only.
  
- You can upload the file by using the free software provided by the authorities. 
