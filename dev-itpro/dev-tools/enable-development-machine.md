---
# required metadata

title: Create a new user on a development machine | Microsoft Docs
description: When an environment is first deployed, only one user account is enabled as a developer on the virtual machine (VM). This article explains how to enable another user account as a developer on a development VM.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-06 00:43:04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 31621
ms.assetid: c67c296c-e40a-4f74-a4ce-aff6fe91f606
ms.region: Global
# ms.industry: 
ms.author: robadawy

---

# Create a new user on a development machine

When an environment is first deployed, only one user account is enabled as a developer on the virtual machine (VM). This article explains how to enable another user account as a developer on a development VM.

When an environment is first deployed, only one user account is enabled as a developer on the virtual machine (VM). This user is preconfigured by Microsoft Dynamics Lifecycle Services (LCS) or is the local administrator account on downloaded virtual hard disks (VHDs). However, you can enable a new user account to develop on the VM. Even after you enable a new account, only one developer can develop at a time on the same VM/application.

## Prerequisites
To enable a new user account to develop on the VM, the user account must be an administrator on the VM. Additionally, you must log on to the VM by using the credentials of the default developer account. If the VM is a Microsoft Azure VM, the account information is available on the environment page in LCS. If the VM is a local VM that runs on the downloaded VHD, use the local administrator account. For more information, see [Access Instances](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-tools/access-microsoft-dynamics-ax-7-instances-2).

## Steps
1.  Download the following script: ProvisionAxDeveloper.ps1, the script is available at <https://github.com/Microsoft/Dynamics-AX-Scripts>.
2.  Open a Microsoft Windows PowerShell **Command Prompt** window as an administrator.
3.  Run the ProvisionAxDeveloper.ps1 script. Specify the following parameters:

    -   **DatabaseServerName** – Typically, this is the machine name.
    -   **Users** – Use the following format: &lt;domain or machine name&gt;\\user1, … &lt;domain or machine name&gt;\\user n

    **Examples**

        > ProvisionAxDeveloper.ps1 RDXP00DB20RAINM RDXP00DB20RAINM\username1

        > ProvisionAxDeveloper.ps1 -databaseservername RDXP00DB20RAINM -users RDXP00DB20RAINM\username1,RDXP00DB20RAINM\username2

4.  If more than one user account will be developing on the same version control workspace, you need to make the workspace public.
    1.  In Visual Studio, open **Source Control Explorer**, select the workspace dropdown and select **Manage workspaces**.
    2.  Select the application workspace, click **Edit,** then click **Advanced** and set the workspace to **Public workspace**.[![publicworkspace](./media/publicworkspace.png)](./media/publicworkspace.png)



