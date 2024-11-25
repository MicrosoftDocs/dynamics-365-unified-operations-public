---
title: Real async feature enhancements
description: Learn about real async feature enhancements to SysOperations, including an outline on how to enable the real async feature with examples.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 11/08/2024
ms.reviewer: twheeloc
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2023-12-01
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Real async feature enhancements

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article describes the real async feature enhancements to SysOperations. These enhancements enable operations to be run asynchronously without blocking the client as the regular SysOperations do. Therefore, users can initiate multiple operations simultaneously. In this way, the enhancements help improve overall performance.

The status of async operations can be viewed on the same page.

To use real async operations, you must extend the `SysOperationServiceController` class.

For more information about the SysOperation framework, see [SysOperation Framework Overview](/dynamicsax-2012/developer/sysoperation-framework-overview).

## Enable the real async feature

1. In the **Feature management** workspace, select **Check for updates**.
2. Enable **SysRealAsyncOperationsFeature**.
2. After you've enabled the feature in Feature management, go to **Client performance options**, and select the **Enable real async operations** option.

### Uptake the real async feature

To use real async operations, you must first extend the `SysOperationServiceController` class, as you normally do to implement SysOperations. Then override the following methods to enable real async operations for your service operation class.

#### Method 1: canRunAsRealAsync

By default, the `canRunAsRealAsync` method returns *false*.

1. To turn ON/OFF the real async execution of your operation at runtime, introduce a feature for your operation and confirm the feature is enabled inside canRunAsRealAsync method. If the main Real Async feature is enabled in Feature management, the returned value decides if the operation will be ran in real async or not.

Here's an example.

```
public boolean canRunAsRealAsync()
{
    if (featureManagementForSalesOrderConfirmationRealAsync::isEnabled())
    {
        // This operation can run through real async
        return true;
    }
    else
    {
        return false;
    }
}
```

2. Return *true* to run the operation in real async by default.

#### Method 2: getSysRealAsyncOperationId

By default, the `getSysRealAsyncOperationId` method returns an empty string.

- Override this new method, and return the ID of the current operation. For example, if the operation is confirming a sales order, return the `SalesId` value of the order.

Here's an example.

```
public SysRealAsyncOperationId getSysRealAsyncOperationId()
{
    Common sourceTable = this.parmSourceTable();
    str orderId;
    if (sourceTable && sourceTable is SalesTable)
    {
        SalesTable salesTable = sourceTable;
        orderId = salesTable.SalesId;
    }
    else
    {
        orderId = this.parmId();
    }
    return orderId;
}
```
