---
# required metadata

title: Manage Dynamics 365 for Operations Support experiences
description: 
author: kfend
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 0fa10573-8146-446e-8124-8a7af9546add
ms.search.region: Global
# ms.search.industry: 
ms.author: anupams
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Manage Dynamics 365 for Operations Support experiences



Support tool on Microsoft Dynamics Lifecycle Services (LCS) helps you manage support incidents. Support tile on LCS lets you create a virtual machine (VM) in Microsoft Azure that has the same hotfixes installed as your local environment. You can reproduce and record the incident on the virtual machine, and then submit the VM to our support team. Support follows up by investigating the incident, testing a fix on the virtual machine, if a fix is found, and sending the VM and the fix back to you for verification.
**Note:** Virtual machines are only available for Microsoft Dynamics AX 2012 R2 and AX 2012 R3 environments.

## Prerequisites
To use Support tool, you must have previously created a project in Lifecycle Services, and installed and run the System diagnostics in your environment. For more information, see [System diagnostics (Lifecycle Services, LCS)](/ax-2012/system-diagnostics-lcs.md).

## Open a new incident
1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Open a project, and then click the Support tile.
3.  On the Incidents list application bar, click Create.
4.  Search for an existing solution by keyword or by object path in the Microsoft Dynamics AX Application Object Tree (AOT).

    | **Note**                                                  |
    |-----------------------------------------------------------|
    | If you click a solution, Issue search opens on a new tab. |

5.  If you don’t find an existing solution, click Create incident.
6.  On the Share diagnostic data page, select the appropriate environment.If you have not previously run the System diagnostics in your environment, you are prompted to install and run it. After you run the System diagnostics, you must update the Share diagnostic data page.
7.  On the Describe the issue pages, enter details about the issue.To create a virtual machine for an issue, select Yes for the question Would you like to create a virtual machine, and then click Create a new virtual machine for your environment. You do not have to submit a virtual machine before you can open an issue.
    
    | **Note**                                                                                                                                                                                             |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | If you have previously created a virtual machine snapshot for another support incident, you can reuse that snapshot for this issue. Only a single virtual machine snapshot is available at any time. |

    After you click Submit, the following steps occur:
    -   An incident is created and added to the Incidents list.
    -   Based on the information that the System diagnostics finds, a VM is created that includes that same kernel and application hotfixes as your local environment.
    -   When the VM has been created, you receive an email invitation to access it.
    -   You receive an email message from the Microsoft Support Engineer who is working on your case. This message asks you to grant the engineer access to your project in the Project contributor role. If you do not grant access, the engineer cannot work on your case. For more information about how to grant access, see [Projects (Lifecycle Services, LCS)](/ax-2012/projects-lcs.md).

## Reproduce an incident
1.  In Lifecycle Services, on the Incidents list, in the Support request ID entry for your incident, under Repro VM action, click Customer repro.
2.  On the Reproduce issue page, click Start VM. Then, after the virtual machine has started, click Connect.
3.  When the VM opens, log on to it.
    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><strong>Note</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>The VMs that Support tile creates are limited-use virtual machines that are hosted on Azure. These VMs have the following restrictions:
    <ul>
    <li>Snapshots cannot be downloaded.</li>
    <li>Only a single snapshot can be created for an environment. Any new snapshot that is created overwrites the previous version.</li>
    <li>VMs are temporary and are deleted when a case is closed. VMs should not be used for any purpose except troubleshooting.</li>
    </ul></td>
    </tr>
    </tbody>
    </table>

4.  Optional: Configure the application settings in the VM so that they match the settings in your local environment. When you have finished configuring the VM, on the Reproduce issue page, click Take Snapshot.
5.  Reproduce the issue on the VM.By default, a video recording tool records your actions as you reproduce the issue. Support can then use the recording to follow the actions that you performed. You can turn off and restart recording.You can also view the recordings.
6.  When you have finished reproducing the issue, on the Reproduce issue page, select Yes for Issue reproduced in VM, and then click Submit your virtual machine.The status of the Support request changes to Submitted.

## Verify a fix
When the support engineer has verified your issue and received a hotfix, he or she sets the status of the incident to Customer verify, and sends an email message.
1.  In Lifecycle Services, on the Incidents list, in the Support request ID entry for your incident, under Repro VM action, click Customer verify.
2.  On the Proposed solution page, click Start VM. Then, after the VM has started, click Connect.
3.  When the VM opens, log on to it.

    | **Important**                               |
    |---------------------------------------------|
    | The proposed hotfix is installed on the VM. |

4.  Try to reproduce the issue on the VM.If you cannot reproduce the issue, on the Proposed solution page, select Yes for Accept proposed solution. Enter remarks about how the solution worked, and then click Submit your response.
5.  When you have finished recreating the issue, on the Reproduce issue page, select Yes for Issue reproduced in VM, and then click Submit your virtual machine.



