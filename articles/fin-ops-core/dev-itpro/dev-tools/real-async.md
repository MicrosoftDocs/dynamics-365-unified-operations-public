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


[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

# Real async feature enhancements
This article describes the real async feature enhancements to the functionality of SysOperations that allows operations to be executed asynchronously without blocking the client as the regular SysOperations do.
This allows users to initiate multiple operations simultaneously and improve the overall performance. The status of Async operations can be viewed on the same screen. 

 
To use real async operations, you must extend the SysOperationServiceController class. 
For more information about the SysOperations framework, see [SysOperation Framework Overview](/dynamicsax-2012/developer/sysoperation-framework-overview.md). 

## Enable the Real Async feature 

1. In **Feature management**, click **Check for updates**. Enable **SysRealAsyncOperationsFeature**. 
2. After enabling the feature in Feature Management, go to **Client performance options**, select the **Enable real async operations** option.  

### How to uptake the real async feature 

To use real async operations, you must extend SysOperationServiceController class as you normally do to implement SysOperation. 
After extending the SysOperationServiceController class, override the following methods to enable real async for your service operation class: 

Method1: canRunAsRealAsync 

1. By default, this method returns false. 
2. For end users to control execution type, introduce a feature in **Feature management** for each operation that must be processed in real async. Confirm that this feature is enabled in your operation class. 
3. To enable/disable by default, return true/false. 

Example: 
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

Method2: canSysRealAsyncOperationId 

1. By default, this method returns an empty string.
2. Override this new method and return the "id" of the current operation. 

For example, if the operation is confirming a sales order, then return the "SalesId" of the order. 

Example: 
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









