---
# required metadata

title: Electronic reporting framework API changes for Application release 7.3
description: This topic describes how the API of the Electronic reporting (ER) framework has been changed in the Dynamics 365 for Finance and Operations, Enterprise edition Application release 7.3.
author: robinarh
manager: AnnBe
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: leok
ms.search.validFrom: 2017-11-28
ms.dyn365.ops.version: Platform update 8
---

# Electronic reporting framework API changes for Application release 7.3

This topic describes how the API of the Electronic reporting (ER) framework has been changed in the Dynamics 365 for Finance and Operations, Enterprise edition Application release 7.3.

There are to types of changes to the ER APIs:
- Several X++ classes were moved from X++ to an external assembly
- The rest of X++ classes were marked as internal

## How to access classes that were moved from X++ to an external assembly

To refer external classes, you need to add **using** directive at the beginning of your file:

    using Microsoft.Dynamics365.LocalizationFramework;

You can then refer an external class without any additional changes, for example:

    var destination = new ERFileDestinationMemory();

You can also create an alias for your namespace:

    using LF = Microsoft.Dynamics365.LocalizationFramework;

You can then refer to an external class by using the namespace alias that you created:

    var destination = new LF.ERFileDestinationMemory();

## How to access internal X++ objects by using ERObjectsFactory

From Application release 7.3 onward, the calling code must access the ER objects by using the methods of the **ERObjectsFactory** class. Several examples of the changes are shown.

### Display format mapping lookup task

Before Application release 7.3:

    ERFormatMappingTableLookup::lookupFormatMapping(<form control>, <model name>[, <data container name>]);
    ERFormatMappingTableLookup::lookupFormatMapping(_referenceGroupControl, bankLCMiscChargeReportERModelName);

Application release 7.3 and later:

    ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(<form control>, <model name>[, <data container name>]).performFormLookup();

    ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(_referenceGroupControl, bankLCMiscChargeReportERModelName).performFormLookup();

### Run format mapping for data export task

Before Application release 7.3:

    ERFormatMappingRun::constructByFormatMappingId(<format mapping id>, <file name>, <show prompt dialog>).run();
    ERFormatMappingRun::constructByFormatMappingId(erBinding, '', true).run();

Application release 7.3 and later:

    ERObjectsFactory::createFormatMappingRunByFormatMappingId(<format mapping id>, <file name>, <show prompt dialog>).run();
    ERObjectsFactory::createFormatMappingRunByFormatMappingId(erBinding, '', true).run();

### Run format mapping for data import task

Before Application release 7.3:

    ERModelMappingDestinationRun::constructByImportFormatMappingId(<mapping id>, <integration point>).run();
    ERModelMappingDestinationRun::constructByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();

Application release 7.3 and later:

    ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(<mapping id>, <integration point>).run();
    ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();

### Create browser file destination task

Before Application release 7.3:

    new ERFileDestinationBrowser();

Application release 7.3 and later:

    ERObjectsFactory::createFileDestinationBrowser();

### Create an attachment file destination task

Before Application release 7.3:

    ERFileDestinationAttachment::construct(<record>, ERDocuManagement::instance().otherDocuType());
    ERFileDestinationAttachment::construct(_cashRegisterFiscalTrans_W, ERDocuManagement::instance().otherDocuType());

Application release 7.3 and later:

    ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(<record>);
    ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(_cashRegisterFiscalTrans_W);
