---
# required metadata

title: TDS group, PAN, and TAN information setup for vendors and customers
description: This topic lists the steps for setting up the Tax Deducted at Source (TDS) group, PAN, and TAN information for vendors and customers.
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

# TDS group, PAN, and TAN information setup for vendors and customers

[!include [banner](../includes/banner.md)]

This topic lists the steps for setting up the Tax Deducted at Source (TDS) group, permanent account number (PAN), and tax account number (TAN) information for vendors and customers.

Begin by opening the **All customers** page (**Accounts payable > Vendors > All vendors** or **Accounts receivable > Customers > All customers**).

[![All vendors](./media/apac-ind-TDS-55.png)](./media/apac-ind-TDS-55.png)

1. Click **New** to create a new vendor or customer and enter the required details or select an existing customer.

2. Click the **Setup** tab. Under the **Withholding tax** field group, select the **Calculate withholding tax** check box to calculate withholding tax, TDS, or TCS for the vendor or customer.

3. In the **TDS group** field, select the default TDS group to calculate TDS for the vendor or customer. Calculate TDS of a purchase invoice based on the default TDS group defined for the vendor or customer.

   > [!Note]
   > The **Withholding tax group** field and **TCS group** field becomes unavailable when you select a TDS group in the **TDS group** field.   

4. Click the **Tax information** tab. Under the **PAN information** field group, in the **Status** field, select the status of the permanent account number for the vendor or customer. The options are:

   - **Not available**: Vendor or customer does not have a PAN.
   - **Received**: Vendor or customer has a PAN.
   - **Applied**: Vendor or customer has applied for a PAN.
   - **Invalid**: Vendor or customer has an invalid PAN. 

  [![Tax information (tab)](./media/apac-ind-TDS-56.png)](./media/apac-ind-TDS-56.png)

5. If the vendor or customer has a PAN and the PAN status is **Received**, enter the PAN information in the **Number** field. The PAN number must consist of 5 alpha characters, 4 numeric characters, and 1 alpha character. For example, ABCDE1260A.

6. If the vendor has applied for PAN and the PAN status is **Applied**, enter the reference number in the **Reference number** field. 

7. In the **Nature of assessee** field, select the nature of assessee category that the vendor or customer belongs to. The options are:

   - **Company**
   - **HUF**
   - **Firm**
   - **Individual**
   - **AOP**
   - **BOI**
   - **Local** **authority**
   - **Others**

8. In **Vendor > Registration** menu, click Registration IDs button. In the **Tax information** tab, click **Add** or **Edit** to maintain the tax registration entry.

9. In the **Withholding tax** tab, enter the **Tax Account Number (TAN)**. The registration number must consist of 4 alpha, 5 numeric, and one alpha character. For example, AFGH54821T.

10. Close the page.
