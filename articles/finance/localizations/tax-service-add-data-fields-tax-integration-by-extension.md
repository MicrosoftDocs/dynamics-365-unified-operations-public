---
# required metadata

title: Add data fields in tax integration by extensions
description: This topic explains how to use X++ extensions to add data fields in tax integration.
author: qire
manager: tfehr
ms.date: 03/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18
---

# Add data fields in tax integration by extension

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides information about how to use X++ extensions to add data fields in tax integration. These fields can be extended to the tax data model of tax service for tax code determination. For more information, see [Add fields in tax configuration](tax-service-add-data-fields-tax-configurations.md).

The following sections in this topic show the principle and practice of tax service integration.

- Data model
- Integration flow 
- Extension implementation detail

## Data model
The data in the data model is _carried_ by objects, implemented by classes.

The major objects:
* AxClass/TaxIntegration**Document**Object
* AxClass/TaxIntegration**Line**Object
* AxClass/TaxIntegration**TaxLine**Object
  

The relationship of these objects is:
```
┏━━━━━━━━━━┓       ┏━━━━━━━━━━┓1  0..n┏━━━━━━━━━━┓1  0..n┏━━━━━━━━━━┓
┃          ┃       ┃          ┃⯁────ᗒ┃  Charge  ┃⯁────ᗒ┃ Tax Line ┃
┃          ┃1  0..n┃   Line   ┃       ┗━━━━━━━━━━┛       ┗━━━━━━━━━━┛
┃          ┃⯁────ᗒ┃          ┃1  0..n┏━━━━━━━━━━┓
┃ Document ┃       ┃          ┃⯁────ᗒ┃ Tax Line ┃
┃          ┃       ┗━━━━━━━━━━┛       ┗━━━━━━━━━━┛
┃          ┃1  0..n┏━━━━━━━━━━┓1  0..n┏━━━━━━━━━━┓
┃          ┃⯁────ᗒ┃  Charge  ┃⯁────ᗒ┃ Tax Line ┃
┗━━━━━━━━━━┛       ┗━━━━━━━━━━┛       ┗━━━━━━━━━━┛
```
> [!NOTE]
> **Charge** is also implemented by `TaxIntegrationLineObject` and focuses on **Document** and **Line** objects.

A **Document** object may contain many **Line** objects and each object contains metadata for the tax service.

- For `TaxIntegrationDocumentObject`, there is `originAddress` which contains the source address info and `includingTax`which indicates whether the line amount includes sales tax.
- For `TaxIntegrationLineObject`, it has `itemId`, `quantity`, and `categoryId`.


## Integration flow
The data in the flow is manipulated by activities.

### Key activities

* AxClass/TaxIntegration**Calculation**ActivityOnDocument
* AxClass/TaxIntegration**CurrencyExchange**ActivityOnDocument
* AxClass/TaxIntegration**DataPersistence**ActivityOnDocument
* AxClass/TaxIntegration**DataRetrieval**ActivityOnDocument
* AxClass/TaxIntegration**SettingRetrieval**ActivityOnDocument

Activities are executed in the following order:
```
             │
             ᗐ
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃     Setting Retrieval     ┃
┗━━━━━━━━━━━━┯━━━━━━━━━━━━━━┛
             │
             ᗐ
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃      Data Retrieval       ┃
┗━━━━━━━━━━━━┯━━━━━━━━━━━━━━┛
             │
             ᗐ               
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃    Calculation Service    ┃
┗━━━━━━━━━━━━┯━━━━━━━━━━━━━━┛
             │
             ᗐ
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃     Currency Exchange     ┃
┗━━━━━━━━━━━━┯━━━━━━━━━━━━━━┛
             │
             ᗐ
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃     Data Persistence      ┃
┗━━━━━━━━━━━━┯━━━━━━━━━━━━━━┛
             │
             ᗐ
```
For example, extend **Data Retrieval** and **Calculation Service**.

#### Data Retrieval

The data is retrieved from the database by **Data Retrieval** activities.  Adapters for different transactions are available to retrieve data from different transaction tables:

