---
title: Install deployable packages from the command line
description: Learn how to use the command line to apply a binary update or an application (AOT) deployable package that was created in your environment.
author: johnmichalak
ms.author: johnmichalak
ms.topic: install-set-up-deploy
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Install deployable packages from the command line

[!include [banner](../includes/banner.md)]

This article shows you how to use the command line to apply either a binary update or an application (AOT) deployable package that you created in your development or build environment.

> [!IMPORTANT]
> For most types of environments, you can apply a deployable package to an environment directly from Microsoft Dynamics Lifecycle Services. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md). Therefore, this article primarily applies to environment types that don't support the application of updates via Lifecycle Services. Examples include local development environments (downloadable virtual hard disks [VHDs]), multibox development and test environments in Microsoft Azure (Lifecycle Services Partner and trial projects), and build environments. However, you can also use this article any time that you want to install deployable packages by using the command line instead of Lifecycle Services.

## Key concepts

- **Deployable package** – A deployable package is a unit of deployment that you can apply to any environment. It can consist of a binary hotfix to the runtime components of Application Object Server (AOS), an updated application package, or a new application package.
- **AXUpdateInstaller** – AXUpdateInstaller is an executable program that's bundled in the deployable package. When you download the package to a computer, the installer is available.
- **Runbook** – The deployment runbook is a series of steps that's generated and used to apply the deployable package to the target environment. Some of the steps are automated, and some are manual. AXUpdateInstaller enables these steps to run one at a time and in the correct order.

## Install an application (AOT) deployable package on a development environment
>
> [!NOTE]
> The following steps apply only to customization packages. Don't use the **devinstall** parameter when running the Data Upgrade deployable package as part of an upgrade from Microsoft Dynamics AX 2012 to a finance and operations app.

An AOT deployable package is a package that contains customizations and extensions to your application. If you want to use the command line just to install an AOT deployable package on a development or demo environment, follow the instructions in this section. You can then skip the rest of this article.

1. On the virtual machine (VM), download the zip file for the deployable package. Make sure that you store the zip file in a non-user folder.

    > [!NOTE]
    > After you download the zip file, right-click it, and then select **Properties**. Then, in the **Properties** dialog box, on the **General** tab, select **Unblock** to unlock the files.

1. Extract the files.
1. Open a Command Prompt window, and go to the folder where you extracted the deployable package.
1. Run the following command.

    ```Console
    AXUpdateInstaller.exe devinstall
    ```

    The **devinstall** option installs the AOT deployable package on the VM.

    > [!NOTE]
    > This command doesn't run database synchronization. You must run database synchronization from Microsoft Visual Studio after you install the deployable package.

## Collect topology configuration data

1. In Lifecycle Services, on the **Environment** page, select the name of a VM. Establish a Remote Desktop connection to the VM by using the user name and password that are provided on the **Environment** page.
1. On the VM, download the zip file for the deployable package from Lifecycle Services. Make sure that you store the zip file in a non-user folder.

    > [!NOTE]
    > After you download the zip file, right-click it, and then select **Properties**. Then, in the **Properties** dialog box, on the **General** tab, select **Unblock** to unlock the files.

1. Extract the files.
1. In the folder where you extracted the deployable package, find and open the file named **DefaultTopologyData.xml**. You must specify the VM name and the installed components in this file.

   - To specify the VM name, follow these steps:

       1. In File Explorer, right-click **This PC**, and then select **Properties**.
       1. In the system properties, find and make a note of the computer name (for example, **AOS-950ed2c3e7b**).
       1. In the DefaultTopologyData.xml file, replace the machine name with the computer name that you found in the previous step.

   - To specify the installed components, follow these steps:

       1. Open a Command Prompt window as an administrator.
       1. Go to the extracted folder, and run the following command to see a list of all the components that are installed on the computer.

           ```Console
           AXUpdateInstaller.exe list
           ```

       1. Update the DefaultTopologyData.xml file with the list of components.

     When you finish specifying the VM name and the installed components, the DefaultTopologyData.xml file should resemble the following illustration.

     :::image type="content" source="./media/defaulttopology.png" alt-text="Screenshot of topology configuration data.":::

1. Repeat steps 1 through 4 for every other VM that is listed on the **Environment** page.

## Generate a runbook from the topology

Based on the topology information in the DefaultTopologyData.xml file, generate the runbook file that provides step-by-step instructions for updating each VM.

