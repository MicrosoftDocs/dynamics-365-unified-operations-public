---
title: Dimension defaulting - Part 6 (Common pattern APIs)
author: jasonsto
---

**Introduction**

Continuing this series of blog posts, this post describes APIs used for most
common defaulting patterns.

This blog post series includes:

-   [Financial dimensions discovery](dimension-defaulting-part1.md)

-   [Control uptake and storage](dimension-defaulting-part2.md)

-   [Copy patterns](dimension-defaulting-part3.md)

-   [Merging patterns](dimension-defaulting-part4.md)

-   [Ledger dimension creation](dimension-defaulting-part5.md)

-   Common pattern APIs (This post)

**Default dimension APIs**

The DimensionDefaultFacade and LedgerDimensionDefaultFacade classes provide the APIs are needed for defaulting
scenarios. The The LedgerDimensionFacade class contains methods for working with ledger dimensions. The methods are highly optimized for
performance.

**Default dimensions**

The *serviceMergeDefaultDimensions()* API is the most commonly used API for
default dimensions. It should be called whenever a new default dimension needs
to be created from 2 to 4 other default dimensions. If more default dimensions
need to be merged than 4, it can be called multiple times with the result of the
prior call used as the first parameter to the subsequent call. This method will 
blindly merge all values whether they are valid or not.

```
public static DimensionDefault serviceMergeDefaultDimensions(
        DimensionDefault _value1,
        DimensionDefault _value2,
        DimensionDefault _value3 = 0,
        DimensionDefault _value4 = 0)
```
**Figure 1: DimensionDefaultFacade::serviceMergeDefaultDimensions()**

The *serviceReplaceAttributeValue()* API is useful in the case that a single
dimension value needs to be copied from one default to another default set. The
value specified will replace whatever value already exists in the source set.

```
public static DimensionDefault serviceReplaceAttributeValue(
        DimensionDefault _target,
        DimensionDefault _source,
        RecId _dimensionAttributeId)
```
**Figure 2: DimensionDefaultFacade::serviceReplaceAttributeValue()** 

The *serviceMergeValidDefaultDimensions* API is useful in the case where you 
want the merge to only merge values that are valid for the current ledger. 
It works exactly the same as *serviceMergeDefaultDimensions* but with the added 
check for valid values.

```
    public static DimensionDefault serviceMergeValidDefaultDimensions(
        DimensionDefault _defaultDimension1,
        DimensionDefault _defaultDimension2,
        DimensionDefault _defaultDimension3 = 0,
        DimensionDefault _defaultDimension4 = 0)
```
**Figure 3: DimensionDefaultFacade::serviceReplaceAttributeValue()** 

**Ledger dimensions**

The *serviceCreateLedgerDimension()* API is the most commonly used API for
ledger dimensions. It should be called whenever a new ledger account combination
needs to be created from a default account or existing ledger account
combination and 0 to 3 default dimensions. If more default dimensions need to be
merged than 3, it can be called multiple times with different sources taking the
result of the prior call as the first parameter to the subsequent call. The
MainAccount dimension is only retrieved from the supplied ledger dimension.

```
public static LedgerDimensionAccount serviceCreateLedgerDimension(
        RecId            _ledgerDimensionId,
        DimensionDefault _dimensionDefault1 = 0,
        DimensionDefault _dimensionDefault2 = 0,
        DimensionDefault _dimensionDefault3 = 0)
    {
```
**Figure 4: LedgerDimensionFacade.serviceCreateLedgerDimension()**

The *serviceCreateLedgerDimensionForType()* API is similar to the previous API
but rather than creating a ledger account combination, it can create other
ledger dimension types such as budget accounts or budget planning accounts
specified by the LedgerDimensionType parameter.
```
 public static LedgerDimensionBase serviceCreateLedgerDimensionForType(
        LedgerDimensionType _ledgerDimensionType,
        LedgerDimensionBase _ledgerDimensionId,
        DimensionDefault    _dimensionDefault1 = 0,
        DimensionDefault    _dimensionDefault2 = 0,
        DimensionDefault    _dimensionDefault3 = 0)
```
**Figure 5: LedgerDimensionFacade.serviceCreateLedgerDimensionForType()**

The *serviceCreateLedgerDimForDefaultDim()* API is similar to the previous APIs,
but the values from the default dimension are copied directly to the new ledger
dimension, while the dimension values from the ledger dimension are merged
afterwards. In the previous APIs, the ledger dimension values were copied, and
the default dimension values were merged.
```
public static LedgerDimensionBase serviceCreateLedgerDimForDefaultDim(
        DimensionDefault    _defaultDimension,
        LedgerDimensionBase _ledgerDimensionId)![\\\\blackwoodstone\\share\\Research\\GFMBlog2\\media\\MSDNBlogsFS\\prod.evol.blogs.msdn.com\\CommunityServer.Blogs.Components.WeblogFiles\\00\\00\\01\\50\\86\\5710.c65.png](media/146d284328279f4737c6e2bd23a30530.png)
```
**Figure 6: LedgerDimensionFacade::serviceCreateLedgerDimForDefaultDim()**

The *serviceLedgerDimensionFromLedgerDims()* API is similar to the previous APIs
but uses only ledger dimensions as sources to construct a new ledger dimension.
The main account will only be retrieved from the first ledger dimension.
```
public static LedgerDimensionAccount serviceLedgerDimensionFromLedgerDims(
        LedgerDimensionBase _ledgerDimensionId1,
        LedgerDimensionBase _ledgerDimensionId2 = 0,
        LedgerDimensionBase _ledgerDimensionId3 = 0,
        LedgerDimensionBase _ledgerDimensionId4 = 0,
        LedgerDimensionBase _ledgerDimensionId5 = 0)
```
**Figure 7: LedgerDimensionFacade::serviceLedgerDimensionFromLedgerDims()**

The *serviceMergeLedgerDimensions()* API is similar to the previous API but is
optimized to combine just 2 ledger dimensions. 

```
public static LedgerDimensionBase serviceMergeLedgerDimensions(
        LedgerDimensionBase _ledgerDimension1,
        LedgerDimensionBase _ledgerDimension2,
        LedgerDimensionType _ledgerDimensionType = LedgerDimensionType::Account)
```
**Figure 8: LedgerDimensionFacade::serviceMergeLedgerDimensions()**

The *serviceCreateLedgerDimFromLedgerDim()* API is useful when copying ledger
dimensions from a historic posted document onto a new unposted document to
ensure that it uses the current account structure configuration.  This will
avoid validation errors when validating the new ledger dimensions during
posting.

```
public static LedgerDimensionAccount serviceCreateLedgerDimFromLedgerDim(
	LedgerDimensionAccount _ledgerDimension)
```
**Figure 9: LedgerDimensionFacade::serviceCreateLedgerDimFromLedgerDim()**