- AxClass/TaxIntegration**PurchTable**DataRetrieval
- AxClass/TaxIntegration**PurchParmTable**DataRetrieval
- AxClass/TaxIntegration**PurchREQTable**DataRetrieval
- AxClass/TaxIntegration**PurchRFQTable**DataRetrieval
- AxClass/TaxIntegration**VendInvoiceInfoTable**DataRetrieval
- AxClass/TaxIntegration**SalesTable**DataRetrieval
- AxClass/TaxIntegration**SalesParm**DataRetrieval

In these **Data Retrieval** activities, data is copied from the database to `TaxIntegrationDocumentObject` and `TaxIntegrationLineObject`. All these activities extend the same abstract template class, so they have common methods.

#### Calculation Service
The **Calculation Service** activity is the link between **tax service** and **tax integration**. This activity is responsible for the following functions:

1. Construct the request.
2. Post the request to **tax service**.
3. Get the response from **tax service**.
4. Parse the response.

Add the data field to the request and it will be posted with other metadata. 

## Extension implementation

This section provies the detailed steps of the extension implementation. Use the two financial dimensions, **Cost center** and **Project** as examples in these procedures.

### 1. Add data variable in **Object** class
The object class contains the data variable and getter/setter method for the data. Based on the data field level, add the field to `TaxIntegrationDocumentObject` or `TaxIntegrationLineObject`. Use the line level as an example, in the `TaxIntegrationLineObject_Extension.xpp`:
```X++
[ExtensionOf(classStr(TaxIntegrationLineObject))]
final class TaxIntegrationLineObject_Extension
{
    private OMOperatingUnitNumber costCenter;
    private ProjId projectId;

    /// <summary>
    /// Gets a costCenter.
    /// </summary>
    /// <returns>The cost center.</returns>
    public final OMOperatingUnitNumber getCostCenter()
    {
        return this.costCenter;
    }

    /// <summary>
    /// Sets the cost center.
    /// </summary>
    /// <param name = "_value">The cost center.</param>
    public final void setCostCenter(OMOperatingUnitNumber _value)
    {
        this.costCenter = _value;
    }

    /// <summary>
    /// Gets a project ID.
    /// </summary>
    /// <returns>The project ID.</returns>
    public final ProjId getProjectId()
    {
        return this.projectId;
    }

    /// <summary>
    /// Sets the project ID.
    /// </summary>
    /// <param name = "_value">The project ID.</param>
    public final void setProjectId(ProjId _value)
    {
        this.projectId = _value;
    }

}
```
**Cost center** and **Project** are added as private variables. Create getter and setter for these data fields to manipulate the data.

> [!NOTE]
> If the fields to be added are at the document level, change the file name to `TaxIntegrationDocuementObject_Extension`.

### 2. Retrieve data from the database
Specify the transaction and extend the respective adapter classes to retrieve the data. For example, if you use a **Purchase order** transaction, you need to extend `TaxIntegrationPurchTableDataRetrieval` and `TaxIntegrationVendInvoiceInfoTableDataRetrieval`. 

> [!NOTE]
> `TaxIntegrationPurchParmTableDataRetrieval` is inherited from `TaxIntegrationPurchTableDataRetrieval` and shouldn't be modified unless the logic is different between `purchTable` and `purchParmTable`.

If the data field should be added for all transactions, extend all `DataRetrieval` classes.

