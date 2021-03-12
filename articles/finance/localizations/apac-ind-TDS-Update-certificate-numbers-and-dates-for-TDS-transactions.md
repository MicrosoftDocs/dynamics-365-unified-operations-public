---
# required metadata

title: Update certificate numbers and dates for TDS transactions
description: This topic lists the steps for updating the recoverable certificate numbers and dates recorded for vendor, customer, and ledger accounts for Tax Deducted at Source (TDS). 
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

# Update certificate numbers and dates for TDS transactions

[!include [banner](../includes/banner.md)]

This topic lists the steps for updating the recoverable certificate numbers and dates recorded for vendor, customer, and ledger accounts for Tax Deducted at Source (TDS). You can view certificates for TDS transactions on the **Recoverable certificates** page. You can update the certificates using the **Update Certificates** page.

Complete the following steps to update certificate numbers and dates for TDS transactions.

To begin, open the **Update certificate** (**Tax > Declarations > Withholding tax > Update certificate**). 

 [![Update certificate](./media/apac-ind-TDS-45.png)](./media/apac-ind-TDS-45.png)

1. Under the **Select** field group, in the **Tax type** field, select the **TDS** option.

2. In the **Certificate number** field, select the customer or vendor TDS certificate number. In the **Certificate date** field, view the certificate date.

>   [!Note]
>   The TDS certificate numbers that the **Closed**  check box isn't selected for in the **Recoverable certificates** page are only available for selection in the **Certificate number**  field.   

3. In the **Account type** field, the account type that the TDS certificate number is received for is displayed. In the **Name** field, the account name is displayed.

4. In the **From date** field and the **To date** field, select the starting date and ending date range to display the TDS transactions.

5. Click the **Show data** button to display the TDS transactions posted during the selected period range in the grid area (upper-pane).

6. In the **Overview** tab (upper-pane), view details of TDS transactions that are posted during the selected period range for the vendor or customer in the following fields:

- **Voucher**: Voucher number of the TDS transaction.
- **Date**: Date of the TDS transaction.
- **Amount**: Invoice amount that the TDS was calculated on.
- **Tax amount**: TDS tax amount calculated for the transaction.

7.  Click the **Include** button to move a specific **TDS transaction** from the grid area (upper-pane) to the grid area (lower-pane). Click the **Include all** button to move all TDS transactions from the grid area (upper-pane) to the grid area (lower-pane).

   Click the **Exclude** button or **Exclude all** button to move back a specific TDS transaction or all TDS transactions from the grid area (lower-pane) to the grid area (upper-pane).

8. Click the **Update** button to update the certificate number and certificate date for TDS transactions that are displayed in the grid area (lower-pane) in the **Certificate number** field and in the **Certificate date** field respectively.

9. Click **Tax > Indirect taxes > Withholding tax > Recoverable certificate > Inquiry button** to view the updated transaction lines with the certificate numbers on the **Certificate transactions** page.

 [![Certificate transactions](./media/apac-ind-TDS-46.png)](./media/apac-ind-TDS-46.png)
