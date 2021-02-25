---
# required metadata

title: Set up payment schedules with TDS allocation
description: 
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

# Set up payment schedules with TDS allocation

[!include [banner](../includes/banner.md)]

This topic lists the steps for setting up payment schedules with Tax Deducted at Source (TDS) allocation.

Begin by opening the **Payment schedules** page t(**Accounts payable > Payment  setup > Payment schedules**).

[![Payment schedules](./media/apac-ind-TDS-27.png)](./media/apac-ind-TDS-27.png)

2. Click **New** to create a payment schedule. Enter the required details.

3. In the **Allocation** field, select the method to allocate the payment for the payment schedule. The options are:

- **Total**
- **Fixed amount**
- **Fixed quantity**
- **Specified**

4. If the **Total** option is selected in the **Allocation** field, the TDS allocation method for the payment schedule is displayed as **Total** in the **Withholding tax allocation** field. If the **Fixed amount**, **Fixed quantity**, or **Specified** option is selected in the **Allocation** field, the TDS allocation method for the payment schedule is displayed automatically as **Proportionally** in the **Withholding tax allocation** field.

   > [!Note]
   > If the **Withholding tax allocation**  field is set to **Total**, the payment installments are calculated based  on the gross amount including the TDS amount.  If the **Withholding tax allocation** field is set to **Proportionally**, the payment installments are calculated based on the net invoice amount after deducting the TDS amount.   

5. Enter the other required details and close the page.
