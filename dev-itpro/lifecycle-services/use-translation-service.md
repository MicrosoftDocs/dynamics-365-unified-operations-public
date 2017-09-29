---
# required metadata

title: Microsoft Dynamics 365 - Translation Service User guide
description: This topic provides information about how to use the Translation service for Microsoft Dynamics 365 products.
author: kfend
manager: AnnBe
ms.date: 09/17/2017
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
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: ejchoGIT
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Microsoft Dynamics 365 - Translation Service - User guide 

[!include[banner](../includes/banner.md)]

## Accessing the Dynamics 365 - Translation Service
There are two ways to access the Dynamics 365 - Translation Service (DTS) in Lifecycle Services (LCS).  

### Option 1: Accessing from LCS Home page
Once you sign in to LCS, scroll the screen to the right to find the tiles waffle. Click the **Translation service** tile to access the DTS dashboard space.  

![alt text](./media/dts-tile.png "DTS tile")  

### Option 2: Accessing from within an LCS project
If you are creating a new LCS project or have an existing LCS project, access the project. Once you are in the project, scroll the screen to the far right to find the **Translation service** tile in **More tools** section and click on it.  

### What is the difference between the two options?
A LCS project is always tied to a product. So, any translation service request you submit from a project will carry the product type/version information automatically from the project, and you are not allowed to select a different product for the Translation service request. Also, when you are in a LCS project, the project owner and the users will have the access permission to the Translation service dashboard and to the service requests you have submitted from that project. This is useful when you work on one product translation project with a group of people in LCS. Below is an example of the dashboard view you and your project users may see.  

![alt text](./media/dts-project-dashboard.png "DTS dashboard view from within a project")

When you are in the LCS home page, you are not tied to any project yet until you create or access a LCS project. In light of that, when you access DTS from LCS home page and create a translation service request, you will be given a choice to select a product to use for the request. You can continue to add more requests with different products selection just by switching the product choice without having to exit the service and access a different translation project. This is very convenient when you are a partner or ISV working on multiple product translation projects. However, since you access the service outside a LCS project, not other user can view your requests in the translation service dashboard than you. So, this option provides you with your own dashboard to show all translation requests you make across all projects and from LCS home page, and help you manage them in one place. Below is an example dashboard view when accessing from LCS home page.  

![alt text](./media/dts-home-dashboard.png "DTS dashboard view from LCS home access")  

## Alignment
If you have previously translated files, you can create a XLIFF TM to recycle the files translation for new or newer version of source files.
The Align tool can be accessed by clicking the **Align** icon in the DTS project dashboard.  

![alt text](./media/dts-align-icon.png "Align icon")  

Once in the Align page, select source and target languages as well as the files to be aligned. Clicking the **Align** button will perform the alignment and pops up the download dialog box once the result is ready. You may need to explicitly allow popup in your browser.  

![alt text](./media/dts-align1.png "Align")  

Here are some tips to create the best XLIFF TM. The Align tool tool is smart enough to alleviate some of these issues, but it is easier to prevent them before you see the unexpected results in the output by following these simple rules:
  1.	Make sure both source and target files have the same number of resources.
  2.	Make sure the resources are in the same order in both source and target files.
  3.	Make sure there is no empty strings. The screenshots below show examples of empty strings from source and target.

Here is an example of empty strings in the source files. 
 
![alt text](./media/dts-align3.png "Empty strings")  

These empty strings are inherited into the XLIFF TM. ‘Rebate’ with empty target string is likely to be translated to empty string if this XLIFF TM is used.  

![alt text](./media/dts-align4.png "Missing strings")  

It is a good practice to review the aligned XLIFF before using it as a TM. Reviewed TUs should be marked as _Final_ or _Signed off_ so that they won’t be confused with unreviewed translations.  

## Creating a translation request
In the main dashboard, click on the **Add** icon to start creating the new translation request.  

![alt text](./media/dts-request1.png "Add a new request")  

