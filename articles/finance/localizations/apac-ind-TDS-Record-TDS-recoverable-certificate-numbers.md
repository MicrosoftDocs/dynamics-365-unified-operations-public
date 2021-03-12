---
# required metadata

title: Record TDS recoverable certificate numbers
description: This topic describes how to record the certificate numbers and dates for Tax Deducted at Source (TDS) certificates received for a specific vendor, customer, or ledger using the Recoverable certificates page.
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Record TDS recoverable certificate numbers

[!include [banner](../includes/banner.md)]

This topic describes how to record the certificate numbers and dates for Tax Deducted at Source (TDS) certificates received for a specific vendor, customer, or ledger using the **Recoverable certificates** page. You can update the TDS certificate numbers and dates recorded in this page for TDS transactions on the **Update certificate** page (**General ledger > Periodic > Withholding tax > Update certificate**). Close **TDS certificate numbers** after the update.

Follow the steps below to record the TDS certificate numbers and dates:

 Begin by opening the **Recoverable certificates** page (**Tax > Indirect tax > Withholding tax > Recoverable certificates**).

[![Recoverable certificates](./media/apac-ind-TDS-49.png)](./media/apac-ind-TDS-49.png) 

1. In the **Tax type** field, select the **TDS** option.

2. Click **NEW** to create a new record. In the **Certificate number** field, enter the TDS certificate number.

3. In the **Account** **type** field, select the account type that the TDS certificate is received for. The options are **Vendor**, **Customer**, or **Ledger**.

4. In the **Account** field, select the vendor, customer, or ledger account number based on the selected account type. In the **Name** field, view the vendor, customer, or ledger account name.

5.  In the **Certificate amount** field, enter the amount of the TDS certificate. In the **Date** field, enter the certificate date for the certificate number.

6. Click **Inquiries** button to open the **Certificate Transactions** page to view the TDS transactions that the TDS certificate number and date are updated for. This information can be updated on the **Updatecertificate** page (**Tax > Declarations > Withholding tax > Update certificate**). View the TDS transactions information in the following fields.

- **Date** field: Posting date of the TDS transaction.
- **Voucher** field: Voucher number of the TDS transaction.
- **Source** field: Module that the TDS transaction is created in.
- **Account** field: Vendor, customer, or ledger account number that the TDS transaction was created for.
- **Name** field: Vendor, customer, or ledger account name that the TDS transaction was created for.
- **Amount** field: Invoice amount that the TDS was calculated on.
- **Tax amount** field: TDS tax amount calculated for the transaction.
- **Certificate date** field: TDS certificate date updated for the TDS transaction.
- **Certificate number** field: TDS certificate number updated for the TDS transaction.

7. On the **Recoverable certificates** page, select the **Closed** check box to close the TDS certificate number after updating it for TDS transactions on the **Update certificate** page.

>   [!Note]
>   TDS certificate numbers with the **Closed** check box selected are not available in the **Update certificate** page.  

8. Click the **Mark all** button to select the **Closed** check box for all records on the page.