All **Data Retrieval** activates extend same template class, so the class structures, variables, and methods are similar.
```X++
    protected TaxIntegrationDocumentObject document;

    /// <summary>
    /// Copies to the document.
    /// </summary>
    protected abstract void copyToDocument()
    {
        // It is recommended to implemented as:
        //
        // this.copyToDocumentByDefault();
        // this.copyToDocumentFromHeaderTable();
        // this.copyAddressToDocument();
    }
 
    /// <summary>
    /// Copies to the current line of the document.
    /// </summary>
    /// <param name = "_line">The current line of the document.</param>
    protected abstract void copyToLine(TaxIntegrationLineObject _line)
    {
        // It is recommended to implemented as:
        //
        // this.copyToLineByDefault(_line);
        // this.copyToLineFromLineTable(_line);
        // this.copyQuantityAndTransactionAmountToLine(_line);
        // this.copyAddressToLine(_line);
        // this.copyToLineFromHeaderTable(_line);
    }
```
Using `PurchTable` as an example, the basic structure is:
```X++
public class TaxIntegrationPurchTableDataRetrieval extends TaxIntegrationAbstractDataRetrievalTemplate
{
    protected PurchTable purchTable;
    protected PurchLine purchLine;

    // Query builder methods
    [Replaceable]
    protected SysDaQueryObject getDocumentQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineQueryObject()
    [Replaceable]
    protected SysDaQueryObject getDocumentChargeQueryObject()
    [Replaceable]
    protected SysDaQueryObject getLineChargeQueryObject()

    // Data retrieval methods
    protected void copyToDocument()
    protected void copyToDocumentFromHeaderTable()
    protected void copyToLine(TaxIntegrationLineObject _line)
    protected void copyToLineFromLineTable(TaxIntegrationLineObject _line)
    ...
}
```
When `CopyToDocument` is called, there is already the `this.purchTable` buffer. The goal of this method is to copy all the necessary data from `this.purchTable` to the `document` object by using the `setter` method created in `DocumentObject` class.

Similarly, in the `CopyToLine` method, we already have a `this.purchLine` buffer. The goal of  this method is to copy all the necessary data from `this.purchLine` to the `_line` object by using the `setter` method created in `LineObject` class.

The most straight forward practice is to extend `CopyToDocument` and `CopyToLine`, however it is still recommened to try `copyToDocumentFromHeaderTable` and `copyToLineFromLineTable` first. If these don't work as needed, implement your own method, and call it in `CopyToDocument` and `CopyToLine`. There are three common circumstances:

- If the necessary field is right at `PurchTable` or `PurchLine`, you could extend `copyToDocumentFromHeaderTable` and `copyToLineFromLineTable`. The sample code is:

```X++
	/// <summary>
	/// Copies to the current line of the document from.
	/// </summary>
	/// <param name = "_line">The current line of the document.</param>
	protected void copyToLineFromLineTable(TaxIntegrationLineObject _line)
	{
		next copyToLineFromLineTable(_line);
		// if we already added XXX in TaxIntegrationLineObject
		_line.setXXX(this.purchLine.XXX);
	}
```
- The necessary data isn't at the default table of the transaction, but there are some join relationship with the default table and this field is needed in most lines. In this situation, replace the `getDocumentQueryObject` or `getLineObject` to query the table by join relationship. The following is an example of integrating the **Deliver Now** field to the sales order at the line level.

~~~X++
public class TaxIntegrationSalesTableDataRetrieval
{
	protected MCRSalesLineDropShipment mcrSalesLineDropShipment;