- On any VM, run the following command to generate the runbook.

    ```Console
    AXUpdateInstaller.exe generate -runbookid=[runbookID] -topologyfile=[topologyFile] -servicemodelfile=[serviceModelFile] -runbookfile=[runbookFile]
    ```

    Here's an explanation of the parameters used in this command:

  - **\[runbookID\]** – A parameter that the developer specifies when applying the deployable package.
  - **\[topologyFile\]** – The path of the DefaultTopologyData.xml file.
  - **\[serviceModelFile\]** – The path of the DefaultServiceModelData.xml file.
  - **\[runbookFile\]** – The name of the runbook file to generate (for example, **AOSRunbook.xml**).

    **Example**

    ```Console
    AXUpdateInstaller.exe generate -runbookid="VAL200AA2BMEDIU-runbook" -topologyfile="DefaultTopologyData.xml" -servicemodelfile="DefaultServiceModelData.xml" -runbookfile="VAL200AA2BMEDIU-runbook.xml"
    ```

The runbook provides the sequence of steps that you must run to update the environment. The following illustration shows an example of a runbook file. Each step in a runbook is associated with an ID, a machine name, and step execution details.

:::image type="content" source="./media/runbook-steps-1024x624.jpg" alt-text="Screenshot of an example runbook file showing steps with IDs, machine names, and execution details." lightbox="./media/runbook-steps.jpg":::

## Install a deployable package

1. On the first machine (VM) listed in the runbook file, follow these steps:

    1. Import the runbook by running the following command.

        ```Console
        AXUpdateInstaller.exe import -runbookfile=[runbookFile]
        ```

        **Example**

        ```Console
        AXUpdateInstaller.exe import -runbookfile="VAL200AA2BMEDIU-runbook.xml"
        ```

    1. Verify the runbook.

        ```Console
        AXUpdateInstaller.exe list
        ```

    1. Run the runbook.

        ```Console
        AXUpdateInstaller.exe execute -runbookid=[runbookID]
        ```

        **Example**

        ```Console
        AXUpdateInstaller.exe execute -runbookid="VAL200AA2BMEDIU-runbook"
        ```

        AXUpdateInstaller updates the runbook file after each step runs on a VM. The runbook also logs information about each step.

        For manual steps, follow the instructions, and then run the following command to mark the step as completed in the runbook.

        ```Console
        AXUpdateInstaller.exe execute -runbookID=[runbookID] -setstepcomplete=[stepID]
        ```

        **Example**

        ```Console
        AXUpdateInstaller.exe execute -runbookid="VAL200AA2BMEDIU-runbook" -setstepcomplete=2
        ```

        If errors occur during any step, debug the script or the instructions in the step, and update them accordingly.

    1. Export the runbook.

        ```Console
        AXUpdateInstaller.exe export -runbookid=[runbookID] -runbookfile=[runbookFile]
        ```

        **Example**

        ```Console
        AXUpdateInstaller.exe export -runbookid="VAL200AA2BMEDIU-runbook" -runbookfile="VAL200AA2BMEDIU-runbook.xml"
        ```

1. Repeat step 1 on every other VM listed in the runbook file. For one-box environments, such as development, build, and demo environments, there's only one VM.

## Verify installation

1. Run the following command to verify that the new updates are installed.

    ```Console
    AXUpdateInstaller.exe list
    ```

1. View the runbook to see the completed steps. Here's an example of a runbook file where the steps are completed.

    :::image type="content" source="./media/image013-1024x978.png" alt-text="Screenshot of completed steps in a runbook." lightbox="./media/image013.png":::

## Backup the runbook file

- After you complete all the steps in the runbook and export the runbook, save the file outside the computer for future reference. For example, you might need to use the runbook file in these situations:

  - You need to analyze the downtime requirements for production, and so on.
  - You need to send the file to Microsoft because a deployable package can't be installed.

## Troubleshooting

- If any step in the runbook fails, rerun it by running the following command.

    ```Console
    AXUpdateInstaller.exe execute -runbookid=[runbookID] -rerunstep=[stepID]
    ```

- To prevent version mismatch, downgrade, or installation of the same deployable package, run the following command.

    ```Console
    AXUpdateInstaller.exe execute -runbookid=[runbook ID] -versioncheck=true
    ```

- To verify database synchronization, in the **aosservice\\scripts\\** folder, find and open the **dbsync.error.txt** file, and look for any errors.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
