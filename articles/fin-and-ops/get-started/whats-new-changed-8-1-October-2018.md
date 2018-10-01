---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 8.1 (October 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 8.1. This version was released in October 2018.
author: tonyafehr
manager: AnnBe
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: b264a51c-52d1-45c5-b698-64c5242c592a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2018-10-01 
ms.dyn365.ops.version: Release 8.1

---
# What's new or changed in Dynamics 365 for Finance and Operations version 8.1 (October 2018)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 8.1 (October 2018). This version was released in October 2018 and has build number 8.1.136.24.

### Announcing the Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

## Use shared number sequences to copy customers or vendors
You can use shared number sequences to assign customer IDs or vendor IDs. Shared number sequences also let you copy customers or vendors from one legal entity to another legal entity but use the same IDs in both legal entities.

## Customer transactions list page
The **View settlements** button on the Action Pane provides quick access to the settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

The **Global transactions** button has been added to the customer page. This button lets you view all transactions for a customer across all legal entities. The **Customer transactions** list page shows transactions only for the legal entities that the user has access to, based on his or her security settings.

The filter for showing open transactions has been replaced with a new filter that lets you view more combinations of transactions. 

You can also update due dates and discount dates for open customer transactions, and you can now add due dates to the **Customer transactions** list page. 

## Vendor transactions list page 
The **View settlements** button on the Action Pane provides quick access to the settlement history and more information about the whole settlement transaction. You can also show additional transactions that are related to the selected transaction, either because they were part of the same settlement or because they are payments that were created in the same payment journal.

The **Global transactions** button has been added to the vendor page. This button lets you view all transactions for a vendor across all legal entities. The **Vendor transactions** list page shows transactions only for the legal entities that the user has access to, based on his or her security settings.

The filter for showing open transactions has been replaced with a new filter that lets you view more combinations of transactions. A **Hide currency revaluations** filter has also been added that lets you hide currency translation transactions. 

You can also update due dates and discount dates for open customer transactions. In release 8.1, the experience has been improved so that you can now add due dates to the **Vendor transactions** list page. 

## Financial dimensions
Use the **Financial dimensions** page to create financial dimensions that you can use as account segments for charts of accounts. There are two types of financial dimensions: custom dimensions and entity-backed dimensions. Custom dimensions are shared across legal entities, and the values are entered and maintained by users. For entity-backed dimensions, the values are defined somewhere else in the system, such as in Customers or Stores entities. Some entity-backed dimensions are shared across legal entities, whereas other entity-backed dimensions are company specific.

You can use financial dimensions to represent legal entities. You don't have to create the legal entities in Microsoft Dynamics 365 for Finance and Operations. However, financial dimensions aren't designed to address the operational or business requirements of legal entities. The interunit accounting functionality in Finance and Operations is designed to address only the accounting entries that are created by each transaction.

## Extensibility enhancements
In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility through chain of command, delegates, or by providing access to members. In addition, enhancements have been made to enumerations and SQL operations. For detailed information, see [Extensibility changes in Dynamics 365 for Finance and Operations version 8.1](../dev-itpro/extensibility/extensibility-changes-81.md) 

## Phantom items


## VAT reporting for the United Arab Emirates	
Standard sales tax functionality in Finance and Operations now fulfils the majority of legislation requirements of United Arab Emirates VAT law. The following country-specific features are specific to the United Arab Emirates:

  - Legal Entity configuration has been extended with additional fields required in VAT reporting.
  - VAT Reverse Charge functionality has been enabled for UAE (ARE country context) to properly record taxable domestic operations within GCC territory.
  - Additional sales, invoice, and credit notes print layouts have been added with additional columns and VAT summary information.
  - Sales Invoice and Credit notes for UAE are printing in two languages including new ar-AE Arabic language for user interface.
  - VAT Return declaration report is printed to electronic file format ready for uploading to e-TAX FTA portal.
  - Standard Audit File functionality has been shared with UAE local functionality. Required by Federal Tax Authorities FTA VAT audit file - (FAF) can be exported accordingly to required Comma separated file format.