	/// <summary>
	/// Gets the query for the lines of the document.
	/// </summary>
	/// <returns>The query for the lines of the document</returns>
	[Replaceable]
	protected SysDaQueryObject getLineQueryObject()
	{
		return SysDaQueryObjectBuilder::from(this.salesLine)
			.where(this.salesLine, fieldStr(SalesLine, SalesId)).isEqualToLiteral(this.salesTable.SalesId)
			.outerJoin(this.mcrSalesLineDropShipment)
			.where(this.mcrSalesLineDropShipment, fieldStr(MCRSalesLineDropShipment, SalesLine)).isEqualTo(this.salesLine, fieldStr(SalesLine, RecId))
			.toSysDaQueryObject();
	}
}
```
We declare a mcrSalesLineDropShipment buffer, and define the query at `getLineQueryObject`, by the relationship that `MCRSalesLineDropShipment.SalesLine == SalesLine.RecId`. While extending in this circumstance, we can replace this `getLineQueryObject` by our own constructed query object. Just need to note 2 points:
* The return value of this method is SysDaQueryObject, we need to construct this object by the SysDa way.
* Cannot remove existed table.
~~~

- If the necessary data is related to the transaction table by a complicated join relationship, or the relation is not 1:1 but 1:N, things become little complicated. This is the situtation for the example of **financial dimensions**. 
   
    In this case, you can implement your own method to retrieve the data. The following is the sample code in `TaxIntegrationPurchTableDataRetrieval_Extension.xpp`.
    ```X++
    [ExtensionOf(classStr(TaxIntegrationPurchTableDataRetrieval))]
    final class TaxIntegrationPurchTableDataRetrieval_Extension
    {
        private const str CostCenterKey = 'CostCenter';
        private const str ProjectKey = 'Project';

        /// <summary>
        /// Copies to the current line of the document from.
        /// </summary>
        /// <param name = "_line">The current line of the document.</param>
        protected void copyToLineFromLineTable(TaxIntegrationLineObject _line)
        {
            Map dimensionAttributeMap = this.getDimensionAttributeMapByDefaultDimension(this.purchline.DefaultDimension);
            if (dimensionAttributeMap.exists(CostCenterKey))
            {
                _line.setCostCenter(dimensionAttributeMap.lookup(CostCenterKey));
            }
            if (dimensionAttributeMap.exists(ProjectKey))
            {
                _line.setProjectId(dimensionAttributeMap.lookup(ProjectKey));
            }
            next copyToLineFromLineTable(_line);
        }

        private Map getDimensionAttributeMapByDefaultDimension(RefRecId _defaultDimension)
        {
            DimensionAttribute dimensionAttribute;
            DimensionAttributeValue dimensionAttributeValue;
            DimensionAttributeValueSetItem dimensionAttributeValueSetItem;
            Map ret = new Map(Types::String, Types::String);

            select Name, RecId from dimensionAttribute
                join dimensionAttributeValue
                    where dimensionAttributeValue.dimensionAttribute == dimensionAttribute.RecId
                join DimensionAttributeValueSetItem
                    where DimensionAttributeValueSetItem.DimensionAttributeValue == DimensionAttributeValue.RecId
                        && DimensionAttributeValueSetItem.DimensionAttributeValueSet == _defaultDimension;

            while(dimensionAttribute.RecId)
            {
                ret.insert(dimensionAttribute.Name, dimensionAttributeValue.DisplayValue);
                next dimensionAttribute;
            }
            return ret;
        }

    }
    ```
### 3. Add data to the request
Extend the methods `copyToTaxableDocumentHeaderWrapperFromTaxIntegrationDocumentObject` or `copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine` to add data to the request. The following is the sample code in `TaxIntegrationCalculationActivityOnDocument_CalculationService_Extension.xpp`.
```X++
[ExtensionOf(classStr(TaxIntegrationCalculationActivityOnDocument_CalculationService))]
final static class TaxIntegrationCalculationActivityOnDocument_CalculationService_Extension
{
    // Define key for the form in post request
    private const str IOCostCenter = 'Cost Center';
    private const str IOProject = 'Project';

    /// <summary>
    /// Copies to <c>TaxableDocumentLineWrapper</c> from <c>TaxIntegrationLineObject</c> by line.
    /// </summary>
    /// <param name = "_destination"><c>TaxableDocumentLineWrapper</c>.</param>
    /// <param name = "_source"><c>TaxIntegrationLineObject</c>.</param>
    protected static void copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(Microsoft.Dynamics.TaxCalculation.ApiContracts.TaxableDocumentLineWrapper _destination, TaxIntegrationLineObject _source)
    {
		next copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(_destination, _source);
		// Set the field we need to integrated for tax service
        _destination.SetField(IOCostCenter, _source.getCostCenter());
        _destination.SetField(IOProject, _source.getProjectId());
    }

}
```
The `_destination` is the wrapper object used to generate the post request and `_source` is the `TaxIntegrationLineObject`. 

> [!NOTE]
> * Define the `key` used in the request form as `private const str`.
> * Set the field in the `copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine` method by using the `SetField` method. The second parameter should be `string` type. If the data type is not string, convert it to string.
>

## Appendix
The following is the complete sample code for financial dimensions integration (**Cost center** and **Project**) at the line level.

`TaxIntegrationLineObject_Extension.xpp`:

```X++
[ExtensionOf(classStr(TaxIntegrationLineObject))]
final class TaxIntegrationLineObject_Extension
{
    private OMOperatingUnitNumber costCenter;
    private ProjId projectId;

