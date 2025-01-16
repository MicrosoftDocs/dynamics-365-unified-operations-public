---
title: Upload ER configurations and Globalization features as a Dataverse solution
description: Learn how to upload Electronic reporting (ER) configurations and Globalization features as a Microsoft Dataverse solution.
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Upload ER configurations and Globalization features as a Dataverse solution

[!INCLUDE[banner](../../../includes/banner.md)]

[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

You can use Microsoft Dataverse solutions for Application Lifecycle Management (ALM) scenarios. For example, you can move Electronic reporting (ER) configurations to other environments or share them with other tenants via AppSource.

You can also export and import specific versions as a file by using export and import buttons on the page (existing functionality).

## Prerequisites

- Install PowerShell 7. For more information, see [Installing PowerShell on Windows](/powershell/scripting/install/installing-powershell-on-windows).
- Install Microsoft Power Platform CLI. For more information, see [What is Microsoft Power Platform CLI?](/power-platform/developer/cli/introduction)
- Get the **Generate-GlobalizationDataverseSolution.ps1** script from the Shared asset library/Data package files in Microsoft Dynamics Lifecycle Services (\<\<Asset type:, Asset name:\>\>).

## Step 1: Export your artifacts

To export your artifacts, follow these steps.

1. Create a folder, such as **C:\\DvArtifactsSrc**.
1. Export the .xml files of any ER configurations and the .json files of any Globalization features to the new folder.

    > [!IMPORTANT]
    > Do **not** include Microsoft configurations.

## Step 2: Create a Dataverse solution

To create a Dataverse solution, follow these steps.

1. Create a solution in Dataverse, and export it. For more information, see [Create a solution](/power-apps/maker/data-platform/create-solution) and [Export solutions](/power-apps/maker/data-platform/export-solutions).
1. Extract the new solution by using the **pac solution unpack** command. Here's an example.

    ``` command
    pac solution unpack --zipfile C:\SampleEmptySolution.zip --folder C:\SampleSolutionUnpacked
    ```

    For more information, see [pac solution unpack](/power-platform/developer/cli/reference/solution#pac-solution-unpack).

## Step 3: Run the script

- Run the **Generate-GlobalizationDataverseSolution.ps1** script in PowerShell 7. Specify the following parameters:

    - **DvArtifactsSrcFolder** – Specify the working folder.
    - **SolutionFolder** – Specify the solution folder.
    - **ConfigurationsIndexRowName** – Specify the name of the Dataverse table record that has the index file for configurations. Use only alphanumeric characters and spaces. Note that if you change the name later, the corresponding row in the Dataverse table will have a different globally unique identifier (GUID), and index files will be duplicated. If you don't have any ER configurations, you can omit this parameter. Here's an example.

        ``` command
        Contoso Electronic Reporting Configurations Index
        ``` 

    - **FeaturesIndexRowName** – Specify the name of the Dataverse table record that has the index file for features. Use only alphanumeric characters and spaces. Note that if you change the name later, the corresponding row in the Dataverse table will have a different GUID, and index files will be duplicated. If you don't have any Globalization features, you can omit this parameter. Here's an example.

        ``` command
        Contoso Globalization Features Index
        ```

    Here's an example of the full PowerShell 7 command line.

    ``` command
    pwsh -ExecutionPolicy RemoteSigned -File C:\Generate-GlobalizationDataverseSolution.ps1 -DvArtifactsSrcFolder C:\DvArtifactsSrc -SolutionFolder C:\SampleSolutionUnpacked -configurationsIndexRowName "Contoso Electronic Reporting Configurations Index" -featuresIndexRowName "Contoso Globalization Features Index"
    ```

## Step 4: Pack the solution

- Pack the solution by using the **pac solution unpack** command. Here's an example.

    ``` command
    pac solution pack --zipfile C:\SampleSolutionWithContents.zip --folder C:\SampleSolutionUnpacked --packagetype Both
    ```

    For more information, see [pac solution unpack](/power-platform/developer/cli/reference/solution#pac-solution-unpack).

> [!NOTE]
> Check the size of the .zip file that's generated. If it exceeds 90 megabytes (MB), you must split your source files into multiple Dataverse solutions.

## Step 5: Import the solution into Dataverse

1. Import the solution back into Dataverse. For more information, see [Import solutions](/power-apps/maker/data-platform/import-update-export-solutions).

    You can also use the [pac solution import](/power-platform/developer/cli/reference/solution#pac-solution-import) command.

    > [!NOTE]
    > After you import the solution into Dataverse, there's no way to remove it together with the content. Although you can remove the solution, all inserted table records remain and must be manually cleaned up.

1. Publish your app on AppSource. For more information, see [Publish your app on AppSource](/power-platform/developer/appsource/publish-app).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
