---
# required metadata

title: Batch Parameter Versioning
description: This article provides information about the Batch parameter versioning and explains how you can use versioning to avoid issues related to pack/unpack.
author: raanandm
ms.date: 03/20/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: vikaush
ms.search.region: Global
ms.author: raanandm
ms.search.validFrom: 2024-03-20
---
# How to use Batch Parameter Versioning

When updating the parameters list of a batch job, it's advisable to implement versioning. This practice helps prevent errors like 'an error occurred while unpacking parameters for batch job XXXXX' during execution. Integrating versioning into the parameter list updates is beneficial as it mitigates this issue and aligns with recommended best practices.

Here's an example for how it could be achieved:

```X++
#define.Version2(2)
#localMacro.Version2List
#Version1List
,includeNewParam1
,includeNewParam2
#endmacro

#define.Version3(3)
#localMacro.Version3List
#Version2List
,includeNewParam3
,includeNewParam4
#endmacro

#define.Version4(4)
#localMacro.Version4List
#Version3List
,includeNewParam5
,includeNewParam6
#endmacro
#localMacro.VersionList
#Version4List
,includeNewParam7
#endmacro

boolean unpack(container packedClass)
{
    boolean ret = next unpack(packedClass);
    Integer version = conPeek(packedClass,1);
    container packedQueryRun;

    switch(version)
    {
        case #CurrentVersion:
             [version, #VersionList, packedQueryRun] = _packedClass;
             break;
        case #Version2:
             [version, #Version2List, packedQueryRun] = _packedClass;
             break;
        case #Version3:
             [version, #Version3List, packedQueryRun] = _packedClass;
             break;
        case #Version4:
             [version, #Version4List, packedQueryRun] = _packedClass;
             break;
        default:
             return false;
    }
    projectQueryRun = new QueryRun(packedQueryRun);
    return true;
}
```

Example for SysOperationServiceController, where you wish to have pack/unpack logic based on some pre-condition. Here, in the example it's based on isSessionInRealAsyncContext.

```X++
#define.CurrentVersion(2)
#define.version1(1)
#define.version2(2)
#localmacro.version1List
    className,
    methodName
#endmacro
#localmacro.CurrentList
    #version1List
    ,hasPendingAfterOperation
    ,operationReturnValuePacked
#endmacro

public container pack()
{
    Version packVersion = SysOperationServiceController::getPackVersion();
    operationReturnValuePacked = conNull();
    if (#version2 == packVersion)
    {
        if (this.canServiceReturnValueBePacked())
        {
            operationReturnValuePacked = this.packServiceReturnValue();
        }
        return [#version2,#CurrentList, super()];
    }
    else
    {
        return [#version1,#version1List, super()];
    }
}

internal static Version getPackVersion()
{
    if (SysRealAsyncContext::isSessionInRealAsyncContext())
    {
        // Use the version that packs the real async data members
        return #version2;
    }
    else
    {
        return #version1;
    }
}

public boolean unpack(container packedState)
{
    container packedSuper;
    int version;

    version = SysOperationHelper::getVersion(packedState);
    switch (version)
    {
        case #CurrentVersion:
            [version, #CurrentList, packedSuper] = packedState;
            break;
        case #version1:
            [version, #version1List, packedSuper] = packedState;
            break;
        default:
            return false;
    }

    // Check access before unpacking full state
    this.checkAccess();

    if (version == #CurrentVersion && operationReturnValuePacked != conNull())
    {
        this.unPackServiceReturnValue(operationReturnValuePacked);
    }

    return super(packedSuper);
}
```
Recommendations for future changes to batch job parameters:

- **Maintain Versioned Parameter Lists**: Ensure that both the old and new versions of the parameters list are retained. Further, versioning allows for backward compatibility and helps the smooth transition between parameter versions.

- **Adapt Unpacking Process**: Modify the unpacking process to handle both old and new versions of the parameters list. The unpacking mechanism can identify and process parameters from either version seamlessly.

- **Functional Logic Consideration**: The functional logic of the batch job should be designed to accommodate scenarios where an old version of the parameters list is provided. In such cases, the batch job should revert to the previous behavior, adhering to the specifications defined before the parameter change.

Implementing these guidelines empowers the batch job system to effectively manage changes to parameters. It ensures compatibility and consistency in functionality across different versions of the parameters list.
