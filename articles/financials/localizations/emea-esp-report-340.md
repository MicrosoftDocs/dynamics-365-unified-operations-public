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

Report 340 is a new report that will eventually replace two existing reports (Sales and Purchases Statutory Books) that all Spanish companies currently send in hard copy to the Spanish tax authorities. Although Report 340 will replace the sales and purchase statutory books, these reports will not be deleted from Microsoft Dynamics AX, and companies can send either Report 340 or the statutory books to the tax authorities. 

At this time, Spanish companies submit sales and purchase statutory books to the Spanish tax authorities in paper form. Report 340 is a new report that will eventually replace this procedure. The new report will be uploaded to the tax authority Web site or submitted using a software package that is available free of cost from the tax authority. Report 340 will contain information about all invoices and taxes pertaining to invoices that were issued or received by a company during a specific period. Report 340 will be submitted to the tax authorities during the first 20 days of the month or quarter, depending on the size of the company. The first report will be sent in February 2009, and will contain records for January. 

## Basic setup
1. Click Administration > Setup > System > Configuration to open the Configuration form.
2. Under Country/Regional specific features, select the Spain configuration key. 
3. Under Multiple countries/regions, select the Credit invoicing key. 

## Entries included in Report 340
Report 340 includes the following entries: 
- Sales entries: Entries of VAT report lines corresponding to sales invoices and project invoices. These records are Type 2 issued invoices.
- Sales credit memos (corrective invoices): Entries of VAT report lines corresponding to corrective invoices. 
- Purchase entries: Entries of VAT report lines corresponding to purchase invoices. These records are Type 2 received invoices.
- Purchase credit memos: Entries of VAT report lines corresponding to corrective invoices. 
- Auto-invoices and auto-credit memos: Entries of VAT report lines corresponding to auto-invoices and auto-credit memos, which are created when goods or services are delivered by a vendor in the European Union.
- Invoices that include equivalence charge. Equivalence charge is a Spanish sales tax type.
- Invoices including different VAT% or equivalence charge percentage (EC%) – Entries of invoices that have more than one VAT% or EC%.

## Generate a Spanish VAT book and export the Report 340 ASCII file
1. Click General ledger > Setup > Sales tax > External > Spanish VAT books. 
2. In the VAT book field and Description fields, enter the name and the description for the VAT book. 
3. In the Book type field, select the VAT book type from the following options:  Sales tax receivable  Sales tax payable  All the books Note:  The All the books option will create a book that contains both sales tax receivables and sales tax payables entries. 
4. In the Number sequence code field, select a number sequence code for the selected Book type. 
5. Click the Setup tab. In the Sales tax code field, select a sales tax code. The sales tax code that you select determines which VAT transactions are entered in the VAT book created. 
6. In the Equivalence charge code field, select the equivalence charge if needed. The sales tax code that you select determines which VAT transactions are entered in the VAT book created. 
7. Select the Non-Deductible VAT check box to activate non-deductible VAT for a sales tax code. Note:  A purchaser is not allowed to deduct non-deductible VAT from his own VAT liability. 
8. Select the Reverse Charge check box to activate reverse charge for a sales tax code. Note:  In some cases, goods or services are delivered by a foreign company. Reverse charge is a component of the VAT law whereby the VAT on such goods and services is payable by the recipient company and not the foreign company. 
9. Click the Spanish VAT reports button to open the Spanish VAT reports form. 
10. Click Create new to open the Spanish VAT list form. 
11. In the VAT book field, select the VAT book. 
12. In the Settlement period field, select a period that is created in the Sales tax settlement periods table. 
13. In the From date field, select the starting date of the settlement period. 
14. Select the Replacement declaration check box to replace the previous declaration. 
15. In the Previous declaration number field, enter the 13-digit number of the previous declaration. Note:  The Previous declaration number field is editable only if the Replacement declaration check box is selected. 
16. Click OK to return to the Spanish VAT reports form. The information is retrieved from the Spanish VAT list form and entered in the Spanish VAT reports form, including the Settlement period and From date information. You cannot modify the values in the Settlement period field and the From date field in the Spanish VAT reports form. Note:  The To date field is displayed only if the Settlements periods field is blank. If the Settlement period field contains a value, the To date field is hidden. However, the To date field remains in the table. 
17. On the General tab, in the Presentation type field, select the type of media to be used to export the file:  Telematic – Upload the report to the tax authority Web site or submit the report using software provided by the tax authority.  CD-R – Send the report to the tax authority on a CD-ROM.  Report  Note:  Select either Telematic or CD-R. If you select Report, an error message is displayed. 
18. Select the Reported check box to generate the final report. When you click the Output button, the Presentation date field and Reported by field are automatically filled with the relevant data. 
19. In the Contact person field, enter the name of the contact person. 
20. In the Telephone field, enter the telephone number of the contact person. 
21. In the Document field, enter the four-digit document number. If you enter a number containing fewer than four digits, preceding zeros are appended to create a four-digit number. For example, if you enter 1, AX will automatically convert it to 0001 and store it. 
22. In the Electronic field, enter the 16-digit electronic code. This number is provided by the authorities and it is mandatory. 
23. Click the Totals button to open the Totals form. In the form, you can view:  Number of operations – The total number of sales or receivables under the Deliveries field group and the total number of purchases or payables under the Acquisitions field group.  Amount – The total amount of the sales or receivables under the Deliveries field group and the total number of purchases or payables under the Acquisitions field group. 
24. Click the VAT report lines button to open the VAT report lines form. In the form, you can view the details of VAT transactions. You can delete lines if they are not required to be reported at the time of exporting the report. 
25. Click the Output button and select from the following:  Print  Export to ASCII file Note:  If the VAT report contains no transactions, an error message is displayed. 
26. In the Export to ASCII form, select the file to be exported and click OK. The information is retrieved from the VAT report lines form. Tax law forbids the export of ASCII files for years prior to 2009. However, you can print pre-2009 records. 

## File format
The Report 340 text file format complies with the regulatory requirements and contains the following record types:  One Type 1 record – The Type 1 record contains information about the company filing the Report 340 (the deponent). The information will be retrieved from the Company Information table and from the Spanish VAT Books form.  At least one Type 2 record – Type 2 records contain information about the goods and services purchased and sold during a specific period. Customer and vendor information will be retrieved from the Customer and Vendor cards. Note:  If no Type 2 records are present, the file is not generated. 

## Validate the file format and submit the Report 340 file to the tax authorities
You can validate the file format by using either of the following two methods: 

- You can upload the file to the [tax authority Web site] (https://www5.aeat.es/es13/h/iemodelk.html?mod=9340). You can test the file on a specific page of the site. To do this, however, you require a valid E-certificate. 

  > [!NOTE]
  > E-certificates are issued to Spanish citizens only.
  
- You can upload the file by using the free software provided by the authorities. 
