---
# required metadata

title: Set up withholding tax reporting codes for the TDS tax type
description: Withholding tax reporting codes are used to generate Form 26Q and Form 27Q statements for Tax Deducted at Source (TDS). This article explains how to set up withholding tax reporting codes steps so that you can set up TDS reporting codes.
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Set up withholding tax reporting codes for the TDS tax type

[!include [banner](../includes/banner.md)]

Withholding tax reporting codes are used to generate Form 26Q and Form 27Q statements for Tax Deducted at Source (TDS). This article explains how to set up withholding tax reporting codes steps so that you can set up TDS reporting codes.

1. Go to **Tax \> Setup \> Withholding tax \> Withholding tax reporting codes**.

    [![Withholding tax reporting codes page.](./media/apac-ind-TDS-16.png)](./media/apac-ind-TDS-16.png)

2. In the **Tax type** field, select **TDS** to define withholding tax reporting codes for the TDS tax type.
3. In the **Withholding tax component** field, select the TDS component to that you're defining the withholding tax reporting code for. The **Withholding tax component group** field shows the TDS component group that was defined for the TDS component that you're defining.

    The **Section code** field on the **General** FastTab shows the section code that is attached to the TDS component group.

4. On the **General** FastTab, in the **Reporting code** field, select the TDS reporting code:

    - TDS
    - TCS
    - Surcharge
    - PE\_Cess
    - SHE\_Cess

5. Close the page.
