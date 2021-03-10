---
title: Configure non-administrator users to use RSAT
description: This article explains how grant these privileged resources to users in RSAT version 2.2 and later.
author: FrankDahl
manager: tfehr
ms.date: 03/09/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.custom:
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2021-03-09
ms.dyn365.ops.version: AX 7.0.0
---

# Configure non-administrator users to use RSAT

[!include [banner](../../includes/banner.md)]

The Regression suite automation tool (RSAT) uses privileged resources on the machine it is running on, that has required users to be an administrator on the machine to be able to run RSAT tests. This article explain how it is possible with RSAT version 2.2 or later to grant these privileged resources to users, such that they will be able to run RSAT tests without their user account need to be administrator on the machine.

These instructions will not allow users to install RSAT on the machine but only enable using RSAT once it has been installed. This includes first time use of RSAT where the Selenium framework install, or with new browser driver installation after updating browser versions. Those installation steps will still require running RSAT with administrator privileges.

When RSAT is installed on a VM that is shared by multiple users, then users can experience to become blocked when multiple users running RSAT at the same time. This happen when one user use resources like while running test cases that blocks access to other users. Changes with these instructions do not address this.

## Instructions for enabling non-administrator RSAT use

The tools for enabling non-administrator use consists of three files, two PowerShell scripts and a new shortcut file. These files are found in the RSAT installation folder within the subfolder called “Enable non admin”. Follow these detailed steps.

1. Run Windows PowerShell as Administrator.
2. Change directory to the folder “Enable non admin” in RSAT installation folder. The installation folder will be named according to the localized windows running on the machine.

    + Example “C:\Program Files (x86)\Regression Suite Automation Tool\Enable non admin”:

    ![List of files in PowerShell](media/config-file-list.png)

3. In the folder “Enable non admin” you will find these files:

    + Enable-non-admin-mode.ps1
    + Enable-non-admin-user.ps1
    + Regression Suite Automation Tool (Non admin).lnk

4. The first file "Enable-non-admin-mode.ps1" is a PowerShell script that enable non administrator mode for the machine. This does only need to be run once on each machine.

    Run the script “Enable-non-admin-mode.ps1” directly from “Enable non admin” folder and include passing of these required parameters:

    + (string)[action] – Option to enable/disable non administrator mode. Pick from two available values: "enable" or "disable".
    + (string)[thumbprint] – Certificate thumbprint. This must be the same as specified in RSAT under General settings.

    **DO NOT remove/copy this PowerShell script from the “Enable non admin” folder but run it only from this folder.

    Example:

    ```powershell
    .\Enable-non-admin-mode.ps1 "enable" "23055S5D1974C5E9467690DE4328FA6AC533632D"
    ```

    To get help execute this command:

    ```powershell
    help .\Enable-non-admin-mode.ps1 -full
    ```

5. The second file "Enable-non-admin-user.ps1" is a PowerShell script that enables non administrator mode for a user. Run this script for each user that is going to use RSAT on the machine.

    Run the script “Enable-non-admin-user.ps1” directly from “Enable non admin” folder and include passing of these required parameters:

    + (string)[action] – Option to define enable/disable non administrator mode. Has two available values: "enable" or "disable".

    + (string)[user] – The local username provided in the format "domain\userName"

    + (string)[thumbprint] – Certificate thumbprint. This must be the same as specified on RSAT settings form.

    **DO NOT remove/copy this PowerShell script from the “Enable non admin” folder but run it only from this folder.

    Example:

    ```powershell
    .\Enable-non-admin-user.ps1 "enable" "TESTDOMAIN\testuser" "23055S5D1974C5E9467690DE4328FA6AC533632D"
    ```

    To get help execute this command:

    ```powershell
    help .\Enable-non-admin-user.ps1 -full
    ```

6. You may now close the Windows PowerShell.

7. Copy the shortcut file “Regression Suite Automation Tool (Non admin).lnk” from the “Enable non admin” folder onto the users’ desktop. Technically the old shortcut called a VBS script that some users may not be allowed to execute, and the new shortcut will call the executable file directly.

    **DO NOT remove the old shortcut as this is a shared file that is used by all users on the machine. If you remove the file, then it will disappear for all users. It is fine to remove the old shortcut if all users are getting enabled to run non administrator use but notice that the shortcut  will reappear next time a new version of RSAT is installed on the machine.

8. Make sure to run RSAT using an administrator user at least once after it has been installed on the machine. This is for RSAT to complete installation of the Selenium framework, or installing new drivers needed with updated browser versions. Those installation steps still require to be run by a user with administrator privileges.

9. Finally, instruct the user to use the new shortcut Regression Suite Automation Tool (Non admin) for starting RSAT.

## Instructions for disabling non-administrator RSAT use

Should there be a need to reverting the machine back to run with administrator use, then this can be done by running the first PowerShell script “Enable-non-admin-mode.ps1” while passing the action parameter value “disable”.

Example:

```powershell
.\Enable-non-admin-mode.ps1 "disable"
```

## What about future versions of RSAT?

The current plan is to collect feedback from users running RSAT with this non administrator mode. The experience gained from this may result in that non administrator mode becomes the standard operation. The installation process may then be changed to automatically include the steps that enable this. Time will tell where this will lead.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
