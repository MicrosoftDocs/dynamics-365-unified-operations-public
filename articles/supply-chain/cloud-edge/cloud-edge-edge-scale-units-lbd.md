---
title: Deploy edge scale units on custom hardware using LBD (Preview)
description: This topic explains how to provision on-premises edge scale units by using custom hardware and deployment that is based on local business data (LBD). 
author: cabeln
ms.date: 04/22/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: cabeln
ms.search.validFrom: 2021-04-13
ms.dyn365.ops.version: 10.0.19
---

# Deploy edge scale units on custom hardware using LBD (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Edge scale units play an important role in the distributed hybrid topology for supply chain management. In the hybrid topology you can distribute workloads between your Supply Chain Management cloud hub and additional scale units in the cloud or on the edge.

Edge scale units can be deployed by creating a local business data (LBD) [on-premises environment](../../fin-ops-core/dev-itpro/deployment/on-premises-deployment-landing-page.md) and then configuring it to function as a scale unit in your distributed hybrid topology for supply chain management. This is achieved by associating the on-premises LBD environment with a Supply Chain Management environment in the cloud, which has been configured to function as a hub.  

Edge scale units are currently in preview. Therefore, you may use an environment of this type only according to the [preview terms](https://aka.ms/scmcnepreviewterms).

This topic describes how to set up an on-premises LBD environment as an edge scale unit and then associate it with a hub.

## Deployment overview

Here is an overview of the deployment steps.

1. **Enable an LBD slot in your LBD project in Microsoft Dynamics Lifecycle Services (LCS).**

    During preview, LBD edge scale units target existing LBD customers. An additional 60-day limited LBD sandbox slot will be provided in only specific customer situations.

1. **Set up and deploy an LBD environment with an *empty* database.**

    Use LCS to deploy the LBD environment with the latest topology and an empty database. For more information, see the [Setup and deploy an LBD environment with empty database](#set-up-deploy) section later in this topic. You must use Supply Chain Management version 10.0.19 with platform update 43 or higher across hub and scale unit environments.

1. **Upload target packages into LBD project assets in LCS.**

    Prepare application, platform, and customization packages that you use across the hub and the edge scale unit. For more information, see the [Upload target packages into LBD project assets in LCS](#upload-packages) section later in this topic.

1. **Service the LBD environment with the target packages.**

    This step ensures that the same build and customizations are deployed on the hub and the spoke. For more information, see the [Service the LBD environment with target packages](#service-target-packages) section later in this topic.

1. **Complete the scale unit configuration and workload assignment.**

    For more information, see the [Assign your LBD edge scale unit to a hub](#assign-edge-to-hub) section later in this topic.

The remaining sections of this topic provide more details about how to complete these steps.

## <a name="set-up-deploy"></a>Set up and deploy an LBD environment with an empty database

This step creates a functional LBD environment. However, the environment doesn't necessarily have the same application and platform versions as the hub environment. Additionally, it's still missing the customizations, and it hasn't yet been enabled to work as a scale unit.

1. Follow the instructions in [Setup and deploy on-premises environments (Platform update 41 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md). You must use Supply Chain Management version 10.0.19 with platform update 43 or higher across hub and scale unit environments

    > [!IMPORTANT]
    > Read the rest of this section **before** you complete the steps in that topic.

1. Before you describe your configuration in the infrastructure\\ConfigTemplate.xml file, run the following script:

    ```powershell
    .\Configure-ScriptsForEdgeScaleUnits.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!NOTE]
    > This script will remove any configuration that is not needed for deploying edge scale units.

1. Set up a database that contains empty data, as described in [Configure databases](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md#configuredb). Use the empty data.bak file for this step.
1. Set up the pre-deployment script. For more information, see [Local agent pre-deployment and post-deployment scripts](../../fin-ops-core/dev-itpro/lifecycle-services/pre-post-scripts.md).

    1. Copy the contents from the **ScaleUnit** folder in **Infrastructure Scripts** to the **Scripts** folder in the agent file storage share that was set up in the environment. A typical path is \\\\lbdiscsi01\\agent\\Scripts.
    2. Create the **PreDeployment.ps1** script that will invoke the scripts by using the required parameters. The pre-deployment script must be put in the **Scripts** folder in the agent file storage share. Otherwise, it can't be run. A typical path is \\\\lbdiscsi01\\agent\\Scripts\\PreDeployment.ps1.

        The contents of the PreDeployment.ps1 script will resemble the following example.

        ```powershell
        $agentShare = '\\lbdiscsi01\agent'
        
        Write-Output "AgentShare is set to $agentShare" 
        & $agentShare\Scripts\Configure-CloudandEdge.ps1 -AgentShare $agentShare -InstanceId '@A' -DatabaseServer 'lbdsqla01.contoso.com' -DatabaseName 'AXDB'
        ```

        > [!NOTE]
        > The InstanceId parameter should be only two characters. The first character is @ and the second can be any capital letter in the English alphabet.
        >
        > - Valid values:
        >   - @D
        >   - @X
        > - Not valid values:
        >   - @a
        >   - @4
        >   - @#

1. Deploy the environment by using the latest base topology that is available.

## <a name="upload-packages"></a>Upload target packages into LBD project assets in LCS

This step prepares the application version, platform version, and customizations that will be transitioned to your LBD scale unit environment.

1. Upload the same combined application/platform package that was applied to the hub environment into the asset library of the LCS on-premises project.
1. Get a copy of the custom deployable package that was applied to the hub environment, and upload it into the asset library of the LCS on-premises project.

## <a name="service-target-packages"></a>Service the LBD environment with target packages

This step aligns the application version, platform version, and customizations in your LBD scale unit environment with the hub.

1. Service the LBD environment with the combined application/platform package that you uploaded in the previous step.
1. Service the LBD environment with the custom deployable package that you uploaded in the previous step.

    ![Selecting Maintain > Apply updates in LCS](media/cloud_edge-LBD-LCS-ServiceLBDEnv1.png "Selecting Maintain > Apply updates in LCS")

    ![Selecting your customization package](media/cloud_edge-LBD-LCS-ServiceLBDEnv2.png "Selecting your customization package")

## <a name="assign-edge-to-hub"></a>Assign your LBD edge scale unit to a hub

While edge scale units are still in preview, you must use the [scale unit deployment and configuration tools](https://github.com/microsoft/SCMScaleUnitDevTools) that are available on GitHub to assign your LBD edge scale unit to a hub. The process enables an LBD configuration to function as an edge scale unit and associates it with the hub. The process is similar to configuring a one-box development environment.

1. Download the latest release of [SCMScaleUnitDevTools](https://github.com/microsoft/SCMScaleUnitDevTools/releases) and unzip the contents of the file.
1. Create a copy of the `UserConfig.sample.xml` file and name it `UserConfig.xml`.
1. Create a Microsoft Azure Active Directory (Azure AD) application in your Azure AD tenant, as mentioned in [Deployment guide for scale unit and workloads](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide#aad-application-registrations).
    1. Once created, navigate to the Azure AD applications form (SysAADClientTable) on your hub.
    1. Create a new entry and set the **Client ID** to the ID of the application you created. Set the **Name** to *ScaleUnits* and the **User ID** to *Admin*.

1. Create an Active Directory Federation Service (AD FS) application as mentioned in [Deployment guide for scale unit and workloads](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide#adfs-application-registrations).
    1. Once created, navigate to the Azure AD applications form (SysAADClientTable) on your edge scale unit.
    1. Create a new entry and set the **Client ID** to the ID of the application you created. Set the **User ID** to *Admin*.

1. Modify the `UserConfig.xml` file.
    1. Under the `InterAOSAADConfiguration` section, enter the information from the Azure AD application you created previously.
        - In the `AppId` element, enter the application ID of the Azure application.
        - In the `AppSecret` element, enter the application secret of the Azure application.
        - The `Authority` element must contain the URL specifying the security authority for your tenant.

        ```xml
        <InterAOSAADConfiguration>
            <AppId>8dab14f6-97b1-48e3-b51b-350b45f6ede5</AppId>
            <AppSecret>k6em-_7.lopty56TGUedDTVhtER-j_6anY1</AppSecret>
            <Authority>https://login.windows.net/contoso.onmicrosoft.com</Authority>
        </InterAOSAADConfiguration>
        ```

    1. Under the `ScaleUnitConfiguration` section, for the first `ScaleUnitInstance`, modify the `AuthConfiguration` section.
        - In the `AppId` element, enter the application ID of the Azure application.
        - In the `AppSecret` element, enter the application secret of the Azure application.
        - The `Authority` element must contain the URL specifying the security authority for your tenant.

        ```xml
        <AuthConfiguration>
            <AppId>8dab14f6-97b1-48e3-b51b-350b45f6ede5</AppId>
            <AppSecret>k6em-_7.lopdz.6d3DTVOtf9Lo-j_6anY1</AppSecret>
            <Authority>https://login.windows.net/contoso.onmicrosoft.com</Authority>
        </AuthConfiguration>
        ```

    1. Additionally, for this same `ScaleUnitInstance`, set the following values:
        - In the `Domain` element, specify the URL of your hub. For example: `https://cloudhub.sandbox.operations.dynamics.com/`
        - In the `EnvironmentType` element, ensure the value `LCSHosted` is set.

    1. Under the `ScaleUnitConfiguration` section, for the second `ScaleUnitInstance`, modify the `AuthConfiguration` section.
        - In the `AppId` element, enter the application ID of the AD FS application.
        - In the `AppSecret` element, enter the application secret of the ADFS application.
        - The `Authority` element must contain the URL of your AD FS instance.

        ```xml
        <AuthConfiguration>
            <AppId>26b16f25-21d8-4d36-987b-62df292895aa</AppId>
            <AppSecret>iZFfObgI6lLtY9kEbBjEFV98NqI5_YZ0e5SBcWER</AppSecret>
            <Authority>https://adfs.contoso.com/adfs</Authority>
        </AuthConfiguration>
        ```

    1. Additionally, for this same `ScaleUnitInstance`, set the following values:
        - In the `Domain` element, specify the URL of your edge scale unit. For example: https://ax.contoso.com/
        - In the `EnvironmentType` element, ensure the value LBD is set.
        - In the `ScaleUnitId` element, input the same value you specified for the `InstanceId` when configuring the `Configure-CloudandEdge.ps1` pre-deployment script.

        > [!NOTE]
        > If you don't use the default Id (@A), ensure you update the ScaleUnitId for each ConfiguredWorkload under the Workloads section.

1. Open PowerShell and navigate to the folder containing the `UserConfig.xml` file.

1. Run the tool with this command.

    ```powershell
    .\CLI.exe
    ```

    > [!NOTE]
    > After every action you will have to start the tool again.

1. In the tool, select **2. Prepare environments for workload installation**. Then run the following steps:
    1. Select **1. Prepare the Hub**.
    1. Select **2. Prepare the Scale Unit**.

    > [!NOTE]
    > If you are not running this command from a clean installation and it fails, do the following actions:
    >
    > - Remove all folders from the `aos-storage` folder (except for `GACAssemblies`).
    > - Run the following SQL command on your business database (AXDB):
    >
    > ```sql 
    > delete from storagefoler
    > ```

1. Run the following SQL commands on your business database (AXDB):

    ```sql
    delete from FEATUREMANAGEMENTMETADATA
    delete from FEATUREMANAGEMENTSTATE
    delete from NUMBERSEQUENCESCOPE
    ```

1. Verify that change tracking has been enabled on your business database (AXDB)
    1. Start SQL Server Management Studio (SSMS).
    1. Right-click your business database (AXDB) and select properties.
    1. In the window that opens, select **Change Tracking** and make the following settings:

        - **Change Tracking:** *True*
        - **Retention Period:** *7*
        - **Retention Units:** *Days*
        - **Auto Cleanup:** *True*

1. In the tool, select **3. Install workloads**. Then run the following steps:
    1. Select **1. Install on Hub**.
    1. Select **2. Install on Scale Unit**.

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
