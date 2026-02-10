---
title: Enable cross legal entity inventory lookup for POS
description: Learn how to enable and configure cross legal entity inventory lookup in Microsoft Dynamics 365 Commerce point of sale (POS) to view inventory availability across different legal entities.
author: johnmichalak
ms.date: 02/09/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: johnmichalak
ms.search.validFrom: 2026-02-09
ms.custom: bap-template
---

# Enable cross legal entity inventory lookup for POS

[!include [banner](includes/banner.md)]

This article describes how to enable and configure cross legal entity inventory lookup in Dynamics 365 Commerce point of sale (POS). This feature allows retail associates to view real-time inventory availability across multiple legal entities, enabling better customer service and informed purchase decisions.

## Overview

Cross legal entity inventory lookup extends the standard POS inventory lookup functionality to search for product availability across different legal entities within your organization. This capability is particularly useful for:

- Organizations with multiple legal entities sharing inventory visibility
- Retail scenarios where stores under different legal entities need to coordinate stock
- Customer service representatives who need to locate products across the entire organization

## Prerequisites

Before enabling cross legal entity inventory lookup, ensure that:

- Your environment is running Dynamics 365 Commerce version 10.0.47 or later
- The standard POS inventory lookup operation is already configured and working
- Appropriate security roles and permissions are set up for cross legal entity access
- Commerce Scale Unit (CSU) is properly configured for your stores

## Enable cross legal entity inventory lookup

To enable cross legal entity inventory lookup in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce parameters**.
2. On the **Inventory** tab, locate the **Cross legal entity inventory lookup** section.
3. Set the **Enable cross legal entity inventory lookup** option to **Yes**.
4. In the **Legal entities** field, select which legal entities should be included in the lookup scope.
5. Configure the **Maximum results** field to limit the number of results returned from cross legal entity searches.
6. Select **Save** to apply the changes.

## Configure POS permissions

To allow POS users to perform cross legal entity inventory lookups:

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Permission groups**.
2. Select the permission group to modify, or create a new one.
3. On the **Permissions** FastTab, locate the **Inventory lookup** section.
4. Enable the **Allow cross legal entity lookup** permission.
5. Select **Save** to apply the changes.
6. Run the **1060** (Staff) distribution schedule to sync the changes to stores.

## Use cross legal entity inventory lookup in POS

Once configured, retail associates can use the cross legal entity inventory lookup feature:

1. In POS, search for a product using the search bar or by scanning a barcode.
2. From the product details page, select the **Inventory lookup** operation.
3. In the inventory lookup view, select **All legal entities** from the scope dropdown.
4. The system displays inventory availability across all configured legal entities.
5. Filter or sort results by legal entity, location, quantity, or other criteria.
6. Select a location to view detailed inventory information.

## Performance considerations

When implementing cross legal entity inventory lookup, consider the following:

- **Response time**: Querying multiple legal entities may increase lookup time. Consider limiting the number of legal entities in scope.
- **Network latency**: Cross legal entity lookups may traverse multiple databases. Ensure adequate network bandwidth.
- **Caching**: Enable channel-side inventory calculation to improve performance for frequently accessed products.
- **Result limits**: Configure appropriate maximum result limits to prevent performance degradation.

## Troubleshooting

### No results returned from other legal entities

If cross legal entity inventory lookup returns no results:

1. Verify that the feature is enabled in Commerce parameters.
2. Check that users have the appropriate permissions assigned.
3. Confirm that the CDX jobs (1060, 1070, 1110) have run successfully.
4. Verify network connectivity between legal entities.

### Performance issues

If inventory lookups are slow:

1. Reduce the number of legal entities in scope.
2. Enable channel-side inventory calculation.
3. Configure appropriate result limits.
4. Review network infrastructure and database performance.

## Additional resources

- [Inventory lookup operation in POS](pos-inventory-lookup-operation.md)
- [Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)
- [Configure channel-side inventory calculation](inventory-lookup-channel-side-calc.md)
- [POS inventory lookup with channel-side calculation](pos-inventory-lookup-operation.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
