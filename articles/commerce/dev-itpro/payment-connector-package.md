---
title: Create Commerce payment packaging for finance and operations deployment
description: Learn how to package a payment connector for finance and operations deployment in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-02-02
ms.custom: 
  - bap-template
---

# Create Commerce payment packaging for finance and operations deployment

[!include [banner](../../includes/banner.md)]

This article explains how to package a payment connector for finance and operations deployment in Microsoft Dynamics 365 Commerce.

In releases earlier than 10.0.10, use the Commerce software development kit (SDK) to create a payment connector package. (The Commerce SDK was previously known as the Retail SDK.) In the 10.0.10 release and later, you can use only Visual Studio to create an Application Object Server (AOS) payment connector package. You can deploy packages that you create by using this approach for both earlier deployments and self-service deployments by using [all-in-one packages](../../fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages.md).

> [!NOTE]
> In releases earlier than 10.0.10, you can create a single payment package and use it both for Application Explorer and for the commerce channel and cloud components (Commerce Scale unit). In the 10.0.10 release, you must create two packages. One package is for Application Explorer, and you create it by using the Dynamics 365 packaging model. The other package is for the commerce channel and cloud components, and you create it by using the Commerce SDK. The previous approach, where the Commerce SDK is used to create Application Explorer payment packaging, is obsolete (deprecated) as of the 10.0.10 release.

To create a payment package that you can deploy, follow the steps in the next section.

> [!NOTE]
> The steps for using the Commerce SDK to create the package for the commerce channel and cloud components haven't changed. For more information, see [Create and deploy connector](deploy-payment-connector.md).

## Create an AOS payment package in the 10.0.10 release

1. In Visual Studio, on the **Dynamics 365** menu, select **Model Management \> Create model**.
1. Enter the model name, the model publisher, and other required details. Then select **Next**.

    The model name must start with the prefix **RetailPaymentConnectors**. After this prefix, add information about the custom model name. For example, the model that you create might be named **RetailPaymentConnectorsCustomConnector**. Only model names that begin with the **RetailPaymentConnectors** prefix appear in the Commerce payment connector options.

    :::image type="content" source="./media/CreateModel.png" alt-text="Screenshot of the Add parameters page in the Create model wizard.":::

1. Select the **Create new package** option, and then select **Next**.
1. Select the required referenced package, and then select **Next**.
1. Select **Finish** to finish creating the model.
1. In Solution Explorer, select the project, right-click **References**, and then select **Add Reference**.
1. Add all the payment connector assemblies and their dependencies to the project as references.

    :::image type="content" source="./media/Reference.png" alt-text="Screenshot of the Add Reference dialog box.":::

    > [!NOTE]
    > All payment connector DLLs must be portable. Having both portable and nonportable payment connector DLLs causes problems when loading the connector.

1. If your extension needs an HTML and CSS file for the implementation, add them as resource files to your project. During deployment, the HTML files are copied to the `AosService\WebRoot\Resources\Html` folder. The CSS files are copied to the `AosService\WebRoot\Resources\Styles` folder. You can access them by using the following URL format.

    Example: If necessary, update the `GetPaymentAcceptPoint` implementation to return this URL.

    ```
    https://AOSUrl/resources/html/Myhtml.html
    https://AOSUrl/resources/styles/Mycss.css
    ```

    > [!NOTE]
    > Only HTML and CSS file formats added as resources to the project are copied to the `AosService\WebRoot\`. Other file formats aren't copied to the `AosService\WebRoot\`. If you need the file in the `AosService\WebRoot\` folder, migrate it to an HTML file format or host the nonsupported file formats externally. If hosted externally, hosting must be managed by the customer or partner.

1. If you don't have any other payment X++ extensions that are related to the payment connector, build the solution.

    > [!NOTE]
    > If there are no other extensions packages, continue with these steps. If you have more extensions packages, combine them into one all-in-one deployable package. If you don't combine them, this package overrides other packages. For more information, see [All-in-one deployable packages](../../fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages.md).

1. To create the deployable package, on the **Dynamics 365** menu, select **Deploy \> Create Deployment Package**.
1. Select the model that you created earlier, specify the location of the package file, and then select **Create**.

    :::image type="content" source="./media/Create.png" alt-text="Screenshot of the Create Deployment Package dialog box.":::

    Visual Studio builds the model and creates the deployable package.

1. After the deployable package is created, sign in to Microsoft Dynamics Lifecycle Services (LCS), and then, in your LCS project, select the **Asset Library** tile.
1. Upload the deployable package that you created.

## Apply a deployable package

For information about how to apply a deployable package to an environment, see [Apply updates to cloud environments](../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md).

## Remove a deployable package

For information about how to uninstall or remove a deployable package from an environment, see [Uninstall a package](../../fin-ops-core/dev-itpro/deployment/uninstall-deployable-package.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]