---
title: Add a new activity in tax integration
description: This article explains how to add a new activity in tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/14/2022
ms.custom: bap-template
---

# Add a new activity in tax integration

[!include [banner](../includes/banner.md)]

This article introduces how to add a new (customized) activity to the tax integration framework. Before getting into details, please read [Facade, Sequence, Activity - Integration - Tax Service](./tax-integration-facade-sequence-activity.md) for background knowledge.

## Create a new activity

### Document activity or line activity?

Before creating the activity class, think about what kinds of activities should be added.

- If all actions are done in line (including charge), nothing from the document level is needed, should consider a line activity. Create a line activity and extend `TaxIntegrationAbstractActivityOnLine`.

    ```X++
    public class TaxIntegrationTaxCodeCheckActivityOnLine
        extends TaxIntegrationAbstractActivityOnLine
    {
    }
    ```

- If actions are done both at the document and line level, a document object is needed. Create a document activity and extend `TaxIntegrationAbstractActivityOnDocument`.

    ```X++
    public class TaxIntegrationDataPersistenceActivityOnDocument
        extends TaxIntegrationAbstractActivityOnDocument
    {
    }
    ```

### Implement shouldSkip

Implement `shouldSkip` method to skip the activity under certain scenarios. It is defined in `TaxIntegrationAbstractActivity`. `shouldSkip` method of both document and line activity have the same signature, they all accept `TaxIntegrationDocumentActivity` as input.

For example, if this activity is not applicable for purchase orders, we can add a business process check in its `shouldSkip` method:

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

> [!Note]
>
> - In most cases, `super()` should be called since `shouldSkip()` in `TaxIntegrationAbstractActivity` has some basic check like whether the document has exceptions or not.
> - For line activity, `shouldSkip()` also takes a document object as input, which means it will determine whether **all lines (including charges)** in the current document should be skipped. There is no ability to determine whether a certain line should be skipped in the framework. If it is really needed, the determination can be done in `actInternal` method of line activity.

### Implement actInternal

The real business logic of the activity is written in `actInternal` method. `actInternal` has different signatures in document activity and line activity.

#### For line activity

`actInternal` of line activity accepts a `TaxIntegrationLineObject` as input. It can manipulate data at the line level.

#### For document activity

`actInternal` of document activity accepts a `TaxIntegrationDocumentObject` as input. It can manipulate data within the whole document.

Most of the document activities actually also manipulate data at the line level. Just enumerate the lines in the document object, then do the needful. Below is an example of `TaxIntegrationTaxIdActivityOnDocument.xpp`

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

## Append activity to the sequence

The new activity cannot take effect until it is added to a `TaxIntegrationSequence`. So, the final step is to append it to the `TaxIntegrationSequence` object in `TaxIntegrationFacade::calculate` method, just like the other activities.

```X++
TaxIntegrationSequence sequence = TaxIntegrationSequence::construct(LoggerName)
    .appendActivityOnDocument(TaxIntegrationSettingRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationDataRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationCalculationActivityOnDocument::construct())
    // ...
    .appendActivityOnDocument(TaxIntegrationDataPersistenceActivityOnDocument::construct());
sequence.act(_document);
```

> [!Note]
>
> - If it is done by extension, just replace the whole method, since the method is replaceable.
> - The order of the activity should be carefully arranged. Usually, the activity depends on the activities that are appended in front of it.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
