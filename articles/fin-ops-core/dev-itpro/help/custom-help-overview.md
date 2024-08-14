---
title: Custom Help overview
description: Learn about how you can extend the Microsoft Help system so that it reflects your solution and then connect your content to the Help pane.
author: edupont04
ms.author: edupont
ms.topic: overview
ms.date: 07/17/2024
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Custom Help overview

[!include [banner](../includes/banner.md)]

[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Finance and operations apps are often customized and extended to fit an organization's needs. If your solution is based on Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, or Dynamics 365 Commerce, you can connect solution-specific and customer-specific Help content to the [Help pane](../../fin-ops/get-started/help-overview.md#in-product-help) in the finance and operations client. This article describes the main steps and decision points.

> [!NOTE]
> Users of finance and operations apps can create custom task guides to supplement conceptual content that describes the functionality of their solution. These conceptual descriptions are also referred to as Help and can be provided by Microsoft, partners, and an organization itself. For more information, go to [Help system](../../fin-ops/get-started/help-overview.md).

The following illustration, and this article in general, use the term *Help* for conceptual descriptions that either include or exclude how-to guides. The term *task guides* refers to in-product task guides.

![Customized Help solution and the Help pane.](../../fin-ops/get-started/media/help-architecture.png)

## Custom Help content

Custom Help content typically originates from one of three sources:

- Microsoft documentation repositories (repos)

    Microsoft's content in the various GitHub repos is optimized for the learn.microsoft.com site and the tools that are used for this site. It is not intended to be customized directly but to be supplemented by articles on your local website. However, depending on your solution, you might need a copy of Microsoft's content.

- Existing customized Dynamics AX content

    You can convert Dynamics AX custom Help content so that it can be used in Dynamics 365.

- HTML files that are created specifically for your solution

    Learn more about the metadata that must be added to your HTML files for context-sensitive Help and search to work correctly in the [Metadata requirements for custom Help files](#metadata-requirements-for-custom-help-files) section.

## Process

The end-to-end process depends on the customer's solution and the users' expectations. A typical process involves the following steps:

1. Create the custom Help content.
2. Publish the content on a website.
3. Index the content by using a search service.
4. Connect the custom **Help** pane to the website and the search service.

Microsoft provides sample tools and scripts that can help you covert content and configure the Help pane to include your custom Help. Find the samples at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/).  
<!-- 
You're welcome to share your knowledge by contributing to this documentation through the link on the page or by joining the [Dynamics 365 community](https://community.dynamics.com/). -->

The following table outlines the main objectives that admins typically have for configuring the Help experience.

| Objective | Learn more |
|-----------|------------|
| I want to give my users a customized in-product Help experience that reflects their actual solution. | Go to the [Custom Help websites](#custom-help-sites) section of this article and [Create documentation or training with Task Recorder](../user-interface/task-recorder-training-docs.md). |
| I want to add my content to the **Help** pane. | Go to [Connect a custom Help website to the Help pane](connect-help-pane.md). |
|I want to reuse content that was originally created for Dynamics AX.|Go to the [Reuse Dynamics AX 2012 content](#reuse-dynamics-ax-2012-content) section.|
|I want to reuse content in one language for another, related language.|Go to the [Language and locale descriptors in Help](language-locale.md) article.|
| I want to contribute to the Microsoft Help content. | Go to [Contribute to the Help](contributor-guide.md). |

## <a name="custom-help-sites"></a>Custom Help websites

Before the product can connect to your Help content, you must customize the in-product **Help** pane so that it shows your content. Learn more at [Connect a custom Help website to the Help pane](connect-help-pane.md).  

The following conditions must be met:

- Your content must be available on a website.

    You can deploy your content to an existing website, or you can set up a dedicated website to host your content. The website can be private or public, but we recommend that you **do not** require users to sign in to access your content.

- Your content must be indexed by a search service.

  Learn more in the [Generate JSON files for the search service](#json) section.

- The content must include the right metadata properties.

  Learn more in the section.

## Metadata requirements for custom Help files

The following metadata must be present in your topics for context-sensitive Help and full-text search to return results.

| Property | Description |
|----------|-------------|
| title | The value is used for full-text search from the **Help** pane. |
| description | The value is used for full-text search from the **Help** pane. |
| ms.search.form | The value contains the Application Object Tree (AOT) name of a page and is used for context-sensitive search from the **Help** pane. |
| ms.locale | The value indicates the language of the article. It's mapped against the current browser locale when the **Help** pane searches the content. Language fallback can be configured for the target custom Help website. Learn more at [Language and locale descriptors in the product and in Help](language-locale.md). |
| ms.search.scope | The value determines which client the Help article is shown in. You can specify one or more values. Values include **Core**, **Operations**, **Retail**, and **Human Resources**. |

The following table describes the values that can be specified for the **ms.search.scope** property. You can specify one or more values. The values determine which client a Help article is shown in.

| Value | Description |
|-------|-------------|
| Core | If this value is present, the article appears in the **Help** pane. Otherwise, the article doesn't appear in the **Help** pane. This value is set for the part of the Microsoft content that must always be available in the **Help** pane, for all users across all supported Dynamics 365 solutions. |
| Operations | This value applies to solutions that are based on Finance or Supply Chain Management. |
| Retail | This value applies to solutions that are based on Commerce. |
| Human Resources | This value applies to solutions that are based on Dynamics 365 Human Resources. |

### Non-required metadata

The following properties are reserved for future use:

- **ms.search.region** – Eventually, this property might be used to limit the content that is shown to content that is tagged either as global or for the region of the implementation.
- **ms.search.validFrom** – Eventually, this property might be used to limit the content that is shown to content for a product that was released on a given date or earlier.
- **ms.dyn365.ops.version** – Eventually, this property might be used to limit the content that is shown to content for a specific version of a product or earlier.
- **ms.search.industry** – Eventually, this property might be used to limit the content that is shown to content for a specific industry.

## <a name="json"></a>Generate JSON files for the search service

The **ConvertHtmlToJson** tool transforms HTML files into JSON files. You can then add the JSON files to the Microsoft Azure Search service, which will generate context-sensitive links to your Help content. Find the tool at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/).

The JSON files include metadata that the indexer uses to identify the form and language that the target Help page is intended for.

Here is the syntax for running ConvertHtmlToJson.exe.

```
ConvertHtmlToJson.exe --h <path> -j <path> --v <true|false>
```

The following table explains the parameters.

| Parameter | Description |
|-----------|-------------|
| h | Specify the path of the HTML files to process. |
| j | Specify the folder to save the JSON files to. The folder must already exist. |
| v | Set this parameter to **true** to turn on verbose logging. Otherwise, set it to **false**. |

The following example generates JSON files without verbose logging.

```
ConvertHtmlToJson.exe --h D:\D365-Operations\d365F-O\supply-chain\de -j D:\D365-Operations\json\supply-chain\de
```

## Reuse Dynamics AX 2012 content

If you have content from Dynamics AX 2012, you can reuse it for Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce. However, you must first transform the HTML files so that they can be used in the custom Help environment.  

The **run_ax2012.ps1** Windows PowerShell script transforms AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the AX 2012 HTML files:

- Replace the **Microsoft.Help.F1** metadata name with **ms.search.form**.
- Replace the **Title** metadata name with **title**.
- Change the file name extension from **.htm** to **.html**.
- Add the following metadata.

    ```html
    <meta name="ms.search.region" content="Global" />
    <meta name="ms.search.scope" content="Operations, Core" />
    <meta name="ms.dyn365.ops.version" content="AX 7.0.0" />
    <meta name="ms.search.validFrom" content="2016-05-31" />
    <meta name="ms.search.industry" content="cross" />
    ```

### Run the script

Run the following command from a Command Prompt window, or directly in Windows PowerShell.

```powershell
PowerShell.exe -File run_ax2012.ps1 "Original file location" "New file location"
```

The following metadata is used, or it's reserved so that it can be used during indexing.

```html
<meta name="title" content="Title of file" />
<meta name="ms.locale" content="locale" />
<meta name="ms.search.form" content="FormAOTName" />
<meta name="description" content="Description of file" />
<meta name="ms.search.region" content="Global" />
<meta name="ms.search.scope" content="Operations, Core" />
<meta name="ms.dyn365.ops.version" content="AX 7.0.0" />
<meta name="ms.search.validFrom" content="2016-05-31" />
<meta name="ms.search.industry" content="cross" />
```

For a description of the required metadata, go to the [Metadata requirements for custom Help files](#metadata-requirements-for-custom-help-files) section.

### <a name="moving-to-markdown"></a>Convert HTML content to Markdown

To convert your content to Markdown, use a third-party tool. Microsoft does not provide a tool that can convert HTML to Markdown.

After you've converted your content to Markdown, use an open-source tool to generate content for your website. Markdown gives you access to a wide range of open-source tools. For more information, go to [Contribute to the Help](contributor-guide.md).

## See also

[Connect a custom Help website to the Help pane](connect-help-pane.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Configure the Help experience for finance and operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
