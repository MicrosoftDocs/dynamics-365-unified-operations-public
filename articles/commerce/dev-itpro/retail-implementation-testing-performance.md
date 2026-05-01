---
title: Testing and performance issues
description: This article provides an overview of practices and tools related to functional testing, performance testing, and performance troubleshooting of Microsoft Dynamics 365 Commerce implementation projects.
author: andreashofmann1
ms.date: 02/19/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2017-12-31
ms.custom: 
  - bap-template
---

# Testing and performance issues

[!include [banner](../../includes/banner.md)]

This article provides an overview of practices and tools related to functional testing, performance testing, and performance troubleshooting of Microsoft Dynamics 365 Commerce implementation projects.

## User acceptance testing

The main purpose of user acceptance testing (UAT) is to verify that specific business scenarios work as you expect. The testing should include not only the customizations but also out-of-box Microsoft functionality and non-happy-path testing. The goal is to catch anything that doesn't work correctly before you go to the production environment.

For the best results, use a Tier 2 through Tier 5 environment for UAT, not a development environment (Tier 1).

If you use a development environment, errors can occur when a developer uses the same environment. For example, errors can happen because of uncommitted source changes or debugger attached errors. The switch between Microsoft Internet Information Services (IIS) Express and IIS can also cause errors. Additionally, because there's no way to know exactly what happened on a development machine, Microsoft support for a Tier 1 environment is limited.

You can use a production environment for UAT (for example, as a "dry run" for go-live). However, if you require access to the database for any reason, you must go through deployment support engineer (DSE) service requests. Therefore, this approach might not be efficient. Additionally, the production environment isn't available for a long period before the planned go-live date.

Perform UAT after you deploy officially built deployable packages. Don't perform UAT on packages that are manually built in Microsoft Visual Studio. The reason is that there's no way to prove what code changes were included in a manually built package. Only an official build system provides assurance and an audit trail of the exact changes that are in a specific build.

If you use the Store Commerce app or Store Commerce for web, make sure that you use the correct user roles. Test by signing in as both a manager and a cashier who has lower privileges.

## Performance

### Channel performance

In some cases, channel performance isn't as good as you expected. Poor performance often comes from the following factors. This list is in order from highest to lowest impact.

- Additional custom calls to Commerce Scale Unit. If you extend the product with extra calls, performance often decreases significantly. Not only is there a possibility of extra processing, but you must also consider the network latency. Avoid any extra Commerce Scale Unit calls. Often, you can accomplish the same tasks by using extension properties and extending existing Commerce runtime (CRT) handlers or triggers.
- Extra channel database extensions. Make sure that your custom SQL is efficient and uses correct indexes.
- Multiple runs of the same custom or built-in CRT SQL queries. If this approach is too expensive, you can apply caching in the CRT request handler, as appropriate.

For more information, see [Commerce for IT pros and developers](/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page).

### Use telemetry data to find performance problems

If you need to troubleshoot performance problems (especially slow SQL queries or SQL deadlocks), the environment diagnostics page in Microsoft Dynamics Lifecycle Services (LCS) shows valuable telemetry data. You can use this data to find potential performance problems in code, configuration, or design. For more information, see [Monitoring and diagnostics tools in Lifecycle Services](../../fin-ops-core/dev-itpro/lifecycle-services/monitoring-diagnostics.md). That information should help you determine why some batch processes or form loads are slow.

### Performance testing

Typically, when you test the performance of a system, focus on components where many shared resources create competition. These resources might differ for different projects, customers, or requirements.

Here are some reasons why bottlenecks can occur:

- Resource-intensive calculations, such as statement posting, change calculations for channel data synchronization, warehousing operations that involve a large product assortment, and MRP (Material Requirements Planning) runs
- Complex business logic for multiple terminals or stores that run on a few Commerce Scale Unit
- Integrated partner systems (integrated from either Commerce or Commerce Scale Unit)
- Real-time transaction services that Commerce Scale Unit frequently calls
- Nonstandard or extended standard functionality (for example, extended statement posting that uses a custom WHS code)

In general, default and non-real-time POS operations aren't bottlenecks because they have their own dedicated resource: the computer that the POS is installed on or running on. Performance issues typically stem from the business logic or "chatty" calls to Commerce Scale Unit.

Ideally, you complete performance testing after you address some initial optimizations by using the information earlier in this article. If the system doesn't perform well for a single user or process, it doesn't perform well for concurrent users or processes. For more information, search for "PerfSdk" or "Trace parser" in the Finance documentation.

Because every project is different, it's difficult to give a general answer about the exact performance tests that you must run. For example, if the count of transaction sales lines is low (less than 100,000 per day for all stores), and if you don't add custom extension code for statement posting, a performance test isn't required for posting. However, if the count of sales lines is substantially higher, or if you add major custom changes, a performance test for posting is a good idea.

Usually, the hardware capabilities of every environment differ. However, you can usually reproduce performance issues in other environments if the code and data are similar. Don't use a production environment for performance testing. Use the same data in development, test, and production environments. You can use the development environment to work on and verify a fix. Because many performance-critical code paths are data-dependent, you might not see the same issues for a Contoso sample database.

After you complete a performance fix, verify the fix in a test environment. Deploy an officially built package to the test environment, and if the issue is fixed, mark the package as a release package.

Any fix for a larger performance issue should be followed by a new performance test. Often, a large issue masks other smaller issues. After you resolve the top issue, you can find and work on the next issues until the performance meets the customer's expectations.

## Additional resources

[Set up new environments, Azure DevOps, and branches for Commerce projects](./new-environments-visual-studio-teams-branch-retail-projects.md)

[Update code and environments for Retail projects](./updating-environments.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
