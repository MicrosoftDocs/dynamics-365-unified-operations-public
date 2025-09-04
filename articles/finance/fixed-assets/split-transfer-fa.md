---
title: Fixed asset intercompany split and transfer (preview) 
description: Learn how to split and transfer fixed assets between legal entitiies using Dynamics 365 Finance.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 09/04/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-11-19
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Fixed asset intercompany split and transfer (preview)

[!include banner]

This article describes how to split and transfer fixed assets between legal entitiies.

[!INCLUDE preview-note]

The Fixed asset intercompany split and transfer feature allows organizations to efficiently manage the movement of fixed assets between legal entities—whether through full transfers or partial splits—without switching between companies. It automates the mapping of asset groups, books, and key fields between source and destination entities, streamlining intercompany asset operations.

This feature supports transfers based on acquisition and accumulated depreciation, as well as net book value. It also provides flexible options for handling service life and exchange rates. Users can choose from the following options how to configure the destination asset.

-	Inherit the remaining depreciation periods from the source asset.
-	Use predefined service life settings at the destination.
-	Copy the service life from the source asset.
  
The Fixed asset intercompany split and transfer feature provides flexible exchange rate options for accounting and reporting currencies. Users can choose from the following options.

-	The historical acquisition rate of the source asset
-	The exchange rate on the transfer date
-	The rate that yields the highest asset value

The wizard also offers granular control over financial dimensions and tags. Before journal creation, users can preview key financial data—including acquisition cost, accumulated depreciation, and net book value per asset book—ensuring transparency and accuracy.

Intercompany journals are automatically generated using clearing accounts, which ensures proper balancing and audit compliance. The system maintains a complete transfer history, enabling full traceability of asset movements across legal entities. Whether transferring a single asset or performing bulk transfers with percentage-based splits, the wizard simplifies cross-company asset management while maintaining consistency, control, and auditability.

## Enable the feature

### Prerequisites

Before you begin, enable the following preview features in **Feature management**.
-	Split and transfer fixed assets between legal entities (preview)
-	Fixed asset history (preview)

### Set up intercompany transfer mapping
This value defines how assets are transferred between legal entities. It ensures consistency in asset classification and field values across companies.

1.	Go to Fixed assets > Setup > Assets intercompany transfer mapping.
1.	Define the source and destination legal entities.
1.	Enable bidirectional mapping if needed, or create separate records for each direction.


### Map specific values

Map the following values before you split and transfer fixed assets.
-	**Asset groups**: Map source asset groups to destination groups (for example, COPM → Computers).
-	**Asset books**: Ensure posting layers match between source and destination books.
-	**Asset book fields**: Map fields such as acquisition method and depreciation. 
   -	**Copy**: Replicate values from the source asset to the destination asset. When a field value is called from a table, values in the destination legal entity are created.
   - **Constant**: Assign a fixed value. For example, if you set the Acquisition method field in the asset book to Transferred, that value is assigned to the destination asset.
   - **Map values**: Translate values between entities. For example, if you map the Acquisition method field to Purchased in the source asset, and map that to Transferred in the destination asset. 
   > [!NOTE]
   > The **Copy** and **Map** options enable **Assign field values** so you can define the constant value or mapping values.

### Configure fixed assets parameters

To establish the core numbering rules for intercompany asset transfers, ensuring that each transfer is assigned a number sequence, set up the intercompany transfer ID number sequence under **Shared settings**.

### Configure fixed assets intercompany accounting

For each legal entity pair, do the following.
-	Configure the fixed asset intercompany accounting by specifying the journal names.
-	Select intercompany accounts for both the source and destination companies.
-	Select an asset transfer clearing account.
-	Define the intercompany accounts and clearing accounts for both the source and destination companies.
-	Assign the appropriate journals for each company and applicable posting layer.

### Complete transfer process

