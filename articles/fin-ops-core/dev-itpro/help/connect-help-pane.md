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

# Connect your Help website with the in-product Help pane

[!include [banner](../includes/banner.md)]

If you plan to deliver custom help content for a Finance and Operations solution, you can extend the Help pane to consume this content. It is a one-time configuration that requires the Finance and Operations development environment in Visual Studio. The result is that users can choose between tabs for Task guides, Microsoft's Help content, and your Help content.

Connecting your [custom help](custom-help-overview.md#custom-help-sites) with the in-product Help pane involves the following steps:

1. Extend the Help pane in Visual Studio
2. Assign a language to an index
3. Customize language fallback

> [!IMPORTANT]
> The following sections require the development tools for Finance and Operations apps in Visual Studio. For more information, see [Development tools in Visual Studio](../dev-tools/development-tools-overview.md).

## <a name="extendhelppane"></a>Extend the Help pane and assign the language index in Visual Studio

The **Help Pane extension** folder of the [Custom Help Toolkit](custom-help-toolkit.md) contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. The same folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.  

### To extend the Help pane

1. In the Finance and Operations development environment, open the **AzureSearchCustomHelp.sln** solution.
2. On the Dynamics 365 menu, choose **Import project**.
3. In the **File name** field, specify the path to **HelppaneOption.axpp**, and then choose OK to complete the import process. Update the references so that there are no missing references.  
4. In the **HelppaneMacro** file, update the values for the following parameters:

    - [WebAppName]: Specify the Web App name that you created for your custom Help solution, such as *MyCustomHelpWebApp*.
    - Admin key value: Specify the Azure Cognitive Search service admin key. You can find the key in **Access keys** under **Settings** in the left blade of the search service in the [Azure portal](https://portal.azure.com/).
    - [SearchServiceName]: Specify the search service name, such as *mycustomhelpsearch*.

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

5. Optionally, to update any UI strings in the Help pane, modify them in the **Customhelppane.en-US.label.txt** file.  

Next, you must specify the language that your custom help search index is intended for.  

### To assign a language to a custom index

1. Open the **Language.config** file in the solution.
2. Find the language of the index in the list, and specify an index name in ```index=""```, ```parentindex="```, or ```ultimateindex=""```.  

    For example, you created search indexes for English (United States) and German (Austria) with the names *myenusindex* and *mydeatindex*, respectively. Here is what your entries will look like.

    ```
    <add language="en-US" ultimateindex="myenusindex" />
    <add language="de-AT" parentlanguage="de" index="mydeatindex" />
    ```
3. Optionally, customize the language fallback for your index as described in the next section.

3. Build the **AzureSearchCustomHelp** solution.  

The result is a model that you then upload to the Asset Library of the customer project or the Microsoft Dynamics Lifecycle Services (LCS) solution project.

### Customize language fallback

Language fallback means that the Help pane runs a search in additional languages when the intended language does not return a result, or if that language does not exist.

> [!NOTE]
> A custom index must be available for those additional languages.

The search and fallback order are defined in the following order of priority:

1. The language that is set in the client, such as de-AT
2. The language that is defined in the **parentlanguage** attribute for that language, such as ```<add language="de-AT" parentlanguage="de" index="mydeindex" />```
3. The language that has the **ultimateindex** attribute set, such as ```<add language="en-US" ultimateindex="myenusindex" />```

> [!IMPORTANT]
> If **parentlanguage** is set, there must be a corresponding **parentindex**. Note that the following scenario is valid as ```language="de"``` has ```parentindex=""indexde``` and both de-DE and de-AT are descendants of de.

    ```
    <add language="de" parentindex="indexde"/>
    <add language="de-DE" parentlanguage="de" index=""/>
    <add language="de-AT" parentlanguage="de-DE" index="indexdeat"/>
    ```

Here are some sample configurations:

#### Single-locale help content

In this configuration, you only have help content for English (US). Clients set to any locale will display the help content in English (US).

    ```
    <add language=“en-US” ulitmateindex="indexenus"/>
    ```

#### Multiple-locale help content

In this configuration, you have help content for French, German and English (US). Clients set to `de` will display content in German, clients set to `fr` will display content in French, and clients set to any other locale will display the help content in English (US).

    ```
    <add language=“en-US” ulitmateindex="indexenus"/>
    <add language="fr" parentindex="indexfr"/>
    <add language="de" parentindex="indexde"/>
    ```

If clients are set to `de` or `fr` and no results are found in the German and French content respectively, results will be displayed in English (US) if available.

#### Multiple-locale-with-parent help content

In this configuration, you have help content for German (Austria), German, and English (US).

    ```
    <add language=“en-US” ulitmateindex="indexenus"/>
    <add language="de" parentindex="indexde"/>
    <add language="de-AT" parentlanguage="de" index="indexdeat"/>
    ```

If the client is set to `de-AT` and no results are found in the German (Austria) content, results will be displayed in German and English (US) where available.

## See also

[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
