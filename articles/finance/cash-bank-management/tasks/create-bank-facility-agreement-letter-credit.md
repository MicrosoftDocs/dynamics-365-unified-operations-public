--- 
title: Create a bank facility agreement for a letter of credit
description: Learn about creating a bank facility agreement for a letter of credit, including a detailed step-by-step process, which uses the demo company "USMF".
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 05/27/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: BankDocumentFacilityAgreement, BankAccountTableLookUp, BankDocumentFacilityAgreementExtension, DefaultDashboard
ms.dyn365.ops.version: Version 7.0.0 
---

# Create a bank facility agreement for a letter of credit

[!include [banner](../../includes/banner.md)]

This article describes the steps for creating a bank facility agreement to process a letter of credit. For more information, see [Set up bank facilities and posting profiles](set-up-bank-facilities-posting-profiles-letter-credit.md) before running the steps in this article.

## Create bank facility agreement

1. Go to **Cash and bank management > Letters of credit > Bank facility agreements**.
1. Select **New**.
1. In the **Agreement number** field, enter the agreement number according to the agreement with the bank.
1. In the **Bank account** field, enter the account number at the issuing bank.
1. In the **Start date** field, enter a start date and time of the agreement.
1. In the **End date** field, enter a date and time of the agreement.
1. Expand or collapse the **General** section.
1. Select **Add line**.
1. In the **Facility type** field, select the drop-down button to open the lookup and select a record.
1. In the **Limit** field, enter the facility amount that you negotiated with the bank.
1. Select **Save**.
1. To extend the agreement, select **Extend** and open the drop dialog.
1. Type a value in the **New agreement number** field.
1. Enter an end date and time in the **End date** field.
1. Select **Extend**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
