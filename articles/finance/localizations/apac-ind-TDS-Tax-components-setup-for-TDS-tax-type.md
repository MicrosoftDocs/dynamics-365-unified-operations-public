---
# required metadata

title: Set up tax components for the TDS tax type
description: This topic describes the process of setting up withholding tax components for the Tax Deducted at Source (TDS) tax type. The topic also describes the process of defining the threshold for calculating TDS for each TDS component.
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
# Set up tax components for the TDS tax type

[!include [banner](../includes/banner.md)]

This topic describes the process of setting up withholding tax components for the Tax Deducted at Source (TDS) tax type. The topic also describes the process of defining the threshold for calculating TDS for each TDS component. The different TDS components are TDS, surcharge, PE-Cess, and SHE Cess. You also can define an exception threshold to calculate TDS for each TDS component. Follow these steps to set up TDS components.

Go to **Tax > Setup > Withholding tax > Withholding tax component**

[![Withholding tax component](./media/apac-ind-TDS-9.png)](./media/apac-ind-TDS-9.png)

1. In the **Tax** **type** field, select the **TDS** option to set up withholding tax components for TDS tax type.

2. Click **New** to create a new line. In the **Withholding** **tax** **component** field, enter a name for the TDS component. In the **Description** field, enter a description for the TDS component.

3. In the **Withholding** **tax** **component** **group** field, select the TDS withholding tax component group to attach the TDS component to.

4. Click the **Threshold** button to open **Threshold** form to define the threshold limit to calculate TDS for the TDS component.

5. In the **From** **date** field and **To** **date** field, select the period range that the threshold limit is applied for.

6. In the **Threshold** field, enter the threshold amount limit to calculate TDS for the TDS component. The tax is deducted at source only when the cumulative invoice amount has crossed the threshold limit.

   For example, if the threshold limit is 10000, the TDS is calculated after the cumulative invoice amount has crossed 10000, that is, 10001 or above.

7. In the **Exception** **threshold** field, enter the exception threshold amount limit to calculate TDS for the TDS component. The tax is deducted at source on an invoice line if the amount has crossed the exception threshold limit.

   For example, if the exception threshold limit is 5000, the TDS is calculated on a specific invoice line if the invoice line amount has crossed 5000, which is, 5001 or above.

[![Threshold](./media/apac-ind-TDS-10.png)](./media/apac-ind-TDS-10.png)

>   [!Note]
>
>   The exception threshold amount must be  lesser than or equal to the threshold amount.  

>   [!Note]
>
>   The tax is deducted for a transaction  if the transaction amount crosses the exception threshold limit even if the  cumulative invoice amount does not cross the threshold limit specified in the  **Threshold** field.  

8. Close the **Threshold** form to return to the **Withholding** **tax** **components** form.

9. Click the **Copy** button to open the **Copy** **withholding** **tax** **components** form to copy the TDS components set up for a TDS component group to another TDS component group.

10. In the **From** field, select the TDS component group to copy the TDS components from. In the **To** field, select the withholding tax component group to copy the TDS components to.

>   **NOTE**: The common TDS components that are  attached to both the TDS component groups are not copied.  

11. Click **OK** to copy and create TDS components for the other TDS component group in the **Withholding** **tax** **components** form.

 [![Copy withholding tax component](./media/apac-ind-TDS-11.png)](./media/apac-ind-TDS-11.png)

12. Close the form.



 
