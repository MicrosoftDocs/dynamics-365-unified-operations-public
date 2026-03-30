---
title: Show counts in fields
description: Learn about how to calculate a count that is correct and appears quickly due to a limit on the number of rows that are retrieved.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-07-20
ms.custom: 
  - bap-template
---

# Show counts in fields

[!include [banner](../../../includes/banner.md)]
[!include [mobile app deprecated](../../../includes/mobile-app-deprecation-banner.md)]

Although you can use a **pageLink** control to show counts (totals), it can be slow because it must load the target page before it counts the number of rows. Additionally, the count it calculates can be incorrect because there's a limit on the number of rows it retrieves.

:::image type="content" source="media/optimizing-workspace/Tiles_Original.png" alt-text="Screenshot of workspace with tiles that show counts.":::

To make mobile workspaces work more quickly, use a regular field to show the count, and then model the field as a **pageLink** control in the mobile client.

The following example uses the Fleet Management app. In the Fleet Management app, the workspace shows the total number of customers, reservations, and vehicles. Previously, these counts came from a **pageLink** control that had AllCustomers, AllReservations, and AllVehicles as targets. The **pageLink** control loaded the rows and did the count. (This approach isn't the recommended approach.)

Follow these steps to configure the workspace page to use the recommended approach.

1. On the server, create a new form to contain fields that are also on the server. (You can also add the new fields to an existing form). In the following illustration, a new **FMMobSummary** form is created that has three fields.

   :::image type="content" source="media/optimizing-workspace/FMMobSummary.png" alt-text="Screenshot of form that has three fields.":::

1. Create a page by using the mobile app designer for the **FMMobSummary** form.

   :::image type="content" source="media/optimizing-workspace/NewPageInDesigner.png" alt-text="Screenshot of new page in the designer.":::

1. Update the business logic to transform the fields into a **pageLink** control. Use the **configureControl** method to add a navigation target to the fields. The fields are then configured as **pageLink** controls. The arguments for the **configureControl** method are the page name, the control name, and an object of properties that you must update.
1. Update the workspace design. Embed the summary page as a part in the workspace page. Reference the fields that you configured as **pageLink** controls. Provide a style, and set the **showCount:true** property so that the count shows on the **pageLink** control.

   :::image type="content" source="media/optimizing-workspace/ChangesToBL.png" alt-text="Screenshot of changes to the business logic.":::

By using this approach, you also get the localized labels for **pageLink** controls. The result is a much faster experience when workspaces load.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
