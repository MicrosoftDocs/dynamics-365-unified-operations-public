---
title: Create a new transportation management engine
description: Learn how to create a new transportation management engine in Dynamics 365 Supply Chain Management, including an outline on creating new TMS engines. 
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 06/10/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: TMSGenericEngine, TMSRateEngine, TMSMileageEngine, TMSEngineParameters
---

# Create a new transportation management engine

[!include [banner](../../finance/includes/banner.md)]

This article describes how to create a new transportation management engine in Dynamics 365 Supply Chain Management.

Transportation management (TMS) engines define the logic that is used to generate and process transportation rates in Transportation management. Supply Chain Management provides several different engine types that calculate different parameters, such as rates, transit times, and the number of zones that will be crossed during transit. This article explains how to use the Microsoft Visual Studio development environment together with Supply Chain Management development tools to create and deploy a new TMS engine, and then how to set up the engine in Operations. For more information about the engines, see [Transportation management engines](../transportation/transportation-management-engines.md).

## <a name="create-tms-engine"></a>Create a new TMS engine

This section explains how to create a class library that has a TMS engine implementation, and how to reference it from a Supply Chain Management model.

1. To deploy your new engines, you must have a model that will contain the engines. On the **Dynamics 365** &gt; **Model Management** menu, select **Create model** to create a new model. On the first page of the **Create model** wizard, name the model **TMSEngines**.

   ![Creating a model.](../transportation/media/012.png)

2. On the next page, select **Create new package**.

   ![Creating a new package.](../transportation/media/021.png)

3. On the next page, select the **ApplicationSuite** model to reference. (The **ApplicationPlatform** model is preselected.)

   ![Selecting the model to reference.](../transportation/media/032.png)

4. On the next page, select **Finish** to confirm the creation of a new model.

   ![Completing model creation.](../transportation/media/042.png)

5. In a new solution, create a new Supply Chain Management project, and name it `TMSThirdParty`. In the project properties, set the project's model to **TMSEngines**.
6. Add a new C\# class library to your solution, and name it `ThirdPartyTMSEngines`.
7. In the `ThirdPartyTMSEngines` project, add references to Supply Chain Management–specific assemblies:
   - Application assemblies that enable X++ types to be referenced. These assemblies can be found in the following locations. \[Packages root\] is the path of the location where all the deployed assemblies are placed, such as C:\\Packages.

        ```xpp
        [Packages root]\ApplicationPlatform\bin\Dynamics.AX.ApplicationPlatform.dll
        [Packages root]\ApplicationFoundation\bin\Dynamics.AX.ApplicationFoundation.dll
        [Packages root]\ApplicationSuite\bin\Dynamics.AX.ApplicationSuite.dll
        ```

   - Framework assemblies that enable access to data, LINQ, and auxiliary functions. All these assembles can be found in \[Packages root\]\\bin.

        ```xpp
        Microsoft.Dynamics.ApplicationPlatform.Environment.dll
        Microsoft.Dynamics.AX.Data.Core.dll
        Microsoft.Dynamics.AX.Framework.Linq.Data.AdoNet.dll
        Microsoft.Dynamics.AX.Framework.Linq.Data.dll
        Microsoft.Dynamics.AX.Framework.Linq.Data.Interface.dll
        Microsoft.Dynamics.AX.Framework.Linq.Data.Msil.dll
        Microsoft.Dynamics.AX.Server.Core.dll
        Microsoft.Dynamics.AX.Xpp.AxShared.dll
        Microsoft.Dynamics.AX.Xpp.Support.dll
        ```

   - The core TMS assembly (which contains engines) and the TMS base assembly (which contains helpers, constants, data transfer class definitions, and so on). These assemblies can be found in the following locations.

        ```xpp
        [Packages root]\ApplicationSuite\bin\Microsoft.Dynamics.AX.Tms.dll
        [Packages root]\ApplicationSuite\bin\Microsoft.Dynamics.AX.Tms.Base.dll
        ```

