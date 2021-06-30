---
# required metadata

title: Bank statement file import troubleshooting
description: It's important that the bank statement file from the bank matches the layout that Microsoft Dynamics 365 Finance supports. Because of strict standards for bank statements, most integrations will work correctly. However, sometimes the statement file can't be imported or has incorrect results. Typically, these issues are caused by small differences in the bank statement file. This article explains how to fix these differences and resolve the issues.
author: panolte
ms.date: 03/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankStatementFormat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 141273
ms.assetid: 3ee2f32b-02aa-420b-8990-e6aa5fc6bda3
ms.search.region: global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Bank statement file import troubleshooting

[!include [banner](../includes/banner.md)]

It's important that the bank statement file from the bank matches the layout that Microsoft Dynamics 365 Finance supports. Because of strict standards for bank statements, most integrations will work correctly. However, sometimes the statement file can't be imported or has incorrect results. Typically, these issues are caused by small differences in the bank statement file. This article explains how to fix these differences and resolve the issues.

## What is the error?

After you try to import a bank statement file, go to the Data management job history and its execution details to find the error. The error can help by pointing to the statement, balance, or statement line. However, it's unlikely to provide enough information to help you identify the field or element that is causing the issue.

> [!NOTE]
> Imported bank statements can overlap only for single a point in time.  For example, if a statement ends at 12:00 AM on January 1, 2021, then beginning date for the next statement can be 12:00 AM on Jarnuary 1, 2021 12:00:00 AM.

## What are the differences?
Compare the bank file layout definition to the Finance import definition, and note any differences in the fields and elements. Compare the bank statement file to the related sample Finance file. In the ISO20022 files, any differences should be easy to see.

## Time zone differences on imported bank statements
The date-time values in the import file can differ from the date-time values that are shown in Finance and Operations. To prevent this discrepancy, enter a time zone preference on the **Configure data sources** page. For more information about entering a time zone preference, see [Set up the advanced bank reconciliation import process](set-up-advanced-bank-reconciliation-import-process.md).

## Transformations
Typically, the change must be made in one of three transformations. Each transformation is written for a specific standard.

| Resource name                                         | File name                          |
|-------------------------------------------------------|------------------------------------|
| BankStmtImport\_BAI2CSV\_to\_BAI2XML\_xslt            | BAI2CSV-to-BAI2XML.xslt            |
| BankStmtImport\_ISO20022XML\_to\_Reconciliation\_xslt | ISO20022XML-to-Reconciliation.xslt |
| BankStmtImport\_MT940TXT\_to\_MT940XML\_xslt          | MT940TXT-to-MT940XML.xslt          |

## Debugging transformations
### Adjust the BAI2 and MT940 files

The BAI2 and MT940 files are text-based files and require an adjustment to enable Extensible Stylesheet Language Transformations (XSLT) debugging. The program makes this adjustment when a file is imported.

1.  Create an XML file, and copy the following text into it.

    ```xml
    <Batch><![CDATA[PASTESTATEMENTFILEHERE
        ]]></Batch>
    ```
    
2.  Copy the contents of the bank statement file, and paste them into the XML file so that they replace **PASTESTATEMENTFILEHERE**.

### Debug the XSLT

For more information, see <https://msdn.microsoft.com/library/ms255605.aspx>.

1.  Start Microsoft Visual Studio.
2.  Create a console application.
3.  Open the appropriate XSLT.
4.  Click the XLST and its properties page.
5.  Set the input to the location of the bank statement file.
6.  Define a location and file name for the output.
7.  Set the required break points.
8.  On the menu, click **XML** &gt; **Start XSLT Debugging**.

### Format the XSLT output

When the transformation runs, it creates an output file that you can view in Visual Studio. Use Ctrl+A, Ctrl+K, and Ctrl+D to quickly format the output file.

### Adjust the transformation

Adjust the transformation to get the appropriate field or element in the bank statement file. Then map that field or element to the appropriate Finance element.

### Debit/credit indicator

Sometimes, debits might be imported as credits, and credits might be imported as debits. To resolve this issue, you must change the appropriate XSLT. If bank statements come from multiple banks, make sure that they all use the same debit/credit approach, or create separate transformations.

-   BAI2XML-to-Reconciliation.xlst GetAmountCreditDebitIndicator template
-   ISO20022XML-to-Reconcilation.xslt GetCreditDebit template
-   MT940XML-to-Reconcilation.xslt GetCreditDebitIndicator template

## Examples of bank statement formats and technical layouts
The following table lists examples of the technical layout definitions for advanced bank reconciliation import files and three related bank statement example files. You can download the example files and technical layouts here: [Import file examples](//download.microsoft.com/download/8/e/c/8ec8d2d0-eb8c-41fb-ad8c-f01a4d670a44/Dynamics365FinanceAdvancedBankStatementLayouts.xlsx)  

| Technical layout definition                             | Bank statement example file          |
|---------------------------------------------------------|--------------------------------------|
| DynamicsAXMT940Layout                                   | [MT940StatementExample](//download.microsoft.com/download/2/d/c/2dcc4e55-ddc8-4a74-b79c-250fae201c3c/mt940StatementExample.txt)                |
| DynamicsAXISO20022Layout                                | [ISO20022StatementExample](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdownload.microsoft.com%2Fdownload%2F1%2F5%2F5%2F155d84ed-c250-48f3-b0b1-c5a431e7855b%2FISO20022-MultipleStatements.xml&data=04%7C01%7CRobert.Schlomann%40microsoft.com%7C30d0c233cb6546547d0a08d8f4965edc%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637528273956712775%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=3VzvLZK%2BO8PjuI7XVdC6rD2j3nUJfteo7zFp%2B1s9BwM%3D&reserved=0)             |
| DynamicsAXBAI2Layout                                    | [BAI2StatementExample](//download.microsoft.com/download/1/1/6/11693f57-bfc1-4993-a274-5fb978be70fa/BAI2StatementExample.txt)                 |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
