---
title: Example custom request handler code
description: Learn how to implement a custom request handler for custom pricing attributes
author: sherry-zheng
ms.author: chuzheng
ms.topic: article
ms.date: 07/10/2025
ms.custom: bap-template
ms.reviewer:
ms.search.form:
---

# Example custom request handler code

This article provides sample code for the `GetCustomizedPricingPropertiesRequestHandler` class, which is used to implement custom pricing attributes. This handler enables you to retrieve and process custom pricing properties for products, customers, orders, and order lines.

The code demonstrates how to extend the pricing framework by defining custom attributes and linking them to specific fields in the database. It also shows how to process requests programmatically to fetch and merge these attributes into the pricing logic. For more details about adding custom pricing attributes, see [Add custom pricing attributes for POS](upm-support-custom-attributes.md).

```X++
/**
 * SAMPLE CODE NOTICE
 * 
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS.  MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
 * NO TECHNICAL SUPPORT IS PROVIDED.  YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
 */

namespace Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages
{
    using System;
    using System.Collections;
    using System.Collections.Concurrent;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using System.Diagnostics.CodeAnalysis;
    using System.Linq;
    using System.Runtime.Serialization;
    using System.Text;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Dynamics.Commerce.Runtime;
    using Microsoft.Dynamics.Commerce.Runtime.Data;
    using Microsoft.Dynamics.Commerce.Runtime.Data.Types;
    using Microsoft.Dynamics.Commerce.Runtime.DataModel;
    using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages.Pricing.AttributePricing;
    using Microsoft.Dynamics.Commerce.Runtime.Handlers;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;
    using Microsoft.Dynamics.Retail.Diagnostics;

    /// <summary>
    /// The request handler for <c>GetCustomizedPricingPropertiesRequest</c> class.
    /// </summary>
    public sealed class GetCustomizedPricingPropertiesRequestHandler : SingleAsyncRequestHandler<GetCustomizedPricingPropertiesRequest>
    {
        private const string PricingAttributeLinkFieldPathNotExists = "PATH_NOT_EXIST";

        private IPricingAttribute SalesOrderInclTax
        {
            get
            {
                return new PricingAttributeLink()
                {
                    AttributeName = "Prices include sales tax",
                    TypeName = "Customization",
                    SourceName = "SalesTable",
                    FieldName = "InclTax",
                    FieldPath = "SalesTable#InclTax",
                    DataType = ExtensibleAttributeDataType.Boolean,
                };
            }
        }

        private IPricingAttribute SalesLineLineNumber
        {
            get
            {
                return new PricingAttributeLink()
                {
                    AttributeName = "Line number",
                    TypeName = "Customization",
                    SourceName = "SalesLine",
                    FieldName = "LineNum",
                    FieldPath = "SalesLine#LineNum",
                    DataType = ExtensibleAttributeDataType.Integer,
                };
            }
        }

        /// <summary>
        /// Processes the <c>GetCustomizedPricingPropertiesRequest</c>.
        /// The request should not be null.
        /// </summary>
        /// <param name="request">The request parameter.</param>
        /// <returns>The <c>GetCustomizedPricingPropertiesResponse</c>.</returns>
        protected override async Task<Response> Process(GetCustomizedPricingPropertiesRequest request)
        {
            ThrowIf.Null(request, nameof(request));
            ThrowIf.Null(request.RequestContext, nameof(request.RequestContext));

            var databaseContext = new DatabaseContext(request.RequestContext);

            foreach (PricingAttributeLink link in request.PricingAttributeLinks)
            {
                if (request.SourceEntity is Customer customer)
                {
                    if (string.Equals(link.TypeName, "Customization", StringComparison.OrdinalIgnoreCase)
                            && string.Equals(link.FieldName, "StatisticsGroup", StringComparison.OrdinalIgnoreCase))
                    {
                        await this.GetCustomizedCustomerPricingPropertiesFromTable(
                                        request,
                                        databaseContext,
                                        request.PricingAttributeLinks,
                                        customer.AccountNumber)
                                    .ConfigureAwait(false);
                    }
                }

                if (request.SourceEntity is Item item)
                {
                    if (string.Equals(link.TypeName, "Customization", StringComparison.OrdinalIgnoreCase)
                            && string.Equals(link.FieldName, "NameAlias", StringComparison.OrdinalIgnoreCase))
                    {
                        await this.GetCustomizedItemPricingPropertiesFromTable(
                                        request,
                                        databaseContext,
                                        request.PricingAttributeLinks,
                                        item.ItemId)
                                    .ConfigureAwait(false);
                    }
                }

                if (request.SourceEntity is SalesLine salesLine)
                {
                    if (salesLine.LineNumber != 0)
                    {
                        request.AttributeSource.PricingProperties[this.SalesLineLineNumber] = salesLine.LineNumber;
                    }
                }

                if (request.SourceEntity is SalesTransaction salesTransaction)
                {
                    request.AttributeSource.PricingProperties[this.SalesOrderInclTax] = salesTransaction.IsTaxIncludedInPrice;
                }
            }

            return new GetCustomizedPricingPropertiesResponse(request.AttributeSource.PricingProperties);
        }

        private async Task<Response> GetCustomizedCustomerPricingPropertiesFromTable(
            GetCustomizedPricingPropertiesRequest request,
            DatabaseContext databaseContext,
            IEnumerable<PricingAttributeLink> pricingAttributes,
            string accountNumber)
        {
            pricingAttributes = pricingAttributes
                .Where(attr => attr.Source.Equals(PricingAttributeSourceType.Customer))
                .Where(attr =>
                    !string.IsNullOrWhiteSpace(attr.FieldPath)
                    && !attr.FieldPath.Equals(PricingAttributeLinkFieldPathNotExists, StringComparison.OrdinalIgnoreCase));

            if (pricingAttributes.Any())
            {
                var query = new SqlPagedQuery(QueryResultSettings.AllRecords)
                {
                    DatabaseSchema = "ax",
                    Select = new ColumnSet("StatisticsGroup"),
                    From = "CustTable",
                    Where = "ACCOUNTNUM = @accountNumber and DATAAREAID = @dataAreaId",
                    Parameters =
                    {
                        ["@accountNumber"] = accountNumber,
                        ["@dataAreaId"] = request.RequestContext.GetChannelConfiguration().InventLocationDataAreaId,
                    },
                };

                var selectedPricingProperties = await this.ExecuteSelectedPricingAttributesQueryAndResolveResult(databaseContext, query, pricingAttributes, request).ConfigureAwait(false);
                request.AttributeSource.Merge(selectedPricingProperties);
            }

            return NullResponse.Instance;
        }

        private async Task<Response> GetCustomizedItemPricingPropertiesFromTable(
            GetCustomizedPricingPropertiesRequest request,
            DatabaseContext databaseContext,
            IEnumerable<PricingAttributeLink> pricingAttributes,
            string itemId)
        {
            pricingAttributes = pricingAttributes
                .Where(attr => attr.Source.Equals(PricingAttributeSourceType.Product))
                .Where(attr =>
                    !string.IsNullOrWhiteSpace(attr.FieldPath)
                    && !attr.FieldPath.Equals(PricingAttributeLinkFieldPathNotExists, StringComparison.OrdinalIgnoreCase));

            if (pricingAttributes.Any())
            {
                var query = new SqlPagedQuery(QueryResultSettings.AllRecords)
                {
                    DatabaseSchema = "ax",
                    Select = new ColumnSet("NameAlias"),
                    From = "InventTable",
                    Where = "ITEMID = @itemId and DATAAREAID = @dataAreaId",
                    Parameters =
                    {
                        ["@itemId"] = itemId,
                        ["@dataAreaId"] = request.RequestContext.GetChannelConfiguration().InventLocationDataAreaId,
                    },
                };

                var selectedPricingProperties = await this.ExecuteSelectedPricingAttributesQueryAndResolveResult(databaseContext, query, pricingAttributes, request).ConfigureAwait(false);
                request.AttributeSource.Merge(selectedPricingProperties);
            }

            return NullResponse.Instance;
        }

        private async Task<SortedDictionary<IPricingAttribute, object>> ExecuteSelectedPricingAttributesQueryAndResolveResult(
            DatabaseContext databaseContext,
            SqlPagedQuery query,
            IEnumerable<PricingAttributeLink> pricingAttributes,
            Request request)
        {
            IDictionary<string, ISet<object>> dbResults = new Dictionary<string, ISet<object>>();

            await databaseContext
                .ExecuteQueryWithRetryAsync(
                    query,
                    (result) =>
                    {
                        for (int i = 0; i < result.FieldCount; ++i)
                        {
                            var columnName = result.GetName(i);
                            var columnValue = result.GetValue<object>(i);

                            if (columnValue is not null)
                            {
                                if (!dbResults.ContainsKey(columnName))
                                {
                                    dbResults[columnName] = new HashSet<object>();
                                }

                                dbResults[columnName].Add(columnValue);
                            }
                        }

                        return Task.CompletedTask;
                    })
                .ConfigureAwait(false);

            var selectedPricingProperties = new SortedDictionary<IPricingAttribute, object>(PricingComparer.Instance);

            foreach (var dbResult in dbResults)
            {
                var attributeLink = pricingAttributes.FirstOrDefault(attr => attr.FieldName.Equals(dbResult.Key, StringComparison.OrdinalIgnoreCase));

                if (attributeLink != default)
                {
                    if (dbResult.Value.Count > 1)
                    {
                        selectedPricingProperties[attributeLink] = string.Join(",", dbResult.Value);
                    }
                    else
                    {
                        selectedPricingProperties[attributeLink] = dbResult.Value.FirstOrDefault();
                    }
                }
            }

            return selectedPricingProperties;
        }
    }
}
```
