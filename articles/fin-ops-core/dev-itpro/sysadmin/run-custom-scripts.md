---
title: Run custom scripts
description: This topic describes how to upload and execute a deployable package with a custom X++ script without requiring any downtime.
author: XXXX
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

This topic describes how to upload and execute a deployable package with a custom X++ script without requiring any downtime.

> [!IMPORTANT]
> This feature is intended for correcting minor data inconsistencies only. It must not be used for other purposes, including but not limited to:
> 
> - Data collection
> - Schema changes
> - Data migration
> - Other long-running processes

## Upload and run a script

Use the following procedure to upload and run a script.

1. Go to **System administration \> Periodic \> Data base \> Custom scripts**. <!-- KFM: I don't see this. FM needed? Version required? "Data base" is usually one word.-->
1. Select **Upload**. You will be asked to provide the purpose of the script.
1. The script must now be approved by another user (not the same user that uploaded the script). The approver must do the following:
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**
    1. Select the script to be approved and select **Details**.
    1. On the Action Pane, open the **Process** tab and, from the **Approval** group, select **Approve** or **Reject**.
1. To ensure the script actually does what is intended, you must test your script. The tester must do the following:
    1. Go to **System administration \> Periodic \> Data base \> Custom scripts**
    1. Select the script to be approved and select **Details**.
    1. On the Action Pane, open the **Process** tab and, from the **Validation** group, select **Test**. This will run the script inside a temporary transaction that the system will automatically abort while collecting various logs and SQL statements.
    1.  When it completes verify the logs meet expectations and click "Test verified" (or "Abandon" if you are not satisfied.)  <!-- KFM: Explain how to check the log.-->


Run the script.
When you are confident the script is meeting your expectations, click "Run" to execute the script. This will do the same as the previous test run, except the transaction will be committed at the end.
Final verification.
Now that the script has been run, you should confirm that it solved the purpose it was intended for. If it did, click "Verified"; otherwise click "Failed". In either case, this will be the final state for the script. If needed the process can be started over.
Creating a deployable package
This feature uses a regular deployable package that can be created in Visual Studio.

Please see https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/create-apply-deployable-package  for instructions.

The upload step will only accept deployable packages containing exactly one runnable X++ class. That is, one class with a method with this signature:
public static void main(Args _args)
Note: The name main of the method must be lowercase

Segregation of duties
This feature enables running a custom script without going through LCS. To minimize the risk of malicious intend each script must be explicitly approved. To enable this two duties exist: "Maintain custom scripts" and "Approve custom scripts". Assign these duties to highly trusted users within your organization. One individual can be both maintainer and approver, but will not be able to approve own scripts.

Alternatives
The deployable package can also be uploaded via LCS and deployed using the normal procedure. This will have fewer restrictions, and less protection from honest mistakes, but it will require a restart of all servers.


