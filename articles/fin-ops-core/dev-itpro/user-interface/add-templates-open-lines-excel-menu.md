---
title: Add templates to the Open lines in Excel menu
description: This article describes how you can promote a template to the Open lines in the Excel menu that is available on journal pages.
author: aprilolson
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9793bf54-cfb8-4ba1-bc8f-ba49ef37884a
---

# Add templates to the Open lines in Excel menu

[!include [banner](../includes/banner.md)]

This article describes how you can promote a template to the Open lines in the Excel menu that is available on journal pages.

Some of the most frequently used templates are the journal templates. Some of these journal templates have been promoted so that they appear on the **Open lines in Excel** menu by default. However, when you add a new template to the system, it must be promoted so that it's available on both the **Open in Office** menu and the **Open lines in Excel** menu. To promote a new template, follow these steps.

1.  Create a Microsoft Excel template, and save it locally. For more information, see [Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md).

2.  In Microsoft Visual Studio, create a new project for a model that has a reference to the ApplicationSuite model. 

3.  Create a new class, implement the **LedgerIJournalExcelTemplate** interface, and extend **DocuTemplateRegistrationBase**. Your implementation (supported journal type, and so on) defines the context that your template will be available as an option for in the Open in Excel experience. This example uses LedgerJournalHeaderEntity and LedgerJournalLineEntity, but you aren't limited to these entities. You can define your own entities, as long as they follow the journal header/line entity pattern. Here is an example from the **LedgerDailyJournalExcelTemplate** class.

    ```xpp
    using Microsoft.Dynamics.Platform.Integration.Office;  
    public class TestNewTemplate extends DocuTemplateRegistrationBase implements LedgerIJournalExcelTemplate
    {
        private const DocuTemplateName ExcelTemplateName = resourceStr(TestNewTemplate);
        private const EntityName LineEntityName = tableStr(LedgerJournalLineEntity);
        private const FieldName LineEntityJournalNum = fieldStr(LedgerJournalLineEntity, JournalBatchNumber);
        private const FieldName LineEntityDataAreaId = fieldStr(LedgerJournalLineEntity, dataAreaId);
        private const FieldName HeaderEntityName = tableStr(LedgerJournalHeaderEntity);
        private const FieldName HeaderEntityJournalNum = fieldStr(LedgerJournalHeaderEntity, JournalBatchNumber);
        private const FieldName HeaderEntityDataAreaId = fieldStr(LedgerJournalHeaderEntity, dataAreaId);
        /// <summary>
        /// A boolean value which indicates whether the journal type is supported for the Excel template.
        /// </summary>
        /// <param name = "_ledgerJournalType">The ledger journal type.</param>
        /// <returns>True if the journal type is supported; otherwise, false.</returns>
        public boolean isJournalTypeSupported(LedgerJournalType _ledgerJournalType)
        {
            return _ledgerJournalType == LedgerJournalType::Daily;
        }
        /// <summary>
        /// Gets the document template name.
        /// </summary>
        /// <returns>The document template name</returns>
        public DocuTemplateName documentTemplateName()
        {
            return ExcelTemplateName;
        }
        /// <summary>
        /// Gets a collection of the supported account types for the entity.
        /// </summary>
        /// <returns>A collection of <c>LedgerJournalACType</c> values.</returns>
        public Set supportedAccountTypes()
        {
            Set accountTypeSet = new Set(Types::Integer);
            accountTypeSet.add(LedgerJournalACType::Ledger);
            return accountTypeSet;
        }
        /// <summary>
        /// Gets a collection of the supported offset account types for the entity.
        /// </summary>
        /// <returns>A collection of <c>LedgerJournalACType</c> values.</returns>
        public Set supportedOffsetAccountTypes()
        {
            Set offsetAccountTypeSet = new Set(Types::Integer);
            offsetAccountTypeSet.add(LedgerJournalACType::Ledger);
            return offsetAccountTypeSet;
        }
        /// <summary>
        /// Validates the journal is valid for the template.
        /// </summary>
        /// <param name = "_ledgerJournalTable">The <c>LedgerJournalTable</c> record.</param>
        /// <returns>True if the journal is valid for the template; otherwise, false.</returns>
        public boolean validateJournalForTemplate(LedgerJournalTable _ledgerJournalTable)
        {
            return LedgerJournalExcelTemplate::validateJournalForTemplate(_ledgerJournalTable, this);
        }
        public void registerTemplates()
        {
            this.addTemplate(
                OfficeAppApplicationType::Excel,
                ExcelTemplateName,
                ExcelTemplateName,
                'Test new template',
                'Test new template',
                NoYes::No,
                NoYes::No,
                NoYes::No);
        }
        /// <summary>
        /// The resource name of the header entity.
        /// </summary>
        /// <returns>The resource name of the header entity.</returns>
        public EntityName headerEntityName()
        {
            return HeaderEntityName;
        }
        /// <summary>
        /// The resource name of the line entity.
        /// </summary>
        /// <returns>The resource name of the line entity.</returns>
        public EntityName lineEntityName()
        {
            return LineEntityName;
        }
        /// <summary>
        /// The field name for the header journal batch number.
        /// </summary>
        /// <returns>The field name for the header journal batch number.</returns>
        public FieldName headerJournalBatchNumberFieldName()
        {
            return HeaderEntityJournalNum;
        }
        /// <summary>
        /// The field name for the header data area.
        /// </summary>
        /// <returns>The field name for the header data area.</returns>
        public FieldName headerDataAreaFieldName()
        {
            return HeaderEntityDataAreaId;
        }
        /// <summary>
        /// The field name for the line journal batch number.
        /// </summary>
        /// <returns>The field name for the line journal batch number.</returns>
        public FieldName lineJournalBatchNumberFieldName()
        {
            return LineEntityJournalNum;
        }
        /// <summary>
        /// The field name for the line data area.
        /// </summary>
        /// <returns>The field name for the line data area.</returns>
        public FieldName lineDataAreaFieldName()
        {
            return LineEntityDataAreaId;
        }
        /// <summary>
        /// Append additional filter to the default filtering behavior.
        /// </summary>
        /// <returns>The original filter with new filter(s) appended; Otherwise, the original filter</returns>
        public FilterCollectionNode appendHeaderEntityFilters(FilterCollectionNode _headerFilter, ExportToExcelFilterTreeBuilder _headerFilterBuilder)
        {
            return _headerFilter;
        }
        /// <summary>
        /// Append additional filter to the default filtering behavior.
        /// </summary>
        /// <returns>The original filter with new filter(s) appended; Otherwise, the original filter</returns>
        public FilterCollectionNode appendLineEntityFilters(FilterCollectionNode _lineFilter, ExportToExcelFilterTreeBuilder _lineFilterBuilder)
        {
            FilterCollectionNode lineFilter = _lineFilterBuilder.and(
                _lineFilterBuilder.areEqual(fieldStr(LedgerJournalLineEntity, AccountType), LedgerJournalACType::Ledger),
                _lineFilterBuilder.areEqual(fieldStr(LedgerJournalLineEntity, OffsetAccountType), LedgerJournalACType::Ledger));
            return _lineFilterBuilder.and(_lineFilter, lineFilter);
        }
    }
    ```

4.  Build the project/model that has the new resources. You should have one new resource and one new class. 

5.  In the client, go to **Common** &gt; **Common** &gt; **Office integration** &gt; **Document templates** &gt; **Reload system templates**. You will see the new template in the list, and if you open the journal page that you added the template to, you will also see that template on the **Open lines in Excel** menu.


## Additional resources

[Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
