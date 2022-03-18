---
title: Edit a legal entity after dual-write setup
description: This topic explains how to add or remove a company or legal entity after dual-write has been set up.
author: nhelgren
ms.date: 07/21/2020
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: nhelgren
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Edit a legal entity after dual-write setup 

[!include [banner](../../includes/banner.md)]





The dual-write wizard enables you to add or remove a company or legal entity after dual-write has been set up. You can do this without having to unlink and relink your dual-write environment. 

The wizard enables you to link your Finance and Operations apps to Dataverse environments. As part of this wizard, you also can select one or more companies or legal entities. The company or legal entity list doesn’t remain static and is constantly changing. This is because you may need to add new companies, especially as part of a phased rollout or acquisitions. Until now, you were unable to add a company or legal entity without system down-time, which required you to unlink and relink your environment. All of this can be expensive, especially because of pre-existing data. With this feature, you can add a company in a live environment without the need to unlink your existing dual-write environment.

## Add a company or legal entity after dual-write has been set up 

Follow these steps to add a company or legal entity after dual-write has been set up.

1. On the **Dual-write table map** list page, select the **Environment details** button.

![Select the Environment details button.](media/select-environment-details.png)

2. On the **Legal entities** tab, you see the company that you selected as part of the dual-write wizard to link environments. In this example, the company is USMF.

![Legal entities tab displaying the selected company.](media/legal-entities.png)

3. Select **Add legal entity** to add one or more companies to dual-write. In this example, GBSI. Select **Save**.

![Add new legal entity.](media/add-legal-entity.png)

  At this point, the legal entities start updating. The table maps that are currently running or paused go through the initial write process by copying pre-existing data. Until the process is completed, we recommend that you do not perform any actions to modify your table maps. 

![Update legal entities is in progress.](media/update-progress.png)

  >[!NOTE]
  > This operation may fail if either of the following conditions are true: 
  >
  > * You add or remove a new company when one or more table maps is already in the Initial writes state. This the process where the system is copying pre-existing data. 
  >
  > * You remove a company when one or more table maps is in the Paused state. 

4. After the process is complete, a banner displays informing you that the legal entities have been updated successfully. You can now resume updates to your table maps. 

![Legal entities update succeeded.](media/legal-entities-updated.png)



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]