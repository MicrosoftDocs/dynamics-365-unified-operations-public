---
# required metadata

title: Withholding tax codes setup for TDS tax type
description: This topic lists the steps for setting up tax codes for Tax Deducted at Source (TDS). 
author: GitHub_ID
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
ms.author: MS_Alias
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Withholding tax codes setup for TDS tax type

This topic lists the steps for setting up tax codes for Tax Deducted at Source (TDS). 

Begin by opening the **Withholding tax codes** page (**Tax > Setup > Withholding tax > Withholding tax codes**).

[![Withholding tax codes](./media/apac-ind-TDS-17.png)](./media/apac-ind-TDS-17.png)

1. Click **New** to create a withholding tax code for TDS and enter the required details.

2. In the **Tax type** field, select the **TDS** option to categorize the tax code as a TDS tax code.

3. In the **Settlement period** field, select the TDS settlement period for the TDS tax code. In the **Account** field, select the ledger account to post the TDS amount to.

4. In the **Receivable** **account** field, select the receivable account to post the TDS amount that is deducted in sales transactions.

5. In the **Origin** field, the **Percentage of gross amount** option is displayed and can't be changed. 

>   [!Note]
>   You cannot set the origin to **Percentage of net amount** for a TDS tax type.   

6. In the **Withholding tax component** field, select the TDS tax component for the TDS tax code.

7. Click the **Values** button to open the **Withholding tax values** pshr. In the **From date** field and the **To date** field, enter the starting date and ending date for the TDS value. 

>   [!Note]
>   The **Minimum limit** field, **Upper limit** field, and the **Exclude %** field are not available for the tax codes with TDS tax type.   

8. In the **Value** field, enter the percentage of TDS for the TDS tax code.  

9. Close the **Withholding tax values** page to return to **Withholding tax codes**.

>   [!Note]
>   The **Limits** button is not available for TDS tax type.  

10. Close the page.
