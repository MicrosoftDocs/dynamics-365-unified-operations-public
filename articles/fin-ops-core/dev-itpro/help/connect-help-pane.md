---
title: Connect a custom Help website to the Help pane
description: This article explains how you can extend the in-product Help pane with custom Help content.
author: edupont04
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Connect a custom Help website to the Help pane

[!include [banner](../includes/banner.md)]

If you deliver custom Help content for a finance and operations solution, you can extend the **Help** pane so that it consumes that content. You complete this one-time configuration by using the finance and operations development environment in Microsoft Visual Studio. After you've finished, users can select among tabs for task guides, Microsoft Help content, and your Help content.

The process for connecting your [custom Help website](custom-help-overview.md#custom-help-sites) to the in-product **Help** pane involves the following steps:

1. Extend the **Help** pane in Visual Studio.
2. Assign an index to a language.
3. Customize language fallback.

> [!IMPORTANT]
> The procedures that follow require the development tools for finance and operations apps in Visual Studio. For more information, see [Development tools in Visual Studio](../dev-tools/development-tools-overview.md).

## <a name="extendhelppane"></a>Extend the Help pane and assign the custom Help indexes to languages

[!INCLUDE [custom-help-toolkit-tools](../includes/custom-help-toolkit-tools.md)]

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

[Language and locale descriptors in the product and in Help](language-locale.md)  
[Configure the Help experience for finance and operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
