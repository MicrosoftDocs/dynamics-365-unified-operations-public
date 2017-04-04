---
# required metadata

title: Retail Server customer and consumer APIs
description: This article provides an overview of the APIs that are available across various roles, and that can be used by various clients. The focus is on customer-facing application clients and eCommerce clients.
author: robinr
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 84383
ms.assetid: c60de19f-06e5-4e57-8956-7fd17c460e52
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Retail Server customer and consumer APIs

This article provides an overview of the APIs that are available across various roles, and that can be used by various clients. The focus is on customer-facing application clients and eCommerce clients.

Overview
--------

-   Retail Server business data and operations are available to any connected device through the OData Web API, across both employee (point of sale) scenarios and customer (online store) scenarios.
-   The embedded commerce runtime (CRT) enables a unified omni-channel platform.
-   The application programming interfaces (APIs) are stateless and can process requests from many channels.
-   The APIs have a linear scale-out model (“brick” scale-out).
-   You use a composition pattern for plug-and-play customizations.
-   The APIs are built on the .NET stack by using C\#.

## Roles
Every request to Retail Server (via retail proxy) operates under three main roles:

-   CommerceRole.Employee
-   CommerceRole.Anonymous
-   CommerceRole.Customer

The Anonymous and Customer roles apply to eCommerce (customer/consumer) scenarios. The Anonymous role is used for requests that represent an eCommerce customer who hasn't signed in. The Customer role is used for requests that represent an eCommerce customer who has been authenticated and has signed in. A role filter is applied to every API that is exposed in Retail Server. For eCommerce scenarios, you can use only APIs that have either CommerceRole.Anonymous or CommerceRole.Customer associated with them.

### APIs that are available for an authenticated customer role

#### CartManager APIs

