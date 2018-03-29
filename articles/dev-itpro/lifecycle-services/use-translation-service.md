---
# required metadata

title: Microsoft Dynamics 365 Translation Service - User interface file translation
description: This topic provides information about how to use the UI translation service for Microsoft Dynamics 365 products.
author: kfend
manager: AnnBe
ms.date: 03/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ejchoGIT
ms.search.validFrom: 2018-03-27
ms.dyn365.ops.version: AX 7.0.0

---

# Microsoft Dynamics 365 Translation Service - User interface file translation

[!include[banner](../includes/banner.md)]

This topic provides information about how to translate a user interface (UI) file for Microsoft Dynamics products or solutions.  

For more information about the Dynamics 365 Translation Service, see [Dynamics 365 - Translation Service overview](translation-service-overview.md#microsoft-dynamics-365---translation-service-overview).  
for information about how to translate a document, see [Dynamics 365 - Translation Service user guide - Documentation file translation](use-translation-service-ua.md). 

## Create a translation request
1. In Lifecycle Services (LCS), on the DTS dashboard, click**Add** to create a new translation request.  

    ![Add button](./media/dts-request1.png "Add button")

2. Enter the required information for the request.  

    | Field name        | Description |
    |-------------------|-------------|
    | Request name      | Enter a description of your request. |
    | File type      | Select **User Interface**. |
    | Product name      | Select a product. If you accessed DTS from within a LCS project, this field is automatically filled in and is read-only. |
    | Product version   | Select a product version. If you accessed DTS from within a LCS project, this field will show the default product version information from the project. If needed, select a different version if needed.|
    | Target country/region | Select the country/region where the translated file will be released to.|
    | Translation source/target languages | Select the language pair from/to which translation will be done. All languages that are supported for the selected product name and version will be available in these fields. The language name in BOLD in the list represents a Dynamics product General Availability (GA) language. Microsoft-trained machine translation (MT) systems are available in those languages. In other words, the MT system is trained on Microsoft Dynamics terminology. For non-GA languages, the MT system falls back to the general domain training.|

3. Click **Create**.
        
    > [!NOTE]
    > To take advantage of the Microsoft-trained MT system on Microsoft Dynamics linguistic assets, you must select **English – United States** as either the source language or the target language.

    For example, 

    | Source language         | Target language         | MT system that will be used |
    |-------------------------|-------------------------|-----------------------------|
    | English – United States | Japanese	              | Microsoft-trained MT system |
    | Japanese                | English – United States	| Microsoft-trained MT system |
    | German                  | Japanese                | Generic MT system, unless the user provides an XLIFF TM that has more than 10,000 TUs |


## Upload the files
Select the plus sign (**+**) in each section to open the **File upload** form.  

### Upload files to translate (Required)
Create one zip file that contains all of the user interface files in source language that you would like to translate in the request. The zip file can include different file types, provided the file types are supported for the product. For more information about supported file types, see [Supported products](translation-service-overview.md#supported-products). Note that the source files you are uploading are not altered by DTS but are instead used to create the corresponding target language files from them. 

### Upload XLIFF translation memory files (optional)
If you have XLIFF translation memory (TM) files from a previous UI translation request, or if you used the [Align](use-translation-service-tm.md#creating-a-translation-memory---alignment) tool to create an XLIFF TM, you can zip them before you upload. Strings that match are recycled to ensure consistency between product versions. For more information about XLIFF TM, see the [Microsoft Dynamics 365 Translation service - Translation memory](use-translation-service-tm.md) topic.

In addition to using the XLIFF TM for the recycling process, DTS uses the XLIFF TM to create a customized [MT system](translation-service-overview.md#custom-trained-mt-system), based on the following rules:

+ Either the source language or the target language is a Microsoft GA language, and the other language is **English – United States**.
+ Neither the source language or the target language is a Microsoft GA language, and the XLIFF TM contains more than 10,000 TUs.

If neither the source language or the target language is a Microsoft GA language, and the XLIFF TM contains fewer than 10,000 TUs, DTS uses a general domain MT system after recycling. This occurs because of the requirements that are set by MT Hub.

After you upload the required files, select **Submit** to start the translation process. After you submit and a new request is created in the DTS dashboard, you can click the request ID to view a summary of your request and the status in **Request status** tab. 

![Request status tab](./media/dts-request-status.png "Request status tab")

Note that the processing time depends on the number of requests that are in the DTS queue and the volume of the word count in the source files that you submit.

+ Depending on the file size, UI requests that don't have an XLIFF TM may be completed in a few minutes.
+ If a UI request does have an XLIFF TM, the time that is required depends on the type of MT system:

    + Creating a custom MT system requires two to three days.
    + If you're using a generic MT system, requests can be completed in a few minutes, depending on the file size.


## After translation is complete
When the translation process is complete, you will receive an email notification from DTS. The result is available on the **Request output** tab of the **Request details** page.

![Request output tab](./media/dts-output.png "Request output tab")

For a UI request type, after the translation process is completed, two types of output file are available:

+ **File for translation review** – Download the XLIFF file to review and, as required, edit the translations in this file. The file shows the side-by-side source and target languages.
+ **Translated file in source format** – Download this file if you don't intend to review or edit the translations. Native format means that the file is in the same format as the source file you submitted.


### Review and edit the UI translation in XLIFF file
We recommend that you review and edit the translations in the XLIFF file that DTS provided to verify that the translation output meets your product's quality standards. For more inofrmation about editing the XLIFF file, see [Editing an XLIFF translation memory](use-translation-service-tm.md#editing-an-xliff-translation-memory). 

### Regenerate output files
When you finish reviewing and editing the translation files, you must regenerate the output files in the source file format so you can apply the latest translations you edited into your target language user interface files.

1. On the **Request output** tab, click **Regenerate**. A new tab, **Regenerate(By Partner)** will be added. 
2. Click the plus (**+**) to open the **File upload** form. 
3. Zip the edited XLIFF file(s) and then click **Upload**. Do not change the XLIFF file name from what DTS provided on the **Request output** tab. DTS will also regenerate the refreshed output file in the source format in the same file name as provided in **Request output** tab. 
4. After you click **Upload** , you're prompted to confirm that action. DTS regenerates the new output files shortly after confirmation on the **Regenerate(By Partner)** tab. 

![Regenerated output](./media/dts-regenerate-output.png "Regenerated output")

You can repeat the regeneration process as many times as is necessary.

