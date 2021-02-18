---
# required metadata

title: 
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

# TDS parameters setup in accounts payable parameters and accounts receivable parameters

[!include [banner](../includes/banner.md)]

Follow these steps to set up parameters in the Accounts payable and Accounts receivable modules.

Go to **Tax > Setup > Parameters > Accounts receivable parameters > Updates > Update order lines**

[![Update order lines](./media/apac-ind-TDS-26.png)](./media/apac-ind-TDS-26.png) 

1. Under the **TDS** **group** field group, in the **Updating** **TDS** **group** field, specify the method used to update the TDS group in the line-level when the TDS group is updated in the header-level. The options are:

- **Never**: The TDS group is not updated in the order lines when the TDS group is updated in the order header.

- **Always**: The TDS group is updated automatically in the order lines when the TDS group is updated in the order header.

- **Prompt**: A message is displayed that prompts you to update the TDS group in the order lines.

2. Click **OK**.

Go to **Tax > Setup > Parameters > Accounts payable parameters > General** > **Split based on delivery information**

[![Split based on delivery information](./media/apac-ind-TDS-25.png)](./media/apac-ind-TDS-25.png)

3. In **Split based on delivery information** tab, select the **Product receipt** check box to post and split a product receipt with different delivery addresses and Tax Account Numbers (TAN). If you do not select this check box, you cannot post a purchase packing slip with different delivery addresses and Tax Account Numbers (TAN).

4. Select the **Invoice** check box to post and split a purchase invoice with different delivery addresses and Tax Account Numbers (TAN).

5. Close the form.
