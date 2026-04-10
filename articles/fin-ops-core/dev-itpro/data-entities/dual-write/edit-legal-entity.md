---
title: Edit a legal entity after dual-write setup
description: Learn about how to add or remove a company or legal entity after dual-write has been set up, including a step-by-step overview.
author: nhelgren
ms.author: nhelgren
ms.topic: install-set-up-deploy
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Edit a legal entity after dual-write setup 

[!include [banner](../../includes/banner.md)]

The dual-write wizard enables you to add or remove a company or legal entity after dual-write setup. You don't need to unlink and relink your dual-write environment.

The wizard enables you to link your finance and operations apps to Dataverse environments. As part of this wizard, you can select one or more companies or legal entities. The company or legal entity list doesn't remain static and is constantly changing. This constant change happens because you might need to add new companies, especially as part of a phased rollout or acquisitions. Until now, you couldn't add a company or legal entity without system downtime, which required you to unlink and relink your environment. This process can be expensive, especially because of pre-existing data. By using this feature, you can add a company in a live environment without the need to unlink your existing dual-write environment.

## Add a company or legal entity after setting up dual-write 

Follow these steps to add a company or legal entity after setting up dual-write.

1. On the **Dual-write table map** list page, select the **Environment details** button.

   :::image type="content" source="media/select-environment-details.png" alt-text="Screenshot of the Environment details button selected on the Dual-write table map list page.":::

1. On the **Legal entities** tab, you see the company that you selected as part of the dual-write wizard to link environments. In this example, the company is USMF.

   :::image type="content" source="media/legal-entities.png" alt-text="Screenshot of the Legal entities tab displaying the selected company.":::

1. To add one or more companies to dual-write, select **Add legal entity**. For example, GBSI.

   :::image type="content" source="media/add-legal-entity.png" alt-text="Screenshot of the Add legal entity option selected to add a new legal entity.":::

1. Determine if you want to skip initial writes for the legal entities you add to the list by selecting or unselecting **Skip initial writes for newly added legal entities**.
1. Select **Save**.

   When you select **Save**, the legal entities update. If you didn't select the **Skip initial writes for newly added legal entities** option, the table maps that are currently running or paused go through the initial write process by copying pre-existing data. Until the process completes, don't perform any actions that modify your table maps. 

   > [!NOTE]
   > Initial writes support up to 40 legal entities. If the total number of legal entities in the list is greater than 40, initial writes aren't processed for the newly added legal entities.

   :::image type="content" source="media/update-progress.png" alt-text="Screenshot of the Update legal entities progress indicator showing the update in progress.":::

   >[!NOTE]
   > This operation fails if either of the following conditions are true: 
   >
   > * You add or remove a new company when one or more table maps is already in the **Initial writes** state. This state is the process where the system is copying pre-existing data. 
   >
   > * You remove a company when one or more table maps is in the **Paused** state. 

1. After the process completes, a banner displays informing you that the legal entities are updated successfully. You can now resume updates to your table maps. 

   :::image type="content" source="media/legal-entities-updated.png" alt-text="Screenshot of the banner displaying a message that legal entities have been updated successfully.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
