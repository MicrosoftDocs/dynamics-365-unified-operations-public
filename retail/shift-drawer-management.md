---
# required metadata

title: Shift and cash drawer management
description: This article explains how to set up and use the two types of retail point of sale (POS) shifts -  shared and stand-alone. Shared shifts can be used by multiple users in multiple places, whereas stand-alone shifts can be used by only one worker at a time.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2041
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 105011
ms.assetid: 49a0fcc9-d4db-45ad-8c4b-213ccaced82b
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Shift and cash drawer management

[!include[banner](includes/banner.md)]


This article explains how to set up and use the two types of retail point of sale (POS) shifts -  shared and stand-alone. Shared shifts can be used by multiple users in multiple places, whereas stand-alone shifts can be used by only one worker at a time.

There are two types of retail point of sale (POS) shifts: stand-alone and shared. Stand-alone shifts can be used by only one worker at a time. Shared shifts can be used by multiple users in multiple places. Therefore, they effectively create a single shift for multiple workers in a store.

## Standalone shifts
Stand-alone shifts are used in a traditional, fixed POS scenario, where cash is reconciled independently for each POS register. For example, in a grocery store setting, there are typically several fixed POS registers, and a cashier is assigned to each register. In this case, each register likely uses a stand-alone shift, and the cashier is responsible for the till or physical cash at that register. A stand-alone shift encompasses all the activity on that register during the cashier’s work shift. Activities can include the opening amount that is deposited in the till, all removal and addition of cash through operations such as bank drops and float entry, and the tender declaration at the end of the shift.

### Set up a stand-alone shift

A stand-alone shift is designated at the cash drawer level. This procedure explains how to set up a stand-alone shift on a POS register.

1.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2.  Select the hardware profile to use for the stand-alone shift.
3.  On the **Drawer** FastTab, confirm that the **Shared shift drawer** option is set to **No**.
4.  Click **Save**.
5.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**.
6.  Select the register that requires a stand-alone shift, and then click **Edit**.
7.  In the **Hardware profile** field, select the hardware profile that you selected in step 2.
8.  Click **Save**.
9.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
10. Select the **1090** distribution schedule, and then click **Run now** to synchronize changes to the POS.

### Use a stand-alone shift

1.  Sign in to the POS.
2.  If no shift is open, select **Open a new shift**.
3.  Go to the **Declare start amount** operation, and specify the amount of cash that is being added to the till to start the work day.
4.  Perform some transactions.
5.  At the end of the day, select **Declare tender** to declare the amount of cash that remains in the cash drawer.
6.  Enter the amount of cash, and then click **Save** to save the tender declaration.
7.  Select **Close shift** to close the shift.

**Note:** Other operations are available during the shift, depending on the business processes that are in place. The **Safe drop**, **Bank drop**, and **Tender removal** operations can be used to remove money from the till during the day or before the shift is closed. If a till runs low on cash, the **Float entry** operation can be used to add cash to the till.

## Shared shifts
A shared shift is used in an environment where multiple cashiers share a cash drawer or a set of cash drawers throughout the work day. Typically, a shared shift is used in mobile POS environments. In a mobile environment, each cashier isn’t assigned to and responsible for a single cash drawer. Instead, all cashiers must be able to tender a sale and add cash to whatever cash drawer is closest to them. In this scenario, the cash drawers that are shared among cashiers are included in a shared shift. All the cash drawers in a shared shift are included in the same shift for the purpose of activities that are related to cash management for that shift. Therefore, the starting amount for the shift should include the sum of all cash in all the cash drawers that are included in the shared shift. Likewise, the tender declaration will be the sum of all the cash in all the cash drawers that are included in the shared shift. **Note:** Only one shared shift can be open at a time in each store. Shared shifts and stand-alone shifts can be used in the same store.

### Set up a shared shift

1.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**.
2.  Select the hardware profile to use for the shared shift.
3.  On the **Drawer** FastTab, set the **Shared shift drawer** option to **Yes**.
4.  Click **Save**.
5.  Click **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Registers**.
6.  Select the register that requires a shared shift, and then click **Edit**.
7.  In the **Hardware profile** field, select the hardware profile that you selected in step 2.
8.  Click **Save**.
9.  Click **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
10. Select the **1090** distribution schedule, and then click **Run now** to synchronize changes to the POS.

### Use a shared shift

1.  Sign in to the POS.
2.  If the POS isn’t yet connected to a hardware station, select **Non-drawer operation**, and then select the **Select hardware station** operation to make a hardware station active for the shared shift. This step is required only the first time that a register is added to a shared shift environment.
3.  Sign out of the POS, and then sign back in.
4.  Select **Create a new shift**.
5.  Select **Declare start amount**.
6.  Enter the starting amount of all the cash drawers in the store that are part of the shared shift, and then click **Save**.
    -   To add part of the starting amount to each subsequent cash drawer, use the **Select hardware station** operation to make the hardware station active.
    -   To add a till to a specific cash drawer, use the **Open drawer** operation.
    -   Continue until all cash drawers in the shared shift have their part of the starting amount.

7.  At the end of the day, open each cash drawer, and remove the cash.
8.  After you’ve removed the cash from the last cash drawer, count all the cash from all the cash drawers.
9.  Use the **Declare tender** operation to declare the total amount of cash from all the cash drawers that are included in the shared shift.
10. Use the **Close shift** operation to close the shared shift.




