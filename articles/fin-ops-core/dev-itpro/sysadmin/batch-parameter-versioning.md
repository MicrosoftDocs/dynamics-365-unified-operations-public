---
title: Batch parameter versioning
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

# Batch parameter versioning

[!include [banner](../includes/banner.md)]


In Finance and Operations, batch processing is used for executing tasks asynchronously in the background. Batch jobs can range from simple tasks like data imports to complex calculations or integrations.

Updating batch parameters and versioning them might be necessary in various situations, including:

- **Configuration Changes**: When there are changes in the configuration settings or parameters required for batch processing. For example, if a batch job previously processed data in a certain way but now needs to accommodate new fields or data sources, the batch parameters might need to be updated accordingly.

- **Performance Optimization**: As your system evolves and grows, you might find opportunities to optimize batch processing for better performance. It could involve tweaking batch parameters such as batch size or datasets to make the processing more efficient.

- **Bug Fixes or Enhancements**: If bugs are found in batch processing or if new features affect batch jobs, you might have to change batch parameters to fix problems or include new functions.

- **Integration Changes**: If there are changes in external systems or interfaces that interact with batch jobs, such as API endpoints or data formats, you might need to update batch parameters to accommodate these changes and ensure seamless integration.

Versioning batch parameters is essential for maintaining a record of changes and ensuring consistency and reliability in batch processing. Versioning allows you to track the history of parameter changes, revert to previous versions if necessary, and maintain documentation for auditing purposes. It also helps in managing and deploying changes across different environments such as development, testing, and production. 

## Why do you get errors during batch parameter unpack?

While executing a batch, you might get error message like **an error occurred while unpacking parameters for batch job XXXXX**. This error occurs when the batch job is unable to unpack the parameters correctly due to issues such as:

- **Parameter Changes**: When you update batch parameters, you might encounter errors during the pack/unpack process if the batch job isn't designed to handle different versions of the parameters list. The pack/unpack process is used to serialize and deserialize batch parameters for storage and execution. If the batch job expects a specific set of parameters and receives a different set due to version changes, it can lead to errors during execution.

- **Custom Code or Extensions**: If custom code or extensions are being used with the batch job, errors in the code or extensions could cause issues during parameter unpacking. Check the custom code or extensions for any errors or inconsistencies and address them accordingly.

- **Security Permissions**: Insufficient permissions or security settings can sometimes prevent the batch job from accessing the necessary data or resources, resulting in errors during parameter unpacking. Ensure that the user executing the batch job has the appropriate permissions to access all required resources.

## How to version batch parameters?

Here's an example for how it could be achieved in **RunBaseBatch** or **SysOperationServiceController** implementation of batch class:

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
    ,includeNewParam8
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

Here's an example for how it could be achieved in a batch class that is extending another batch class, which has its own implementation of unpack:

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

Recommendations for future changes to batch job parameters:

- **Maintain Versioned Parameter Lists**: Ensure that both the old and new versions of the parameters list are retained. Further, versioning allows for backward compatibility and helps the smooth transition between parameter versions.

- **Adapt Unpacking Process**: Modify the unpacking process to handle both old and new versions of the parameters list. The unpacking mechanism can identify and process parameters from either version seamlessly.

- **Functional Logic Consideration**: The functional logic of the batch job should be designed to accommodate scenarios where an old version of the parameters list is provided. In such cases, the batch job should revert to the previous behavior, adhering to the specifications defined before the parameter change.

Implementing these guidelines enables the batch processing to effectively manage changes to parameters. It ensures compatibility and consistency in functionality across different versions of the parameters list.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