Fill out the necessary fields for the request.

  +	**Request name** – Give a name to your request to easily identify it.
  +	**Product name** – Select the product that your source files are supporting. 
  +	**Product version** – Select the version of the product.
  +	**Target country/region** – Select a country/region to use the translation service for.
  +	**Translation source language** – Select a language that source files are written in.
  +	**Translation target language** – Select a language to translate into.

When selecting the languages, you will notice that some language names are in **bold**. Microsoft ships those languages commercially for the supported products (General Availability languages or GA languages), hence there are Microsoft trained MT systems available in those languages (trained on Dynamics terminology). For non-GA languages the MT system falls back to the general domain training.  
Please note that you will have to select **English – United States** for either source or target language to take advantage of Microsoft trained MT system on Dynamics linguistic assets.  

For example:

Source language |	Target language |	MT system to be used
--- | --- | ---
English – United States |	Japanese	| Microsoft trained MT system
Japanese |	English – United States	| Microsoft trained MT system
German	| Japanese	| Generic MT system*

*Unless the user provides XLIFF TM with more than 10,000 TUs.  

![alt text](./media/dts-request2.png "Create a new request")
 
Click **Create** to confirm the information and complete the creation of the request. This will take you to the next step, _‘Upload’_.  

## Uploading the files
Clicking the **Plus** icon will bring the **File upload** pane. You can upload a single zip file for each of two file types: Source zip file and XLIF TM zip file.  

