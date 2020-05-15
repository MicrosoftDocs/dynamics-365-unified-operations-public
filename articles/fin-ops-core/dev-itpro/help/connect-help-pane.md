---
# required metadata

title: Connect a custom Help website to the Help pane
description: This topic explains how you can extend the in-product Help pane with custom Help content. 
author: edupont04
manager: AnnBe
ms.date: 05/11/2020
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

# Connect a custom Help website to the Help pane

[!include [banner](../includes/banner.md)]

If you deliver custom Help content for a Finance and Operations solution, you can extend the **Help** pane so that it consumes that content. You complete this one-time configuration by using the Finance and Operations development environment in Microsoft Visual Studio. After you've finished, users can select among tabs for task guides, Microsoft Help content, and your Help content.

The process for connecting your [custom Help website](custom-help-overview.md#custom-help-sites) to the in-product **Help** pane involves the following steps:

1. Extend the **Help** pane in Visual Studio.
2. Assign an index to a language.
3. Customize language fallback.

> [!IMPORTANT]
> The procedures that follow require the development tools for Finance and Operations apps in Visual Studio. For more information, see [Development tools in Visual Studio](../dev-tools/development-tools-overview.md).

## <a name="extendhelppane"></a>Extend the Help pane and assign the custom Help indexes to languages

The **Help Pane extension** folder of the [Custom Help Toolkit](custom-help-toolkit.md) contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. That folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.

### Extend the Help pane

1. In the Finance and Operations development environment, open the **AzureSearchCustomHelp.sln** solution.
2. On the **Dynamics 365** menu, select **Import project**.
3. In the **File name** field, specify the path of the **HelppaneOption.axpp** project, and then select **OK** to complete the import process. Update the references so that no references are missing.
4. In the **HelppaneMacro** file, update the values of the following parameters:

    - **\[WebAppName\]** – Specify the name of the web app that you created in [Create a web app](walkthrough-help-azure.md#webapp). For example, specify **MyCustomHelpWebApp**.
    - **Admin key value** – Specify the admin key for the Azure Cognitive Search service. You can find the key in **Access keys** under **Settings** on the left of the search service in the [Azure portal](https://portal.azure.com/).
    - **\[SearchServiceName\]** – Specify the name of the search service that you created in [Create a search service](walkthrough-help-azure.md#searchservice). For example, specify **mycustomhelpsearch**.

    The following example shows the content of the HelppaneMacro file.

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

5. Optional: If you want to change any of the user interface (UI) strings that appear in the **Help** pane, edit the **Customhelppane.en-US.label.txt** file.

Next, you must specify the language that the search index for your custom Help is intended for.

### Assign a custom index to a language

1. Open the **Language.config** file in the solution.
2. In the list, find the language of the index, and specify an index name by using the **index=""**, **parentindex=""**, or **ultimateindex=""** key.

    For example, you created search indexes for English (United States) and German (Austria), and you named them **myenusindex** and **mydeatindex**, respectively. In this case, here is what your entries will look like.

    ```
    <add language="en-US" ultimateindex="myenusindex" />
    <add language="de-AT" parentlanguage="de" index="mydeatindex" />
    ```

3. Optional: Customize language fallback for your index, as described in the next section.
4. Build the **AzureSearchCustomHelp** solution.

The result is a model that you upload to the Asset library of the customer project or the solution project in Microsoft Dynamics Lifecycle Services (LCS).

## Customize language fallback

*Language fallback* means that the **Help** pane runs a search in additional languages if the intended language either doesn't return a result or doesn't exist.

> [!NOTE]
> A custom index must be available for the additional languages.

The search and fallback order have the following order of priority:

1. The language that is set in the client (for example, **de-AT**)
2. The language that is defined in the **parentlanguage** attribute for that language (for example, **\<add language="de-AT" parentlanguage="de" index="mydeindex" /\>**)
3. The language that the **ultimateindex** attribute is set for (for example, **\<add language="en-US" ultimateindex="myenusindex" /\>**)

> [!IMPORTANT]
> If the **parentlanguage** attribute is set, there must be a corresponding **parentindex** key.

The following scenario is valid, because **language="de"** has **parentindex="indexde"**, and both **de-DE** and **de-AT** are descendants of **de**.

```
<add language="de" parentindex="indexde"/>
<add language="de-DE" parentlanguage="de" index=""/>
<add language="de-AT" parentlanguage="de-DE" index="indexdeat"/>
```

For more information about languages, see [Languages, translations, and adaptations](language-locale.md#languages-translations-and-adaptations).

The following sections provide sample configurations.

### Help content for one locale

In this configuration, you have Help content only for English (United States). Regardless of the locale that clients are set to, they will show the Help content in English (United States).

```
<add language="en-US" ulitmateindex="indexenus"/>
```

### Help content for multiple locales

In this configuration, you have Help content for French, German, and English (United States). Clients that are set to the **de** locale will show the Help content in German, clients that are set to the **fr** locale will show the content in French, and clients that are set to any other locale will show the content in English (United States).

```
<add language="en-US" ulitmateindex="indexenus"/>
<add language="fr" parentindex="indexfr"/>
<add language="de" parentindex="indexde"/>
```

If clients are set to the **de** or **fr** locale, but no results are found in the German or French content, respectively, results will be shown in English (United States), if content is available in that language.

### Help content that uses parent locales

In this configuration, you have Help content for German, German (Austria), and English (United States). For example, you have several topics that are related specifically to features for Austria, but topics in German can be used otherwise.

```
<add language="en-US" ulitmateindex="indexenus"/>
<add language="de" parentindex="indexde"/>
<add language="de-AT" parentlanguage="de" index="indexdeat"/>
```

If the client is set to the **de-AT** locale, but no results are found in the German (Austria) content, results will be shown in German and English (United States), if content is available in those languages.

## See also

[Deploy custom Help to Azure](walkthrough-help-azure.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Configure the Help experience for Finance and Operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)