    /// <summary>
    /// Gets a costCenter.
    /// </summary>
    /// <returns>The cost center.</returns>
    public final OMOperatingUnitNumber getCostCenter()
    {
        return this.costCenter;
    }

    /// <summary>
    /// Sets the cost center.
    /// </summary>
    /// <param name = "_value">The cost center.</param>
    public final void setCostCenter(OMOperatingUnitNumber _value)
    {
        this.costCenter = _value;
    }

    /// <summary>
    /// Gets a project ID.
    /// </summary>
    /// <returns>The project ID.</returns>
    public final ProjId getProjectId()
    {
        return this.projectId;
    }

    /// <summary>
    /// Sets the project ID.
    /// </summary>
    /// <param name = "_value">The project ID.</param>
    public final void setProjectId(ProjId _value)
    {
        this.projectId = _value;
    }

}
```

`TaxIntegrationPurchTableDataRetrieval_Extension.xpp`:
```X++
[ExtensionOf(classStr(TaxIntegrationPurchTableDataRetrieval))]
final class TaxIntegrationPurchTableDataRetrieval_Extension
{
    private const str CostCenterKey = 'CostCenter';
    private const str ProjectKey = 'Project';

    /// <summary>
    /// Copies to the current line of the document from.
    /// </summary>
    /// <param name = "_line">The current line of the document.</param>
    protected void copyToLineFromLineTable(TaxIntegrationLineObject _line)
    {
        Map dimensionAttributeMap = this.getDimensionAttributeMapByDefaultDimension(this.purchline.DefaultDimension);
        if (dimensionAttributeMap.exists(CostCenterKey))
        {
            _line.setCostCenter(dimensionAttributeMap.lookup(CostCenterKey));
        }
        if (dimensionAttributeMap.exists(ProjectKey))
        {
            _line.setProjectId(dimensionAttributeMap.lookup(ProjectKey));
        }
        next copyToLineFromLineTable(_line);
    }

    private Map getDimensionAttributeMapByDefaultDimension(RefRecId _defaultDimension)
    {
        DimensionAttribute dimensionAttribute;
        DimensionAttributeValue dimensionAttributeValue;
        DimensionAttributeValueSetItem dimensionAttributeValueSetItem;
        Map ret = new Map(Types::String, Types::String);

        select Name, RecId from dimensionAttribute
            join dimensionAttributeValue
                where dimensionAttributeValue.dimensionAttribute == dimensionAttribute.RecId
            join DimensionAttributeValueSetItem
                where DimensionAttributeValueSetItem.DimensionAttributeValue == DimensionAttributeValue.RecId
                    && DimensionAttributeValueSetItem.DimensionAttributeValueSet == _defaultDimension;

        while(dimensionAttribute.RecId)
        {
            ret.insert(dimensionAttribute.Name, dimensionAttributeValue.DisplayValue);
            next dimensionAttribute;
        }
        return ret;
    }

}
```

`TaxIntegrationCalculationActivityOnDocument_CalculationService_Extension.xpp`:
```X++
[ExtensionOf(classStr(TaxIntegrationCalculationActivityOnDocument_CalculationService))]
final static class TaxIntegrationCalculationActivityOnDocument_CalculationService_Extension
{
	// Define key for the form in post request
    private const str IOCostCenter = 'Cost Center';
    private const str IOProject = 'Project';

    /// <summary>
    /// Copies to <c>TaxableDocumentLineWrapper</c> from <c>TaxIntegrationLineObject</c> by line.
    /// </summary>
    /// <param name = "_destination"><c>TaxableDocumentLineWrapper</c>.</param>
    /// <param name = "_source"><c>TaxIntegrationLineObject</c>.</param>
    protected static void copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(Microsoft.Dynamics.TaxCalculation.ApiContracts.TaxableDocumentLineWrapper _destination, TaxIntegrationLineObject _source)
    {
		next copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine(_destination, _source);
		// Set the field we need to integrated for tax service
        _destination.SetField(IOCostCenter, _source.getCostCenter());
        _destination.SetField(IOProject, _source.getProjectId());
    }

}
```
