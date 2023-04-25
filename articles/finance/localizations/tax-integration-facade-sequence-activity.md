---
title: Facade, sequence, and activities in tax integration 
description: This article introduces the features and functions that must be implemented to integrate a new transaction.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/25/2022
ms.custom: bap-template
---

# Facade, sequence, and activities in tax integration

[!include [banner](../includes/banner.md)]

Facade controls the tax integration flow by a sequence that maintains a list of activities. This article introduces these three classes in tax integration.

## Facade

``X++
public final static class TaxIntegrationFacade
```

**The facade** (`TaxIntegrationFacade`) is the outmost interface of tax integration, and it is a bridge to the [Tax Calculation Service](global-tax-calcuation-service-overview.md).

The most important method is:

```X++
[Replaceable]
public static void calculate(TaxIntegrationDocumentObject _document)
```

The method accepts a **document** (`TaxIntegrationDocumentObject`) as its input, and returns `void`.

The method modifies the **document** directly. The **document** serves as the output as well.

> [!NOTE]
> The method is `Replaceable`, which means it can be completely replaced (customized).

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

## Sequence

**The sequence** (`TaxIntegrationSquence`) is a special activity that maintains an activity sequence. When its `act` method is invoked, all activities are executed in the order in which they are appended.

```X++
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

Internally, the sequence maintains an activity list (`List`) inside, and enumerates the list upon invocation (`act`).

- The sequence checks whether an activity should be skipped for the current document by calling the `shouldSkip` method of the activity.
- For `TaxIntegrationSequence` and `TaxIntegrationAbstractActivityOnDocument`, `act` is invoked directly if it shouldn't be skipped.
- For `TaxIntegrationAbstractActivityOnLine`, the sequence will enumerate all `TaxIntegrationLineObject` in the document and invoke its `act` method (charge is also implemented by TaxIntegrationLine object). `act` is invoked first on the charges of the document, and then on the lines of the document with the charges of each line. For example, if there are two charges and two lines on a document, and at the same time, two charges on each line, the complete sequence will be:
  1. The 1st charge of the document
  2. The 2nd charge of the document
  3. The 1st line of the document
  4. The 1st charge of the 1st line
  5. The 2nd charge of the 1st line
  6. The 2nd line of the document
  7. The 1st charge of the 2nd line
  8. The 2nd charge of the 2nd line


`TaxIntegrationSequence` is intended to be used directly, and is implemented as a concrete class with a `public` `act` method.
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

## Activity

Activity does the real work in an integration flow. An activity acts as a segment in the integration flow. The name of an activity describes its purpose.

 All activities are inherited from the same class `TaxIntegrationAbstractActivity`. There are three kinds of activities:
 
 - `TaxIntegrationSequence`
 - `TaxIntegrationAbstractActivityOnDocument`
 - `TaxIntegrationAbstractActivityOnLine` 
 
 Each of these activities contain an `act` and an `actInternal` methods but accept different arguments. However, `TaxIntegrationAbstractActivityOnDocument` and `TaxIntegrationAbstractActivityOnLine` are intended to be extended. They are implemented as an `abstract` class with an `internal` `act` method and an `abstract` `actInternal` method. So, a new activity should extend one of these two abstract classes. The activity should implement its own `actInternal` method to hold the real logic of the activity. If the activity is not applicable for all transactions/documents, it should implement its own `shouldSkip` method. `TaxIntegrationSequence` is intended to be used directly, and it's implemented as a concrete class with a `public` `act` method.
 
 All three activities log events during the `act` method if necessary after `TaxIntegrationLogLevelUtility` is checked, with the logging context inherited from `TaxIntegrationAbstractActivity`. The following graphic shows the hierarchy of activities.

![activity hierarchy.png](./media/tax-integration-activity-hierarchy.png)

For more information about adding a new activity, see [How to add an activity in tax integration](./tax-integration-how-to-add-an-activity.md).

### Sequence

`TaxIntegrationSequence` is a special activity.

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

A new document activity should implement the `actInternal` method to hold the logic of this activity. `actInternal` accepts a `TaxIntegrationDocumentObject` as input so it can manipulate data on the document level, which can't be done by a line activity. However, a document activity can also act on `TaxIntegrationLineObject` by enumerating the `TaxIntegrationDocumentObject`. Most document activities are handling data both on document and line levels. If an activity isn't applicable for all transactions and documents, the activity should implement its own `shouldSkip` method.

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

New line activity should implement the `actInternal` method to hold the logic of this activity. `actInternal` accepts a `TaxIntegrationLineObject` as input and can only manipulate data on the line object given. However, charges are also described as a `TaxIntegrationLineObject`, so charges will also be processed by line activity. If an activity isn't applicable for **all lines** in the document, it should implement its own `shouldSkip` method. The `shouldSkip` method indicates whether the current activity should be skipped for **all lines** (including charges) in the document since it accepts a `TaxIntegrationDocumentObject` as input.

### Current activites

Here is the list of current activities, in the order of `TaxIntegrationFacade::calculate`:

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
