---
# required metadata

title: Deploy your custom Help
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in certain Dynamics 365 apps. 
author: edupont04
manager: AnnBe
ms.date: 10/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SystemParameters
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 16141
ms.assetid: 0b9c8630-9474-4473-80fd-7db5d54b2275
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Deploying custom Help

[!include [banner](../includes/banner.md)]

You can configure your own help to connect to the Help pane in Dynamics 365 Finance, Supply Chain Management, Retail, and Talent. In this topic, you can read about how to do that.  

## Plan your Help system

Depending on the customer's Dynamics 365 solution, their final Help system can come from a number of different sources. In the following, we assume that you are a consultant from a Dynamics 365 partner who wants to add custom Help to their customer's solution.  

There are at least three different scenarios for where the source content for the customer's Help experience comes from:

- The Help pane serves content from Microsoft and one additional provider on a custom help tab  

- The Help pane serves content from Microsoft and multiple additional providers on a custom help tab  

- The Help pane serves content from one provider on a custom help tab, and does not include Microsoft Help content  

- The Help pane serves content from multiple providers on each their custom help tab, and does not include Microsoft Help content  

The choice of scenario that you support in your implementation determines whether your custom Help implementation includes Microsoft Help content, and whether you need to collaborate with other solution providers or partners to combine help from multiple solutions.  

### Help site

In order to provide the users of the solution with access to Help in the Help pane, you must publish your content on a website. The website can be private or public, but we recommend that users do not have to log in so that they can access your content.  

You can deploy your content to an existing website, or you can set up a dedicated website based on Azure.  

### Reuse Dynamics AX 2012 content

You can reuse content from Dynamics AX 2012. For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).  

### Getting updated content from Microsoft

If your Help solution is based on Microsoft's content, then you can fork our repo and then use standard Git tools to keep your fork updated with our content updates. However, because we make frequent updates, it may be easiest to get a completely new clone of the content of our repo and regenerate the Help from the clone on a regular basis.  

> [!TIP]
> The Custom Help Toolkit includes a console app that can help integrate the latest Microsoft content with yours. For more information, see [Running the Custom Help Toolkit](custom-help-toolkit.md).

## Host your content on Azure

