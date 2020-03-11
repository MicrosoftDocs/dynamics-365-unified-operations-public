---
# required metadata

title: Deploying custom help to Azure
description: This article walks you through an example of how you can deploy Dynamics 365 Help content to an Azure web app. 
author: edupont04
manager: AnnBe
ms.date: 03/03/2020
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

# Deploying custom help to Azure

[!include [banner](../includes/banner.md)]

You can set up an Azure web app and use the web app to host your content for easy integration with the in-product Help pane. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

In this article, we will describe the steps for setting up a web app to host your content and setting up a search service to make the content discoverable by the in-product Help pane.  

## Get started

You must have [content](preparing-content.md) hosted on a website so that it can be accessed by the in-product Help pane. You can include a copy of Microsoft's content in your website, or you can deploy content that only describes your own functionality.

If you want to publish just your own content, in [Extend, Customize, and Collaborate on the Help](contributor-guide.md), we suggest that you do what we do on the *docs.microsoft.com* site: Create the content in MarkDown files and then use DocFx.exe to generate HTML files. The [Custom Help Toolkit](custom-help-toolkit.md) includes the [HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md) that can help you prepare the HTML files even if you do not derive your content from Microsoft's content.  

### Process overview

The general process for creating your Azure resources consists of the following steps:

1. In the Azure portal, [create a resource group](#resgr).  

2. In the Azure portal, [create a web app](#webapp), [a storage account](#jsonstorage), and [an Azure search service](#searchservice).  

    - The web app stores and serves HTML files  

        The HTML files contain your Help content, no matter if it's based on Microsoft's content or not.  

    - The storage account uses a Blob container to store JSON files  

        The JSON files are your Help files converted to JSON so that they can be used to generate an index of your content for search purposes. For more information, see [Custom Help Toolkit: The ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md).  

    - The Search service performs indexing  

        Indexing makes your content discoverable by the in-product Help pane. For more information, see [Create a basic index in Azure Cognitive Search](/azure/search/search-what-is-an-index).

3. [Upload HTML files](#uploadhtml) to the Web App by using File Transfer Protocol (FTP).

    Place the HTML files in the relevant language subfolders. For the language name to use for the subfolder, see [Language and locale descriptors across product and Help](language-locale.md).  

4. [Upload JSON files](#jsonstorage) into Blob storage in the Storage container, in a subfolder that corresponds to the HTML language subfolder.  
5. [Configure the Search service](#searchconfig) to have a data source, index, and indexer on the Search service by using the REST API.

    In this example, we use an API tool, [Postman](https://www.postman.com/), to make the REST API calls. The [REST API CREATION.txt file](https://github.com/microsoft/dynamics365f-o-custom-help/tree/master/Help%20Pane%20extension) contains sample REST API requests to create a data source, index, and indexer. You must create language-specific indexes to use a language-specific index analyzer.

In the following, we assume that you have an Azure account and a valid subscription. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

## <a name="resgr"></a>Create a resource group

To host your Web App, Search service, and Storage account, you must first create one or more resource groups. We recommend that you create all resources in a single resource group for easy management. For more information, see [Create resource groups](/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups)

### To create a resource group

1. In the [Azure portal](https://portal.azure.com/), choose **Resource groups**, choose **Add**, and then specify a name for the resource group, such as *MyCustomHelp*.
2. Choose **Review + Create** to finish creating the resource group.

## <a name="webapp"></a>Create a web app

To host your content, you will need to create a web app in Azure. For more information, see [Create a static HTML web app in Azure](/azure/app-service/app-service-web-get-started-html).

### To create the web app

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Web App**, and then fill in the fields in the form.  

    Specify a name for the web app, the Azure region, the runtime stack, and other information. If you are unsure which runtime stack you should use, you can use any **.Net Core** stack. For more information, see [Create an ASP.NET Core web app in Azure](/azure/app-service/app-service-web-get-started-dotnet). When the deployment completes, choose **Go to resource**.

2. Select **Deployment Center** from the left blade. Select **FTP** under **Manual Deployment (push/sync)** then choose **Dashboard**. You can use either App Credentials or User Credentials to upload your content to the web app that you have created. You will need the FTP/FTPS endpoint, the username, and the password to upload your content.

Next, you will add your HTML files to the web app. You can use an FTP client such as [FileZilla](https://filezilla-project.org/), [Visual Studio](https://www.visualstudio.com/vs/community/), [Cyberduck](https://cyberduck.io/), or [WinSCP](https://winscp.net/index.php). For more information, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).

### <a name="uploadhtml"></a>To upload HTML files

1. Start your preferred FTP client. For best practices around uploading files to a web app, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).

2. Enter the host (FTPS endpoint value from the **Deployment center** for the web app), user name, and password, and then connect.  

3. Under */site/wwwroot* on the host, create a language folder for each of the languages that your custom help site must support. Upload the HTML files and other associated files to each language folder.  

> [!IMPORTANT]
> Remember to use folder names that map to the languages that the client expects. For more information, see [Language and locale descriptors in across product and Help](language-locale.md).

Your custom help site has now been deployed to Azure and should be visible in a browser.

## <a name="jsonstorage"></a>Create storage for the JSON files

Next, you will create a storage account with a Blob container that will store JSON files that are used by the search service. For more information about Azure storage, see [Azure Storage Documentation](/azure/storage/).

You can generate these JSON files from your Help files by using the [ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md) that is part of the Custom Help Toolkit.

### To create storage for the JSON files

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Storage account**, specify a **Storage account name**, and choose **Review + Create**. For more information, see [Create a storage account](/azure/storage/common/storage-account-create#create-a-storage-account).  

2. Validate and create the storage account.

    After the deployment is completed, the new storage account is listed under the resource group.  

3. Choose the storage account name, choose **Containers** under **Blob Service** in the left blade, and then add a container. For more information, see [Quickstart: Upload, download, and list blobs with the Azure portal](/azure/storage/blobs/storage-quickstart-blobs-portal).  

You can now upload your JSON files. The folder structure that you use must match the folder structure you created for the HTML files to match the languages of your solution. For example, if your web app has HTML files in an ```en-US``` folder, create an ```en-US``` folder in the container, and upload the en-US JSON files to this folder.  

There are several ways to upload JSON files to the Blob container. If you prefer to use a UI, [Azure Storage Explorer](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer) is a convenient tool for managing file operations by using Azure storage. If you prefer a command-line option, you can use AzCopy. For more information, see [Transfer data with the AzCopy on Windows](/azure/storage/common/storage-use-azcopy).  

## <a name="searchservice"></a>Create a search service

Next, you will create a search service so that your content can be indexed and found by the in-product Help pane. For more information, see [What is Azure Cognitive Search?](/azure/search/search-what-is-azure-search).  

### To create a search service

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, choose **Add**, choose **Azure Cognitive Search**, specify a service name under **URL**, then choose **Review + Create**.  

    The service will be added to your resource group.

## <a name="searchconfig"></a>Configure the search service

In the previous section, you created a search service. You must now configure it by creating a data source, index, and indexer, so that the JSON files that you uploaded to the Blob container will be indexed and searchable. In the examples that follow, we use the [Postman tool](https://www.getpostman.com/) to make several API calls; however, you can use your own method to call those APIs.  







### To create a data source

1. Start Postman and set up an HTTP request. If you are unfamiliar with this tool, see [Explore Azure Cognitive Search REST APIs using Postman](/azure/search/search-get-started-postman.md).  

    The request methods for every call in this tutorial are **POST** and **GET**. You'll make three API calls to your search service to create a data source, an index, and an indexer. The data source includes a pointer to your storage account and your JSON data. Your search service makes the connection when loading the data.

2. In Headers, set `"Content-type"` to `application/json` and set `api-key` to the admin api-key of your Azure Cognitive Search service. Once you set the headers, you can use them for every request in this exercise.

    URIs must specify an api-version and each call should return a **201 Created**. The generally available api-version for using JSON arrays is `2019-05-06`.

    For more information, see [Tutorial: Index JSON blobs from Azure Storage using REST](/azure/search/search-semi-structured-data).

3. Create a new POST request that has the following parameters:

    - **URL**: `https://[AzureSearchServicename].search.windows.net/datasources?api-version=[api-version=2019-05-06]`

        Replace *[AzureSearchServicename]* with the name of your search service, and make sure that the API version is the right one for your service.
    - **Type** (on the Authorization tab): No Auth
    - **Content-Type** (on the Headers tab): application/json
    - **api-key** (on the Headers tab): The admin key found in your Azure Search service

4. On the Body tab, paste the following text.

    ```json
    {
        "name" : "[datasourcename]",
        "type" : "azureblob",
        "credentials" :
        {
            "connectionString" : "DefaultEndpointsProtocol=https;AccountName=[StorageAccountName];AccountKey=[key];EndpointSuffix=core.windows.net"
        },
        "container" :
        {
            "name" : "[JSONStorageContainerName]"
        }
    }
    ```

    Replace the following parameters with the relevant values:  
        - **[datasourcename]**: Specify a name for the data source, such as *customhelpdatasource*.  
        - **[StorageAccountName]**: Specify the storage account name, such as *customhelpstorage*.  
        - **[key]**: Specify the access key for your storage account, such as */Equl2ErBeArcbW8mxQdFDRP9fxPcnNOaUayMqfgxiZ6h/LhKSUchTf0m6Z8HgBOTBzUdaPvQu4bpdflej p6w==*.  
        - **[JSONStorageContainerName]**: Specify the name of your BLOB container, such as *customhelpcontainer*.  

    You can find the relevant information in the settings for your storage account in the Azure portal.
5. Choose **Send**, and make sure that the value in the **Status** field is **201 Created**.  

Next, you configure the search service to have an index of your content.

### To create an index

1. In Postman, create a new POST request that has the following parameters:

    - **URL**: `https://[AzureSearchServicename].search.windows.net/indexes/[indexenus]/docs?[api-version=2019-05-06]&search=*`

        Replace the following parameters with the relevant values:  
        - **[AzureSearchServicename]**: Specify the name of your search service.
        - **[indexes]**: Specify the language-specific index that you want to create.
        - **[api-version=2019-05-06]**: Specify the API version for your search service.  

            In the **Search explorer** for your search service in the Azure portal, check if there are more recent API versions. You can also switch to an older version.
    - **Type** (on the Authorization tab): No Auth
    - **Content-Type** (on the Headers tab): application/json
    - **api-key** (on the Headers tab): The admin key found in your Azure Search service
2. On the Body tab, paste the following text.

    > [!NOTE]
    > The index is language-specific. The title and description fields contain translations, and it's important that you set the corresponding language analyzer value. Use an appropriate value, based on the language of the index that you're creating. For a list of language analyzers, see [Analyzer List](/azure/search/index-add-language-analyzers#analyzer-list).  

    ```json
    {
        "name" : "[IndexName]",
        "fields": [
            { "name": "id", "type": "Edm.String", "key": true,"searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "title", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true, "analyzer":"[AnalyzerName]" },
            { "name": "description", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true, "analyzer":"[AnalyzerName]" },
            { "name": "ms_search_form", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "ms_search_region", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "ms_locale", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_path", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_name", "type": "Edm.String", "searchable": true, "filterable": true, "sortable": true, "facetable": true },
            { "name": "metadata_storage_content_type", "type": "Edm.String", "searchable": true, "filterable": false, "sortable": false, "facetable": false }
        ]
    }
    ```

    Replace the following parameters with the relevant values:
    - **[IndexName]**: Specify the name of the index that should be created, such as *indexenus*.
    - **[AnalyzerName]**: Specify the name of the language analyzer that should be used, such as *en.microsoft*.

    For more information, see [Tutorial: Index JSON blobs from Azure Storage using REST](/azure/search/search-semi-structured-data).

3. Click Send, and make sure that the value in the **Status** field is *201 Created*.
4. If you prepared custom Help content for multiple languages, repeat these steps to create a unique index for each language.

> [!NOTE]
> If you customize the index, such as by adding or renaming a field, you must update the Document.cs file in the AzureSearchCustomHelp solution in the development environment. For more information, see [Connect your Help website with the Help pane](connect-help-pane.md).

The index is not an index until it has been processed by an *indexer*. Like the librarian who maintains the index over the books in a library, the indexer for your search service populates the index based on a search. For more information, see [Indexers in Azure Cognitive Search](/azure/search/search-indexer-overview).

### To create an indexer

1. In Postman, create a new POST request that has the following parameters:

    - **URL**: `https://[AzureSearchServicename].search.windows.net/indexers?api-version=[2019-05-06]`
    - **Type** (on the Authorization tab): No Auth
    - **Content-Type** (on the Headers tab): application/json
    - **api-key** (on the Headers tab): The admin key found in your Azure Search service  

2. On the Body tab, paste the following text.

    ```json
    {
        "name" : "[IndexerName]",
        "dataSourceName" : "[DatasourceName]",
        "targetIndexName" : "[IndexName]",
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

    Replace the following parameters with the relevant values:

    - **[IndexerName]**: Specify the name of the indexer that should be created, such as *indexerenus*.
    - **[DatasourceName]**: Specify the name of the data source, such as *customhelpdatasource*.
    - **[IndexName]**: Specify the name of the index, such as *indexenus*.

3. Click Send, and make sure that the value in the **Status** field is *201 Created*.

Optionally, use Postman to test the search. For an example of how to do that, see [Search your JSON files](/azure/search/search-semi-structured-data#6---search-your-json-files).

If you prepared custom Help content for multiple languages, repeat these steps to create a unique indexer for each index.

> [!NOTE]
> If you update your content, remember to regenerate the JSON files and upload them to the storage service. If you add content, run the indexers manually, or wait for the next scheduled run. Your updated content will not be available in search results until after the indexers' next run.  

## Next steps

At this point, you have uploaded your Help content to an Azure web app and indexed it so that the in-product Help pane can generate context-sensitive links to your Help when users open the Help pane in your Dynamics 365 solution.  

However, you still have one important task to do, which is to extend the Help pane to be aware of your content. For more information, see [Connect your Help website with the in-product help pane](connect-help-pane.md).  

## See also

[Custom Help Overview](custom-help-overview.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
