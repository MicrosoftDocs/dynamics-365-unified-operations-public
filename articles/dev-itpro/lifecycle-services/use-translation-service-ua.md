
# Microsoft Dynamics 365 - Translation Service user guide - Documentation file translation

[!include[banner](../includes/banner.md)]

This topic describes the steps you can follow to translate a documentation file for the Dynamics products or solutions. 
+ Create a new translation request
+ Review and edit the translation
+ Upload the edited translation to regenerate the target language documentation file  

See [Dynamics 365 - Translation Service Overview topic](./translation-service-overview.md#microsoft-dynamics-365---translation-service-overview) to learn how the service works and how to access it.  
See [Dynamics 365 - Translation Service user guide - User interface file translation](./use-translation-service.md#) for the steps to translate a user interface file. 

## Create a translation request
1. On the DTS dashboard, select the **Add** button to create a new translation request.  

    ![Add button](./media/dts-request1.png "Add button")

2. Enter the required information for the request. See below for details of each field.  

    | Field name        | Description |
    |-------------------|-------------|
    | Request name      | Type your own description |
    | File type      | Select **Documentation**. Note this will be only available if you have turned on the **Dynamics 365 Translation Service - Documentation Translation Support** from [LCS Preview features](./translation-service-overview.md#accessing-lcs-preview-features). |
    | Product name      | Select a product name. If you accessed DTS from within a LCS project, this field is automatically filled in as read-only. |
    | Product version   | Select a product version. If you accessed DTS from within a LCS project, this field will show the product version information from the project as a default and you can select a different version if needed.|
    | Target country/region | select a country where the translated file will be released to.|
    | Translation source/target languages | Select the language pair from/to which translation will be done. All languages that are supported for the selected product name and version will be available in these fields. Language name in BOLD in the list represents Dynamics product General Availability (GA) language. Microsoft-trained machine translation (MT) systems are available in those languages. In other words, the MT system is trained on Microsoft Dynamics terminology. For non-GA languages, the MT system falls back to the general domain training.|

3. Click **Create** to go to the next step.
        
    > [!NOTE]
    > To take advantage of the Microsoft-trained MT system on Microsoft Dynamics linguistic assets, you must select **English – United States** as either the source language or the target language.

    Here is an example.

    | Source language         | Target language         | MT system that will be used |
    |-------------------------|-------------------------|-----------------------------|
    | English – United States | Japanese	              | Microsoft-trained MT system |
    | Japanese                | English – United States	| Microsoft-trained MT system |
    | German                  | Japanese                | Generic MT system, unless the user provides an XLIFF TM that has more than 10,000 TUs |


## Upload the files
Select the plus sign (**+**) button in each section to open the **File upload** form. 

### Upload files to translate (Required)
Currently only Microsoft Word documentation (.docx) file format is accepted to process. Create a zip file including all the docx files you want to translate. You can upload only one zip file. 

### Upload XLIFF or TMX translation memory files (Optional)
If you have a TMX translation memory you got from a previous DTS request, and/or a XLIFF TM from a user interface file translation, you can attach them to recycle the translations from them in the new document translation you are submitting. Zip the files before you can upload it. Only one zip file is accepted. 

After you've uploaded the required files, select **Submit** to start the translation process. Once submitted and a new request ID is created in the DTS dashboard, you can click the request ID to see the summary of your request and the status in **Request status** tab. 

![Request status tab](./media/dts-request-status-ua.png "Request status tab")

Note that the processing time depends on the number of requests that are in the DTS queue and the volume of the word count in the source files that you submit. 

## After translation is completed
When DTS is done processing your translation request, you will receive an email notification from DTS. The result is available on the **Request output** tab of your request details page.

![Request output tab](./media/dts-output-ua.png "Request output tab")

There are three types of output files available:

+ **File for translation review** - Doenload this file to review and edit the translated document strings in a table view. The file provides the side-by-side source and target languages segments.
+ **Translated file in source format** - Download this file if you don't intend to review or edit the translations. This file is in the same style as the source docx file you submitted and ready to use. 
+ **Translation memory** - Download this file if you want to recycle these translations the next time you are submitting a new translation request with a newer version of the source document. 


### Review and edit the Documentation translation
DTS provides the Documentation translation review file in .docx format. You can download it from **File for translation review** section above and open it in Microsoft Word. It provides a convenient side-by-side table view as shown in the example below so you can easily compare the source and target text to help your review and edit. Once the review is done to this file, you will have to save and upload it back to DTS to generate the refreshed .docx file output in the original source style. See the next [Regenerate output files](./use-translation-service.md#regenerate-output-files) section for this step.    

![DOCX file to review](./media/dts-doc-review.png "DOCX file for translation review") 
 
When editing the review .docx file, please make note of the following:

+ Only edit the text in the **Target segment** column.
+ Do not add/remove any row.
+ Do not change the order of the rows or columns.
+ Do not add/remove the red tags. Most red tags represent formatting and styles in .docx. 
+ If it is necessary to move the red tags, be careful not to switch a start tag (i.e. <116>) and its end tag (i.e. </116>).


### Regenerate output files
When you've finished reviewing and editing a review docx file, you must regenerate the output file in the source document style so you can apply the latest translations you edited into your target language document.

In the **Request output** tab, click **Regenerate** button. It will add a new tab **Regenerate(By Partner)**. Using the plus (**+**) button, open the **File upload** form and upload the edited files. Do not change the .docx review file name from what DTS provided in **Request output** tab. Be sure to zip the files before you upload them.

After you select **Upload** button, you're prompted to confirm that action. It may take a while for DTS to process to regenerate the refreshed docx in the source document style and you will receive an automated email notification once it's ready. Then you can come back to the request to download the final output files in the **Regenerate(By Partner)** tab.  

![Regenerated output](./media/dts-regenerate-output-ua.png "Regenerated output")

You can repeat the regeneration process as many times as you require.