You can set up an Azure web app and host your content there for easy integration with the in-product Help pane. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create [a free account](https://azure.microsoft.com/free/) before you begin. The general process for creating your Azure resources consists of the following steps:

1. In the Azure portal, create a web app, storage account, and Azure Search Service.  

    - The Web App stores and serves HTML files  
    - The Storage account stores JSON files  
    - The Search service performs indexing  
2. Upload the HTML files to the Web App by using File Transfer Protocol (FTP).

    HTML files are put under the relevant language subfolders. For the language name to use for the subfolder, see [Language and locale descriptors in across product and Help](language-locale.md).  
3. Upload your JSON files into BLOB storage in the Storage container, in a subfolder that corresponds to the HTML language subfolder.  
4. Create a data source, index, and indexer on the Search service by using the REST API.

    API tools such as Postman are used to make the REST API calls. The REST API CREATION.txt file contains example REST API requests to create a data source, index, and indexer. You create language-specific indexes to use a language-specific index analyzer.

### <a name="resgr"></a>Create a resource group

To host your Web App, Search service, and Storage account, you must first create one or more resource groups. We recommend that you create all resources in a single resource group for easy management.  

#### To create a resource group

1. In the [Azure portal](https://portal.azure.com/), choose **Resource groups**, choose **Add**, and then specify a name for the resource group, such as *MyCustomHelp*.
2. Choose **Create** to finish creating the resource group.

### <a name="webapp"></a>Create a Web App

To host your content, you can create a static HTML Web App in Azure. For more information, see [Create a static HTML web app in Azure](/azure/app-service/app-service-web-get-started-html).

#### To set up the Web App

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Web App**, and then fill in the fields in the form.  

    You must specify a name for the Web App, the Azure region, and the runtime stack. We recommend that you choose the latest version of .NET Core as the runtime.<!--TODO: Is that safe to assume?-->

2. In the new Web App, create or reset your deployment credentials. The user name and password that you create here are used in the FTP client when you upload the HTML files.  

    You can find the FTP/deployment username and FTP hostname values in the Overview section of the Web App.

Next, you add the HTML files to the Web App. You can use an FTP client such as FileZilla, for example. For more information, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).

#### To upload HTML files

1. Start an FTP client such as FileZilla.

2. Enter the host (FTP hostname value from the **Overview** tab in the web app) and user name (**FTP/deployment username** value from the **Overview** tab), enter the password (from the **Deployment credentials** tab), and then click **Quickconnect**.  
3. Under */site/wwwroot* on the host, create a language subfolder that has the relevant language name. Upload the HTML files and other associated files to the language subfolder.  

### <a name="searchservice"></a>Create a search service

Next, you will create a search service so that your content can be indexed and found by the in-product Help pane. For more information, see [Azure Search](/azure/search/).  

#### To create a search service

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Azure Search**, and then fill in the fields in the form.  

    The service will be added to your resource group.

### <a name="jsonstorage"></a>Create storage for the JSON files

Next, you will create a storage account with a BLOB container that will store the JSON files that are used by your search service.

#### To create storage for the JSON files

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Storage account**, and then fill in the fields in the form.  
2. Validate and create the storage account.

    After the deployment is completed, the new Storage account is listed under the resource group.  
3. Choose the storage account name, and under **Services**, choose **Blobs**, add a container, specify a name, and then choose OK.  

You can now upload the JSON files. You must create a folder structure that matches the folder structure you created for the HTML files to match the languages of your solution. For example, create en-US virtual folder in the container, and upload the en-US JSON files to this folder.  

There are several ways to upload JSON files to the Blob container that you created earlier. If you prefer to use a UI, [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/) is a convenient tool for managing file operations by using Azure storage. If you prefer a command-line option, you can use AzCopy. For more information, see [Transfer data with the AzCopy on Windows](/azure/storage/common/storage-use-azcopy).  

Here is the syntax: 

```
AzCopy /Source:C:\myfolder /Dest:https://myaccount.blob.core.windows.net/mycontainer /DestKey:key /S 
```

This example shows how to upload the JSON files from local folder to the en-US virtual directory in *customhelpcontainer*.

```
AzCopy /Source:C:\Users\username\Desktop\customhelp\JSON /Dest: 
https://customhelpstorage.blob.core.windows.net/customhelpcontainer/en-US 
/DestKey:53vDyPAMPaXaxW/UEqWl4+/8+ssSfbdM yMqfgxiZ6h/LhKSUchTf0m6Z8HgBOTBzzUdaPvQu4bpdflejp6w== /S 
```

### <a name="searchconfig"></a>Configure the search service

In the previous sections, you created a search service. You must now set it up by creating a data source, index, and indexer, so that the JSON files that you uploaded to the BLOB container will be indexed and searchable. In the examples that follow, Postman is used to make several API calls. However, you can use your own method to call those APIs.  

#### To create a data source

1. In Postman, create a new POST request that has the following parameters:

    - URL: https://AzureSearchServicename.search.windows.net/datasources?api-version=2017-11-11 

        Replace *AzureSearchServicename* with the name of your search servive.
    - Type (on the Authorization tab): No Auth
    - Content-Type (on the Headers tab): application/json
    - api-key (on the Headers tab): The admin key found in your Azure Search service
2. On the Body tab, paste the following text.

    ```
    {
        "name" : "datasourcename",
        "type" : "azureblob",
        "credentials" : { "connectionString" : "DefaultEndpointsProtocol=https;AccountName=[StorageAccountName];AccountKey=[key];EndpointSuffix=core .windows.net" },
        "container" : { "name" : "[JSONStorageContainerName]" }
    }

    ```
    Replace the following parameters with appropriate values:
        - *Datasourcename*: Specify a name for the data source, such as *customhelpdatasource*.  
        - [*StorageAccountName*]: Specify the storage account name, such as *customhelpstorage*.  
        - [*key*]: Specify the access key for your storage account, such as */Equl2ErBeArcbW8mxQdFDRP9fxPcnNOaUayMqfgxiZ6h/LhKSUchTf0m6Z8HgBOTBzUdaPvQu4bpdflej p6w==*.  
        - [*JSONStorageContainerName*]: Specify the name of your BLOB container, such as *customhelpcontainer*.  
3. Choose **Send**, and make sure that the value in the **Status** field is **201 Created**.  

Next, you configure the search service to have an index of your content.

#### To create an index

1. In Postman, create a new POST request that has the following parameters:

    - URL: https://[AzureSearchServicename].search.windows.net/indexes?api-version=2017-11-11 
    - Type (on the Authorization tab): No Auth
    - Content-Type (on the Headers tab): application/json
    - api-key (on the Headers tab): The admin key found in your Azure Search service
2. On the Body tab, paste the following text.

    > [!NOTE]
    > The index is language-specific. The title and description fields contain translations, and it’s important that you set the corresponding language analyzer value. Use an appropriate value, based on the language of the index that you’re creating. For a list of language analyzers, see [Analyzer List](/azure/search/index-add-language-analyzers#analyzer-list).  

    ```
    { 
        "name" : "IndexName",
        "fields": [
            { "name": "id", "type": "Edm.String", "key": true,"searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "title", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true, "analyzer":"AnalyzerName" },
            { "name": "ms_search_form", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "ms_search_region", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "ms_locale", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_path", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_name", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, facetable": true },
            { "name": "metadata_storage_content_type", "type": "Edm.String", "searchable": true, "filterable": false, "sortable": false, "facetable": false },
            { "name": "description", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true, "analyzer":" AnalyzerName" }
        ]
    }
    ```

    Replace the following parameters with the relevant values:
    - IndexName: Specify the name of the index that should be created, such as *indexenus*.
    - AnalyzerName: Specify the name of the language analyzer that should be used, such as *en.microsoft*.

3. Click Send, and make sure that the value in the **Status** field is *201 Created*.
4. If you prepared custom Help content for multiple languages, repeat these steps to create a unique index for each language.

#### To create an indexer

1. In Postman, create a new POST request that has the following parameters:

    - URL: https://[AzureSearchServicename].search.windows.net/indexers?api-version=2017-11-11
    - Type (on the Authorization tab): No Auth
    - Content-Type (on the Headers tab): application/json
    - api-key (on the Headers tab): The admin key found in your Azure Search service 2 On the Body tab, paste the following text.

    ```
    {
        "name" : "IndexerName",
        "dataSourceName" : "DatasourceName",
        "targetIndexName" : "IndexName",
        "schedule" : { "interval" : "PT10H" },
        "parameters" : { "configuration" : { "parsingMode" : "json" } },
        "fieldMappings" : [
            { "sourceFieldName" : "/title", "targetFieldName" : "title" },
            { "sourceFieldName" : "/ms.search.form", "targetFieldName" : "ms_search_form" },
            { "sourceFieldName" : "/ms.search.region", "targetFieldName" : "ms_search_region" },
            { "sourceFieldName" : "/ms.locale", "targetFieldName" : "ms_locale" },
            { "sourceFieldName" : "/description", "targetFieldName" : "description" }
        ]
    }
    ```

2. Replace the following parameters with the relevant values:

    - IndexerName: Specify the name of the indexer that should be created, such as *indexerenus*.
    - DatasourceName: Specify the name of the data source, such as *customhelpdatasource*.
    - IndexName: Specify the name of the index, such as *indexenus*.

3. Click Send, and make sure that the value in the **Status** field is *201 Created*.
4. You may want to manually run the indexer from Azure Search Service for the first time.
5. If you prepared custom Help content for multiple languages, repeat these steps to create a unique indexer for each index.
6. After indexers are created, you might want to run them manually in the Azure Search service. When you add or modify the content (for example JSON files), you might also want to run it manually because, by default, indexers are set to run every 10 hours after the first run.

## Connect your Help website with the Help pane

You have your Help content on a website, and now you must extend the Help pane to consume this content. This is a one-time configuration that requires the development environment and Visual Studio. The purpose is to add a tab to the Help pane that will show your content so that users can choose between tabs for Task guides, Microsoft's Help content, and your Help content.

### To extend the Help pane

1. In the Finance and Operations development environment, start Microsoft Visual Studio, and open the **AzureSearchCustomHelp.sln** solution from the **AzureSearchCustomHelp.zip** file in the **Help Pane** extension folder in the https://github.com/microsoft/dynamics356f-ocustom-help repo. Update the references so that there are no missing references.
2. On the Dynamics 365 menu, choose **Import project**.
3. In the **File name** field, specify the path to *HelppaneOption.axpp* that you also retrieved from the https://github.com/microsoft/dynamics356f-ocustom-help repo, and then choose OK to complete the import process.
4. If you add a new field to the index or change the existing field name, you must also make corresponding changes to the Document.cs file.
5. In the **HelppaneMacro** file, update the values for the following parameters:

    - WebAppName: Specify the Web App name that you created for your custom Help solution, such as *customhelpwebapp*.
    - Admin key value: Specify the search service Admin key, such as *8DE388D04EC5E13D884E3E90FF72F8*.
    - [SearchServiceName]: Specify the search service name, such as *customhelpsearchservice*.

    The following snippet illustrates the content of the **HelppaneMacro** file:

    ```
    #define.webApp('http://[WebAppName].azurewebsites.net/')
    #define.queryApiKey('Admin key value')
    #define.defaultstring('dashboard')
    #define.searchservicename('[SearchServiceName]')
    #define.CustomResultError('error')
    #define.CustomTabPage('CustomTabPage')
    #define.CustomHelp('Custom Help')
    #define.CustomTitle('CustomTitle')
    #define.htm('html')
    ```

6. If you want to update any UI labels, modify them in **Customhelppane.en-US.label.txt**.  

Before you build AzureSearchCustomHelp.sln, you must specify the language that your custom Help index is intended for. You can also change the language fallback if you want to override the default behavior.

### To assign a language to a custom index

1. Open the **Language.config** file in the solution.
2. Find the language of the index in the list, and specify an index name in ```index=""```, ```parentindex="```, or ```ultimateindex=""```.  

    For example, you created an index for English (United States) and Spanish (Mexico). In this case, the index names are *customenus* and *customes*, respectively. Here is what your entries will look like.

    ```
    <add language="en-US" ulitmateindex=" customenus" />
    <add language="es-MX" parentlanguage="es" index=" customes" />
    ```

3. Build the **AzureSearchCustomHelp** solution, or customize language fallback for your index.

### Customize language fallback

Language fallback is designed to perform a search in additional languages when the intended language doesn’t return any result or doesn’t exist.

> [!NOTE]
> A custom index must be available for those additional languages.

For example, you’ve created a custom Help index for en-US, de, and de-AT, and added them to the **Language.config** file. You use *de-AT* as the product language for your Dynamics 365 solution and perform the custom search. If the search result is found in the *de-AT* index, the result is just presented. If no result is found in *de-AT*, an additional search is performed on *de* and *en-US*. The search pane indicates that no result was found in *de-AT*, but that found some results were found in *de* and *en-US*.

This behavior is controlled through the **parentlanguage** and **ultimateindex** attributes in the **Language.config** file.

The search and fallback order are defined in the following order of priorty:

1. The language that is set in the client, such as de-AT
2. The language that is defined in the **parentlanguage** attribute for that language, such as ```<add language="de-AT" parentlanguage="de" index="yourdeindex" />```
3. The language that has the **ultimateindex** attribute set, such as ```<add language="en-US" ultimateindex="yourenusindex" />```

## See also

[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
