---
title: Electronic reporting (ER) extended format lookup
description: Learn about how an ER format reference can be set up in the ER format lookup when the required format is stored in the Global repository.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-04-01
ms.search.form: ERSolutionTable, ERWorkspace
ms.dyn365.ops.version: AX 10.0.9
ms.assetid: 
---

# Allow users to set up an ER format reference inquiring a format from the Global repository

[!include [banner](../includes/banner.md)]

Use the [Electronic reporting](general-electronic-reporting.md) (ER) framework to configure formats for outbound documents that comply with the legal requirements of various countries or regions. You can also use the ER framework to configure formats for parsing inbound documents and use the information from those documents to append or update application data. You can use each of these formats in your Dynamics 365 Finance instance for handling inbound or outbound business documents as part of a certain business process.

Usually, you must specify what ER format to use in a certain business process. To specify the format, select a single ER format in a lookup field that is configured as part of business process-specific parameters. The appropriate API of the ER framework usually implements these lookup fields. For more information, see [ER framework API - code to display a format mapping lookup](er-apis-app73.md#code-to-display-a-format-mapping-lookup).

For example, when you configure [foreign trade parameters](../../../finance/localizations/emea-intrastat.md#set-up-foreign-trade-parameters), you need to set up the references to individual ER formats that generate the Intrastat declaration and the Intrastat declaration control report. The following screenshots show how the ER formats lookup field looks in the **Foreign trade parameters** page.

If the current Finance instance contains no Intrastat business process-related ER formats, this lookup field is empty.

:::image type="content" source="./media/ER-ExtLookup-Lookup1.gif" alt-text="Screenshot of the Foreign trade parameters page with empty Report format mapping field.":::

If the current Finance instance contains Intrastat business process related ER formats, this lookup field offers the ER formats.

:::image type="content" source="./media/ER-ExtLookup-Lookup2.png" alt-text="Screenshot of the Foreign trade parameters page with Report format mapping field showing options.":::

This lookup offers only the ER formats that are already imported to the current Finance instance. To
[import](./tasks/er-import-configuration-lifecycle-services.md) ER solutions to the current Finance instance, you need permissions to run the appropriate function of the ER framework that supports the [lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md) of ER solutions that contain ER formats.

Starting in Finance version 10.0.9 (April 2020 release), the user interface of the ER format lookup that the ER framework API implements is extended. You can still select the existing ER formats, which are on the **Select format configuration** FastTab. In addition, the extended lookup offers the new option to search the Global repository (GR) to locate specific ER formats. All ER formats of the GR are offered on the **Import from Global repository** FastTab.

:::image type="content" source="./media/ER-ExtLookup-Lookup3.png" alt-text="Screenshot of the Foreign trade parameters page showing the Import from Global repository FastTab.":::

Similar to the **Select format configuration** FastTab, the **Import from Global repository** FastTab shows only the ER formats that are applicable to the business process for which an ER format is selected in this lookup field. In this example, the generation of Intrastat declaration. The ER format is applicable for the company to which the user is currently signed in, depending on the company country or region context.

When you select an ER format on the **Import from Global repository** FastTab, the selected ER format
[configuration](general-electronic-reporting.md#Configuration) is imported from the GR to the current Finance instance.

:::image type="content" source="./media/ER-ExtLookup-FormatImport.png" alt-text="Screenshot of the Foreign trade parameters page showing a Processing operation note.":::

If the import completes successfully, the reference to the imported ER format is stored in this lookup field. When you access the GR for the first time, you need to follow the link provided to sign up for the Globalization studio workspace that is used to manage access to the GR storage.

:::image type="content" source="./media/ER-ExtLookup-RepoSignUp.png" alt-text="Screenshot of the Foreign trade parameters page showing a link to sign up for RCS.":::

By default, the **Import from Global repository** FastTab presents the list of ER formats from the temporary storage that is automatically created based on the GR content for performance improvements. This temporary storage is created when the **Import from Global repository** FastTab is opened the first time, which might take several seconds.

If you don't see the required ER format in the **Import from Global repository** FastTab, but you're sure that this ER format is stored in the GR, select the **Synchronize** option. This option updates the temporary storage and synchronizes it with the current content of the GR.

## Feature activation

The availability of this functionality is controlled by the feature **Extended lookup of ER format configurations allowing to inquire the Global repository** in **Feature management**. This feature is enabled by default.

:::image type="content" source="./media/ER-ExtLookup-FeatureMngt.png" alt-text="Screenshot of the Feature management page.":::

## Security considerations

The **Maintain configuration repositories** (**ERMaintainSolutionRepositories**) privilege controls access to the GR for a user opening the ER format lookup with the enabled **Import from Global repository** FastTab. To allow users to access the GR content from the ER format lookups, change the security settings by granting the **ERMaintainSolutionRepositories** privilege to users either directly or by using already assigned roles and duties.

The following screenshot shows how to grant this privilege to users assigned to the **Accountant** role. This role allows users to configure foreign trade parameters and set up references to the ER formats in the **File format mapping** and **Report format mapping** fields on the **Foreign trade parameters** page.

:::image type="content" source="./media/ER-ExtLookup-SecuritySetting.png" alt-text="Screenshot of the Security configuration page.":::

## Limitations

Access to the GR in the ER format lookup currently supports only the selection of ER formats that are used to generate outbound documents.

## Frequently asked questions

### Why can't I access the Global repository from the ER format lookup?

If you enable the **Extended lookup of ER format configurations allowing to inquire the Global repository** feature in **Feature management**, but users can't see ER formats on the **Import from Global repository** FastTab and the **Synchronize** option is visible but disabled, make sure that the **Maintain configuration repositories** (**ERMaintainSolutionRepositories**) privilege is granted to the user. Contact your system administrator to receive this privilege.

## Additional resources

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Electronic reporting (ER) framework API](er-apis-app73.md)
- [Manage Electronic reporting (ER) configurations lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
