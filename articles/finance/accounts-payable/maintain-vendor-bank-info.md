---
# required metadata

title: Maintain vendor bank account information
description: Vendors can use the Vendor collaboration functionality to maintain their bank account information. This topic explains how to add and maintain bank information for vendors that you do business with.
author: v-kiarnd
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 26181
ms.assetid: 10f56dea-ea2d-48ea-9622-4ef715eb1179
ms.search.region: USA
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2011-01-14
ms.dyn365.ops.version: AX 10.0.17

---

# Maintain vendor bank account information

[!include [banner](../includes/banner.md)]

Vendors can use the Vendor collaboration functionality to maintain their bank account information. This topic explains how to add and maintain bank information for vendors that you do business with.

After you give access to vendors, they can add information for new bank accounts. You can then review that information and complete the pre-note process, so that the new accounts will be used for payments to those vendors.

You can maintain your vendor account in the **Vendor information** workspace. There, vendors will select **More details** and then **Bank accounts** from the drop-down list. To add a new bank account, select **Add** above the bank account grid. In the **New** dialog box that appears, you can enter the following information:

- Bank account
- Bank name
- Bank account number
- Bank routing number
- Effective date
- Expiration date
- Comments (optional)

If the legal entity is outside the United States, the dialog box also includes fields for the SWIFT code and the International Bank Account Number (IBAN).

If there are any documents that are related to the specific certification, you can attach them by selecting **Document**.

Bank information that vendors enter on the page will show **Vendor** as the source. You can also enter bank account information on a vendor's behalf. That information will appear here, and **Customer** will be shown as the source. For more information, see [Create a vendor bank account](../../supply-chain/procurement/tasks/create-vendor-bank-account.md).

After an account has been added, vendors can edit their bank's effective and expiration dates as required.

## Vendor collaboration-generated bank changes page

After vendors update their bank information, that information will be visible on the new **Vendor collaboration-generated bank changes** page that is available under **Accounts payable \> Inquiries \> Vendor reports**. By default, all newly entered or modified bank records are shown. The accounts payable clerk can view the changes and run the account information through the pre-note process to validate it. When this process is completed, and the primary payment method has been manually updated, the bank account that is shown on the **Vendor collaboration-generated bank changes** page can be selected and marked as reviewed. This action removes the account from the default list.

To view all changes that have been made to a vendor's bank information, you can change the filters to view the page by vendor account, effective date range, and whether the changes have been reviewed.
