---
# required metadata

title: Deploy custom Help to Azure
description: This topic walks you through an example that shows how you can deploy Microsoft Dynamics 365 Help content to an Azure web app. 
author: edupont04
ms.date: 05/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations

---

# Deploy custom Help to Azure

[!include [banner](../includes/banner.md)]

This topic describes the steps for setting up a web app to host your content and for setting up a search service to make the content discoverable by the in-product **Help** pane. You will set up a Microsoft Azure web app and then use that web app to host content that is connected to the in-product **Help** pane.

If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you follow the steps in this topic. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).

## Get started

The [Prepare content for use with the Help pane](preparing-content.md) topic describes the steps for preparing Help content so that it can be used with the in-product **Help** pane. After you have a set of HTML files and their equivalent JavaScript Object Notation (JSON) files, you can set up the web app and the search service.

### Process overview

The general process for creating your Azure resources consists of the following steps:

1. In the Azure portal, [create a resource group](#resgr).
2. In the Azure portal, [create a web app](#webapp), [a storage account](#jsonstorage), and [a search service](#searchservice).

    - The web app stores and serves HTML files. The HTML files contain your Help content.
    - The storage account uses a blob container to store JSON files. The JSON files are your Help files after they have been converted to JSON format so that they can be used to generate an index of your content for search purposes. For more information, see [Custom Help Toolkit: The ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md).
    - The search service indexes the Help content. An index makes your content discoverable by the in-product **Help** pane. For more information, see [Create a basic index in Azure Cognitive Search](/azure/search/search-what-is-an-index).

3. [Upload HTML files](#uploadhtml) to the web app by using File Transfer Protocol (FTP).

    When you complete this step, you put the HTML files in the relevant language subfolders, based on the locales that the content was written for. For information about the names to use for these subfolders, see [Language and locale descriptors in the product and in Help](language-locale.md).

4. [Upload JSON files](#jsonstorage) into Azure Blob storage in the storage container, in subfolders that correspond to the language subfolders for the HTML files.
5. [Configure the search service](#searchconfig) so that it has a data source, index, and indexer on the search service, by using the REST application programming interface (API).

    In this example, an API tool that is named [Postman](https://www.postman.com/) is used to make the REST API calls. To use a language-specific index analyzer, you must create language-specific indexes.

In the remaining sections of this topic, the assumption is that you have an Azure account and a valid subscription. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).

## <a name="resgr"></a>Create a resource group

To host your web app, search service, and storage account, you must first create one or more resource groups. We recommend that you create all resources in a single resource group to make management easier. For more information, see [Create resource groups](/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups).

1. In the [Azure portal](https://portal.azure.com/), select **Resource groups**, select **Add**, and then specify a name for the resource group, such as **MyCustomHelp**.
2. Select **Review + Create** to finish creating the resource group.

## <a name="webapp"></a>Create a web app

To host your content, you must create a web app in Azure. For more information, see [Create a static HTML web app in Azure](/azure/app-service/app-service-web-get-started-html).

### Create the web app

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, select **Add**, select **Web App**, and then specify the runtime stack and a name for the web app, such as **MyCustomHelpWebApp**.

    You can use any .NET Core stack as the runtime stack. For more information, see [Create an ASP.NET Core web app in Azure](/azure/app-service/app-service-web-get-started-dotnet).

2. After the deployment is completed, select **Go to resource**.
3. On the left side of the page, select **Deployment Center**. Under **Manual Deployment (push/sync)**, select **FTP**, and then select **Dashboard**.

    You can use either *app credentials* or *user credentials* to upload your content to the web app. We recommend that you use app credentials. To upload your content, you must have the FTP/FTPS endpoint, the user name, and the password.

    You might want to copy the user name and password to a temporary location before you continue. Additionally, we recommend that you reset the credentials after you've completed the deployment. For more information, see [Configure deployment credentials for Azure App Service](/azure/app-service/deploy-configure-credentials).

Next, you will add your HTML files to the web app. You can use an FTP client such as [FileZilla](https://filezilla-project.org/), [Visual Studio](https://www.visualstudio.com/vs/community/), [Cyberduck](https://cyberduck.io/), or [WinSCP](https://winscp.net/index.php). For more information, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).

### <a name="uploadhtml"></a>Upload HTML files

1. Open your preferred FTP client. For information about best practices that are related to uploading files to a web app, see [Deploy your app to Azure App Service using FTP/S](/azure/app-service/deploy-ftp).
2. Enter the host (the FTPS endpoint value from the Deployment Center for the web app), user name, and password, and then connect.
3. Under **/site/wwwroot** on the host, create a language folder for each language that your custom Help website must support. Upload the HTML files and other associated files to each language folder.

    > [!IMPORTANT]
    > Remember to use folder names that correspond to the languages that the client expects. For more information, see [Language and locale descriptors in the product and in Help](language-locale.md).

Your custom Help website has now been deployed to Azure and should be visible in a browser.

## <a name="jsonstorage"></a>Create a storage account

Next, create a storage account that uses a blob container to store the JSON files that the search service will use. For more information about Azure Storage, see the [Azure Storage documentation](/azure/storage/).

You can generate the JSON files from your HTML Help files by using the [ConvertHtmlToJson](custom-help-toolkit-ConvertHtmlToJson.md) tool that is part of the Custom Help Toolkit.

1. In the [Azure portal](https://portal.azure.com/), go to your resource group, select **Add**, select **Storage account**, and specify a name for the storage account, such as **mycustomhelpstorage**. Then select **Review + Create**. For more information, see [Create a storage account](/azure/storage/common/storage-account-create#create-a-storage-account).
2. Validate and create the storage account.

    After the deployment is completed, the new storage account is listed under the resource group.

3. Select your storage account, and then, on the left side of the page, under **Blob Service**, select **Containers**. Add a container, and specify a name, such as **mycustomhelpcontainer**. For more information, see [Quickstart: Upload, download, and list blobs with the Azure portal](/azure/storage/blobs/storage-quickstart-blobs-portal).

You can now upload your JSON files. The folder structure that you use must match the folder structure that you created for the HTML files to match the languages of your solution. For example, if your web app has HTML files in an **en-US** folder, create an **en-US** folder in the container, and upload the en-US JSON files to this folder.

There are several ways to upload JSON files to the blob container. If you prefer to use a user interface (UI), [Azure Storage Explorer](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer) is a convenient tool that lets you use Azure Storage to manage file operations. If you prefer a command-line option, you can use AzCopy. For more information, see [Transfer data with the AzCopy on Windows](/azure/storage/common/storage-use-azcopy).

## <a name="searchservice"></a>Create a search service

Next, create a search service, so that the content can be indexed and is discoverable by the in-product **Help** pane. For more information, see [What is Azure Cognitive Search?](/azure/search/search-what-is-azure-search)

- In the [Azure portal](https://portal.azure.com/), go to your resource group, select **Add**, and select **Azure Cognitive Search**, and then, under **URL**, specify a name for the service, such as **mycustomhelpsearch**. Then select **Review + Create**.

    The service is added to the resource group.

## <a name="searchconfig"></a>Configure the search service

In the previous section, you created a search service. In this section, you will configure it by creating a [data source](#searchdatasource), an [index](#searchindex), and an [indexer](#searchindexer) for each locale. The JSON files that you uploaded to the blob container will then be indexed and searchable. In the examples that follow, the [Postman](https://www.getpostman.com/) tool is used to make several API calls. However, you can use your own method to call those APIs.

### <a name="searchdatasource"></a>Create a data source

1. Open Postman, and create a new POST request. If you're unfamiliar with this tool, see [Explore Azure Cognitive Search REST APIs using Postman](/azure/search/search-get-started-postman).
2. In the **Enter request URL** field, enter `https://[AzureSearchServicename].search.windows.net/datasources?api-version=2017-11-11`. Replace **\[AzureSearchServicename\]** with the name of the search service that you created in the [Create a search service](#searchservice) section of this topic (for example, **mycustomhelpsearch**).
3. On the **Headers** tab, set **"Content-type"** to **application/json**, and set **api-key** to the key from your Azure Cognitive Search service. You can find the key in **Access keys** under **Settings** on the left side of the search service.
4. In the **Authorization** tab, set **Type** to **No Auth**.
5. On the **Body** tab, paste the following text.

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

    - **\[datasourcename\]** – Specify a name for the data source, such as **mycustomhelpdatasource**.
    - **\[StorageAccountName\]** – Specify the name of the storage account that you created in the [Create a storage account](#jsonstorage) section (for example, **mycustomhelpstorage**).
    - **\[key\]** – Specify the access key for your storage account. You can find the key in **Keys** under **Settings** on the left side of the storage account.
    - **\[JSONStorageContainerName\]** – Specify the name of the blob container that you created in the [Create a storage account](#jsonstorage) section (for example, **mycustomhelpcontainer**).

6. Select **Send**, and make sure that the value in the **Status** field is **201 Created**.

Next, you will configure the search service so that it has an index of the content for each locale that you want to support.

### <a name="searchindex"></a>Create an index

1. In Postman, create a new POST request that has the following parameters:

    - **URL**: `https://[AzureSearchServicename].search.windows.net/indexes?api-version=2017-11-11` (Replace **\[AzureSearchServicename\]** with the name of your search service.)
    - **Type** (on the **Authorization** tab): **No Auth**
    - **Content-Type** (on the **Headers** tab): **application/json**
    - **api-key** (on the **Headers** tab): The key from your Azure Cognitive Search service

2. On the **Body** tab, paste the following text.

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

    - **\[IndexName\]** – Specify the name of the index that should be created, such as **indexenus**.
    - **\[AnalyzerName\]** – Specify the name of the language analyzer that should be used, such as **en.microsoft**.

    > [!NOTE]
    > The index is language-specific. The **title** and **description** fields contain translations, and it's important that you set the corresponding language analyzer value. Use an appropriate value, based on the language of the index that you're creating. For a list of language analyzers, see [Analyzer List](/azure/search/index-add-language-analyzers#analyzer-list).

3. Select **Send**, and make sure that the **Status** field is set to **201 Created**.
4. If you prepared custom Help content for multiple languages, repeat these steps to create a unique index for each language.

The index isn't an index until it has been processed by an indexer. Think of the table of contents in a reference book. It would not really be useful unless it also lists the page numbers for where to find the various sections in the book. Similarly, the indexer for your search service fills in the index, based on a search. For more information, see [Indexers in Azure Cognitive Search](/azure/search/search-indexer-overview).

### <a name="searchindexer"></a>Create an indexer

1. In Postman, create a new POST request that has the following parameters:

    - **URL**: `https://[AzureSearchServicename].search.windows.net/indexers?api-version=2017-11-11` (Replace **\[AzureSearchServicename\]** with the name of your search service.)
    - **Type** (on the **Authorization** tab): **No Auth**
    - **Content-Type** (on the **Headers** tab): **application/json**
    - **api-key** (on the **Headers** tab): The key from your Azure Cognitive Search service

2. On the **Body** tab, paste the following text.

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

    - **\[IndexerName\]** – Specify the name of the indexer that should be created, such as **indexerenus**.
    - **\[DatasourceName\]** – Specify the name of the data source that you created, such as **mycustomhelpdatasource**.
    - **\[IndexName\]** – Specify the name of the index that you created, such as **indexenus**.

    > [!NOTE]
    > This configuration will set up an indexer that is scheduled to run every 10 hours (**"schedule" : { "interval" : "PT10H" }**). However, you can adjust the interval as appropriate.

3. Select **Send**, and make sure that the **Status** field is set to **201 Created**.
4. If you prepared custom Help content for multiple languages, repeat these steps to create a unique indexer for each index.

> [!NOTE]
> An index will contain data only after its indexer has run. You might want to manually run the indexer if you're planning to test the index immediately.

> [!IMPORTANT]
> If you update your content, remember to regenerate the JSON files and upload them to the storage service. If you add content, you can either manually run the indexers or wait for the next scheduled run. Your updated content won't be available in search results until the next time that the indexers are run.

You can optionally use Postman to test the search. For an example that shows how to use Postman for testing, see [Search your JSON files](/azure/search/search-semi-structured-data#6---search-your-json-files).

## Next steps

If you completed all the steps in this topic, your Help content has now been uploaded to an Azure web app, and it has been indexed.

The next step is to extend the **Help** pane so that it can detect your content. In that way, when users open the **Help** pane in your Dynamics 365 solution, the in-product **Help** pane will be able to generate context-sensitive links to your Help. For more information, see [Connect a custom Help website to the Help pane](connect-help-pane.md).

## See also

[Custom Help overview](custom-help-overview.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]