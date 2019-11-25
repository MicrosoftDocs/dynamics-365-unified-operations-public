---
# required metadata

title: Preview features in Platform update 32 for Finance and Operations apps (February 2020)
description: This topic lists features that are in preview in Platform update 32 for Finance and Operations apps. 
author: sericks007
manager: AnnBe
ms.date: 11/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2019-11-30
ms.dyn365.ops.version: Platform update 32

---
# Preview features in Platform update 32 for Finance and Operations apps (February 2020)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists preview features that are new or changed for Platform update 32 for Finance and Operations apps. This version has a build number of 7.0.XXXX and is available as follows:

- Preview release is November 2019.
- General availability (self-update) is January 2020.
- Auto-update is February 2020.

For more information about Platform update 32, see [Additional resources](whats-new-platform-update-32.md#additional-resources).

## Features included in this release

### Data management export file size limit removed
When exporting files using Data management, there was a maximum file size of 256 MB. You can remove this limitation in Platform update 32 by implementing flight **DMFBlobSize256**. If needed, you can revert to the previous behavior if you encounter issues due to enabling this feature.

### Finance and Operations AOS (kernel) improvements
As we focus on continuous improvements to provide a more reliable and stable experience for our customers, this is a required milestone on this journey.

Starting with Platform update 32, AOS (kernel) will uptake Visual C++ 17 runtime libraries to take advantage of compiler performance optimizations. Platform engineers will benefit from the new upgrade while using their development environments to provide a more robust and reliable experience for our customers.

This will require that existing environments be updated to use the VC++ 17 redistributables.

- For Microsoft-managed Standard Acceptance Test Sandbox and higher (Tier 2 and higher) and Production environments, VC++ 17 redistributables are already installed and no action is needed.
- For Microsoft-managed Dev environment (Tier 1) customers, partners, and ISV’s will need to reboot their virtual machines before applying Platform update 32.
- For non-managed Dev, Build, Test, Demo (Tier 1), and on-premises environments, customers, partners, and ISV’s will need to download and install VC++ 17 redistributables from the shared asset library in Lifecycle Services and reboot their machines.

If you have the latest redistributables already installed, then no action is needed.

If you apply Platform update 32 and redistributables are missing, you might get an error when starting your services. If needed, refer to the following instructions to resolve this issue.

To install the redistributables:
1. Go to Lifecycle Services.
2. Select **Shared asset library**.
3. Select **Model** from the asset type list.
4. Select **VC++ 17 Redistributables**.
5. The download will automatically start.
6. Apply on your machine and reboot.

### Continued stabilization of saved views
For more information about saved views, see [User productivity – Saved views](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/user-productivity-saved-views).

### Improved responsiveness of Action Panes on smaller viewports
Pages with an Action Pane show the Action Pane collapsed when opened on a smaller screen, with no ability to pin open the Action pane in those situations.  

### Ability to filter on blank values with the Filter Pane and grid column filters
Users can now filter for blank values via the Filter Pane and grid column header filters. The syntax for looking for a blank value in a column is simply **""**.  

### Continued evolution of the new grid
The new grid provides a number of benefits: 

- **Performance**: The new grid provides improved rendering speed and a faster scrolling experience.
- **Positionally scroll**: Users are now able to positionally scroll in the data that has been loaded in the browser. For example, if you want to scroll through 10,000 rows in a grid, click the middle of the scrollbar to immediately position to record 5,000 without having to retrieve data from the server.  
- **General improvements**: The new grid eliminates issues from the existing grid with misalignment of grid headers and data, as well as the grid jumping while scrolling or creating new records. 
- **Reorder columns**: Users are now able to reorder columns by dragging and dropping. Simply hover the mouse over the column header, and a gripper for drag-and-drop will appear on the left side of the column.  
- **Mathematical formulas**: Users can now enter mathematical formulas into numeric cells in a grid. For example, a user could enter "=15*4. For the system to recognize the value as an expression, you simply need to start with an "=". 

The new grid also provides the ability to build more complex features into the new grid. These additions to the grid will be introduced and enhanced in subsequent monthly updates:

- **Totals**: Business users can see totals for numeric columns in tabular grids. For example, financial users will be able to view totals for a filtered set of transactions for a specific customer. This feature is first available as part of the new grid control feature starting in Platform update 29, and will continue to evolve in subsequent platform versions. 
- **Fast data entry**: This feature allows users to enter data in a grid ahead of the server, minimizing the need for users to wait for the server to validate a row before moving to another row in the grid. This feature is first available as part of the new grid control feature in Platform update 31, and will continue to evolve in subsequent platform versions. 

Starting in Platform update 31, the new grid control can be turned on for qualified environments using the Feature management workspace (see the steps below for instructions on how to enable the flight). For older updates, the new grid control is available by adding "&debug=reactGrid" to the environment URL.  

To enable the new grid while this feature is in preview, follow these steps:
1.  **Enable the flight** by using the following SQL statement:
    
    INSERT INTO SYSFLIGHTING (FLIGHTNAME, enabled, FLIGHTSERVICEID, PARTITION) VALUES('CLIReactGridEnableFeature', 1, 0, 5637144576);
    
2.  **Reset IIS** to flush the static flighting cache.
3.  Go to the **Feature management** workspace in your Finance and Operations app.
4.  Select the **New grid control** feature in the list of features, and then select Enable now in the details pane.
If New grid control does not appear in the list of features, select Check for updates.

All subsequent user sessions will start with the new grid enabled.

## Additional resources

### Platform update 32 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 32, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
