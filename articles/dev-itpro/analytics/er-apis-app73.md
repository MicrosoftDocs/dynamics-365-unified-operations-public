

This topic describes how the API of the Electronic reporting (ER) framework has been changed in the Dynamics 365 for Finance and Operations 2017 Fall release.

Two major types of changes can be highlighted:

1.  Several X++ classes were moved from X++ to an external assembly;

2.  Rest of X++ classes were marked as internal.

Find below the samples of new API usage.

How to access classes that were moved from X++ to external assembly
-------------------------------------------------------------------

To refer external classes, you need to add **using** directive at the beginning of your file:

using Microsoft.Dynamics365.LocalizationFramework;

After that, you can refer an external class without any additional changes, e.g.:

var destination = new ERFileDestinationMemory();

You can also create an alias for your namespace and refer it:

Adding an alias:

using LF = Microsoft.Dynamics365.LocalizationFramework;

Referring an external class by using its namespace alias:

var destination = new LF.ERFileDestinationMemory();

How to access internal X++ objects via ERObjectsFactory
-------------------------------------------------------

From now on, the calling code should access the ER objects via the methods of the **ERObjectsFactory** class. The tables below illustrate how the existing calling code should be changed: code that was changed shown as black, unchanged parts are shown gray.

### ‘Display format mapping lookup’ task

Old code pattern and example:

ERFormatMappingTableLookup::lookupFormatMapping(&lt;form control&gt;, &lt;model name&gt;\[, &lt;data container name&gt;\]);

ERFormatMappingTableLookup::lookupFormatMapping(\_referenceGroupControl, bankLCMiscChargeReportERModelName);

New code pattern and example:

ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(&lt;form control&gt;, &lt;model name&gt;\[, &lt;data container name&gt;\]).performFormLookup();

ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(\_referenceGroupControl, bankLCMiscChargeReportERModelName).performFormLookup();

### 

### ‘Run format mapping for data export’ task

Old code pattern and example:

ERFormatMappingRun::constructByFormatMappingId(&lt;format mapping id&gt;, &lt;file name&gt;, &lt;show prompt dialog&gt;).run();

ERFormatMappingRun::constructByFormatMappingId(erBinding, '', **true**).run();

New code pattern and example:

ERObjectsFactory::createFormatMappingRunByFormatMappingId(&lt;format mapping id&gt;, &lt;file name&gt;, &lt;show prompt dialog&gt;).run();

ERObjectsFactory::createFormatMappingRunByFormatMappingId(erBinding, '', **true**).run();

### ‘Run format mapping for data import’ task

Old code pattern and example:

ERModelMappingDestinationRun::constructByImportFormatMappingId(&lt;mapping id&gt;, &lt;integration point&gt;).run();

ERModelMappingDestinationRun::constructByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();

New code pattern and example:

ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(&lt;mapping id&gt;, &lt;integration point&gt;).run();

ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();

### 

### ‘Create browser file destination’ task

Old code pattern and example:

**new** ERFileDestinationBrowser();

New code pattern and example:

ERObjectsFactory::createFileDestinationBrowser();

### 

### ‘Create an attachment file destination’ task

Old code pattern and example:

ERFileDestinationAttachment::construct(&lt;record&gt;, ERDocuManagement::instance().otherDocuType());

ERFileDestinationAttachment::construct(\_cashRegisterFiscalTrans\_W, ERDocuManagement::instance().otherDocuType());

New code pattern and example:

ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(&lt;record&gt;);

ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(\_cashRegisterFiscalTrans\_W);
