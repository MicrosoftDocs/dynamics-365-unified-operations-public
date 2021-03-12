---
# required metadata

title: Run the periodic TDS settlement process
description: This topic lists the steps to complete for settling periodic Tax Deducted at Source (TDS).
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

# Run the periodic TDS settlement process

[!include [banner](../includes/banner.md)

This topic lists the steps to complete for settling periodic Tax Deducted at Source (TDS).

Begin by opening the **Withholding tax payment** page (**Tax > Declarations > Withholding tax > Withholding tax payment**).

[![Withholding tax payment](./media/apac-ind-TDS-47.png)](./media/apac-ind-TDS-47.png)

1. In the **Tax type** field, select the **TDS** option.

2. In the **Tax Account Number (TAN)** field, select the Tax Account Number to run the settlement process for.

3. In the **Withholding tax component group** field, select the TDS component group to run the settlement process for.

4. In the **Settlement period** field, select the TDS settlement period to run the settlement process for. 

>   [!Note]
>   The TDS settlement process is run for all periods that are set up for the TDS settlement period in the **Periods** tab (**Tax > Indirect taxes > Withholding tax > Withholding tax settlement periods  > Periods**).   

5. In the **From date** field, select the starting date to run the TDS settlement process from.

   For a specific period within the settlement period, the starting date that is defined for the period is taken as the **From** date. Example; the TDS settlement period has 2 periods, that is 04/01/2009 to 04/30/2009 and 05/01/2009 to 05/31/2009. If 04/06/2009 is entered as the starting date in the **From date** field, the settlement process will still run from 04/01/2009.

   If a later period is entered in the **From date** field without settling a previous period within the settlement period, the settlement will not take place for any previous periods. For example, suppose the TDS settlement period has three periods 04/01/2009 to 04/30/2009, 05/01/2009 to 05/31/2009, and 06/01/2009 to 06/30/2009. If 05/01/2009 is entered as the starting date in the **From date** field, the settlement process will only run from 05/01/2009 to 05/31/2009. The settlement process will not take place for 04/01/2009 to 04/30/2009.

6. In the **Transaction date** field, select the date to post the TDS settlement transaction.

7. In the **Withholding tax payment version** field, select the TDS settlement version. The options are:

- **Original**: Use this option to run the TDS settlement process the first time. The TDS settlement process is run only once using the Original payment version for a Tax Account Number (TAN), withholding tax component group, and withholding tax settlement period combination.
- **Latest versions:** Use this option if the TDS settlement process has been run once already for the specified period. Include back-dated transactions posted after the settlement process was run once for the period. Run the settlement process using the **Latest versions** option any number of times.

8. Select the **Update** check box to run the TDS settlement process and post the amounts to the ledger accounts. If this check box is cleared, the settlement process won't take place and the financial entries won't be generated.

9. Click **OK** to run the TDS settlement process and generate the withholding tax payment report. The TDS transactions that are included in the settlement process are displayed with the **Settled** status on the **Settlement** page (**Accounts payable > Payments > Vendor payment journal > Lines button > Functions button > Settlement**).

### Important points

- If a withholding tax component group isn't selected during the settlement process, the settlement takes place for all the withholding tax component groups for the selected TAN and settlement period. Separate lines are created for each withholding tax component group in the **Open transaction editing** page.
- The settlement process takes place based on the nature of assessee for a settlement period. The transactions with **Company** as the nature of assessee are settled and displayed on the **Open transaction editing** page as one line. The transactions with nature of assessee other than **Company** are settled and displayed on the **Open transaction editing** page as one line.
- The due date for the settled TDS transaction lines in the **Open transaction editing** page is based on the terms of payment defined for the TDS authority vendor in the **Vendors** page. If the terms of payments are not defined for the TDS authority vendor, the last day of the settlement period is displayed as the due date.
