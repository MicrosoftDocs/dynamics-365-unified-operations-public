---
title: Run the Regression suite automation tool (RSAT) with parallel execution
description: This topic explains how you can use the Regression suite automation tool (RSAT) version 2.3 and later to run multiple RSAT apps in parallel.
author: FrankDahl
ms.date: 12/16/2021
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.custom:
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2021-12-16

---

# Run the Regression suite automation tool (RSAT) with parallel execution

[!include [banner](../../includes/banner.md)]

The Regression suite automation tool (RSAT) version 2.3 and later let you run multiple RSAT apps in parallel.

## Benefits of parallel RSAT execution

You might be satisfied using RSAT on your own machine and running the app only once, because this approach meets your current needs. Nevertheless, parallel execution can make testing easier.

### One user runs two RSAT apps

When parallel execution is enabled, you can open the RSAT app more than once in your environment. In this way, you can use one or more RSAT apps to run tests, and at the same time use an RSAT app to create or maintain tests.

### Multiple users share an environment that they use to run the RSAT app

Parallel execution enables multiple users who share the same environment to run RSAT tests at the same time. In this way, you can create fewer virtual machine (VM) environments and share them with users. Therefore, individual users don't have to maintain an RSAT installation on their own machine. Instead, users can use the shared environment with RSAT.

### Run test suites in multiple Azure DevOps validation pipelines

Companies often set up Azure DevOps validation pipelines to run their test suites. The benefit of this approach is that pipelines can be started at a scheduled time or triggered as part of a build pipeline, and so on.

Parallel execution lets you split the full set of tests so that they run in smaller pipelines. You can then run multiple pipelines in parallel instead of in sequence. In this way, the tests might be able to be completed more quickly.

## Parallel RSAT execution in shared environments

Because you can create shared environments, individual users don't have to maintain an RSAT installation on their own machine. You just have to install RSAT and certificates, configure RSAT settings, and renew certificates every 60 days in each shared environment. Therefore, you can benefit from less overhead time and better total cost of ownership (TCO).

> [!NOTE]
> New certificates still require that non-admin scripts be run for each non-admin user in the environment.

If you have a limited number of available machines, shared environments help you make efficient use of your resources.

Shared environments aren't typically used to full capacity. Therefore, individual users can benefit from running multiple RSAT apps that make good use of the capacity. When multiple RSAT apps are run in parallel, test runs might be able to be completed more quickly than if the tests are run in sequence. This approach can also be used with Azure DevOps validation pipelines that run in parallel to complete validation passes more quickly.

Even users who continue to run tests on their own dedicated machine benefit from the new parallel execution if they run some of their tests in parallel. Because the tests might be able to be completed more quickly, wait times can be reduced, and productivity can increase.

## Changes that have been made to RSAT to enable parallel execution

The way that RSAT communicates with the test environment has changed. Technically, RSAT communicates with a Finance and Operations environment through communication port 745, which is used to communicate with the web. Previously, this port was exclusively used each time that RSAT started a test run.

In the new RSAT release, port 745 is no longer exclusively used. Instead, endpoints are technically added for each test run. The endpoints provide isolation from other test runs. Each endpoint has its own dedicated browser window where Finance and Operation apps perform processing. Everything is now neatly isolated during the communication, and no intervention or blocking occurs.

RSAT runs tests from local files in the working directory that is specified in the settings. During test runs, some existing files are changed, and some new files that contain results are added. Previously, this behavior could cause issues if two or more RSAT apps ran the same test case in the same working directory at the same time, because files could be overwritten and information could be lost.

The new RSAT release introduces new logic to manage files. When you try to run a test, if RSAT detects that another test run is currently using a specific test case, it blocks the new test run to help reduce the risk of overwritten files. You receive the following warning message:

> Currently another RSAT application is running playback that is locking test case '\[\<test case number\>\]'. Please hold a moment for this other RSAT application to complete the test case and try again.

If you're using the command-line interface (CLI) to run RSAT, you can specify the following switch: `/retry=[seconds]`. Then, if a test case is blocked, RSAT will wait for the specified number of seconds and then try to run the test again. However, RSAT will retry only once. If the second attempt fails, you receive the preceding message.

> [!TIP]
> To help prevent file locking issues, use separate working directories for each RSAT app that is running. If multiple users share the same machine, each user should use their own working directory on it. If multiple Azure DevOps pipelines run in parallel on the same machine, each pipeline should use its own settings and specific working directories.

## Considerations before you upgrade to RSAT version 2.3 and enable parallel execution

You should consider upgrading to the new RSAT version 2.3. We recommend that you coordinate with other users about a good time to upgrade. We also recommend that all users upgrade together. This approach is practical because executable files for test cases match only the RSAT version that they are generated by. If you mix different versions, executable files might have to be regenerated multiple times to match a running RSAT version.

In RSAT version 2.2 and earlier, multiple instances of the app can be open in your environment at the same time, although run test cases can be run from only one instance. In RSAT version 2.3, you can open the app more than once in your environment only if parallel execution is enabled in that environment. If parallel execution isn't enabled, and you try to open a second RSAT app when another RSAT app is already open, you receive the following error message.

> RSAT could not be run. There is currently running \<number\> instances of RSAT, and maximum on this environment is configured to \<number\>. Please close some of the running RSAT instances and try again, or increase the maximum number of allowed instances on the environment.

> [!NOTE]
> After you upgrade to RSAT version 2.3, you can revert to an earlier version, such as version 2.2, if you must. To revert, first uninstall RSAT version 2.3, and then install the RSAT version that you require. Your existing settings file will be kept. However, you will have to regenerate any test executable files that you generated while you were using RSAT version 2.3.

