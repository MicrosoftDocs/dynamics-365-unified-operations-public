---
# required metadata

title: Set up withholding tax authorities for TDS tax type
description: This topic lists the steps for setting up the Tax Deducted at Source (TDS) authorities.
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

# Set up withholding tax authorities for TDS tax type

[!include [banner](../includes/banner.md)]

This topic lists the steps for setting up the Tax Deducted at Source (TDS) authorities.

Open the **Withholding tax authorities** page (**Tax > Indirect Taxes > Withholding tax authorities**).

[![Withholding tax authorities](./media/apac-ind-TDS-12.png)](./media/apac-ind-TDS-12.png)

1. In the **Tax type** field, select the **TDS** option to set up withholding tax authorities for TDS tax type.

2. Click **New** to create a new line. In the **Withholding tax authority** field, enter a name for the TDS authority. In the **Description** field, enter a description for the TDS authority.

3. In the **Vendor** **account** field, select the vendor account for the TDS authority. 

   > [!Note]
   > You must define the name of the bank where funds that are owed to the TDS authority vendor will be deposited. The bank's name is defined on the **Bank accounts** page (**Accounts payable > Vendors > Setup button > Bank accounts**).

4. Close the page.