8. Rename the C\# class that is automatically generated in the `ThirdPartyTMSEngines` project to **SampleRatingEngine**.
9. Implement the engine. Because we're creating a rate engine in this example, we inherit from the base class for rate engines. The base class implements most of the rate engine interface (**TMSFwkIRateEngine**). We just have to implement the rate method. To keep this example simple, we'll make this method register a hard-coded rate of 100. You can create engines that implement any of the engine interfaces, such as **TMSFwkIAccessorialEngine**. All the engine interfaces are defined in X++.

    ```xpp
    namespace ThirdPartyTMSEngines
    {
        using Dynamics.AX.Application;
        using Microsoft.Dynamics.Ax.Tms.Base.Data;
        using Microsoft.Dynamics.Ax.Tms.Base.Utility;
        using Microsoft.Dynamics.Ax.Tms.Bll;
        using System.Xml.Linq;
        public class SampleRatingEngine : BaseRateEngine
        {
            public override RatingDto rate(TmsTransactionFacade transactionFacade, XElement shipment, TMSRateMasterCode rateMasterCode)
            {
               XElement re = shipment.RetrieveOrCreateRatingEntity(this.RatingDto);
               re.AddRate(TmsRateType.Rate, 100);
               return this.RatingDto;
            }
        }
    }
    ```

10. Build the solution.
11. Add a new reference to the `TMSThirdParty` project. The reference should point to the `ThirdPartyTMSEngines` project. When you've finished, your solution should look like this.

    ![The solution, which includes a reference to the TMSThirdParty project.](../transportation/media/052.png)

12. Build the solution. Verify that the new library appears in the **References** node in Application Explorer.

    ![The new library in Application Explorer’s References node.](../transportation/media/061.png)

## <a name="deploy-engine-as-package"></a>Deploy the TMS engine as a package

One way to deploy third-party TMS engines is through a deployment package. To deploy the engine as a package, follow these steps.

1. In Visual Studio, go to **Extensions \> Dynamics 365 \> Deploy \> Create Deployment Package** and create a deployment package for the new model you created as described in [Create a new TMS engine](#create-tms-engine).

1. In Dynamics Lifecycle Services, go to **Asset Library \> Software deployable package**. Select **Add** to add the deployment package you created to LCS.

1. After the validation completes, go to **Environments \> {Your Environment ID} \> Maintain \> Apply updates**, select the deployable package, and apply.

> [!NOTE]
> If the system warns you that you don't have permission to deploy packages on Lifecycle Services, please contact your LCS administrator for support.

## Set up the TMS engine in Supply Chain Management

This section explains how to set up Supply Chain Management to use a TMS engine, and shows how the new engine that we have created is used in rate shopping. The example in this section uses the USMF demo data company.

1. Create a new engine as described in [Create a new TMS engine](#create-tms-engine).
1. Build your solution.
1. Deploy the TMS engine DLL file through a deployment package, as described in [Deploy the TMS engine as a package](#deploy-engine-as-package).

1. In Supply Chain Management, on the **Rate engines** page, create a new rating engine. The engine should point to the engine assembly produced by building the engine class library and the engine class that you implemented.

    :::image type="content" source="../transportation/media/081.png" alt-text="Creating a new rating engine on the Rate engines page." lightbox="../transportation/media/081.png":::

1. Create a shipping carrier that uses the Sample rate engine. Because our engine doesn't use any data, you don’t have to assign a rate master.

    :::image type="content" source="../transportation/media/092.png" alt-text="Creating a new shipping carrier." lightbox="../transportation/media/092.png":::

1. On the **Rate route workbench** page, select **Rate shop**. You should see a rate of 100.00 from SampleCarrier, as shown in the following screenshot. In this example, we're rate shopping for a route from warehouse 24 to customer US-004. However, but because the rate is hard-coded, you'll always see a rate of 100.00.

    :::image type="content" source="../transportation/media/101.png" alt-text="Rate route workbench." lightbox="../transportation/media/101.png":::

## Tips and tricks

- If you’re using development tools for Supply Chain Management, it's useful to add a new project to your solution. If you set this project as your startup project and start a debugging session, you can debug both X++ and C\# code in the same debugging session.
- Every time that you change and recompile your `ThirdPartyTMSEngines` project, you must deploy through a deployment package. Otherwise, you might run using a stale assembly.
- After you execute TMS-specific operations inSupply Chain Management, the Internet Information Services (IIS) worker process might lock the `ThirdPartyTMSEngines` assembly so that the assembly can’t be updated. In this case, restart the w3svc process.

### Whitepaper

For more information, download the following white paper (written to support AX2012, but still partially applies for Dynamics 365 Supply Chain Management)

- [Implementing and deploying Transportation management engines](https://download.microsoft.com/download/b/5/f/b5ff8fef-3918-4c1d-92d5-b67eb0971684/ImplementingAndDeployingTransportationManagementEnginesInAX.pdf)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
