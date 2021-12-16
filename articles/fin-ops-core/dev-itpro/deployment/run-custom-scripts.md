---
title: Run custom X++ scripts with zero downtime
description: This topic describes how to upload and execute a deployable package with a custom X++ script without requiring any downtime.
author: AndersGirke
ms.date: 12/16/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-12-16
ms.dyn365.ops.version: 10.0.25
---

# Run custom X++ scripts with zero downtime

[!include [banner](../includes/banner.md)]

This feature lets you to upload and run deployable packages containing custom X++ scripts without going through Dynamics Lifecycle Services (LCS), and without needing to suspend your system. This lets you correct minor data inconsistences without introducing any disruptive downtime.

The benefit of using an X++ script to correct minor data inconsistences is that the system will automatically adjust all related tables as needed when it runs the script. This secures the integrity of the correction and minimize the chance of introducing new inconsistencies.

All deployable packages uploaded to the system must go through a mandatory workflow. As a safety precaution, and to secure segregation of duties, the user who uploads a deployable package is not allowed to approve it for the next steps in the workflow (another user must do this). However, once the package is approved, the original uploader will be permitted to complete the remaining steps.

The system requires all deployable packages to go through a test run, and a user must validate the output as passed (Accept test log) before the script will be allowed to run on production data. If the output is not correct, the user marks the package as failed (Abandoned) and the script won't be allowed to run on production data.

Each uploaded package is saved in the system and goes through a defined workflow of events. For each event, the system keeps a log with a timestamp and the identity of the person who performed the event, thereby securing an audit trail.

As shown in the following illustration, the system provides details of how each deployable package was run in X++ and which entities were touched.

![Script details page](media/script-details.png "Script details page")

> [!IMPORTANT]
> This feature is intended for correcting minor data inconsistencies only. It must not be used for other purposes, including but not limited to:
>
>- Data collection
>- Schema changes
>- Data migration, or other long-running processes
>- Correction of data that can be corrected using other means, such as regularly business processes, data consistency tools or other self-service tools

> [!IMPORTANT]
> This feature lets authorized users change entities and their records directly, without running the business logic associated with those entities. This may result in data integrity issues. Your organization may require you to obtain approval and signoff by internal and external auditors (or other equivalent stakeholders) before and/or after running a script. For compliance reasons, changes that affect certain characteristics may also need to be disclosed in external reports (such as financial statements) or reported to government authorities. Your organization is solely responsibility for any changes made to its data using this feature, any approval and signoff or disclosure of such changes, and for complying with applicable laws. You bear all risks of using this feature.

## Assign duties to users to control access

This feature provides the following duties, which admins can use to control access to it:

- **Maintain custom scripts** – Grants the ability to upload, test, verify and run custom X++ scripts in environments (UAT, Prod)
- **Approve custom scripts** – Grants the ability to approve an uploaded custom X++ script. Approval is a mandatory step before any script can be tested, verified, and run.

To minimize the risk of malicious action, each script must be explicitly approved by a user other than the uploader. Before you can use this feature in your organization, an admin must assign the above duties to at least two relevant and highly trusted users. A single user can have both duties, but that user still won't be able to approve their own scripts.

## Create a deployable package

The feature requires a regular deployable package that can be created in Visual Studio. For instructions, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md).

Your deployable package must contain exactly one runnable X++ class. In other words, it must have one class with a method with the following signature:

```xpp
public static void main(Args _args)
```

> [!NOTE]
> The name of the main method must be lowercase.

## Code example

The following code example shows how a deployable package could be structured.

```xpp
class MyScriptClassForIssueXYZ
{
    public static void main(Args _args)
    {
        if (curExt() != 'DAT')
        {
            throw error("This script must run in the DAT company!");
        }

        ttsbegin;

        MyTable myTable;

        update_recordset myTable
            setting myField = 17
            where myTable.myReference == 'xyz';

        if (myTable.RowCount() != 1)
        {
            throw error("Not updating the expected row!");
        }

        info("Success");
  
        ttscommit;
    }

}
```

## Best practices

