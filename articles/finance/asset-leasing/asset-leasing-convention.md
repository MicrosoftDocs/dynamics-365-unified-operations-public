---
# required metadata

title: Asset leasing conventions 
description: This topic describes conventions for leased assets
author: moaamer
manager: Ann Beebe
ms.date: 1/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: AssetLease
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations, Finance

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2021-1-28
ms.dyn365.ops.version: 10.0.17


---

# Asset leasing conventions  

This topic describes conventions for leased assets. Leasing conventions are used to determine the commencement date of a lease book. If the leasing convention is set to **None**, the commencement date is the same as the starting date for the lease. If the Leasing convention is set to **Full month**, the commencement date is the first day of the month in the **Lease start date** field. 

The commencement date determines period start date of the liability amortization and asset depreciation schedules. Interest expense and depreciation expense are posted on the period end date of their respective schedules. The initial recognition and adjustment journal entry are posted on the commencement date. 
 > [!NOTE] 
 > This is a feature enabled through the Feature Management workspace. Please navigate to the Feature Management workspace and enable the Leasing convention for asset leasing feature. 

Leasing conventions are assigned to the setup for a lease asset book.  

1. To view or assign the leasing convention, in the setup area of Asset leasing, select **Lease books**.  
2. Select an option from the **Leasing convention** dropdown list and click **Save**. 

   | Leasing convention | Description |
   | ------------------ | ----------- |
   | None               | The liability amortization and asset depreciation schedules start on the Lease start date because the commencement date is equal to the starting date of the lease. The period end date is one month later. This method does not guarantee the interest will be posted on the last day of each month. |
   | Full month         | For leases that have a starting date that occurs at any time during the month, the liability amortization and asset depreciation schedules start to accrue expense on the first day of that month. This convention ensures that interest is accrued on the last day of each month for the entire month. |

3. When creating a lease, the commencement date on each book will be entered automatically based on the value entered in the lease start date and the leasing convention specified for the book. 