-   Task&lt;SalesOrder&gt; CartManager.Checkout(String id, String receiptEmail, TokenizedPaymentCard tokenizedPaymentCard, String receiptNumberSequence, IEnumerable&lt;CartTenderLine&gt; cartTenderLines)
-   Task&lt;Cart&gt; CartManager.Copy(String id, Int32 targetCartType)
-   Task&lt;Cart&gt; CartManager.AddCartLines(String id, IEnumerable&lt;CartLine&gt; cartLines)
-   Task&lt;Cart&gt; CartManager.UpdateCartLines(String id, IEnumerable&lt;CartLine&gt; cartLines)
-   Task&lt;CartDeliveryPreferences&gt; CartManager.GetDeliveryPreferences(String id)
-   Task&lt;PagedResult&lt;SalesLineDeliveryOption&gt;&gt; CartManager.GetLineDeliveryOptions(String id, IEnumerable&lt;String&gt; cartLineIds, Address shippingAddress, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;DeliveryOption&gt;&gt; CartManager.GetDeliveryOptions(String id, Address shippingAddress, QueryResultSettings queryResultSettings)
-   Task&lt;Cart&gt; CartManager.UpdateLineDeliverySpecifications(String id, IEnumerable&lt;LineDeliverySpecification&gt; lineDeliverySpecifications)
-   Task&lt;Cart&gt; CartManager.UpdateDeliverySpecification(String id, DeliverySpecification deliverySpecification)
-   Task&lt;PagedResult&lt;Product&gt;&gt; CartManager.GetProductsInCart(String id, QueryResultSettings queryResultSettings)
-   Task&lt;CartPromotions&gt; CartManager.GetPromotions(String id)
-   Task&lt;Cart&gt; CartManager.AddDiscountCode(String id, String discountCode)
-   Task&lt;Cart&gt; CartManager.RemoveDiscountCodes(String id, IEnumerable&lt;String&gt; discountCodes)
-   Task&lt;Cart&gt; CartManager.RemoveCartLines(String id, IEnumerable&lt;String&gt; cartLineIds)
-   Task&lt;PagedResult&lt;Cart&gt;&gt; CartManager.Search(CartSearchCriteria cartSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;CardPaymentAcceptPoint&gt; CartManager.GetCardPaymentAcceptPoint(String id, CardPaymentAcceptSettings cardPaymentAcceptSettings)
-   Task&lt;CardPaymentAcceptResult&gt; CartManager.RetrieveCardPaymentAcceptResult(String resultAccessCode)
-   Task&lt;Cart&gt; CartManager.Read(String id, ICollection&lt;String&gt; expandProperties)
-   Task&lt;Cart&gt; CartManager.Update(Cart entity)
-   Task&lt;Cart&gt; CartManager.Create(Cart entity)CartsController.GetEntityByKey()

#### ProductCatalogManager and CategoryManager APIs

-   Task&lt;PagedResult&lt;ProductCatalog&gt;&gt; ProductCatalogManager.GetCatalogs(Int64 channelId, Boolean activeOnly, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;Category&gt;&gt; CategoryManager.GetCategories(Int64 channelId, QueryResultSettings queryResultSettings)

#### CommerceList and CommerceListManager APIs

-   Task&lt;PagedResult&lt;CommerceList&gt;&gt; CommerceListManager.GetByCustomer(String customerId, QueryResultSettings queryResultSettings)
-   Task&lt;CommerceList&gt; CommerceListManager.AddLines(Int64 id, IEnumerable&lt;CommerceListLine&gt; commerceListLines)
-   Task&lt;CommerceList&gt; CommerceListManager.UpdateLines(Int64 id, IEnumerable&lt;CommerceListLine&gt; commerceListLines)
-   Task&lt;CommerceList&gt; CommerceListManager.RemoveLines(Int64 id, IEnumerable&lt;CommerceListLine&gt; commerceListLines)
-   Task&lt;CommerceList&gt; CommerceListManager.MoveLines(IEnumerable&lt;CommerceListLine&gt; commerceListLines, Int64 destinationId)
-   Task&lt;CommerceList&gt; CommerceListManager.CopyLines(IEnumerable&lt;CommerceListLine&gt; commerceListLines, Int64 destinationId)
-   Task&lt;CommerceList&gt; CommerceListManager.AddContributors(Int64 id, IEnumerable&lt;CommerceListContributor&gt; commerceListContributors)
-   Task&lt;CommerceList&gt; CommerceListManager.RemoveContributors(Int64 id, IEnumerable&lt;CommerceListContributor&gt; commerceListContributors)
-   Task&lt;CommerceList&gt; CommerceListManager.CreateInvitations(Int64 id, IEnumerable&lt;CommerceListInvitation&gt; commerceListInvitations)
-   Task CommerceListManager.AcceptInvitation(String invitationToken, String customerId)
-   Task&lt;CommerceList&gt; CommerceListManager.Read(Int64 id, ICollection&lt;String&gt; expandProperties)
-   Task&lt;CommerceList&gt; CommerceListManager.Create(CommerceList entity)
-   Task&lt;CommerceList&gt; CommerceListManager.Update(CommerceList entity)
-   Task CommerceListManager.Delete(CommerceList entity)

#### CustomerManager APIs

-   Task&lt;PagedResult&lt;SalesOrder&gt;&gt; CustomerManager.GetOrderHistory(String accountNumber, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;PurchaseHistory&gt;&gt; CustomerManager.GetPurchaseHistory(String accountNumber, QueryResultSettings queryResultSettings)
-   Task&lt;Customer&gt; CustomerManager.Read(String accountNumber, ICollection&lt;String&gt; expandProperties)
-   Task&lt;Customer&gt; CustomerManager.Update(Customer entity)

#### StoreOperationsManager and OrgUnitManager APIs

-   Task&lt;PagedResult&lt;CardTypeInfo&gt;&gt; StoreOperationsManager.GetCardTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;String&gt;&gt; StoreOperationsManager.GetSupportedPaymentCardTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;CountryRegionInfo&gt;&gt; StoreOperationsManager.GetCountryRegionsByLanguageId(String languageId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;DeliveryOption&gt;&gt; StoreOperationsManager.GetDeliveryOptions(QueryResultSettings queryResultSettings)
-   Task&lt;GiftCard&gt; StoreOperationsManager.GetGiftCard(String giftCardId)
-   Task&lt;LinkToExistingCustomerResult&gt; StoreOperationsManager.InitiateLinkToExistingCustomer(String email, String activationToken, String emailTemplateId, IEnumerable&lt;NameValuePair&gt; emailProperties)
-   Task StoreOperationsManager.UnlinkFromExistingCustomer()
-   Task&lt;LoyaltyCard&gt; StoreOperationsManager.IssueLoyaltyCard(LoyaltyCard loyaltyCard)
-   Task&lt;LoyaltyCard&gt; StoreOperationsManager.GetLoyaltyCard(String cardNumber)
-   Task&lt;PagedResult&lt;LoyaltyCard&gt;&gt; StoreOperationsManager.GetCustomerLoyaltyCards(String accountNumber, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;LoyaltyCardTransaction&gt;&gt; StoreOperationsManager.GetLoyaltyCardTransactions(String cardNumber, String rewardPointId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;StateProvinceInfo&gt;&gt; StoreOperationsManager.GetStateProvinces(String countryRegionId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;TenderType&gt;&gt; StoreOperationsManager.GetTenderTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnit&gt;&gt; OrgUnitManager.ReadAll(QueryResultSettings queryResultSettings, ICollection&lt;String&gt; expandProperties)
-   Task&lt;PagedResult&lt;OrgUnitLocation&gt;&gt; OrgUnitManager.GetOrgUnitLocationsByArea(SearchArea searchArea, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnitAvailability&gt;&gt; OrgUnitManager.GetAvailableInventory(String itemId, String variantId, String barcode, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnitAvailability&gt;&gt; OrgUnitManager.GetAvailableInventoryNearby(IEnumerable&lt;ItemUnit&gt; itemIds, SearchArea searchArea, QueryResultSettings queryResultSettings)
-   Task&lt;TillLayout&gt; OrgUnitManager.GetTillLayout()
-   Task&lt;ChannelConfiguration&gt; OrgUnitManager.GetOrgUnitConfiguration()
-   Task&lt;PagedResult&lt;OrgUnit&gt;&gt; OrgUnitManager.Search(SearchStoreCriteria storeSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;OrgUnit&gt; OrgUnitManager.Read(String orgUnitNumber, ICollection&lt;String&gt; expandProperties)

#### ProductManager APIs

-   Task&lt;PagedResult&lt;Product&gt;&gt; ProductManager.ReadAll(QueryResultSettings queryResultSettings, ICollection&lt;String&gt; expandProperties)
-   Task&lt;PagedResult&lt;Product&gt;&gt; ProductManager.Search(ProductSearchCriteria productSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;SimpleProduct&gt; ProductManager.GetById(Int64 recordId, Int64 channelId)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.SearchByCategory(Int64 channelId, Int64 catalogId, Int64 categoryId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.SearchByText(Int64 channelId, Int64 catalogId, String searchText, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefinersByCategory(Int64 catalogId, Int64 categoryId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefinersByText(Int64 catalogId, String searchText, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefinerValue&gt;&gt; ProductManager.GetRefinerValuesByCategory(Int64 catalogId, Int64 categoryId, Int64 refinerId, Int32 refinerSourceValue, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefinerValue&gt;&gt; ProductManager.GetRefinerValuesByText(Int64 catalogId, String searchText, Int64 refinerId, Int32 refinerSourceValue, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.RefineSearchByCategory(Int64 channelId, Int64 catalogId, Int64 categoryId, IEnumerable&lt;ProductRefinerValue&gt; refinementCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.RefineSearchByText(Int64 channelId, Int64 catalogId, String searchText, IEnumerable&lt;ProductRefinerValue&gt; refinementCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductDimensionValue&gt;&gt; ProductManager.GetDimensionValues(Int64 recordId, Int64 channelId, Int32 dimension, IEnumerable&lt;ProductDimensionValue&gt; matchingDimensionValues, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;SimpleProduct&gt;&gt; ProductManager.GetVariantsByDimensionValues(Int64 recordId, Int64 channelId, IEnumerable&lt;ProductDimensionValue&gt; matchingDimensionValues, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;SimpleProduct&gt;&gt; ProductManager.GetVariantsByComponentsInSlots(Int64 recordId, Int64 channelId, IEnumerable&lt;ComponentInSlotRelation&gt; matchingSlotToComponentRelationship, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductComponent&gt;&gt; ProductManager.GetDefaultComponents(Int64 recordId, Int64 channelId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductComponent&gt;&gt; ProductManager.GetSlotComponents(Int64 recordId, Int64 channelId, Int64 slotId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;AttributeValue&gt;&gt; ProductManager.GetAttributeValues(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRelationType&gt;&gt; ProductManager.GetRelationTypes(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.GetRelatedProducts(Int64 recordId, Int64 channelId, Int64 catalogId, Int64 relationTypeId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefiners(ProductSearchCriteria productSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductAvailableQuantity&gt;&gt; ProductManager.GetProductAvailabilities(IEnumerable&lt;Int64&gt; itemIds, Int64 channelId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductPrice&gt;&gt; ProductManager.GetActivePrices(ProjectionDomain projectDomain, IEnumerable&lt;Int64&gt; productIds, DateTimeOffset activeDate, String customerId, IEnumerable&lt;AffiliationLoyaltyTier&gt; affiliationLoyaltyTiers, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;MediaLocation&gt;&gt; ProductManager.GetMediaLocations(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;MediaBlob&gt;&gt; ProductManager.GetMediaBlobs(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)

#### SalesOrderManager APIs

-   Task&lt;PagedResult&lt;SalesOrder&gt;&gt; SalesOrderManager.Search(SalesOrderSearchCriteria salesOrderSearchCriteria, QueryResultSettings queryResultSettings)

### APIs that are available for an anonymous role

#### CartManager APIs

-   Task&lt;SalesOrder&gt; CartManager.Checkout(String id, String receiptEmail, TokenizedPaymentCard tokenizedPaymentCard, String receiptNumberSequence, IEnumerable&lt;CartTenderLine&gt; cartTenderLines)
-   Task&lt;Cart&gt; CartManager.Copy(String id, Int32 targetCartType)
-   Task&lt;Cart&gt; CartManager.AddCartLines(String id, IEnumerable&lt;CartLine&gt; cartLines)
-   Task&lt;Cart&gt; CartManager.UpdateCartLines(String id, IEnumerable&lt;CartLine&gt; cartLines)
-   Task&lt;CartDeliveryPreferences&gt; CartManager.GetDeliveryPreferences(String id)
-   Task&lt;PagedResult&lt;SalesLineDeliveryOption&gt;&gt; CartManager.GetLineDeliveryOptions(String id, IEnumerable&lt;String&gt; cartLineIds, Address shippingAddress, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;DeliveryOption&gt;&gt; CartManager.GetDeliveryOptions(String id, Address shippingAddress, QueryResultSettings queryResultSettings)
-   Task&lt;Cart&gt; CartManager.UpdateLineDeliverySpecifications(String id, IEnumerable&lt;LineDeliverySpecification&gt; lineDeliverySpecifications)
-   Task&lt;Cart&gt; CartManager.UpdateDeliverySpecification(String id, DeliverySpecification deliverySpecification)
-   Task&lt;PagedResult&lt;Product&gt;&gt; CartManager.GetProductsInCart(String id, QueryResultSettings queryResultSettings)
-   Task&lt;CartPromotions&gt; CartManager.GetPromotions(String id)
-   Task&lt;Cart&gt; CartManager.AddDiscountCode(String id, String discountCode)
-   Task&lt;Cart&gt; CartManager.RemoveDiscountCodes(String id, IEnumerable&lt;String&gt; discountCodes)
-   Task&lt;Cart&gt; CartManager.RemoveCartLines(String id, IEnumerable&lt;String&gt; cartLineIds)
-   Task&lt;CardPaymentAcceptPoint&gt; CartManager.GetCardPaymentAcceptPoint(String id, CardPaymentAcceptSettings cardPaymentAcceptSettings)
-   Task&lt;CardPaymentAcceptResult&gt; CartManager.RetrieveCardPaymentAcceptResult(String resultAccessCode)
-   Task&lt;Cart&gt; CartManager.Read(String id, ICollection&lt;String&gt; expandProperties)
-   Task&lt;Cart&gt; CartManager.Update(Cart entity)
-   Task&lt;Cart&gt; CartManager.Create(Cart entity)

#### CatalogManager and ProductCatalogManager APIs

-   Task&lt;PagedResult&lt;ProductCatalog&gt;&gt; ProductCatalogManager.GetCatalogs(Int64 channelId, Boolean activeOnly, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;Category&gt;&gt; CategoryManager.ReadAll(QueryResultSettings queryResultSettings, ICollection&lt;String&gt; expandProperties)
-   Task&lt;PagedResult&lt;Category&gt;&gt; CategoryManager.GetCategories(Int64 channelId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;Category&gt;&gt; CategoryManager.GetChildren(Int64 channelId, Int64 categoryId, QueryResultSettings queryResultSettings)

#### StoreOperationsManager and OrgUnitManager APIs

-   Task&lt;PagedResult&lt;CardTypeInfo&gt;&gt; StoreOperationsManager.GetCardTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;String&gt;&gt; StoreOperationsManager.GetSupportedPaymentCardTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;CountryRegionInfo&gt;&gt; StoreOperationsManager.GetCountryRegionsByLanguageId(String languageId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;DeliveryOption&gt;&gt; StoreOperationsManager.GetDeliveryOptions(QueryResultSettings queryResultSettings)
-   Task&lt;GiftCard&gt; StoreOperationsManager.GetGiftCard(String giftCardId)
-   Task&lt;LinkToExistingCustomerResult&gt; StoreOperationsManager.InitiateLinkToExistingCustomer(String email, String activationToken, String emailTemplateId, IEnumerable&lt;NameValuePair&gt; emailProperties)
-   Task&lt;LinkToExistingCustomerResult&gt; StoreOperationsManager.FinalizeLinkToExistingCustomer(String email, String activationToken)
-   Task&lt;ValidateHardwareStationTokenResult&gt; StoreOperationsManager.ValidateHardwareStationToken(String deviceNumber, String hardwareStationToken)
-   Task&lt;PagedResult&lt;StateProvinceInfo&gt;&gt; StoreOperationsManager.GetStateProvinces(String countryRegionId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;TenderType&gt;&gt; StoreOperationsManager.GetTenderTypes(QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnit&gt;&gt; OrgUnitManager.ReadAll(QueryResultSettings queryResultSettings, ICollection&lt;String&gt; expandProperties)
-   Task&lt;PagedResult&lt;OrgUnitLocation&gt;&gt; OrgUnitManager.GetOrgUnitLocationsByArea(SearchArea searchArea, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnitAvailability&gt;&gt; OrgUnitManager.GetAvailableInventory(String itemId, String variantId, String barcode, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;OrgUnitAvailability&gt;&gt; OrgUnitManager.GetAvailableInventoryNearby(IEnumerable&lt;ItemUnit&gt; itemIds, SearchArea searchArea, QueryResultSettings queryResultSettings)
-   Task&lt;TillLayout&gt; OrgUnitManager.GetTillLayout()
-   Task&lt;ChannelConfiguration&gt; OrgUnitManager.GetOrgUnitConfiguration()
-   Task&lt;PagedResult&lt;OrgUnit&gt;&gt; OrgUnitManager.Search(SearchStoreCriteria storeSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;OrgUnit&gt; OrgUnitManager.Read(String orgUnitNumber, ICollection&lt;String&gt; expandProperties)

#### CustomerManager APIs

-   Task&lt;Customer&gt; CustomerManager.Create(Customer entity)

#### ProductManager APIs

-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.SearchByCategory(Int64 channelId, Int64 catalogId, Int64 categoryId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.SearchByText(Int64 channelId, Int64 catalogId, String searchText, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefinersByCategory(Int64 catalogId, Int64 categoryId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefinersByText(Int64 catalogId, String searchText, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefinerValue&gt;&gt; ProductManager.GetRefinerValuesByCategory(Int64 catalogId, Int64 categoryId, Int64 refinerId, Int32 refinerSourceValue, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefinerValue&gt;&gt; ProductManager.GetRefinerValuesByText(Int64 catalogId, String searchText, Int64 refinerId, Int32 refinerSourceValue, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.RefineSearchByCategory(Int64 channelId, Int64 catalogId, Int64 categoryId, IEnumerable&lt;ProductRefinerValue&gt; refinementCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.RefineSearchByText(Int64 channelId, Int64 catalogId, String searchText, IEnumerable&lt;ProductRefinerValue&gt; refinementCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductDimensionValue&gt;&gt; ProductManager.GetDimensionValues(Int64 recordId, Int64 channelId, Int32 dimension, IEnumerable&lt;ProductDimensionValue&gt; matchingDimensionValues, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;SimpleProduct&gt;&gt; ProductManager.GetVariantsByDimensionValues(Int64 recordId, Int64 channelId, IEnumerable&lt;ProductDimensionValue&gt; matchingDimensionValues, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;SimpleProduct&gt;&gt; ProductManager.GetVariantsByComponentsInSlots(Int64 recordId, Int64 channelId, IEnumerable&lt;ComponentInSlotRelation&gt; matchingSlotToComponentRelationship, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductComponent&gt;&gt; ProductManager.GetDefaultComponents(Int64 recordId, Int64 channelId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductComponent&gt;&gt; ProductManager.GetSlotComponents(Int64 recordId, Int64 channelId, Int64 slotId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;AttributeValue&gt;&gt; ProductManager.GetAttributeValues(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRelationType&gt;&gt; ProductManager.GetRelationTypes(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductSearchResult&gt;&gt; ProductManager.GetRelatedProducts(Int64 recordId, Int64 channelId, Int64 catalogId, Int64 relationTypeId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductRefiner&gt;&gt; ProductManager.GetRefiners(ProductSearchCriteria productSearchCriteria, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductAvailableQuantity&gt;&gt; ProductManager.GetProductAvailabilities(IEnumerable&lt;Int64&gt; itemIds, Int64 channelId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;ProductPrice&gt;&gt; ProductManager.GetActivePrices(ProjectionDomain projectDomain, IEnumerable&lt;Int64&gt; productIds, DateTimeOffset activeDate, String customerId, IEnumerable&lt;AffiliationLoyaltyTier&gt; affiliationLoyaltyTiers, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;MediaLocation&gt;&gt; ProductManager.GetMediaLocations(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)
-   Task&lt;PagedResult&lt;MediaBlob&gt;&gt; ProductManager.GetMediaBlobs(Int64 recordId, Int64 channelId, Int64 catalogId, QueryResultSettings queryResultSettings)


