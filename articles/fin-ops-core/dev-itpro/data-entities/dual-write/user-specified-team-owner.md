---
title: User-specified team owner
description: Learn how to set a user-specified team owner and how to view the owning team after initial sync instead of using the default team owner.  
author: nhelgren
ms.author: nhelgren
ms.topic: article
ms.date: 04/26/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2021-04-26
ms.dyn365.ops.version: AX 7.0.0
---

# User-specified team owner

[!include [banner](../../includes/banner.md)]



In finance and operations apps, global tables are not associated with a company or legal entity. For these tables, you can specify a team and not use a default team as owner when writing to Microsoft Dataverse using dual-write. 

By default, when you enable dual-write, the root business unit’s default team will become the default owner for all rows integrated through dual-write. This may not be what you want when you want to limit access to these records to just a subset of users. It’s not uncommon for an organization to have multiple departments defined by business units with corresponding teams under them. You don’t want all users of the default team to have access to all the records integrated via dual-write. In these situations, you can specify a different team for each global table as an owner for these records. 

## Change the owning team

When you select a global table map such as **Global Products**, under **Table mappings**, you can view the list of teams in the **Update owning team** section. By default, dual-write uses the default team, which is indicated by a blank value. After you create a new map with a new version, you change the default behavior by picking a new team from the owning team list and then save the new value. The **Owning team** field is shown in the following screenshot.

:::image type="content" source="media/owning-team-1.png" alt-text="Update owning team.":::
  
>[!NOTE]
> After you set the owning team, it works across both initial and live sync. 
> The owning team setting does not transfer across environments. 

## View the owning team after initial sync

After you run the initial sync, the owner is shown in the integrated records. In the following screenshot, the owner has changed from **dwteam** to **Sales** for the integrated records in **Global Product** table map.
  
:::image type="content" source="media/owning-team-2.png" alt-text="Initial sync with default and user specified team.":::
  
[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

