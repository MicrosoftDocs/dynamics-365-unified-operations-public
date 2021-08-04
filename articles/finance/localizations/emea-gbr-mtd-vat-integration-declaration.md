---
# required metadata

title: VAT setup details for VAT declaration of the United Kingdom
description: This topic gives an overview of details of VAT setup for VAT declaration of the United Kingdom (UK).
author: liza-golub
ms.date: 08/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 08/03/2021
ms.dyn365.ops.version: AX 10.0.22

---

# VAT setup details for VAT declaration of the United Kingdom

[!include [banner](../includes/banner.md)]

This topic gives an overview of details of VAT setup for VAT declaration of the United Kingdom (UK).

Information about the administration of VAT in the UK can be found on the official website for the British Tax Authority – HM Revenue & Customs: https://www.gov.uk/topic/business-tax/vat.

Once a company is registered for VAT, this company is required by British law to charge VAT on your sales of goods and services. The comapny is also entitled to reclaim VAT on Goods and Services that you have purchased.

There are currently three rates of VAT:

•	Standard rate - applies to most goods and services.

•	Reduced rate - applies to some goods and services, eg children’s car seats and home energy.

•	Zero rate	0% - applies to zero-rated goods and services, eg most food and children’s clothes.

The VAT rate businesses charge depends on their goods and services. Some things are exempt from VAT, such as postage stamps, financial and property transactions.
Some goods and services are outside the VAT tax system so you cannot charge or reclaim the VAT on them.
Rates can change and you must apply any changes to the rates from the date they change. For actuale information about VAT rates in the UK, see [VAT rates](https://www.gov.uk/vat-rates).

Company registered for VAT in the UK must submit a VAT Return to HM Revenue and Customs (HMRC) on periodical basis which is called accounting period. VAT Return must be submitted even if ther is no VAT to pay or reclaim.

The VAT return for the UK is build in boxes:

Box 1: VAT due in the period on sales and other outputs

Box 2: VAT due in the period on acquisitions of goods made in Northern Ireland from EU Member States

Box 3: total VAT due

Box 4: VAT reclaimed in the period on purchases and other inputs (including acquisitions from the EU)

Box 5: net VAT to pay to HMRC or reclaim

Box 6: total value of sales and all other outputs excluding any VAT

Box 7: total value of purchases and all other inputs excluding any VAT

Box 8: total value of all supplies of goods and related costs, excluding any VAT, from Northern Ireland to EU Member States (from 1st January 2021)

Box 9: total value of acquisitions of goods and related costs, excluding any VAT, from EU Member States to Northern Ireland (from 1st January 2021)

In Dynamics 365 Finance, the described below setup must be done to ensure correctness of calculation of VAT return.

