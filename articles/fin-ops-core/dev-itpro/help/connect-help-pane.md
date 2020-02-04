---
# required metadata

title: Connect a custom Help website to the Help pane
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 01/31/2020
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

# Connect your Help website with the Help pane

[!include [banner](../includes/banner.md)]

With your custom Help available on a website, you must extend the Help pane to consume this content. This is a one-time configuration that requires the Finance and Operations development environment in Visual Studio. The result is a tab on the Help pane that will show your content so that users can choose between tabs for Task guides, Microsoft's Help content, and your Help content.

This involves the following steps:

1. Extend the Help pane in Visual Studio
2. Assign a language index
3. Customize language fallback

## <a name="extendhelppane"></a>Extend the Help pane and assign the language index in Visual Studio

The **Help Pane extension** folder of the toolkit contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. The same folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.  

### To extend the Help pane

1. In the Finance and Operations development environment, start Microsoft Visual Studio, and open the **AzureSearchCustomHelp.sln** solution from the **AzureSearchCustomHelp.zip** file in the **Help Pane** extension folder in the https://github.com/microsoft/dynamics356f-o-custom-help repo.  
2. On the Dynamics 365 menu, choose **Import project**.
3. In the **File name** field, specify the path to **HelppaneOption.axpp** that you also retrieved from the https://github.com/microsoft/dynamics356f-o-custom-help repo, and then choose OK to complete the import process. Update the references so that there are no missing references.  
4. If you added a new field to the search index in your search service, or you changed an existing field name, you must add that field to the Document.cs file.  

    For an example of an index in a search service see the [Configure the search service](walkthrough-help-azure.md#searchconfig)
 section in [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md).

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

6. If you want to update any UI strings, including labels, in the Help pane, modify them in **Customhelppane.en-US.label.txt**.  

Next, you must specify the language that your custom Help index is intended for. You can also change the language fallback if you want to override the default behavior.

### To assign a language to a custom index

1. Open the **Language.config** file in the solution.
2. Find the language of the index in the list, and specify an index name in ```index=""```, ```parentindex="```, or ```ultimateindex=""```.  

    For example, you created an index for English (United States) and Spanish (Mexico). In this case, the index names are *customenus* and *customes*, respectively. Here is what your entries will look like.

    ```
    <add language="en-US" ultimateindex="customenus" />
    <add language="es-MX" parentlanguage="es" index="customes" />
    ```

3. Build the **AzureSearchCustomHelp** solution. Optionally, you can customize the language fallback for your index.

## Customize language fallback

With language fallback, the Help pane runs a search in additional languages when the intended language does not return a result, or if that language does not exist.

> [!NOTE]
> A custom index must be available for those additional languages.

For example, you have created a custom Help index for en-US, de, and de-AT, and added them to the **Language.config** file. You use *de-AT* as the product language for your Dynamics 365 solution and run the custom search. If the search result is found in the *de-AT* index, the result is just presented. If no result is found in *de-AT*, an additional search is performed on *de* and *en-US*. The Help pane indicates that no result was found in *de-AT*, but that found some results were found in *de* and *en-US*.

This behavior is controlled through the **parentlanguage** and **ultimateindex** attributes in the **Language.config** file.

The search and fallback order are defined in the following order of priority:

1. The language that is set in the client, such as de-AT
2. The language that is defined in the **parentlanguage** attribute for that language, such as ```<add language="de-AT" parentlanguage="de" index="yourdeindex" />```
3. The language that has the **ultimateindex** attribute set, such as ```<add language="en-US" ultimateindex="yourenusindex" />```

## See also

[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
