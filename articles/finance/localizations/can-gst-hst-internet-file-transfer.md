---
# required metadata

title: Canada GST/HST Internet File Transfer (GIFT)
description: This topic explains how to configure and use the Canada Goods and Services Tax or Harmonized Sales Tax (GST/HST) Internet File Transfer (GIFT) feature.
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

# Canada GST/HST Internet File Transfer (GIFT)

[!include [banner](../includes/banner.md)]

Taxpayers in Canada use form GST 34 to manually file Goods and Services Tax or Harmonized Sales Tax (GST/HST) returns, and to remit payments to the Canada Revenue Agency (CRA). However, the CRA allows taxpayers to electronically file and remit taxes that are calculated on acquired fixed assets. You can electronically file GST/HST returns by using any of the following methods:

- **Net file transfer** – An internet-based filing service that taxpayers can use to file their returns directly over the internet.
- **Electronic Data Interchange (EDI)** – A data transfer method that taxpayers can use to file their returns either directly with the CRA or through a third-party service provider.
- **GST/HST Internet File Transfer (GIFT)** – An upload tool that taxpayers can use to submit text files to the CRA website to file GST/HST returns and remit payments.

Before you generate a GIFT file, you have to set up your software identification code, sales tax code, and sales tax group.

Use the following procedures to enter legal entity details, a sales tax code, and a sales tax group for GIFT, and to create sales tax entries for taxes that were paid on fixed asset acquisition.

## Set up legal entities for GIFT

When you submit a request to the CRA to do an internet file transfer, the CRA provides a software identification code. The first two characters are alphabetical, and the last six characters are numerical. To process your returns, you must enter this code on the **Legal entities** page.

1. Go to **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.
2. On the **Statutory reporting** FastTab, in the **Registration number** field, enter the registration number that the CRA provided when you registered for GST/HST.
3. In the **Software identification code** field, enter **AX030003** to transfer the returns.
4. Select **Account identifiers** to open the **Account identifiers** page.
5. On the **Overview** tab, in the **Program identifier** field, select **GST/HST**.
6. In the **Reference number** field, enter the reference number that the CRA provided.
7. Close the pages to save your changes.

## Set up tax codes for GIFT

Use the **Sales tax codes** page to set up tax codes to calculate GST/HST for the GIFT file.

1. Go to **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax codes**.
2. Press **Ctrl+N** to create a tax code.
3. In the **Sales tax code** field, enter a code, such as **GST/HST**, and then enter general information about the sales tax code.
4. On the **Calculation** tab, enter the calculation details that should be used to calculate the GST/HST amount.
5. Select **Values** to open the **Values** page.
6. Enter the dates when the tax code is in effect.
7. In the **Value** field, enter the percentage for the calculation.
8. Close the pages to save your changes.

## Set up tax groups for GIFT

Use the **Sales tax groups** page to set up sales tax groups. You can assign the sales tax groups to companies. Taxes will then be calculated based on the tax codes that were in effect when the transactions occurred.

1. Go to **General ledger** \> **Setup** \> **Sales tax** \> **Sales tax groups**.
2. Press **Ctrl+N** to create a sales tax group.
3. In the **Sales tax group** field, enter a name, such as **GST/HST**, and then enter general information about the sales tax group.
4. On the **Setup** tab, in the **Sales tax code** field, select a sales tax code to add to the sales tax group.
5. Close the page to save your changes.

## Generate a GIFT file

To file your GST/HST returns and remit payments, you can generate a GIFT file and upload it to the CRA website.

1. Go to **General ledger** \> **Periodic** \> **GST/HST Internet File Transfer (GIFT)**.
2. In the **From date** and **To date** fields, select the start and end dates of the reporting period.
3. In the **File name** field, select the path and enter the name of the GIFT file.

    > [!NOTE]
    > For easy identification of the GIFT file, use the format *GSTYYYYMMDD.tax* for the file name. (In other words, enter **GST** followed by the reporting date, and then add the **.tax** file name extension.) For example, if the reporting date is July 28, 2010, enter **GST20100728.tax** as the name of the GIFT file.

4. Select **OK** to export the GIFT file to the specified path.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
