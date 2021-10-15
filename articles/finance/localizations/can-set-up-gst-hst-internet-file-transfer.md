---
# required metadata

title: Canada GST/HST Internet File Transfer
description: This article explains how to configure and use Canada GST/HST internet file transfer feature.
author: EricWangChen
ms.date: 08/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: GST/HST, GIFT
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Canada
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2019-08-14
ms.dyn365.ops.version: 10.0.6

---


# Canada GST/HST Internet File Transfer 

[!include [banner](../includes/banner.md)]

Taxpayers in Canada use form GST 34 to manually file Goods and Services Tax or Harmonized Sales Tax (GST/HST) returns and to remit payments to the Canada Revenue Agency (CRA). However, the CRA allows taxpayers to file and remit taxes calculated on acquired fixed assets electronically. You can file GST/HST returns electronically using any of the following methods:

  - Net file transfer – An Internet-based filing service that allows taxpayers to file their returns directly over the Internet.

  - Electronic Data Interchange (EDI) – A data transfer method that taxpayers can use to file their returns directly with the CRA or through a third-party service provider.

  - GST/HST Internet File Transfer (GIFT) – An uploading tool used to submit text files to the CRA website for filing GST/HST returns and remitting payments.

Before you generate a GIFT file, you should set up your software identification code, sales tax code, and sales tax group. 

Use the following procedures to enter legal entity details, sales tax code, and sales tax group for GIFT, and to create sales tax entries for taxes paid on acquisition.

## Set up legal entities for GIFT

When you submit a request to CRA to perform an Internet file transfer, CRA provides a software identification code. The first two characters are alphabetical and the last six characters are numerical. You must enter this identification code in the **Legal entities** form correctly to process your returns.

1.  Click **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.

2.  Click the **Statutory reporting** FastTab, and in the **Registration number** field, enter the registration number that the CRA provided to you when you registered for GST/HST.

3.  In the **Software identification code** field, enter AX030003 to transfer the returns.

4.  Click **Account identifiers** to open the **Account identifiers** form.

5.  On the **Overview** tab, in the **Program identifier** field, select **GST/HST**.

6.  In the **Reference number** field, enter the reference number provided by the CRA.

7.  Close the forms to save your changes.

## Set up tax codes for GIFT

Use the **Sales tax codes** form to set up tax codes to calculate GST/HST for the GIFT file.

1.  Click **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax codes**.

2.  Press CTRL+N to create a new tax code.

3.  In the **Sales tax code** field, enter a code, such as GST/HST, and then enter general information about the sales tax code.

4.  Click the **Calculation** tab and enter the calculation details to calculate the GST/HST amount.

5.  Click **Values** to open the **Values** form. Enter the dates during which the tax code is in effect.

6.  In the **Value** field, enter the percentage for the calculation.

7.  Close the forms to save your changes.

## Set up tax groups for GIFT

Use the **Sales tax groups** form to set up sales tax groups. You can assign the sales tax groups to companies, and the taxes will be calculated based on the tax codes that were in effect when the transactions took place.

1.  Click **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax groups**.

2.  Press CTRL+N to create a new sales tax group.

3.  In the **Sales tax group** field, enter a name, such as GST/HST, and then enter general information about the sales tax group.

4.  Click the **Setup** tab, and in the **Sales tax code** field, select a sales tax code to add to the sales tax group.

5.  Close the form to save your changes.

## Generate a GIFT file

You can generate a Goods and Services Tax or Harmonized Sales Tax (GST/HST) Internet File Transfer (GIFT) file and upload it to the Canadian Revenue Agency (CRA) website to file your GST/HST returns and remit payments.

1. Click **General ledger** > **Periodic** > **GST/HST Internet File Transfer (GIFT)**.

2. In the **From date** and **To date** fields, select the starting and ending dates of the reporting period.

3. In the **File name** field, select the path and enter the name for the GIFT file.

    Note

   For easy identification, use the format GSTYYYYMMDD.tax (GST, followed by the reporting date, with a .tax extension) as in this example: GST20100728.tax.

4. Click **OK** to export the GIFT file to the specified path.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
