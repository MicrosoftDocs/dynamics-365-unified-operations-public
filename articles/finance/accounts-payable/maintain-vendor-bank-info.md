---
title: Maintain vendor bank account information
description: Learn about how to add and maintain bank information for vendors that you do business with, including an outline on toggling vendor bank account information.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: USA
ms.search.industry: Public sector
ms.search.validFrom: 2011-01-14
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: 10f56dea-ea2d-48ea-9622-4ef715eb1179
---

# Maintain vendor bank account information

[!include [banner](../includes/banner.md)]

Vendors can use the Vendor collaboration functionality to maintain their bank account information. This article explains how to add and maintain bank information for vendors that you do business with.

After you give access to vendors, they can add information for new bank accounts. You can then review that information and complete the pre-note process, so that the new accounts are used for payments to those vendors.

You can maintain your vendor account in the **Vendor information** workspace. There, vendors select **More details** and then **Bank accounts** from the drop-down list. To add a new bank account, select **Add** above the bank account grid. In the **New** dialog box that appears, enter the following information:

- Bank account
- Bank name
- Bank account number
- Bank routing number
- Effective date
- Expiration date
- Comments (optional)

SWIFT and the International Bank Account Number (IBAN) codes are required for all non-US based companies. You can update the SWIFT and IBAN requirements parameter on the **Accounts payable parameters** page after the feature is enabled.

If there are any documents that are related to the specific certification, you can attach them by selecting **Document**.

Bank information that vendors enter on the page shows **Vendor** as the source. You can also enter bank account information on a vendor's behalf. That information appears here, and **Customer** is shown as the source. For more information, see [Create a vendor bank account](../../supply-chain/procurement/tasks/create-vendor-bank-account.md).

After an account is added, vendors can edit their bank's effective and expiration dates as required.

### Vendor collaboration-generated bank changes page

After vendors update their bank information, you can see that information on the new **Vendor collaboration-generated bank changes** page, available under **Accounts payable \> Inquiries \> Vendor reports**. By default, the page shows all newly entered or modified bank records. The accounts payable clerk can view the changes and run the account information through the pre-note process to validate it. When this process is complete and the primary payment method is manually updated, you can select and mark the bank account as reviewed on the **Vendor collaboration-generated bank changes** page. This action removes the account from the default list.

To view all changes to a vendor's bank information, change the filters to view the page by vendor account, effective date range, and whether the changes are reviewed.
