---
title: Run custom scripts
description: This topic describes how to upload and execute a deployable package with a custom X++ script without requiring any downtime.
# author: <!-- KFM: I need your GitHub user name to put here. -->
ms.date: 11/09/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mfp
ms.search.validFrom: 2021-11-09
ms.dyn365.ops.version: 10.0.23
---

# Run custom scripts

[!include [banner](../includes/banner.md)]

This feature lets users develop and run custom scripts on Supply Chain Management without going through Dynamics Lifecycle Services (LCS).

This topic describes how to upload and execute a deployable package with a custom X++ script without requiring any downtime.

> [!IMPORTANT]
> This feature is intended for correcting minor data inconsistencies only. It must not be used for other purposes, including but not limited to:
> 
> - Data collection
> - Schema changes
> - Data migration
> - Other long-running processes

## Assign duties to users to control access

This feature provides the following duties, which let you control access to it:

- **Maintain custom scripts** – <!-- KFM: Add a short description -->
- **Approve custom scripts** – <!-- KFM: Add a short description -->

To minimize the risk of malicious action, each script must be explicitly approved by a user other than the uploader. Before you can use this feature at your organization, an admin must assign these duties to at least two different relevant and highly trusted users. A single user can have both duties, but that user still won't be able to approve their own scripts.

## Create a deployable package

Start by creating a deployable package containing the script you want to run on your system. The feature requires a regular deployable package that can be created in Visual Studio. For instructions, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md).

Your deployable package must contain exactly one runnable X++ class. In other words, it must have one class with a method with the following signature:

```xpp
public static void main(Args _args)
```

> [!NOTE]
> The name of the `main` method must be lowercase.

## Upload and run a deployable package in Supply Chain Management

Use the following procedure to upload and run a script.

1. Go to **System administration \> Periodic tasks \> Database \> Custom scripts**. <!-- KFM: I don't see this. FM needed? SCM Version required? -->
1. Select **Upload**.
1. Select your deployable package (created as described in the previous section). You will also be asked to provide the purpose of the script.
1. The script must now be approved by another user (not the same user that uploaded the script). The approver must do the following:
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**
    1. Select the script to be approved and select **Details**.
    1. On the Action Pane, open the **Process** tab and, from the **Approval** group, select **Approve** or **Reject**.  <!-- KFM: What effects do each of these have? On what basis will the approver make their decision? Do we expect the approver to inspect or test the script somehow? -->
1. To ensure the script actually does what is intended, you must test your script. The tester must do the following:  <!-- KFM: Is this part of the approval process? Or does the script need to be approved before it can be tested? Do we think the tester is the same as the approver or the same as the uploader? -->
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**.
    1. Select the script to be approved and select **Details**.
    1. On the Action Pane, open the **Process** tab and, from the **Validation** group, select **Test**. This will run the script inside a temporary transaction that the system will automatically abort while collecting various logs and SQL statements.
    1. When it completes, review the logs and verify that the results meet your expectations.
        - If you are satisfied with the test result, select **Test verified** on the Action Pane (on the **Process** tab, in the **Validation** group). <!-- KFM: What effect does this have? Unlocks the run command? -->
        - If you aren't satisfied with the test result, select **Abandon** on the Action Pane (on the **Process** tab, in the **Finalize** group). <!-- KFM: What effect does this have, and what do I no next, start over? Also, it seems like this button should be under "Test verified" in the **Validation** group. -->

1. When you are confident the script is meeting your expectations, select **Run** on the Action Pane to run the script (on the **Process** tab, in the **Run** group). This will do the same as the previous test run, except this time the transaction will be committed at the end.
1. Now that you have run the script, check the result and confirm whether it worked as intended.
        - If you are satisfied with the result, select **Verified** on the Action Pane (on the **Process** tab, in the **Finalize** group). <!-- KFM: What effect does this have? -->
        - If you aren't satisfied with the result, select **Failed** on the Action Pane (on the **Process** tab, in the **Finalize** group). <!-- KFM: What effect does this have? -->

    Your selection here becomes the final state for the script. If necessary, you can repeat the process. <!-- KFM: Can we run a script twice, or is it locked once marked verified, failed, or Abandoned? -->

## Upload and run a deployable package through LCS

As an alternative to deploying your package through Supply Chain Management, as described in the previous section, you can instead upload your deployable package to Dynamics Lifecycle Services (LCS) and deploy it using the normal procedure. <!-- KFM: Can we link to more info about this procedure?  --> This approach has fewer restrictions, but also provides less error protection and will require a restart of all servers.
