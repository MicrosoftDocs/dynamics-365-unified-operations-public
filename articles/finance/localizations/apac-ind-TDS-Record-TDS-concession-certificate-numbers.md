---
# required metadata

title: Record TDS concession certificate numbers
description: This topic lists the steps for recording the Tax Deducted at Source (TDS) concession certificate numbers that are issued to vendors.
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

# Record TDS concession certificate numbers

This topic lists the steps for recording the Tax Deducted at Source (TDS) concession certificate numbers that are issued to vendors.

[!include [banner](../includes/banner.md)]

Begin by opening the **Withholding tax concsessions** page (**Tax > Indirect taxes > Withholding tax > Withholding tax concessions**).

 [![Withholding tax concessions](./media/apac-ind-TDS-34.png)](./media/apac-ind-TDS-34.png)

1. In the **Tax type** field, select the **TDS** option to record concession certificates for TDS tax type.

2. On the **Overview** tab, press ALT+N to create a new line. In the **Withholding tax code** field, select the TDS tax code that the vendor concession certificates are issued for. In the **Withholding tax code name** field, the name of the TDS tax code is displayed.

3. In the **From date** field, enter the starting date of validity for the concession certificate used to calculate TDS on a concessional basis for the vendor using the TDS tax code.

4. In the **To date** field, enter the ending date of validity for the concession certificate used to calculate TDS on a concessional basis for the vendor using the TDS tax code.

5. In the **Remarks** field, enter remarks, if any.

6. In the **Section** field, enter the legal section code that the TDS concession certificate is availed under.

   If the section code is defined as 197, the **Reason for non-deduction/lower deduction** column in Form 26Q and the **Reason for non-deduction/lower deduction/grossing up (if any)** column in the Form 27Q displays the value **A**.

   If the section code is defined as 197A, the **Reason for non-deduction/lower deduction** column in the Form 26Q and the **Reason for non-deduction/lower deduction/grossing up (if any)** column in the Form 27Q displays the value **B**.

7. Click the **Certificate** tab to record TDS concession certificate numbers for vendors. In the **Vendor account** field, select the vendor account that the TDS concession certificate is issued for.

8. Enter dates that define a period range for the validity of the TDS concession certificate in the **From date** and **To date** fields. 

   The calculation of TDS on a concessional basis is based on the period range that the certificate is created in for the vendor.

9. In the **Certificate** field, enter the TDS concession certificate number. 

   [![Certificate](./media/apac-ind-TDS-33.png)](./media/apac-ind-TDS-33.png)

10. Close the page.
