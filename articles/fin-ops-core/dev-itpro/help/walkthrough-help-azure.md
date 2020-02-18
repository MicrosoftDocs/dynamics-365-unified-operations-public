---
# required metadata

title: Example of Deploying Help on Azure
description: This topic walks you through an example of how you can deploy Dynamics 365 Help content to an Azure web app. 
author: edupont04
manager: AnnBe
ms.date: 02/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations

---

# Example of Deploying Custom Help on Azure

[!include [banner](../includes/banner.md)]

You can set up an Azure web app and host your content there for easy integration with the in-product Help pane. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

There are several different ways of getting your content hosted on Azure. For example, you can set up Azure Blob storage with your Help as HTML files, set up a web app to consume that content, and then set up a search service that indexes your Blob storage. For more information, see [Azure Blob storage documentation](/azure/storage/blobs/).  

But in this section, we will take your through the steps for setting up a web app, a storage account, and a search service, using tools and scripts that are part of the [Custom Help Toolkit](custom-help-toolkit.md).  

## Get started

First, you must clone the GitHub repo with the [Custom Help Toolkit](custom-help-toolkit.md). The toolkit is available at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/).  

In the following we assume that you have an Azure account and a valid subscription. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

The general process for creating your Azure resources consists of the following steps:

1. In the Azure portal, [create a resource group](#resgr).  

2. In the Azure portal, [create a web app](#webapp), storage account, and [Azure Search Service](#searchservice).  

    - The Web App stores and serves HTML files  

        The HTML files contain your Help content.  

    - The Storage account stores JSON files  

        The JSON files are your Help files converted to JSON and are used to generate an index of your content for search purposes.  

    - The Search service performs indexing  

3. [Upload HTML files](#uploadhtml) to the Web App by using File Transfer Protocol (FTP).

    Place the HTML files in the relevant language subfolders. For the language name to use for the subfolder, see [Language and locale descriptors across product and Help](language-locale.md).  
4. [Upload JSON files](#jsonstorage) into Blob storage in the Storage container, in a subfolder that corresponds to the HTML language subfolder.  
5. [Configure the Search service](#searchconfig) to have a data source, index, and indexer on the Search service by using the REST API.

    In this example, we use an API tool, Postman, to make the REST API calls. The [REST API CREATION.txt file](https://github.com/microsoft/dynamics365f-o-custom-help/tree/master/Help%20Pane%20extension) contains sample REST API requests to create a data source, index, and indexer. You must create language-specific indexes to use a language-specific index analyzer.

## <a name="resgr"></a>Create a resource group

To host your Web App, Search service, and Storage account, you must first create one or more resource groups. We recommend that you create all resources in a single resource group for easy management.  

### To create a resource group

1. In the [Azure portal](https://portal.azure.com/), choose **Resource groups**, choose **Add**, and then specify a name for the resource group, such as *MyCustomHelp*.
2. Choose **Review+Create** to finish creating the resource group.

## <a name="webapp"></a>Create a web app

To host your content, you can create a web app in Azure. For more information, see [Create a static HTML web app in Azure](/azure/app-service/app-service-web-get-started-html).

### To create the web app

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Web App**, and then fill in the fields in the form.  

    You must specify a name for the web app, the Azure region, the runtime stack, and other information. We recommend that you choose the latest version of .NET Core as the runtime.<!--TODO: Is that safe to assume?-->For more information, see [Create an ASP.NET Core web app in Azure](/azure/app-service/app-service-web-get-started-dotnet).

2. In the new web app, create or reset your deployment credentials. You will need the user name and password that you create here in the next step when you upload the HTML files.  

    You can find the FTP/deployment username and FTP hostname values in the Overview section of the web app. For more information, see [Configure deployment credentials for Azure App Service](/azure/app-service/deploy-configure-credentials).

Next, you add the HTML files to the web app. You can use an FTP client such as FileZilla, for example. For more information, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).

### <a name="uploadhtml"></a>To upload HTML files

1. Start an FTP client such as FileZilla.

2. Enter the host (FTP hostname value from the **Overview** tab in the web app) and user name (**FTP/deployment username** value from the **Overview** tab), enter the password (from the **Deployment credentials** tab), and then click **Quickconnect**.  
3. Under */site/wwwroot* on the host, create a language subfolder that has the relevant language name. Upload the HTML files and other associated files to the language subfolder.  

> [!IMPORTANT]
> Remember to use folder names that map to the languages that the client expects. For more information, see [Language and locale descriptors in across product and Help](language-locale.md).

## <a name="jsonstorage"></a>Create storage for the JSON files

Next, you will create a storage account with a Blob container that will store JSON files that are used by the search service that you will [create](#searchservice) and [configure](#searchconfig) later.

These JSON files can be generated from your Help files by the ConvertHtmlToJson tool that is part of the Custom Help Toolkit. For more information, see [Custom Help Toolkit: The Convert HTML To JSON tool](custom-help-toolkit-ConvertHtmlToJson.md).

### To create storage for the JSON files

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Storage account**, and then fill in the fields in the form.  
2. Validate and create the storage account.

    After the deployment is completed, the new Storage account is listed under the resource group.  
3. Choose the storage account name, and under **Services**, choose **Blobs**, add a container, specify a name, and then choose OK.  

You can now upload the JSON files. You must create a folder structure that matches the folder structure you created for the HTML files to match the languages of your solution. For example, create en-US virtual folder in the container, and upload the en-US JSON files to this folder.  

There are several ways to upload JSON files to the Blob container that you created earlier. If you prefer to use a UI, [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) is a convenient tool for managing file operations by using Azure storage. If you prefer a command-line option, you can use AzCopy. For more information, see [Transfer data with the AzCopy on Windows](/azure/storage/common/storage-use-azcopy).  

<!--Comment out for now>Here is the syntax:

```
AzCopy /Source:C:\myfolder /Dest:https://myaccount.blob.core.windows.net/mycontainer /DestKey:key /S
```

This example shows how to upload the JSON files from local folder to the en-US virtual directory in *customhelpcontainer*.

```
AzCopy /Source:C:\Users\username\Desktop\customhelp\JSON /Dest: https://customhelpstorage.blob.core.windows.net/customhelpcontainer/en-US /DestKey:53vDyPAMPaXaxW/UEqWl4+/8+ssSfbdM yMqfgxiZ6h/LhKSUchTf0m6Z8HgBOTBzzUdaPvQu4bpdflejp6w== /S
```
-->
## <a name="searchservice"></a>Create a search service

Next, you will create a search service so that your content can be indexed and found by the in-product Help pane. For more information, see [Azure Search](/azure/search/).  

### To create a search service

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Azure Search**, and then fill in the fields in the form.  

    The service will be added to your resource group.

## <a name="searchconfig"></a>Configure the search service

In the previous section, you created a search service. You must now configure it by creating a data source, index, and indexer, so that the JSON files that you uploaded to the BLOB container will be indexed and searchable. In the examples that follow, Postman is used to make several API calls. However, you can use your own method to call those APIs.  

### To create a data source

1. In Postman, create a new POST request that has the following parameters:

    - URL: https://AzureSearchServicename.search.windows.net/datasources?api-version=2017-11-11 

        Replace *AzureSearchServicename* with the name of your search service.
    - Type (on the Authorization tab): No Auth
    - Content-Type (on the Headers tab): application/json
    - api-key (on the Headers tab): The admin key found in your Azure Search service
2. On the Body tab, paste the following text.

    ```
    {
        "name" : "datasourcename",
        "type" : "azureblob",
        "credentials" : { "connectionString" : "DefaultEndpointsProtocol=https;AccountName=[StorageAccountName];AccountKey=[key];EndpointSuffix=core.windows.net" },
        "container" : { "name" : "[JSONStorageContainerName]" }
    }

    ```
    Replace the following parameters with the relevant values:  
        - *datasourcename*: Specify a name for the data source, such as *customhelpdatasource*.  
        - [*StorageAccountName*]: Specify the storage account name, such as *customhelpstorage*.  
        - [*key*]: Specify the access key for your storage account, such as */Equl2ErBeArcbW8mxQdFDRP9fxPcnNOaUayMqfgxiZ6h/LhKSUchTf0m6Z8HgBOTBzUdaPvQu4bpdflej p6w==*.  
        - [*JSONStorageContainerName*]: Specify the name of your BLOB container, such as *customhelpcontainer*.  
3. Choose **Send**, and make sure that the value in the **Status** field is **201 Created**.  

Next, you configure the search service to have an index of your content.

### To create an index

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
            { "name": "metadata_storage_name", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_content_type", "type": "Edm.String", "searchable": true, "filterable": false, "sortable": false, "facetable": false },
            { "name": "description", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true, "analyzer":"AnalyzerName" }
        ]
    }
    ```

    Replace the following parameters with the relevant values:
    - IndexName: Specify the name of the index that should be created, such as *indexenus*.
    - AnalyzerName: Specify the name of the language analyzer that should be used, such as *en.microsoft*.

3. Click Send, and make sure that the value in the **Status** field is *201 Created*.
4. If you prepared custom Help content for multiple languages, repeat these steps to create a unique index for each language.

> [!NOTE]
> If you customize the index, such as by adding or renaming a field, you must update the Document.cs file in the AzureSearchCustomHelp solution in the development environment. For more information, see [Connect your Help website with the Help pane](connect-help-pane.md).

### To create an indexer

1. In Postman, create a new POST request that has the following parameters:

    - URL: https://[AzureSearchServicename].search.windows.net/indexers?api-version=2017-11-11
    - Type (on the Authorization tab): No Auth
    - Content-Type (on the Headers tab): application/json
    - api-key (on the Headers tab): The admin key found in your Azure Search service  

2. On the Body tab, paste the following text.

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

3. Replace the following parameters with the relevant values:

    - IndexerName: Specify the name of the indexer that should be created, such as *indexerenus*.
    - DatasourceName: Specify the name of the data source, such as *customhelpdatasource*.
    - IndexName: Specify the name of the index, such as *indexenus*.

4. Click Send, and make sure that the value in the **Status** field is *201 Created*.
5. You may want to manually run the indexer from Azure Search Service for the first time.
6. If you prepared custom Help content for multiple languages, repeat these steps to create a unique indexer for each index.

> [!NOTE]
> If you update your content, remember to regenerate the JSON files and upload them to the storage service. Remember that the indexers run at user-specified intervals, so your updated content will not be available in search results until after the indexer’s next run. You can run each indexer manually if you want the search results to appear sooner.

## See also

[Custom Help Overview](custom-help-overview)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