### Source zip file
As the name implies, source zip file is the zip file that contains all the source files you wish to translate in the request. Different file types can be included as long as they are the supported file types for the product. Please refer to the [Supported products](./translation-service-overview.md#supported-products) for the supported file types.  

![alt text](./media/dts-upload1.png "File upload")  

### XLIFF TM zip file (Optional)
If you have XLIFF files from the previous DTS request, or used the **Align** tool to create a XLIFF TM, you can zip the XLIFF files and upload here. Strings that 100% match are recycled into the new source files so that you can keep the consistency between product versions. Details about the XLIFF can be found in the [XLIFF TM](./use-translation-service.md#xliff-tm) section.  

![alt text](./media/dts-upload2.png "File upload")  

In addition to the recycling process, DTS will use the XLIFF TM to create a customized MT system based on these rules:

  + Either source or target language is Microsoft’s GA language, AND the other language is **English- United States**.
  +	Either source or target language is **NOT** Microsoft’s GA language, AND XLIFF TM contains more than 10,000 translation units(TUs).

DTS will use general domain MT system after the recycling if:

  +	Either source or target language is **NOT** Microsoft’s GA language, AND XLIFF TM contains less than 10,000 translation units(TUs).  This is due to the requirements set by MT Hub.
  
When necessary files are uploaded, click **Submit** to start the translation process.

![alt text](./media/dts-submit.png "Submit")  

Please note that the process time depends on the number of requests in the DTS queue and wordcount volume of the submitted files.

  +	Request without XLIFF TM : As short as few minutes (depends on the file size.)

  +	Request with XLIFF TM:

     + Creating a custom MT system: 2~3 days
     + Using generic MT system: As few minutes (depends on the file size.)


## Translation complete
When the translation process is complete, you will receive an email notification. The result is available in the **Request output** section of DTS. 

![alt text](./media/dts-output.png "Request output") 

Once the translation process is done, two types of output files are produced:  

  + Multilingual files in XLIFF format for translation review  
    You can download the XLIFF file to review and edit the translations in this multilingual file which shows side by side source and target languages.  

  + Translated file in native format (same format to the source files)  
    Download this file if you have no intention to review and edit the translations.

We encourage you to post-edit the translations in the provided XLIFF file using the free Multilingual Editor provided or any XLIFF editor, or at least review them to make sure the translation output is up to your product’s quality standard.  


## Editing the translation in XLIFF
The XLIFF file will look similar to this when opened in the Multilingual Editor.  
 
![alt text](./media/dts-editor1.png "Multilingual Editor") 

Note that there are red and yellow circles towards the beginning of each line indicating the state of the translation. These states are automatically assigned by DTS depending on where the translation came from.

+	Red circle: the text is machine translated. DTS assigns the state as _Needs Review_*

+	Yellow, Green/Yellow, Green circle: the text is recycled. DTS inherited the state from the XLIFF TM used in the request.

*Please note that the state value shown may be slightly different depending on the XLIFF editor you are using.

You may apply the filter and only display the _Needs Review_ strings to verify the translation.  

![alt text](./media/dts-editor2.png "Needs Review")  
 
Reviewed string should be marked as _Translated_, _Final_, or _Signed off_ so that they can be used for recycling. **Translations that are marked as _Needs Review_ will not be included for recycling.**

## Regenerate
When you are done reviewing the translations and made edits, you will need to regenerate the output files based on the change you made in the XLIFF files.  

![alt text](./media/dts-regenerate.png "Regenerate")  

Clicking the **Regenerate** button will take you to the Regenerate pane where you can upload the edited XLIFF files. Please make sure to zip the edited XLIFF files before uploading.

![alt text](./media/dts-regenerate-upload.png "Regenerate Upload")  

Once **Upload** button is clicked, DTS will ask you to confirm the upload. DTS will regenerate the new output immediately after the confirmation.

![alt text](./media/dts-regenerate-output.png "Regenerate output")  

You can repeat this regenerate process as many times as necessary.

## XLIFF TM
DTS uses bi-lingual XLIFF format to store source and target language pairs. XLIFF format is based on XML, therefore, you can open it with any text editor. However, we recommend using XLIFF editors that are specifically designed to work with this format. You can use Microsoft free Multilingual Editor available in [Multilingual App Toolkit (MAT)](https://developer.microsoft.com/en-us/windows/develop/multilingual-app-toolkit).

In DTS, you can obtain a XLIFF TM in two different ways.

  +	By running Align tool  
  When you have previously translated files along with corresponding source files, you can use the Align tool to create a XLIFF TM. For more details, please refer to the [Alignment](./use-translation-service.md#alignment) section in this documentation.

  +	By completing the translation request  
  When a translation request is completed, DTS will provide user with XLIFF TMs as well as the translated files in the source format.

XLIFF files contain series of translation units (TUs) that are extracted from the source files. Here is an example of a translation unit:

![alt text](./media/dts-xlf.png "XLIFF translation unit")  

Same translation unit looks like this in the Multilingual Editor (blue highlighted):  
 
![alt text](./media/dts-editor3.png "XLIFF translation unit")  

## State
Each translation in the XLIFF file is associated with a state value. DTS assigns these values to each translation depending on how the string is translated.
When XLIFF TM is created with Align tool, all translations are marked as _Translated_. This is because the aligned TUs are produced from known good translations (i.e. previous product version).

However, when the XLIFF files are generated as results of a translation request, there are two types of states that may be used:

  +	_Needs Review_: the string has been machine translated.
  +	_Translated, Final_, or _Signed off_: These strings have been recycled. The states were inherited from the XLIFF TM.

This helps to immediately identify the _Needs Review_ strings when post editing. Post-reviewed string should be marked as _Translated_, _Final_, or _Signed off_ so that they can be used for recycling. **Translations that are marked as _Needs Review_ will not be included for recycling.**

Inherited state values for recycled strings are also helpful as you will never have to review the same string (with identical ID) again.  

## Glossary

Term | Description
--- | ---
*XLIFF* | XLIFF is an XML-based format created to standardize the way localizable data are passed between tools during a localization process and a common format for CAT tool files.
*Microsoft’s GA languages* | GA means General availability of theMicrosoft produced languages depend on the product.
*TU* | Translation unit. The translation unit typically contains source string, translation, state, state qualifier, and note.

