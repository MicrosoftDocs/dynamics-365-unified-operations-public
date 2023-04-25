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

This article introduces how to add a new, or customized activity to the tax integration framework. Before you begin, make sure that you have read the article, [Facade, Sequence, and Activity](./tax-integration-facade-sequence-activity.md).

## Create a new activity

### Document activity or line activity

Before you create the activity class, think about what kinds of activities should be added.

If all actions are completed in line, nothing from the document level is needed. Therefore, you should consider a line activity. Create a line activity and extend `TaxIntegrationAbstractActivityOnLine`.

    ```X++
    public class TaxIntegrationTaxCodeCheckActivityOnLine
        extends TaxIntegrationAbstractActivityOnLine
    {
    }
    ```

If actions are done at the document level and the line level, a document object is needed. Create a document activity and extend `TaxIntegrationAbstractActivityOnDocument`.

    ```X++
    public class TaxIntegrationDataPersistenceActivityOnDocument
        extends TaxIntegrationAbstractActivityOnDocument
    {
    }
    ```

### Implement shouldSkip

Implement the `shouldSkip` method to skip the activity under certain scenarios. This method is defined in `TaxIntegrationAbstractActivity`. The `shouldSkip` method of the document activity and line activity have the same signature and they accept `TaxIntegrationDocumentActivity` as input.

For example, if this activity isn't applicable for purchase orders, add a business process check in its `shouldSkip` method:

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
> In most cases, `super()` should be called since `shouldSkip()` in `TaxIntegrationAbstractActivity` has some basic check. For example, if the document has exceptions. For a line activity, `shouldSkip()` also takes a document object as input, meaning it will determine whether **all lines (including charges)** in the current document should be skipped. There is no ability to determine whether a certain line should be skipped in the framework. If it's really needed, the determination can be done in `actInternal` method of the line activity.

### Implement actInternal

The real business logic of the activity is written in `actInternal` method. `actInternal` has different signatures in document activity and line activity.

#### For line activity

`actInternal` of the line activity accepts a `TaxIntegrationLineObject` as input and can manipulate data at the line level.

#### For document activity

`actInternal` of document activity accepts a `TaxIntegrationDocumentObject` as input and can manipulate data within the whole document.

Most of the document activities manipulate data at the line level. Enumerate the lines in the document object and then contiue as needed. Below is an example of `TaxIntegrationTaxIdActivityOnDocument.xpp`

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

The new activity can't take effect until it's added to a `TaxIntegrationSequence`. Similar to other activities, the final step is to append it to the `TaxIntegrationSequence` object in `TaxIntegrationFacade::calculate` method.

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
> If you append the activity by extension, replace the whole method, since the method is replaceable. The order of the activity should be carefully arranged as the activity usually depends on the activities that are appended in front of it.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
