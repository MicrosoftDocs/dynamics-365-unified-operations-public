---
# required metadata

title: Set up and generate positive pay files
description: This article explains how to set up positive pay and generate positive pay files. 
author: panolte
ms.date: 03/06/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankPositivePayFormat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Set up and generate positive pay files

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This functionality will be deprecated September 2022, new users should use electronic reporting. For more information, see [Set up positive pay files by using Electronic reporting](set-up-positive-pay-er.md).

This article explains how to set up positive pay and generate positive pay files. 

Set up positive pay to generate an electronic list of checks that is provided to the bank. Then, when a check is presented to the bank, the bank compares it with the list of checks. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

## Security for positive pay files
Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until they are received by the bank. Positive pay files are downloaded to the location that is specified by your web browser. Because positive pay files can contain sensitive information, it's important that only authorized users have access to generate and view this information in Microsoft Dynamics 365 Finance. Use the following table to help you determine the privileges that are required.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Task</th>
<th>Privilege</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Generate positive pay files from the <strong>Bank accounts</strong> list page or the <strong>Bank accounts</strong> page.</td>
<td><ul>
<li><strong>Maintain bank positive pay information</strong> (BankPositivePayProcess)</li>
<li><strong>BankPositivePayExportEntityView</strong> (BankPositivePayExportEntityView)</li>
</ul></td>
</tr>
<tr class="even">
<td>Generate positive pay files for multiple legal entities and bank accounts from the <strong>Generate a positive pay file</strong> page.</td>
<td><ul>
<li><strong>Maintain bank positive pay information</strong> (BankPositivePayProcess)</li>
<li><strong>BankPositivePayExportEntityView</strong> (BankPositivePayExportEntityView)</li>
</ul></td>
</tr>
<tr class="odd">
<td>View positive pay files on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>View bank positive pay information for multiple legal entities</strong> (BankPositivePayView)</td>
</tr>
<tr class="even">
<td>Confirm a bank positive pay file on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>Confirm positive payment file</strong> (BankPositivePayConfirm)</td>
</tr>
<tr class="odd">
<td>Recall a bank positive pay file on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>Recall positive pay file</strong> (BankPositivePayRecall)</td>
</tr>
</tbody>
</table>

## Set up a positive pay format
Positive pay files are created by using data entities. Before you can generate a positive pay file, you must set up a transformation input format that will be used to translate the check information into a format that can communicate with the bank. On the **Positive pay format** page, you can create a file format identifier and a description. The transformation input format must be of the XML type. The specific format depends on the transformation file that you're using. For example, the sample Extensible Stylesheet Language Transformations (XSLT) file that is provided uses the **XML-Element** format. Use the **Upload file used for transformation** action to specify the location of the transform file for the format that your bank requires.

## Example: XSLT file for positive pay file

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl xslthelper" xmlns="urn:iso:std:iso:20022:tech:xsd:pain.001.001.02" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xslthelper="http://schemas.microsoft.com/BizTalk/2003/xslthelper">
  <xsl:output method="xml" omit-xml-declaration="no" version="1.0" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:value-of select="'
'" />
    <Document>
      <xsl:value-of select="'
'" />
      <!--Header Begin-->
      <xsl:value-of select='string("Vendor ID,Vendor Name,Voided,Document Type,Check Date,Check Number,Check Amount,Checkbook ID,Vendor Class ID,Posted Date")'/>
      <xsl:value-of select="'
