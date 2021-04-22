---
# required metadata

title: ER framework API changes for Application update 7.3
description: This topic describes Electronic reporting framework APIs changes in the Dynamics 365 for Finance and Operations, Enterprise edition Application update 7.3.
author: NickSelin
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2017-11-28
ms.dyn365.ops.version: Platform update 8
---

# ER framework API changes for Application update 7.3

[!include [banner](../includes/banner.md)]

This topic describes how the API of the Electronic reporting (ER) framework has been changed in the Dynamics 365 for Finance and Operations, Enterprise edition Application update 7.3.

There are two types of changes to the ER APIs:

- Several X++ classes were moved from X++ to an external assembly.
- The rest of X++ classes were marked as internal.

## How to access classes that were moved from X++ to an external assembly

To access external classes, you need to add the **using** directive to the beginning of your file.

```xpp
using Microsoft.Dynamics365.LocalizationFramework;
```

You can then access an external class without any additional changes, for example.

```xpp
var destination = new ERFileDestinationMemory();
```

You can also create an alias for your namespace.

```xpp
using LF = Microsoft.Dynamics365.LocalizationFramework;
```

You can then refer to an external class by using the namespace alias that you created.

```xpp
var destination = new LF.ERFileDestinationMemory();
```

## How to access internal X++ objects by using ERObjectsFactory

In Application update 7.3 and later updates, the calling code must access the ER objects by using the methods of the **ERObjectsFactory** class. Several examples of these changes are shown.

### Code to display a format mapping lookup

Before Application update 7.3

```xpp
// pattern
ERFormatMappingTableLookup::lookupFormatMapping(<form control>, <model name>[, <data container name>]);
// sample code
ERFormatMappingTableLookup::lookupFormatMapping(_referenceGroupControl, bankLCMiscChargeReportERModelName);
```

Application update 7.3 and later

```xpp
// pattern
ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(<form control>, <model name>[, <data container name>]).performFormLookup();
// sample code
ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(_referenceGroupControl, bankLCMiscChargeReportERModelName).performFormLookup();
```

### Code to run a format mapping for data export

Before Application update 7.3

```xpp
// pattern
ERFormatMappingRun::constructByFormatMappingId(<format mapping id>, <file name>, <show prompt dialog>).run();
// sample code
ERFormatMappingRun::constructByFormatMappingId(erBinding, '', true).run();
```

Application update 7.3 and later

```xpp
// pattern
ERObjectsFactory::createFormatMappingRunByFormatMappingId(<format mapping id>, <file name>, <show prompt dialog>).run();
// sample code
ERObjectsFactory::createFormatMappingRunByFormatMappingId(erBinding, '', true).run();
```

### Code to run a format mapping for data import

Before Application update 7.3

```xpp
// pattern
ERModelMappingDestinationRun::constructByImportFormatMappingId(<mapping id>, <integration point>).run();
// sample code
ERModelMappingDestinationRun::constructByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();
```

Application update 7.3 and later

```xpp
// pattern
ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(<mapping id>, <integration point>).run();
// sample code
ERObjectsFactory::createMappingDestinationRunByImportFormatMappingId(custPaymModeTable.ERModelMappingTable, CustVendOutPaymConstants::IntegrationPoint).run();
```

### Code to create a browser file destination

Before Application update 7.3

```xpp
// sample code
new ERFileDestinationBrowser();
```

Application update 7.3 and later

```xpp
// sample code
ERObjectsFactory::createFileDestinationBrowser();
```

### Code to create an attachment file destination

Before Application update 7.3

```xpp
// pattern
ERFileDestinationAttachment::construct(<record>, ERDocuManagement::instance().otherDocuType());
// sample code
ERFileDestinationAttachment::construct(_cashRegisterFiscalTrans_W, ERDocuManagement::instance().otherDocuType());
```

Application update 7.3 and later

```xpp
// pattern
ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(<record>);
// sample code
ERObjectsFactory::createFileDestinationAttachmentWithOtherDocuType(_cashRegisterFiscalTrans_W);
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]