---
title: Facade, sequence, and activities in tax integration 
description: This article introduces the features and functions that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/14/2022
ms.custom: bap-template
---

# Facade, sequence, and activities in tax integration 

[!include [banner](../includes/banner.md)]

## 1. Facade

```
public final static class TaxIntegrationFacade
```

**The facade** (`TaxIntegrationFacade`) is the outmost interface of **Tax Integration**, and it is a bridge to [tax calculation service](global-tax-calcuation-service-overview.md).

The most important method is:

```X++
[Replaceable]
public static void calculate(TaxIntegrationDocumentObject _document)
```

The method accepts **a document** (`TaxIntegrationDocumentObject`) as its input, and returns `void`.

The method modifies **the document** directly; in other words, **the document** serves as its output as well.

> [!Note]
> The method is `Replaceable`, which means it can be completed replaced (customized).
```X++
TaxIntegrationSequence sequence = TaxIntegrationSequence::construct(LoggerName)
    .appendActivityOnDocument(TaxIntegrationSettingRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationDataRetrievalActivityOnDocument::construct())
    .appendActivityOnDocument(TaxIntegrationCalculationActivityOnDocument::construct())
    // ...
    .appendActivityOnDocument(TaxIntegrationDataPersistenceActivityOnDocument::construct());
sequence.act(_document);
if (!_document.isOK())
{
    throw _document.getException();
}
```

Inside the method, **a sequence** (`TaxIntegrationSequence`) is constructed and invoked. All activities are appended to the sequence in order.

If necessary, an exception is explicitly thrown in the end.

## 2. Sequence

**The sequence** (`TaxIntegrationSquence`) is a special activity which maintains an activity sequence. When its act method is invoked, all activities will be executed in the order in which they are appended.

```xpp
public final class TaxIntegrationSequence
    extends TaxIntegrationAbstractActivity
{
    public final void act(TaxIntegrationDocumentObject _document);
    private void actInternal(TaxIntegrationDocumentObject _document);
}
```

To use **a sequence** (`TaxIntegrationSequence`):

- `construct` creates **a sequence**;
- `appendActivitySequence`, `appendActivityOnDocument`, `appendActivityOnLine` build up **the sequence**;
- `act` plays **the sequence**.

Internally, **the sequence** maintains **an activity list** (`List`) inside, and enumerates the list upon invocation (`act`).

- It checks whether an activity should be skipped for current document by calling `shouldSkip` method of the activity.
- For `TaxIntegrationSequence` or `TaxIntegrationAbstractActivityOnDocument`, `act` is invoked directly if it should not be skipped.
- For `TaxIntegrationAbstractActivityOnLine`, the sequence will enumerate all `TaxIntegrationLineObject` in the document and invoke its `act` method (charge is also implemented by TaxIntegrationLine object). `act` is invoked first on **the charges** of **the document**, and then on **the lines** of **the document** with **the charges** of **each line**: for a lengthy example, if there are 2 charges and 2 lines on a document, and at the same time, 2 charges on each line, the complete sequence will be:
  1. the 1st charge of the document
  2. the 2nd charge of the document
  3. the 1st line of the document
  4. the 1st charge of the 1st line
  5. the 2nd charge of the 1st line
  6. the 2nd line of the document
  7. the 1st charge of the 2nd line
  8. the 2nd charge of the 2nd line

> [!Note]
> `TaxIntegrationSequence` is intended to be used directly, and it is implemented as a concrete class with a `public` `act` method.
Below is the `actInternal` method for quick reference.

```X++
    private void actInternal(TaxIntegrationDocumentObject _document)
    {
        var enumerator = list.getEnumerator();
        while (enumerator.moveNext())
        {
            anytype current = enumerator.current();
            if (current is TaxIntegrationSequence)
            {
                TaxIntegrationSequence sequence = current;
                sequence.act(_document);
                continue;
            }
            if (current is TaxIntegrationAbstractActivityOnDocument)
            {
                TaxIntegrationAbstractActivityOnDocument activity = current;
                if (!activity.shouldSkip(_document))
                {
                    activity.act(_document);
                }
                continue;
            }
            if (current is TaxIntegrationAbstractActivityOnLine)
            {
                TaxIntegrationAbstractActivityOnLine activity = current;
                if (!activity.shouldSkip(_document))
                {
                    SetEnumerator chargeEnumerator = _document.getChargeSet().getEnumerator();
                    while (chargeEnumerator.moveNext())
                    {
                        TaxIntegrationLineObject charge = chargeEnumerator.current();
                        activity.act(charge);
                    }
                    SetEnumerator lineEnumerator = _document.getLineSet().getEnumerator();
                    while (lineEnumerator.moveNext())
                    {
                        TaxIntegrationLineObject line = lineEnumerator.current();
                        activity.act(line);
                        chargeEnumerator = line.getChargeSet().getEnumerator();
                        while (chargeEnumerator.moveNext())
                        {
                            TaxIntegrationLineObject charge = chargeEnumerator.current();
                            activity.act(charge);
                        }
                    }
                }
                continue;
            }
        }
    }
```