'" />
      <!--Header End-->
      <xsl:for-each select="Document/BANKPOSITIVEPAYEXPORTENTITY">
        <!--Cheque Detail begin-->
        <xsl:value-of select='RECIPIENTACCOUNTNUM/text()'/>
        <xsl:value-of select="','" />
        <xsl:value-of select='BANKNEGINSTRECIPIENTNAME/text()'/>
        <xsl:value-of select="','" />
        <xsl:choose>
          <xsl:when test='CHEQUESTATUS/text()=normalize-space("Void") or CHEQUESTATUS/text()=normalize-space("Rejected") or CHEQUESTATUS/text()=normalize-space("Cancelled")'>
            <xsl:value-of select='string("Yes")'/>
          </xsl:when>
          <xsl:when test='CHEQUESTATUS/text()=normalize-space("Payment")'>
            <xsl:value-of select='string("No")'/>
          </xsl:when>
          <xsl:otherwise>
            <xsl:value-of select='string(" ")'/>
          </xsl:otherwise>
        </xsl:choose>
        <xsl:value-of select="','" />
        <xsl:value-of select='string("Payment")'/>
        <xsl:value-of select="','" />
        <xsl:value-of select='TRANSDATE/text()'/>
        <xsl:value-of select="','" />
        <xsl:value-of select='CHEQUENUM/text()'/>
        <xsl:value-of select="','" />
        <xsl:value-of select='AMOUNTCUR/text()'/>
        <xsl:value-of select="','" />
        <xsl:value-of select='string("BOA-#1812")'/>
        <xsl:value-of select="','" />
        <xsl:choose>
          <xsl:when test='RECIPIENTTYPE/text()=normalize-space("Vend")'>
            <xsl:value-of select='VENDGROUP/text()'/>
          </xsl:when>
          <xsl:otherwise>
            <xsl:value-of select='CUSTGROUP/text()'/>
          </xsl:otherwise>
        </xsl:choose>
        <xsl:value-of select="','" />
        <xsl:value-of select='TRANSDATE/text()'/>
        <xsl:value-of select="'
'" />
      </xsl:for-each>
    </Document>
  </xsl:template>
</xsl:stylesheet>
```

> [!NOTE]
> XML names in the XSLT must match the casing of the nodes in the XML. Both the XSLT and XML files are case sensitive. 

## Assign the positive pay format to a bank account
For each bank account that you want to generate positive pay information for, you must assign the positive pay format that you specified in the previous section. On the **Bank accounts** page, select the positive pay format that corresponds to the bank account. In the **Positive pay start date** field, enter the first date to generate positive pay files. It's important that you enter a date in this field. Otherwise, the first positive pay file that you generate will include all checks that have ever been created for this bank account.

## Assign a number sequence for positive pay files
Each positive pay file must have a unique number. Use the **Number sequences** tab on the **Cash and bank management parameters** page to create a number sequence for positive pay files.

## Generate a positive pay file for a single bank account
You can generate a positive pay file for a single legal entity and a single bank account. For information about how to generate positive pay files for multiple legal entities and bank accounts at the same time, see the next section. To generate a positive pay file for a single legal entity and a single bank account, open the **Generate a positive pay file** dialog box from the **Bank accounts** page. In the **Cut-off date** field, enter the last check date to include in the positive pay file. All checks that haven’t been included in a positive pay file by the end of this check date are included in the file.

## Generate a positive pay file for multiple bank accounts
To generate a positive pay file for multiple bank accounts, use the **Generate a positive pay file** periodic task. Select the positive pay format for the file, and specify whether to generate the file for all legal entities or for a selected legal entity. You can also generate the positive pay file for all bank accounts that use the specified positive pay format or for a selected bank account. In the **Cut-off date** field, enter the last check date to include in the positive pay file. All checks that haven’t been included in a positive pay file by the end of this check date are included in the file.

## View the results of positive pay file generation
After the positive pay file is generated, you can view the results on the **Positive pay file summary** page. To view the details of the individual checks, use the **Positive pay file** details page.

## Confirm a positive pay file
After the checks that are listed in a positive pay file have been paid, you receive a confirmation number from your bank. You can then confirm the positive pay file. On the **Positive pay file summary** page, select a positive pay file that has a status of **Created**, and then select the **Enter confirmation** action. When you confirm a positive pay file, the confirmation number that you received from the bank is recorded.

## Recall a positive pay file
If you must change a positive pay file, you can recall it. On the **Positive pay file summary** page, select a positive pay file that has a status of **Created**, and then select the **Recall** action. For each check in the positive pay file, the field that indicates whether that check has been included in a positive pay file is reset. You can then create a new positive pay file that includes the check that was recalled.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
