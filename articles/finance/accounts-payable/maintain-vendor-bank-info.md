---
# required metadata

title: Maintain vendor bank account information
description: Vendors can use the Vendor collaboration functionality to maintain their bank account information. This article explains how to add and maintain bank information for vendors that you do business with.
author: v-kiarnd
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# 
# ms.tgt_pltfrm: 
ms.assetid: 10f56dea-ea2d-48ea-9622-4ef715eb1179
ms.search.region: USA
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2011-01-14
ms.dyn365.ops.version: AX 10.0.17

---

# Maintain vendor bank account information

[!include [banner](../includes/banner.md)]

Vendors can use the Vendor collaboration functionality to maintain their bank account information. This article explains how to add and maintain bank information for vendors that you do business with.

After you give access to vendors, they can add information for new bank accounts. You can then review that information and complete the pre-note process, so that the new accounts will be used for payments to those vendors.

You can maintain your vendor account in the **Vendor information** workspace. There, vendors will select **More details** and then **Bank accounts** from the drop-down list. To add a new bank account, select **Add** above the bank account grid. In the **New** dialog box that appears, you can enter the following information:

- Bank account
- Bank name
- Bank account number
- Bank routing number
- Effective date
- Expiration date
- Comments (optional)

SWIFT and the International Bank Account Number (IBAN) codes are required for all non-US based companies. You can update the SWIFT and IBAN requirements parameter on the **Accounts payable parameters** page after the feature is enabled.

If there are any documents that are related to the specific certification, you can attach them by selecting **Document**.

Bank information that vendors enter on the page will show **Vendor** as the source. You can also enter bank account information on a vendor's behalf. That information will appear here, and **Customer** will be shown as the source. For more information, see [Create a vendor bank account](../../supply-chain/procurement/tasks/create-vendor-bank-account.md).

After an account has been added, vendors can edit their bank's effective and expiration dates as required.

## Turn the vendor bank account information feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Maintain vendor bank information using vendor collaboration workspace* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Vendor collaboration-generated bank changes page

After vendors update their bank information, that information will be visible on the new **Vendor collaboration-generated bank changes** page that is available under **Accounts payable \> Inquiries \> Vendor reports**. By default, all newly entered or modified bank records are shown. The accounts payable clerk can view the changes and run the account information through the pre-note process to validate it. When this process is completed, and the primary payment method has been manually updated, the bank account that is shown on the **Vendor collaboration-generated bank changes** page can be selected and marked as reviewed. This action removes the account from the default list.

To view all changes that have been made to a vendor's bank information, you can change the filters to view the page by vendor account, effective date range, and whether the changes have been reviewed.
