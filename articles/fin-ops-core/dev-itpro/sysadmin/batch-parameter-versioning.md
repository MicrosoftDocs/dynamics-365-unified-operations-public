---
title: Batch parameter versioning
description: Learn about batch parameter versioning and explains how you can use it to avoid issues that are related to pack/unpack.
author: raanandm
ms.author: raanandm
ms.topic: article
ms.date: 03/20/2024
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-03-20
---

# Batch parameter versioning

[!include [banner](../includes/banner.md)]

In finance and operations apps, batch processing is used to run tasks asynchronously in the background. Batch jobs can range from simple tasks such as data import to complex calculations or integrations.

There are various situations where it might be necessary to update batch parameters and version them. Here are some examples:

- **Configuration changes** – Changes in the configuration settings or parameters might be required for batch processing. For example, a batch job that previously processed data in a specific way must now accommodate new fields or data sources. In these cases, you might have to update the batch parameters.
- **Performance optimization** – As your system evolves and grows, you might find opportunities to optimize batch processing for better performance. This optimization might involve adjusting batch parameters such as batch size or datasets to make the processing more efficient.
- **Software updates or enhancements** – If bugs are found in batch processing, or if new features affect batch jobs, you might have to change the batch parameters to fix issues or include new functions.
- **Integration changes** – Changes might be made in external systems or interfaces that interact with batch jobs, such as API endpoints or data formats. In these cases, you might have to update the batch parameters to accommodate the changes and ensure seamless integration.

Versioning of batch parameters is essential for maintaining a record of changes and ensuring consistency and reliability in batch processing. It lets you track the history of parameter changes, revert to previous versions if you must, and maintain documentation for auditing purposes. It also helps you manage and deploy changes across different environments, such as development, testing, and production environments. 

## Why you might receive errors during batch parameter unpack

When you run a batch, you might receive an error message like "An error occurred while unpacking parameters for batch job XXXXX." This error occurs when the batch job can't correctly unpack the parameters because of issues such as the following list:

- **Parameter changes** – When you update batch parameters, you might encounter errors during the pack/unpack process if the batch job isn't designed to handle different versions of the parameters list. The pack/unpack process is used to serialize and deserialize batch parameters for storage and execution. If the batch job expects a specific set of parameters but receives a different set because of version changes, errors can occur during execution.
- **Custom code or extensions** – If custom code or extensions are used with the batch job, errors in the code or extensions might cause issues when parameters are unpacked. Review the custom code or extensions for any errors or inconsistencies, and address them accordingly.
- **Security permissions** – Insufficient permissions or security settings can sometimes prevent the batch job from accessing the necessary data or resources. As a result, errors can occur when parameters are unpacked. Ensure that the user who runs the batch job has the appropriate permissions to access all required resources.

## How to version batch parameters

The following example shows how batch parameter versioning can be achieved in the **RunBaseBatch** or **SysOperationServiceController** implementation of a batch class.

```X++
#define.Version1(1)
#define.Version2(2)
#define.CurrentVersion(3)

#localMacro.Version1List
    includeNewParam1
#endmacro

#localMacro.Version2List
    #Version1List
    ,includeNewParam2
    ,includeNewParam3
#endmacro

#localMacro.CurrentVersionList
    #Version2List
    ,includeNewParam4
#endmacro


boolean unpack(container _packedClass)
{
    Integer version = conPeek(_packedClass,1); 

    switch(version)
    {
        case #CurrentVersion:
            [version, #CurrentVersionList] = _packedClass;
            break;
        case #Version2:
            [version, #Version2List] = _packedClass;
            break;
        case #Version1:
            [version, #Version1List] = _packedClass;
            break; 
        default:
            return false;
    }

    return true;
}
```

The following example shows how batch parameter versioning can be achieved in a batch class that extends another batch class that has its own implementation of **unpack**.

```X++
#define.Version1(1)
#define.CurrentVersion(2)

#localmacro.Version1List
    param1,
    param2
#endmacro

#localmacro.CurrentVersionList
    #Version1List
    param3,
    param4
#endmacro

public boolean unpack(container packedState)
{
    container packedSuper;
    int version;

    version = conPeek(packedState,1);

    switch (version)
    {
        case #CurrentVersion:
            [version, #CurrentVersionList, packedSuper] = packedState;
            break;
        case #Version1:
            [version, #Version1List, packedSuper] = packedState;
            break;
        default:
            return false;
    }

    return super(packedSuper);
}
```

## Best practices

The following list describes recommendations for future changes to batch job parameters:

- **Maintain versioned parameter lists.** Ensure that both old and new versions of the parameter list are retained. Versioning allows for backward compatibility and helps smooth the transition between parameter versions.
- **Adapt the unpacking process.** Modify the unpacking process so that it handles both old and new versions of the parameter list. The unpacking mechanism can seamlessly identify and process parameters from either version.
- **Consider the functional logic.** The functional logic of the batch job should be designed to accommodate scenarios where an old version of the parameter list is provided. In these scenarios, the batch job should revert to the previous behavior and adhere to the specifications that were defined before the parameter change.

Implementation of these recommendations enables the batch job system to effectively manage changes to parameters. It ensures compatibility and consistency in functionality across different versions of the parameters list.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