After you've installed RSAT version 2.3, you should decide when you want to enable parallel execution. Although parallel execution benefits all users and has no downsides, it must be explicitly configured in this version, because there are some preconditions to consider. In RSAT version 2.5 and later, Microsoft expects that parallel execution will be automatically enabled.

The following conditions must be met before you can enable parallel execution:

- Run only RSAT version 2.3 or later in an environment where parallel execution is enabled. If parallel execution is enabled, RSAT version 2.3 won't work well with earlier versions.
- Use only test Finance and Operations environments that run app version 10.0.21 and platform update 45 (PU45) or later. RSAT depends upon platform features.

> [!NOTE]
> Parallel execution doesn't start to be used immediately after you enable it. Instead, the option to use it becomes available to you when you're ready to run your suite of tests.

## Enable parallel RSAT execution

Parallel execution is enabled once for each environment that is used to run RSAT tests. It's enabled separately for RSAT that is run via the user interface (UI) and RSAT that is run via the CLI.

Before you begin, make sure that only version 2.3 or later of the RSAT client is used in an environment. The version is especially important if you're enabling parallel execution in shared environments.

To enable parallel execution, you must edit the relevant configuration file. You can find the configuration files under the RSAT installation folder. On US English machines, this folder is at \\Program Files (x86)\\Regression Suite Automation Tool.

In the RSAT installation folder, open the relevant configuration file for editing:

- To enable parallel execution for RSAT that is run via the UI, open the **Microsoft.Dynamics.RegressionSuite.WpfApp.exe.config** file.
- To enable parallel execution for RSAT that is run via the CLI, open the **Microsoft.Dynamics.RegressionSuite.ConsoleApp.exe.config** file.

> [!IMPORTANT]
> Be sure to close all running RSAT apps in the environment before you change the configuration files.

In both files, there is one main setting that you must configure. Set the value of **ParallelExecution** to **true**, as shown here.

```xml
<add key="ParallelExecution" value="true" />
```

Because the environment that you're using might have limitations on resources, you might want to limit the use of parallel execution. Therefore, the following three settings let you configure how much RSAT is allowed to run in parallel in the environment:

- **SupportedInstances** – This setting defines the number of RSAT apps that can run in the environment at the same time. This setting is shared by all users in the environment. Therefore, if the default value of **5** is used, and one user open three RSAT apps, a second user can open only two RSAT apps.
- **SupportedUsers** – This setting defines the number of concurrent users that can open an RSAT app in the environment. The default value is **10**.
- **SupportedTestCasesForEachInstanceSimultaneously** – This setting defines the number of test cases that can be started in an environment at the same time. The value is set to a very high number and should rarely have to be considered. The default value of **10000** should be suitable for most environments. This value will cause some memory consumption in the environment, but not enough to be concerned about.

The following example shows these three settings when their default values are used.

```xml
<add key="SupportedInstances" value="5" /><br>
<add key="SupportedUsers" value="10" />
<add key="SupportedTestCasesForEachInstanceSimultaneously" value="10000" />
```

Each time that RSAT is opened, it automatically uses any new settings that are saved in the configuration files.

## Best practices for parallel RSAT execution

- Immediately after you install RSAT version 2.3, open the RSAT app, and confirm that your settings are acceptable. If they are, return to your test suites to save the settings. Although this best practice isn't specific to parallel execution, it's especially important if you're using parallel execution. Parallel execution tries to isolate test runs, and some settings were previously stored in a file that was named CloudEnvironment.config. This file is no longer the source for the required data. Instead, that data has been moved to the user credential manager. In this way, RSAT can dynamically change the CloudEnvironment.config file so that it matches each test run to support multiple users.
- Consider organizing your tests into suites that are independent of each other. In other words, no suite should not have a data dependency on another suite. Each suite should be able to run before or in parallel with other suites. Some work will likely be required to make your tests independent so that they can run in parallel.
- Consider using only one RSAT app at a time to maintain tests. When you maintain tests, local files are changed, and those changes must then be uploaded. If two RSAT apps are used to maintain tests at the same time, there is a risk that one RSAT app will overwrite files from another RSAT app. Additional RSAT apps can be used to run tests.
- Consider using separate settings to specify a different working directory for each RSAT app that you use to run tests. In this way, if you use multiple apps to run tests, you help prevent file conflicts and reduce the risk that one RSAT app will overwrite files from another RSAT app. This practice is especially important for RSAT that is run via the CLI.
- A unique ID is assigned to each test case in Azure DevOps. However, a test case can be reused for multiple test suites. Therefore, there is a risk that two test runs will have to run the same test case and will cause a blocked case. RSAT will abort execution for an RSAT app that tries to run a case while another RSAT app is already running it. To help prevent conflicts, you should minimize reuse of test cases. Unfortunately, local files are organized by test case IDs and can cause conflicts. When these situations are unavoidable, consider using the **retry** command-line switch to help RSAT manage the situation.
- Shared environment can be configured so that they interact with only one test Finance and Operations environment at a time. Each test environment has its own set of certificates. Therefore, to switch to another environment, you must install new certificates in it. Users who have administrative access in the environment can install the new certificates for themselves. However, users who don't have administrative access will require help to install new certificates and run non-admin scripts in the environment each time that you change the test environment that is used with an environment that is used to run RSAT. Because this process might be cumbersome, consider whether it's feasible to devote at least one shared environment to each test environment, so that you can avoid regularly changing test environments.

    > [!NOTE]
    > An environment that is used to run RSAT can be configured to work with only one test environment at a time. This limitation exists because the certificates that are used to access the test environment must be bound to communication port 745, and only one set of certificates from one test environment can be bound at a time.

- When new non-admin users start to use a shared environment, you must run the non-admin script for them to enable them to access critical RSAT resources.
