---
title: Package configurations and deploy them to an online environment
description: Learn how to package configurations and deploy them to your Microsoft Dynamics 365 Commerce online environment.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Package configurations and deploy them to an online environment

[!include [banner](../includes/banner.md)]

This article describes how to package configurations and deploy them to your Microsoft Dynamics 365 Commerce online environment.

When your local site configurations (modules, data actions, and themes) are ready to deploy to your online environment, package and deploy them by using Microsoft Dynamics Lifecycle Services (LCS).

## Package the local site configurations for upload

Use the **yarn msdyn365 pack** command to create a package of the local site configurations. You can use this package to upload the configurations to an online environment through LCS.

Run the command from the root directory of your local online software development kit (SDK) files. The command creates a new zip file in the same directory.

Here's an example.

``` bash
c:\repos\D365.Commerce.Fabrikam>yarn msdyn365 pack
```

## Upload a package by using LCS

To upload a site configuration package by using LCS, follow these steps:

1. Go to [https://lcs.dynamics.com](https://lcs.dynamics.com). Alternatively, if you're using the test integration LCS server, go to [https://lcs.tie.dynamics.com](https://lcs.tie.dynamics.com). You should see a sign-in page that resembles the following illustration.

    :::image type="content" source="media/lcs-deploy-1.png" alt-text="Screenshot of LCS sign-in page.":::

1. Select **Sign in**, and enter your LCS-provided account credentials. The main dashboard appears.

    :::image type="content" source="media/lcs-deploy-2.png" alt-text="Screenshot of LCS main dashboard.":::

1. Select the e-commerce project that you're using. The project dashboard appears.

    :::image type="content" source="media/lcs-deploy-3.png" alt-text="Screenshot of LCS project dashboard.":::

1. Scroll right to see more options.

    :::image type="content" source="media/lcs-deploy-4.png" alt-text="Screenshot of LCS options when scrolling right.":::

1. To upload the package, in the **More tools** section, select the **Asset Library** tile.
1. On the **Asset library** page, in the left pane, select the **e-Commerce package** tab. If you don't see the **e-Commerce package** tab, you must enable e-commerce features. Contact your Microsoft Commerce representative to obtain the required code.

    :::image type="content" source="media/lcs-deploy-5.png" alt-text="Screenshot of LCS asset library.":::

1. Select the plus sign (+).
1. In the **Upload e-Commerce package file** dialog box, enter a name and description for the package, and then select **Add a file**.

    :::image type="content" source="media/lcs-deploy-6.png" alt-text="Screenshot of LCS Upload e-commerce package file dialog box.":::

1. In the **Upload file asset** dialog box, select **Browse**, and browse to the location of the package zip file that you created earlier. Select the file, and then select **Upload**.

    :::image type="content" source="media/lcs-deploy-7.png" alt-text="Screenshot of LCS Upload file asset dialog box.":::

1. When the upload finishes, you're returned to the **Upload e-commerce package file** dialog box. Select **Confirm** to process the upload.

    :::image type="content" source="media/lcs-deploy-8.png" alt-text="Screenshot of LCS Upload e-commerce package file dialog box after upload.":::

While the upload is being processed, you might have to refresh the page to see status updates. The processing can take between 45 and 50 minutes. When completed, a success or failure message is shown.

:::image type="content" source="media/lcs-deploy-9.png" alt-text="Screenshot of upload being processed in LCS asset library.":::

If the processing completes successfully, a check mark appears in the **Valid** column.

:::image type="content" source="media/lcs-deploy-10.png" alt-text="Screenshot of upload successfully processed in LCS asset library.":::

## Deploy a package

To deploy a package, follow these steps:

1. In LCS, go to the project dashboard, and select the environment that you want to deploy a package to. For example, in the following illustration, the **RushE2E-TIE-SB3** preproduction environment is selected.

    :::image type="content" source="media/lcs-deploy-11.png" alt-text="Screenshot of selecting an environment in the LCS project dashboard.":::

1. In the **Environment features** section on the right side of the page, select **Manage**.

    :::image type="content" source="media/lcs-deploy-12.png" alt-text="Screenshot of Environment features in LCS project dashboard.":::

1. Select the **E-Commerce (Preview)** tab.

    :::image type="content" source="media/lcs-deploy-13.png" alt-text="Screenshot of E-Commerce Preview tab in LCS project dashboard.":::

1. Select **Apply extension** to select the package to deploy.

    :::image type="content" source="media/lcs-deploy-14.png" alt-text="Screenshot of Apply extension in LCS project dashboard.":::

1. In the **Update e-Commerce** dialog box, select the package that you uploaded earlier, and then select **Update**.

    :::image type="content" source="media/lcs-deploy-15.png" alt-text="Screenshot of Update e-commerce dialog box in LCS project dashboard.":::

You can now track the deployment status in the **Details** section.

:::image type="content" source="media/lcs-deploy-16.png" alt-text="Screenshot of Details section of E-Commerce Preview tab in LCS project dashboard.":::

After the deployment finishes, you see your changes in the authoring tools or on pages that are rendered. For example, new modules or themes are available to page authors, or changes are rendered and appear in the online environment.

## Additional resources

[SDK and core library updates](sdk-updates.md)

[Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
