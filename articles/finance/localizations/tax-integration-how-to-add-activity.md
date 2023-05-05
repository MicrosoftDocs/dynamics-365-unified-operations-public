---
title: Add a new activity in tax integration
description: This article explains how to add a new activity in tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/25/2022
ms.custom: bap-template
---

# Add a new activity in tax integration

[!include [banner](../includes/banner.md)]

This article provides information about how to add a new or customized activity to the tax integration framework. Before you begin, be sure to read [Facade, sequence, and activities in tax integration](./tax-integration-facade-sequence-activity.md).

## Create a new activity

### Document activity or line activity

Before you create the activity class, think about the kinds of activities that should be added.

If all actions are done at the line level, nothing from the document level is required. Therefore, you should consider a line activity. Create a line activity, and extend `TaxIntegrationAbstractActivityOnLine`.

```X++
public class TaxIntegrationTaxCodeCheckActivityOnLine
    extends TaxIntegrationAbstractActivityOnLine
{
}
```

If actions are done at both the document level and the line level, a document object is required. Create a document activity, and extend `TaxIntegrationAbstractActivityOnDocument`.

```X++
public class TaxIntegrationDataPersistenceActivityOnDocument
    extends TaxIntegrationAbstractActivityOnDocument
{
}
```

### Implement shouldSkip

Implement the `shouldSkip` method to skip the activity in specific scenarios. This method is defined in `TaxIntegrationAbstractActivity`. The `shouldSkip` method of the document activity and the `shouldSkip` method of the line activity have the same signature, and they accept `TaxIntegrationDocumentActivity` as input.

For example, if the activity isn't applicable to purchase orders, add a business process check in its `shouldSkip` method.

```X++
internal boolean shouldSkip(TaxIntegrationDocumentObject _document)
{
    // call super() for some common check
    if (super(_document))
    {
        return true;
    }
    // Skip specifically for purchase order
    if (_document.getBusinessProcess() == TaxIntegrationBusinessProcess::Purchase)
    {
        return true;
    }
}
```

> [!NOTE]
> In most cases, `super()` should be called, because `shouldSkip()` in `TaxIntegrationAbstractActivity` has some basic checks (for example, if the document has exceptions). For a line activity, `shouldSkip()` also takes a document object as input. Therefore, it will determine whether **all lines (including charges)** in the current document should be skipped. There's no way to determine whether a specific line should be skipped in the framework. If such a determination is required, it can be done in the `actInternal` method of the line activity.

### Implement actInternal

The real business logic of the activity is written in the `actInternal` method. The `actInternal` method of the document activity and the `actInternal` method of the line activity have different signatures.

#### For the line activity

The `actInternal` method of the line activity accepts a `TaxIntegrationLineObject` object as input and can manipulate data at the line level.

#### For the document activity

The `actInternal` method of the document activity accepts a `TaxIntegrationDocumentObject` object as input and can manipulate data in the whole document.

Most of the document activities manipulate data at the line level. Enumerate the lines in the document object, and then continue as required. The following example shows `TaxIntegrationTaxIdActivityOnDocument.xpp`.

```X++
SetEnumerator chargeEnumerator = _document.getChargeSet().getEnumerator();
while (chargeEnumerator.moveNext())
{
    TaxIntegrationLineObject charge = chargeEnumerator.current();
    // process the document charge
    if (!TaxIntegrationTaxIdActivityOnDocument::populateLine(charge))
    {
        return;
    }
}
SetEnumerator lineEnumerator = _document.getLineSet().getEnumerator();
while (lineEnumerator.moveNext())
{
    TaxIntegrationLineObject line = lineEnumerator.current();
    // process the line
    if (!TaxIntegrationTaxIdActivityOnDocument::populateLine(line))
    {
        return;
    }
    chargeEnumerator = line.getChargeSet().getEnumerator();
    while (chargeEnumerator.moveNext())
    {
        TaxIntegrationLineObject charge = chargeEnumerator.current();
        // process the line charge
        if (!TaxIntegrationTaxIdActivityOnDocument::populateLine(charge))
        {
            return;
        }
    }
}
```

## Append an activity to the sequence

The new activity can't take effect until it's added to a `TaxIntegrationSequence` object. Therefore, as for other activities, the final step is to append it to the `TaxIntegrationSequence` object in the `TaxIntegrationFacade::calculate` method.

```X++
TaxIntegrationSequence sequence = TaxIntegrationSequence::construct(LoggerName)
    .appendActivityOnDocument(TaxIntegrationSettingRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationDataRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationCalculationActivityOnDocument::construct())
    // ...
    .appendActivityOnDocument(TaxIntegrationDataPersistenceActivityOnDocument::construct());
sequence.act(_document);
```

> [!NOTE]
> If you append the activity by extension, replace the whole method, because the method is replaceable. The order of the activity should be carefully arranged, because the activity usually depends on the activities that are appended in front of it.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
