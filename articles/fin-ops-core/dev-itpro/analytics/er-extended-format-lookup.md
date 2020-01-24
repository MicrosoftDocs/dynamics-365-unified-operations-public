---
# required metadata

title: Electronic reporting (ER) extended format lookup
description: This topic describes how an ER format reference can be set up in the ER format lookup when the required format is stored in the Global repository
author: NickSelin
manager: AnnBe
ms.date: 01/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: AX 10.0.9

---

# Allow users to set up an ER format reference inquiring a format from the Global repository

[!include [banner](../includes/banner.md)]

You can use the [Electronic reporting](general-electronic-reporting.md) (ER) to configure 
[formats](general-electronic-reporting.md#FormatComponentOutbound) for outbound documents in accordance to the legal requirements of various countries/regions. You can also use the ER framework to configure [formats](general-electronic-reporting.md#FormatComponentInbound) for parsing of inbound documents and using information from such documents to append or update application data. Each of such formats can be executed in your Finance instance for handling of either inbound or outbound business documents as part of a certain business process. Usually, you must specify what ER format must be used in a certain business process. For doing that, you need to select a single ER format in a lookup field that is usually offered for a business user as part of business process specific parameters. Such lookup field is usually implemented by using the appropriate API of the ER framework – see [ER framework API - code to display a format mapping lookup](er-apis-app73.md#code-to-display-a-format-mapping-lookup)
for more.

For example, when you configure [foreign trade 
parameters](https://docs.microsoft.com/dynamics365/finance/localizations/emea-intrastat#set-up-foreign-trade-parameters),
you need to set up the references to individual ER formats that will be used to generate the Intrastat declaration and the Intrastat declaration control report. The pictures below show how the ER formats lookup field looks like in the foreign trade parameters page.

If the current Finance instance contains no Intrastat business process related ER formats, this lookup field will be empty.

[![Foreign trade parameters page](./media/ER-ExtLookup-Lookup1.gif)](./media/ER-ExtLookup-Lookup1.gif)

If the current Finance instance contains Intrastat business process related ER formats that are applicable for the company to which the user is currently signed in, this lookup field offers such ER formats.

[![Foreign trade parameters page](./media/ER-ExtLookup-Lookup2.png)](./media/ER-ExtLookup-Lookup2.png)

Note that this lookup offers the only ER formats that have been already imported to the current Finance instance. To
[import](./tasks/er-import-configuration-lifecycle-services.md) ER solutions to the current Finance instance, you need to have permissions to execute the appropriate function of the ER framework that supports the [lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md) of ER solutions containing ER formats.

Starting from the Finance version 10.0.9 (April 2020 release), the user interface of the ER formats lookup that is implemented by using the mentioned above ER framework API has been extended. You can still select the already available in the current Finance instance an ER format – all such formats are presented now in the **Select format configuration** fast tab. In addition to that, the extended lookup offers the new optional capability to inquire the [Global repository](rcs-global-repository-overview.md) (GR) to get the desired ER formats. All ER format of the GR are offered in the **Import from Global repository** fast tab.

[![Foreign trade parameters page](./media/ER-ExtLookup-Lookup3.png)](./media/ER-ExtLookup-Lookup3.png)

Note that, like the **Select format configuration** fast tab, the **Import from Global repository** fast tab presents the only ER formats that are applicable to the business process for which an ER formats is selected in this lookup field (generation of Intrastat declaration in our example) and are applicable to for the company to which the user is currently signed in (depending on the company country context).

When you selected an ER format in the **Import from Global repository** fast tab, the containing selected format ER
[configuration](general-electronic-reporting.md#Configuration) is imported from the GR to the current Finance instance.

[![Foreign trade parameters page](./media/ER-ExtLookup-FormatImport.png)](./media/ER-ExtLookup-FormatImport.png)

Then, if this import completed successfully, the reference to the imported ER format is stored in this lookup field. Note that when you access the GR the first time, you need to follow the offered link to sign up to the [Regulatory Configuration Service](https://aka.ms/rcs) (RCS) that is used to manage access to the GR storage.

[![Foreign trade parameters page](./media/ER-ExtLookup-RepoSignUp.png)](./media/ER-ExtLookup-RepoSignUp.png)

By default, the **Import from Global repository** fast tab presents the list of ER formats from the temporary storage that is automatically created based on the GR content for performance improvements. It happens when the **Import from
Global repository** fast tab is opened the first time that may take several seconds.

If you do not see the required ER format in the **Import from Global repository** fast tab but you are sure that this ER format is stored in the GR, select the **Synchronize** option. It will update the temporary storage synchronizing it with the current content of the GR.

## Feature activation

The availability of this functionality is controlled by the **Extended lookup of ER format configurations allowing to inquire the Global repository** feature of the **Feature management**. This feature is enabled by default.

[![Feature management page](./media/ER-ExtLookup-FeatureMngt.png)](./media/ER-ExtLookup-FeatureMngt.png)

## Security considerations

The **Maintain configuration repositories** (**ERMaintainSolutionRepositories**) privilege controls access to the GR for a user opening the ER format lookup with the enabled **Import from Global repository** fast tab. To allow users access the GR content from the ER format lookups, you need to change the security settings granting the **ERMaintainSolutionRepositories** privilege for users either directly or via already assigned roles and duties.

The picture below illustrates how this privilege can be granted for users playing the **Accountant** role that makes such users responsible for configuring foreign trade parameters. It includes the setting of references to the ER formats in the **File format mapping** and **Report format mapping** fields on the **Foreign trade parameters** page.

[![Security configuration page](./media/ER-ExtLookup-SecuritySetting.png)](./media/ER-ExtLookup-SecuritySetting.png)

## Limitations

Access to the GR in the ER format lookup is currently supported for the only selection of ER formats using to generate outbound documents.

## Frequently asked questions

### I cannot access the Global repository from the ER format lookup

I have enabled the **Extended lookup of ER format configurations allowing to inquire the Global repository** feature in the **Feature management** page. But when a user playing the different than the **System administrator** role opened the ER format lookup, the **Import from Global repository** fast tab is visible but shows no ER formats. The **Synchronize** option is visible but disabled and cannot be used.

Make sure that you granted the **Maintain configuration repositories** (**ERMaintainSolutionRepositories**) privilege to the user opening this ER format lookup. Contact your system administrator to get this privilege.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) framework API](er-apis-app73.md)

[Manage Electronic reporting (ER) configurations lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md)
