---
# required metadata

title: Create payment packaging for Application Explorer for self-service deployment
description: This topic explains how to package a payment connector for Application Explorer for self-service deployment in Dynamics 365 Commerce.
author: mugunthanm
manager: AnnBe
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# Create payment packaging for Application Explorer for self-service deployment

[!include [banner](../../includes/banner.md)]

This topic explains how to create payment packaging for Application Explorer for self-service deployment in Dynamics 365 Commerce.

In releases that are earlier than 10.0.10, you use the Commerce software development kit (SDK) to create a payment connector package. (The Commerce SDK was previously known as the Retail SDK.) In the 10.0.10 release and later, you can use only Visual Studio to create an  Application Object Server (AOS) payment connector package. Packages that you create by using this approach can be deployed for both legacy and self-service deployments using [All-in-one packages](../../fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages.md).

> [!NOTE]
> In releases that are earlier than 10.0.10, you can create a single payment package and use it both for Application Explorer and for the commerce channel and cloud components (Commerce Scale unit). In the 10.0.10 release, you must create two packages. One package is for Application Explorer, and you create it by using the Dynamics 365 packaging model. The other package is for the commerce channel and cloud components, and you create it by using the Commerce SDK. The previous approach, where the Commerce SDK is used to create Application Explorer payment packaging, is obsolete (deprecated) as of the 10.0.10 release.

To create a payment package that you can deploy with self-service, follow the steps in the next section.

> [!NOTE]
> The steps for using the Commerce SDK to create the package for the commerce channel and cloud components haven't changed. For more information, see [Create and deploy connector](deploy-payment-connector.md).

## Create an AOS payment package in the 10.0.10 release

1. In Visual Studio, on the **Dynamics 365** menu, select **Model Management \> Create model**.
2. Enter the model name, the model publisher, and other required details. Then select **Next**.

    The model name must be prefixed with (that is, start with) **RetailPaymentConnectors**. After this prefix, add information about the custom model name. For example, the model that you create might be named **RetailPaymentConnectorsCustomConnector**. Only model names that begin with the **RetailPaymentConnectors** prefix will be loaded in the Commerce payment connector options.

    ![Add parameters page in the Create model wizard](./media/CreateModel.png)

3. Select the **Create new package** option, and then select **Next**.
4. Select the required referenced package, and then select **Next**.
5. Select **Finish** to finish creating the model.
6. In Solution Explorer, select the project, right-click **References**, and then select **Add Reference**.
7. Add all the payment connector assemblies and their dependencies to the project as references.

    ![Add Reference dialog box](./media/Reference.png)

8. If you don't have any other payment X++ extensions that are related to the payment connector, build the solution.
9. To create the deployable package, on the **Dynamics 365** menu, select **Deploy \> Create Deployment Package**.
10. Select the model that you created earlier, specify the location of the package file, and then select **Create**.

    ![Create Deployment Package dialog box](./media/Create.png)

    Visual Studio builds the model and creates the deployable package.

10. After the deployable package has been created, sign in to Microsoft Dynamics Lifecycle Services (LCS), and then, in your LCS project, select the **Asset Library** tile.
11. Upload the deployable package that you created.

## Apply a deployable package

For information about how to apply a deployable package to an environment, see [Apply updates to cloud environments](../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md).

## Remove a deployable package

For information about how to uninstall or remove a deployable package from an environment, see [Uninstall a package](../../fin-ops-core/dev-itpro/deployment/uninstall-deployable-package.md).