## 3. Activity

Activity does the real work in integration flow. An activity acts as a segment in the integration flow. The name of an activity describes its purpose.

 All activities are inherited from the same class `TaxIntegrationAbstractActivity`. There are three kinds of activities. The hierarchy of activities are like:
![activity hierarchy.png](./media/tax-integration-activity-hierarchy.png)

- `TaxIntegrationSequence`, `TaxIntegrationAbstractActivityOnDocument`, `TaxIntegrationAbstractActivityOnLine` all extend `TaxIntegrationAbstractActivity`.
- `TaxIntegrationSequence`, `TaxIntegrationAbstractActivityOnDocument`, `TaxIntegrationAbstractActivityOnLine` all contain an `act` and an `actInternal` methods but accept different arguments.
- However, `TaxIntegrationAbstractActivityOnDocument` and `TaxIntegrationAbstractActivityOnLine` are intended to be extended, and they are implemented as an `abstract` class with an `internal` `act` method and an `abstract` `actInternal` method. So, new activity should extend one of these 2 abstract classes.
  - The activity should implement its own `actInternal` method to hold the real logic of the activity.
  - If activity is not applicable for all transactions/documents, the activity should implement its own `shouldSkip` method.
- `TaxIntegrationSequence` is intended to be used directly, and it is implemented as a concrete class with a `public` `act` method.
- They all log events during the `act` method if necessary after `TaxIntegrationLogLevelUtility` is checked, with the logging context inheritted from `TaxIntegrationAbstractActivity`.
- Refer to [How to add an activity in tax integration](./tax-integration-how-to-add-an-activity.md) for adding new activity.

### Sequence

`TaxIntegrationSequence` is a special activity as introduced above.

### Document activity

Document activity acts on `TaxIntegrationDocumentObject` and extends `TaxIntegrationAbstractActivityOnDocument`.

```X++
public abstract class TaxIntegrationAbstractActivityOnDocument
    extends TaxIntegrationAbstractActivity
{
    internal final void act(TaxIntegrationDocumentObject _document);
    protected abstract void actInternal(TaxIntegrationDocumentObject _document);
}
```

- New document activity should implement `actInternal` method to hold the logic of this activity. `actInternal` accepts a `TaxIntegrationDocumentObject` as input. So, it can manipulate data on document level, which cannot be done by line activity.
  - However, document can also act on `TaxIntegrationLineObject` by enumerating the `TaxIntegrationDocumentObject`. Actually, most document activity are handling data both on document and line level.
- If activity is not applicable for all transactions/documents, the activity should implement its own `shouldSkip` method.

### Line activity

Line activity acts on `TaxIntegrationLineObject` and extends `TaxIntegrationAbstractActivityOnLine`

```X++
public abstract class TaxIntegrationAbstractActivityOnLine
    extends TaxIntegrationAbstractActivity
{
    internal final void act(TaxIntegrationLineObject _line);
    protected abstract void actInternal(TaxIntegrationLineObject _line);
}
```

- New line activity should implement `actInternal` method to hold the logic of this activity. `actInternal` accepts a `TaxIntegrationLineObject` as input. So, it can only manipulate data on the line object given.
  - However, charges are also described as a `TaxIntegrationLineObject`. So, charges will also be processed by line activity.
- If activity is not applicable for **all lines** in the document, the activity should implement its own `shouldSkip` method.
  - The `shouldSkip` method indicates whether current activity should be skipped for all lines (including charges) in the document, since it accepts a `TaxIntegrationDocumentObject` as input.
  - When skipping line is necessary and common requirement, we can consider to add this in framework.

### Current activites

Here is the list of activities so far, in the order of `TaxIntegrationFacade::calculate`:

- TaxIntegrationSettingRetrievalActivityOnDocument,
- TaxIntegrationDataRetrievalActivityOnDocument,
- TaxIntegrationCalculationActivityOnDocument,
- TaxIntegrationErrorHandlingActivityOnDocument,
- TaxIntegrationTaxCodeCheckActivityOnLine,
- TaxIntegrationTaxIdActivityOnDocument,
- TaxIntegrationListCodeActivityOnDocument,
- TaxIntegrationCurrencyExchangeActivityOnDocument,
- TaxIntegrationDataPersistenceActivityOnDocument.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
