---
# required metadata

title: Connect a custom Help website to the Help pane
description: This topic describes how you can extend the in-product Help pane with custom help. 
author: edupont04
manager: AnnBe
ms.date: 02/24/2020
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

# Connect your Help website with the in-product help pane

[!include [banner](../includes/banner.md)]

If you deliver custom help content for a Finance and Operations solution, you must extend the Help pane to consume this content. It is a one-time configuration that requires the Finance and Operations development environment in Visual Studio. The result is that users can choose between tabs for Task guides, Microsoft's Help content, and your Help content.

Connecting your [custom help website](custom-help-overview.md#custom-help-sites) with the in-product Help pane involves the following steps:

1. Extend the Help pane in Visual Studio
2. Assign a language index
3. Customize language fallback

> [!IMPORTANT]
> The following sections require the development tools for Finance and Operations apps in Visual Studio. For more information, see [Development tools in Visual Studio](../dev-tools/development-tools-overview.md).

## <a name="extendhelppane"></a>Extend the Help pane and assign the language index in Visual Studio

The **Help Pane extension** folder of the toolkit contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. The same folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.  

### To extend the Help pane

1. In the Finance and Operations development environment, open the **AzureSearchCustomHelp.sln** solution.

    The solution is in the **Help Pane extension** folder in the https://github.com/microsoft/dynamics356f-o-custom-help repo.  
2. On the Dynamics 365 menu, choose **Import project**.
3. In the **File name** field, specify the path to **HelppaneOption.axpp** that you also retrieved from the https://github.com/microsoft/dynamics356f-o-custom-help repo, and then choose OK to complete the import process. Update the references so that there are no missing references.  
4. If you added a new field to the search index in your search service, or you changed an existing field name, you must add that field to the *Document.cs* file.  

    The Document.cs file specifies the metadata properties in the Help content that the search service relies on to find context-sensitive links. If you do not add or modify this metadata, you can ignore this step.

    For an example of an index in a search service, see the [Configure the search service](walkthrough-help-azure.md#searchconfig).
 section in [Deploying custom help to Azure](walkthrough-help-azure.md).

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

6. Optionally, to update any UI strings in the Help pane, modify them in the **Customhelppane.en-US.label.txt** file.  

Next, you must specify the language that your custom help search index is intended for.  

### To assign a language to a custom index

1. Open the **Language.config** file in the solution.
2. Find the language of the index in the list, and specify an index name in ```index=""```, ```parentindex="```, or ```ultimateindex=""```.  

    For example, you created search indexes for English (United States) and German (Austria) with the names *myenusindex* and *mydeindex*, respectively. Here is what your entries will look like.

    ```
    <add language="en-US" ultimateindex="myenusindex" />
    <add language="de-AT" parentlanguage="de" index="mydeindex" />
    ```
3. Optionally, customize the language fallback for your index as described in the next section.

3. Build the **AzureSearchCustomHelp** solution.  

The result is a model that you then upload to the Asset Library of the customer project or the Microsoft Dynamics Lifecycle Services (LCS) solution project.

## Customize language fallback

Language fallback means that the Help pane runs a search in additional languages when the intended language does not return a result, or if that language does not exist.

> [!NOTE]
> A custom index must be available for those additional languages.

For example, you have created a custom Help index for en-US, de, and de-AT, and added them to the **Language.config** file. You test this custom help in a deployment where you set the client language to *de-AT*. You then open the Help pane so that the custom search kicks in based on the part of the product that you are on. The Help pane searches for context-sensitive Help based on your search index. If the search result is found in the *de-AT* index, you see the result in the Help pane. If no result is found in *de-AT*, the Help pane runs an additional search on *de* and *en-US* based on the language fallback in your search index. In this example, the Help pane indicates that no result was found in *de-AT*, but that some results were found in *de* and *en-US*.

The behavior is controlled through the **parentlanguage** and **ultimateindex** attributes in the **Language.config** file.

The search and fallback order are defined in the following order of priority:

1. The language that is set in the client, such as de-AT
2. The language that is defined in the **parentlanguage** attribute for that language, such as ```<add language="de-AT" parentlanguage="de" index="mydeindex" />```
3. The language that has the **ultimateindex** attribute set, such as ```<add language="en-US" ultimateindex="myenusindex" />```

## See also

[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