The transfer wizard guides you through the transfer process step by step, simplifying asset selection, destination, review, and generation of journals.
1.	Go to **Fixed assets > Fixed assets intercompany transfer**.
1.	Create a new transfer record and select the source legal entity.
1.	Launch the wizard and follow the steps on the screen.
1.	The **Asset transfer status** reflects the progress of the transfer process. 
  -	Started: A transfer is created.
  -	**Assets generated**: On the Review journal details step, the destination assets are created but no journal exists yet.
  -	**Journal created**: The wizard is completed and the journal is successfully generated.
  -	**Journal posted**: The journal is posted.
  - **Assets generated**: All generated journals are deleted before posting.

### Select assets

You must choose which assets to transfer and define how to distribute them. This step supports selecting multiple assets or manually adding fixed assets from the source company. You can select assets manually or use filters.

### Choose destination

Define the receiving company, and how the asset values and service life are handled. Complete this step to ensure accurate financial treatment in the destination entity.

Select from the following options how to distribute the fixed assets:
-	**Send all assets to same destination**: Transfer all selected assets as a group to a single destination company. For example, move 100 office furniture assets together to one company.
-	**Split assets value between multiple entities by percentage**: Allocate the value of each asset across multiple companies based on percentages you define. You can assign portions of the asset value to different companies, with any remaining value optionally retained by the source company. For example, 20% of an asset’s value goes to one company, 50% to another, and 30% remains with the source.
-	**Split assets between multiple entities by ID**: Distribute complete assets among multiple companies by assigning them individually in the worksheet. For example, with 100 office furniture assets, you can transfer 70 to one company and 30 to another company.
  
> [!NOTE]
> Confirm that there are mappings between legal entities to avoid errors.

The **Transfer details** section defines how the asset’s value and timing are treated during the transfer. Select the appropriate method to ensure that the destination company reflects the correct financial value, while the source company accurately removes the asset from its books.

- **Transfer value method**: Select how the value of the asset is transferred. You can choose to either use its original acquisition and depreciation values or apply its current net book value. Regardless of the method you select, the transfer process resets the netbook value of the source asset to 0 by removing both the acquisition cost and the accumulated depreciation. That way, financial treatment in the destination company is acurately accounted for. 
  - **Acquisition and depreciation value**: Records the acquisition of the destination asset by using the source asset’s original acquisition and accumulated depreciation amounts separately.
  - **Net book value**: Records the destination asset acquisition as a single amount equal to the source asset’s net book value.
  - **Transfer date**: This value reflects the posting date for the transaction, the acquisition date for the destination asset, and the date the source asset is removed from the source company’s books.
    
### Configure destination details

Select a destination company. In the company, select a **Rate type** from the following options.
- Acquisition date: Use the historical rate from the asset’s original acquisition date.
-	Transfer date rate: Use the exchange rate recorded in the ledger on the transfer date, reflecting the most current rate available and aligning with real time financial reporting.
-	Maximize destination asset value: Select the rate that results in the highest asset value in the destination company’s books.
Select a service life to define how the destination asset’s service life is handled during the transfer.
-	Use the default value from destination configuration: Use the default service life defined in the destination company’s asset book.
-	Copy service life from source asset: Copy the full service life from the source asset.
-	Use source assets remaining periods: Continue the depreciation schedule based on the source asset’s remaining depreciation periods.

### Complete worksheet

Use the worksheet to review and adjust asset level details before reviewing the transfer journal. The following fields can be updated:
-	Source asset
-	Transfer value method
-	Service life configuration
-	Financial dimensions
-	Financial tags
-	Split percentages
  
The **Transfer value** and **Percentage fields** are interdependent. Updating one automatically recalculates the other to maintain consistency. For destination asset IDs, if the field is left blank, an ID is automatically generated and displays Auto-generate. The destination asset is generated when you move to the Review journal details step. Alternatively, you can manually assign a predefined ID. You can also preview asset book values, including acquisition cost, accumulated depreciation, and net book value for both source and destination assets. To streamline updates, bulk editing options are available for financial dimensions and tags. Additionally, the Reapply book mapping function resets and regenerates destination book values based on current mapping settings. This step ensures that all transfer data is validated and tailored before proceeding to journal review and posting.


