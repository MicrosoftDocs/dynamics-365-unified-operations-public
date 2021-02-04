---
# required metadata

title: How to add data fields in tax integration by extensions
description: This topic explains how to use X++ extensions to add data fields in tax integration.
author: qire
manager: beya
ms.date: 02/04/2021
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
# How to add data fields in tax integration by extension
This topic provides information about how to use X++ extensions to add data fields in tax integration. These fields can be extended to the tax data model of tax service for tax code determination, refer to [How to add field in tax configuration](tax-service-how-to-add-data-fields-in-tax-configurations.md) for more details.
Following sections are covered to show the principle and practice of tax service integration.

- Data model
- Integration flow 
- Extension implementation detail

## Data model
Firstly, introduce the data model for tax service integration. The data is _carried_ by objects, implemented by classes.

The major objects:
* AxClass/TaxIntegration**Document**Object
* AxClass/TaxIntegration**Line**Object
* AxClass/TaxIntegration**TaxLine**Object
  

The relationship of these objects is like:
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
> [!Note]
>
> **Charge** is also implemented by `TaxIntegrationLineObject`.  Here, it focuses on **Document** and **Line** objects.

Basically, a **Document** object may contains many **Line** object. Each object contains metadata for tax service.

- For `TaxIntegrationDocumentObject`, it has `originAddress`(contains the source address info), `includingTax`(indicates line amount include sales tax or not) and so on.

- For `TaxIntegrationLineObject`, it has `itemId`, `quantity`, `categoryId`, etc.


## Integration flow
The data in the flow is manipulated by activities.

### Key activities

* AxClass/TaxIntegration**Calculation**ActivityOnDocument
* AxClass/TaxIntegration**CurrencyExchange**ActivityOnDocument
* AxClass/TaxIntegration**DataPersistence**ActivityOnDocument
* AxClass/TaxIntegration**DataRetrieval**ActivityOnDocument
* AxClass/TaxIntegration**SettingRetrieval**ActivityOnDocument

They are executed in below order:
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
Example, extend **Data Retrieval** and **Calculation Service**.

#### Data Retrieval

The data is retrieved from database by **Data Retrieval** activities.  Adapters for different transactions are available to retrieve data from different transaction tables:

- AxClass/TaxIntegration**PurchTable**DataRetrieval
- AxClass/TaxIntegration**PurchParmTable**DataRetrieval
- AxClass/TaxIntegration**PurchREQTable**DataRetrieval
- AxClass/TaxIntegration**PurchRFQTable**DataRetrieval
- AxClass/TaxIntegration**VendInvoiceInfoTable**DataRetrieval
- AxClass/TaxIntegration**SalesTable**DataRetrieval
- AxClass/TaxIntegration**SalesParm**DataRetrieval

In these **Data Retrieval** activities, data get copied from database to `TaxIntegrationDocumentObject` and `TaxIntegrationLineObject`. All these activities extends same abstract template class, so they have common methods.

#### Calculation Service
**Calculation Service** activity is the link between **tax service** and **tax integration**. It is responsible for below functions:
1. Construct the request
2. Post the request to **tax service**
3. Get the response from **tax service**
4. Parse the response

Add the data field to the request and it will be posted along with other metadata. 

## Extension implementation
This section introduces the detail steps of the extension implementation practice. Take two financial dimensions (**Cost center** and **Project**) as example.
### 1. Add data variable in **Object** class
The object class contains the data variable and getter/setter method for the data. Based on the data field level, add the field to `TaxIntegrationDocumentObject` or `TaxIntegrationLineObject`. Take line level as example, in the `TaxIntegrationLineObject_Extension.xpp`:
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
**Cost center** and **Project** shall be added as private variables. Create getter and setter for these data fields to manipulate these data.

> [!Note]
>
> In case the fields to be added are at document level, simply change the file name to `TaxIntegrationDocuementObject_Extension`

### 2. Retrieve data from database
Specify the transaction and extend the respective adapter classes to retrieve data. Take **Purchase order** transaction as example, you need to extend `TaxIntegrationPurchTableDataRetrieval`, `TaxIntegrationVendInvoiceInfoTableDataRetrieval`. 

> [!Note]
>
> `TaxIntegrationPurchParmTableDataRetrieval` is inherited from `TaxIntegrationPurchTableDataRetrieval`. It should not be modified unless the logic is really different between `purchTable` and `purchParmTable`.

If the data field is to be added for all transactions, all `DataRetrieval` classes need to be extended.

All **Data Retrieval** activates extend same template class, so the class structures, variables and methods are similar.
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
Take `PurchTable` as example. The basic structure as follows.
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
When `CopyToDocument` is called, we already have the `this.purchTable` buffer. And our aim in this method is to copy all the data we need from `this.purchTable` to `document` object by the `setter` method we already created in `DocumentObject` class.

Similarly, in `CopyToLine` method, we already have a `this.purchLine` buffer. And our aim in this method is to copy all the data we need from `this.purchLine` to `_line` object by the `setter` method we already created in `LineObject` class.

The most straight forward practice is to extend `CopyToDocument` and `CopyToLine`, but we still recommend to try `copyToDocumentFromHeaderTable` and `copyToLineFromLineTable` first. If these cannot satisfy you, you can implement your own method, and call it in `CopyToDocument` and `CopyToLine`. There are 3 common circumstances:
1. If the field we need is right at `PurchTable` or `PurchLine`, we could simply extend `copyToDocumentFromHeaderTable` and `copyToLineFromLineTable`. Sample code as follows.

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
2. The data we need is not at the default table of the transaction, but have some join relationship with the default table and we indeed need this field in most line. In this case we could replace the `getDocumentQueryObject` or `getLineObject` to query the table we want by join relationship. Here is an example from Sales Order, to integrate **Deliver Now** field to Sales Order at line level.

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

3. If the data we want is related to transaction table by complicated join relationship or the relation is not 1:1 but 1:N. Things become little complicated. And this is the case we need to handle for the example **financial dimensions**. 
   
    In this case, we could implement our own method to retrieve the data. Here is the sample code in `TaxIntegrationPurchTableDataRetrieval_Extension.xpp`
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
Extend `copyToTaxableDocumentHeaderWrapperFromTaxIntegrationDocumentObject` or `copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine` methods to add data to the request. Below is example code in `TaxIntegrationCalculationActivityOnDocument_CalculationService_Extension.xpp`:
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
The `_destination` is wrapper object used to generate the post request. And `_source` is the `TaxIntegrationLineObject`. 

> [!Note]
>
> * Define the `key` used in request form as `private const str`.
> * Set the field in `copyToTaxableDocumentLineWrapperFromTaxIntegrationLineObjectByLine` method by `SetField` method. Note that the second parameter should be `string` type. If the data type is not string, please convert it to string.
>

## Appendix
Complete sample code for integration of financial dimensions (**Cost center** and **Project**) at line level.

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
