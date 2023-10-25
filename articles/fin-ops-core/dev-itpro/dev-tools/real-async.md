---
# required metadata

title: Real async feature enhancements
description: This article describes real async feature enhancements.
author: twheeloc
ms.date: 10/25/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2023-12-01
ms.dyn365.ops.version: AX 7.0.0

---

# Real async feature enhancements

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article describes the real async feature enhancements to SysOperations. These enhancements enable operations to be run asynchronously without blocking the client as the regular SysOperations do. Therefore, users can initiate multiple operations simultaneously. In this way, the enhancements help improve overall performance.

The status of async operations can be viewed on the same page.

To use real async operations, you must extend the `SysOperationServiceController` class.

For more information about the SysOperation framework, see [SysOperation Framework Overview](../../dynamicsax-2012/developer/sysoperation-framework-overview.md).

## Enable the real async feature

1. In the **Feature management** workspace, select **Check for updates**.
2. Enable **SysRealAsyncOperationsFeature**.
2. After you've enabled the feature in Feature management, go to **Client performance options**, and select the **Enable real async operations** option.

### Uptake the real async feature

To use real async operations, you must first extend the `SysOperationServiceController` class, as you normally do to implement SysOperations. Then override the following methods to enable real async operations for your service operation class.

#### Method 1: canRunAsRealAsync

By default, the `canRunAsRealAsync` method returns *false*.

1. To enable users to control the execution type, introduce a feature in Feature management for each operation that must be processed in real async. Then confirm that the feature is enabled in your operation class.
2. To enable user control of the execution type by default, return *true*. To disable it by default, return *false*.

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

#### Method 2: canSysRealAsyncOperationId

By default, the `canSysRealAsyncOperationId` method returns an empty string.

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