The following list provides a few best practices for writing, implementing, and running a script successfully. The list is not exhausted and should only be considered as guidance.

- **Do** write a success message at the end of the script. This will enable you to see that the script ran without exceptions.
- **Do** add explicit handling of the transaction scope.
- **Do** use existing business logic, such as `update()` methods, but **do not** bypass business logic by using `doUpdate()`, `doInsert()` and `doDelete()` methods. This will ensure dependent data is handled correctly and will significantly reduce the risk of further data inconsistencies
- **Do** assert the company context. This will expose common mistakes as a script runs, such as running the script in the wrong company.
- **Do** assert that the number of records impacted match your expectations. This will expose whether data has shifted unexpectedly on the system while the script was being prepared.
- **Do** use unique class names for each script, for example by including a reference to a work item in the name. This will prevent name clash issues when uploading the script. If a new iteration of a script is needed, be sure to give it a new name.
- **Do** test each script on a non-production environment first. Test for the intended impact and for unintentional side-effects on related data. Ensure the business processes that may be impacted can be successfully and fully completed afterwards.

## Upload and run a deployable package in Supply Chain Management

Use the following procedure to upload and run a script.

1. Go to **System administration \> Periodic tasks \> Database \> Custom scripts**.

1. Select **Upload**.

1. Select your deployable package (created as described in previously in this topic). You will also be asked to provide the purpose of the script.

1. The script must now be approved by another user (not the same user that uploaded the script). The approver must do the following:
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**
    1. Select the script to be approved and select **Details**.
    1. On the Action Pane, open the **Process workflow** tab and, from the **Start** group, select **Approve** or **Reject**. On approval, the script will be marked as such and unlocked for testing. If rejected, the script will be locked. Either way, the event is logged, and a copy of the script is kept in the system.

1. To ensure the script does what is intended, you must test it. The tester can be the same as the uploader or the approver or can be a third user (provided they have the required permissions). The tester must do the following:
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**.
    1. Select the script to be tested and select **Details**.
    1. On the Action Pane, open the **Process workflow** tab and, from the **Test** group, select **Run test**. This will run the script inside a temporary transaction that the system will automatically abort while collecting various logs and SQL statements.
    1. When it completes, review the logs, and verify that the results meet your expectations.
        - If you are satisfied with the test result, select **Accept test log** on the Action Pane (on the **Process workflow** tab, in the **Test** group). This will allow the script to be run and the event log will reflect that the script was tested, who tested it, and when.
        - If you aren't satisfied with the test result, select **Abandon** on the Action Pane (on the **Process workflow** tab, in the **End** group). This will prevent the script from being run, but the system will keep a copy of it together with a log of its history.

1. When you are confident the script has met your expectations, select **Run** on the Action Pane to run the script (on the **Process** workflow tab, in the **Run** group). This will do the same as the previous test run, except this time the transaction will be committed at the end.

1. Now that you have run the script, check the result and confirm whether it worked as intended.
    - If you are satisfied with the result, select **Purpose resolved** on the Action Pane (on the **Process** workflow tab, in the **End** group). On choosing this value, the event log will reflect that the script ran successfully, who verified it, and when. The script is saved but is now locked and can't be run again.
    - If you aren't satisfied with the result, select **Purpose unresolved** on the Action Pane (on the **Process workflow** tab, in the **End** group). On choosing this value, the event log will reflect that the script failed to resolve its intended purpose, who ran it, and when. The script is saved but is now locked and can't be run again. However, the system won't automatically undo the script action. You may need to write, import, and run a new script to undo the effects of the failed script on your system.

Your selection here becomes the final state for the script. If necessary, you can repeat the process.

## Upload and run a deployable package through LCS

As an alternative to deploying your package through Supply Chain Management, as described in the previous section, you can instead upload your deployable package to Dynamics Lifecycle Services (LCS) and deploy it using the normal procedure, as described in [Install deployable packages from the command line](../deployment/install-deployable-package.md).

This approach has fewer restrictions, but also provides less error protection and will require a restart of all servers and will therefore result in some downtime.
