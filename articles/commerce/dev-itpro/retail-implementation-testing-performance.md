---
title: Testing and performance issues
description: This article describes recommended practices for testing and performance for Microsoft Dynamics 365 Commerce implementation projects.
author: andreashofmann1
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: andreash
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: Retail 7.3
ms.search.industry: Retail
ms.search.form: 
---


# Testing and performance issues

[!include [banner](../../includes/banner.md)]

This document describes practices and tools that are related to functional testing, performance testing, and performance troubleshooting.

## User acceptance testing

The main purpose of user acceptance testing (UAT) is to verify that specific business scenarios work as you expect. The testing should include not only the customizations, but also out-of-box Microsoft functionality and non-happy-path testing. The goal is to catch anything that doesn't work correctly before you go to the production environment.

For the best results, the UAT environment should be a Tier 2 through Tier 5 environment, not a development environment (Tier 1).

If a development environment is used, there are scenarios where a developer who uses the same environment can cause errors (for example, uncommitted source changes or debugger attached errors). The switch between Microsoft Internet Information Services (IIS) Express and IIS can also cause issues. Additionally, because there is no way to know exactly what has happened on a development machine, Microsoft support for a Tier 1 environment is very limited.

A production environment can be used for UAT (for example, as a "dry run" for go-live). However, if you require access to the database for any reason, you must go through deployment support engineer (DSE) service requests. Therefore, this approach might not be efficient. Additionally, the production environment isn't available for a long period before the planned go-live date.

The UAT should be done after you deploy officially built deployable packages. It should not be done on packages that are manually built in Microsoft Visual Studio. The reason is that there is no way to prove what code changes were included in a manually built package. Only an official build system provides assurance and an audit trail of the exact changes that are in a specific build.

If you use the Store Commerce app or Store Commerce for web, make sure that you use the correct user roles. You should test by signing in as both a manager and a cashier who has lower privileges.

## Performance
### Channel performance

In some cases, channel performance might not be as good as you expected. Poor performance is often caused by the following factors. This list is in order from highest to lowest impact.

- Additional custom calls to Commerce Scale Unit. If you extend the product with additional calls, performance often decreases significantly. Not only is there a possibility of additional processing, but the network latency must also be considered. We recommend that you try to avoid any additional Commerce Scale Unit calls. Often, you can accomplish the same tasks by using extension properties and extending existing Commerce runtime (CRT) handlers or triggers.
- Additional channel database extensions. Make sure that your custom SQL is efficient and uses correct indexes.
- Multiple runs of the same custom or built-in CRT SQL queries. If this approach is too expensive, caching in the CRT request handler can be applied, as appropriate.

For more details, see the [Commerce for IT pros and developers](/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page) articles.

When you investigate store performance, follow the suggestions in [Retail Channel performance investigations](https://dynamicsnotes.com/retail-channel-performance-investigations/).

### Using telemetry data to find performance issues

If you must troubleshoot the performance (especially slow SQL queries or SQL deadlocks), the environment diagnostics page in Microsoft Dynamics Lifecycle Services (LCS) shows valuable telemetry data. You can use this data to find potential performance issues in code, configuration, or design. For more details, see [Monitoring and diagnostics tools in Lifecycle Services](../../fin-ops-core/dev-itpro/lifecycle-services/monitoring-diagnostics.md). That information should help you determine why some batch processes or form loads are slow.


### Performance testing

Typically, when you test the performance of a system, you should focus on components where there is competition for many shared resources. These resources might differ for different projects, customers, or requirements.

Here are some of the reasons why bottlenecks can occur:

- Resource-intensive calculations, such as statement posting, change calculations for channel data synchronization, warehousing operations that involve a large product assortment, and MRP (Material Requirements Planning) runs
- Complex business logic for multiple terminals or stores that run on a few Commerce Scale Unit 
- Integrated third-party systems (integrated from either Commerce or Commerce Scale Unit)
- Real-time transaction services that are frequently called from Commerce Scale Unit.
- Non-standard or extended standard functionality (for example, extended statement posting that uses a custom WHS code)

In general, default and non-real-time POS operations aren't considered bottlenecks because they have their own dedicated resource: the computer that the POS is installed or running on. Performance issues are typically caused by the business logic or "chatty" calls to Commerce Scale Unit.

Ideally, performance testing should be done after some initial optimizations have already been completed by using the information earlier in this article. If the system doesn't perform well for a single user or process, it won't perform well for concurrent users or processes. For more information, see [Retail Channel performance investigations](https://dynamicsnotes.com/retail-channel-performance-investigations/). Additionally, in the Finance documentation, search for "PerfSdk" or "Trace parser."

Because every project is different, it's difficult to give a general answer about the exact performance tests that must be run. For example, if the count of transaction sales lines is low (less than 100,000 per day for all stores), and if no custom extension code has been added for statement posting, a performance test should not be required for posting. However, if the count of sales lines is substantially higher, or if major custom changes have been added, a performance test for posting is a good idea.

Usually, the hardware capabilities of every environment differ. However, performance issues can usually be reproduced in other environments if the code and data are similar. We don't recommend that you use a production environment for performance testing. A good practice is to use the same data in development, test, and production environments. The development environment can then be used to work on and verify a fix. Because many performance-critical code paths are data-dependent, the same issues might not be seen for a Contoso sample database.

After you've completed a performance fix, you should verify the fix in a test environment. Deploy an officially built package to the test environment, and if the issue is fixed, mark the package as a release package. 

Any fix of a larger performance issue should be followed by a new performance test. Often, a large issue masks other smaller issues. After the top issue is resolved, the next issues can be found and worked on until the performance meets the customer's expectations.

## Additional resources
[Set up new environments, Azure DevOps, and branches for Commerce projects](./new-environments-visual-studio-teams-branch-retail-projects.md)

[Update code and environments for Retail projects](./updating-environments.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
