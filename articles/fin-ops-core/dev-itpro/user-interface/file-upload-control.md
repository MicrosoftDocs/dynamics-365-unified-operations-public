---
title: File upload control
description: This article provides information about the file upload control. This control lets users upload files.
author: jasongre
ms.date: 07/27/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 82f47d4d-912c-4f85-81f9-b09c723f72fc
---

# File upload control

[!include [banner](../includes/banner.md)]


This article provides information about the file upload control. This control lets users upload files.

## Overview

The file upload control lets users upload a file. It also lets developers control the upload process and manage the file that is uploaded, based on their requirements. 

[![Illustration of file upload control.](./media/fileupload001.png)](./media/fileupload001.png) 

The file upload control can have three styles. You control the style by using the **Style** property.

-   The **Standard** style shows the file name field together with **Browse**, **Upload**, and **Cancel** buttons.
-   The **Minimal** style shows only the **Browse** button.
-   The **MinimalWithFileName** style shows the file name field and the **Browse** button.

The **FileTypesAccepted** property of the file upload control lets you limit the types of files that users can upload. The file types that users can upload are primarily controlled by the associated upload strategy. The **FileTypesAccepted** property on the file upload control should be used only if further restrictions are required. If the upload control tries to specify file types that are restricted by the upload strategy, the **Browse** button becomes unavailable.

| Allowed file types    | Allowed file types from the upload strategy | Final result                          |
|-----------------------|---------------------------------------------|---------------------------------------|
| ".jpg,.png"           | ".jpg,.png,.gif,.txt"                       | ".jpg,.png"                           |
| "image/png"           | "image/\*"                                  | "image/png"                           |
| "image/\*"            | "image/png"                                 | The **Browse** button is unavailable. |
| ".jpg,.png,.gif,.txt" | ".jpg,.png"                                 | The **Browse** button is unavailable. |

You can use the **OnBrowseButtonClicked**, **OnUploadAttemptStarted**, and **OnUploadCompleted** overrides to hook into the various stages of the file upload process. You can also create custom file upload strategies and associate them with a file upload control by using the **FileUpload Strategy Class** property.

## Design classes
There are two base classes that developers can work with for the file upload control:

-   **Upload strategy class** – This base class lets developers control various parameters that should be enforced for uploaded files, such as the types of files that a user can upload and the maximum size of a file. It also lets developers determine where and how the uploaded file should be stored. All derived classes used for upload strategies must inherit from the abstract **FileUploadStrategyBase** class.
-   **Upload result class** – This base class lets developers access the details of a file that was uploaded by a user, such as its name, content type, and upload status. It also lets developers open and delete the corresponding file. All derived classes used for specializing upload results must inherit from the abstract **FileUploadResultBase** class.

The framework provides a default upload strategy class that is named **FileUploadTemporaryStorageStrategy** and a default upload result class that is named **FileUploadTemporaryStorageResult**. This upload result class stores uploaded files to the temporary blob storage and provides a download URL. Developers can also implement their own custom upload strategy and upload result classes as required. For the upload strategy, two abstract methods from the **FileUploadStrategyBase** class must be implemented: **uploadFile** and **getResultClassName**. The **uploadFile** method handles where and how the file is stored. The **getResultClassName** method retrieves the upload result class that is used in this strategy. The **FileUploadResultBase** class has fields for the file name, the upload status, the content type of the file, and the log message. This class can be extended as required. All new properties should be able to be serialized and deserialized. The **openResult** method opens the file as a stream, and the **deleteResult** method deletes the file from the corresponding data storage.

## Sequence diagram
The file upload control accepts the file and upload strategy in the client, and sends them to the file services. The file services start a new session, create an instance of a strategy class, and call the **uploadFile** method. When the **uploadFile** method has finished storing the file in the data source, a file upload result class returns to the file services. This class is sent back to the client, which might trigger the **OnUploadCompleted** event to deal with the post-process. 

[![File upload sequence diagram.](./media/fileuploadcontrolusageanddesign1.png)](./media/fileuploadcontrolusageanddesign1.png)

## Scanning uploaded files for viruses and malicious code
Before you upload a file into the system, you might want to scan it for viruses or malicious code. Therefore, in version 10.0.12 and later, an extension point is available so that customers can integrate the file scanning software of their choice into the file upload process. Similar extension points are also available for scanning attachments. For more information about those extension points, see [Configure document management](../../fin-ops/organization-administration/configure-document-management.md). 

> [!IMPORTANT]
> Out of the box, finance and operations apps don't scan files for viruses and malicious code, and we don't recommend specific software for file scanning. Instead, customers are responsible for choosing their own file scanning software, and for adding the appropriate code to the delegate handlers so that they can use the software or service of their choice to scan files.

In particular, the **FileUploadResultBase** class exposes the **delegateScanStream()** delegate. This delegate applies to any file upload scenario where the **Upload strategy class** has been specialized. The upload process will fail if the scanning service determines that the file is malicious.    

### Implementation details
The following example of the **ScanDocuments** class shows boilerplate code for the handler. For general information about how to implement handlers for delegates, see [EventHandlerResult classes in request or response scenarios](../dev-tools/event-handler-result-class.md).

```xpp
    public final class ScanDocuments
    {

        [SubscribesTo(classStr(FileUploadResultBase), staticDelegateStr(FileUploadResultBase, delegateScanStream))]
        public static void FileUploadResultBase_delegateScanStream(System.IO.Stream _stream, EventHandlerRejectResult _validationResult)
        {
            if (!ScanDocuments::scanStream(_stream))
            {
                _validationResult.reject();           
            }
        }

        private static boolean scanStream(System.IO.Stream _stream)
        {
            /* 
            Custom implementation required for connecting to a scanning service
            If document scanning process found an issue, return false; otherwise, return true;
            */
            return true;
        }
    }
```



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
