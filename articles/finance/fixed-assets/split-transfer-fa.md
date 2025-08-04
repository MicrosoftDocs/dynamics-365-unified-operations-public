---
title: Fixed asset intercompany split and transfer (preview)
description: Learn about Fixed asset intercompany split and transfer 
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 08/12/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-11-19
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Fixed asset intercompany split and transfer (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This feature is currently in preview. Enable it in Feature management before use.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

The Fixed Asset Intercompany Split and Transfer Wizard enables organizations to efficiently manage the movement of fixed assets across legal entities—whether through full transfers or partial splits—without 
the need to switch between companies. This feature streamlines intercompany asset operations by automating the mapping of asset groups, books, and key fields between source and destination entities. It supports 
both acquisition and accumulated depreciation based and net book value transfers, while offering flexible options for handling service life and exchange rates. Users can define whether the destination asset 
should inherit the remaining depreciation periods from the source asset, use predefined service life settings at the destination asset, or copy service life from the source asset. The exchange rate options 
applied to the accounting and reporting currency either historical acquisition rate of the source asset, the transfer date rate, or the rate that yields the highest asset value. The wizard also allows for 
precise control over financial dimensions and tags, and provides a preview of financial data—including acquisition cost, accumulated depreciation, and net book value per asset book—before journal creation. 
Intercompany journals are automatically generated using clearing accounts, ensuring accurate balancing and audit. Additionally, the system maintains a complete transfer history, enabling traceability of asset 
movements across entities. Whether transferring a single asset or executing bulk transfers with percentage-based splits, this wizard simplifies cross-company asset management with consistency and control.

## Enable the feature

This step ensures the functionality is available in your environment.

Before you begin, enable the following preview features in Feature management:

- Split and transfer fixed assets between legal entities (preview)
- Fixed asset history (preview)

## Set up intercompany transfer mapping

This setup defines how assets are transferred between legal entities. It ensures consistency in asset classification, and field values across companies.

1. Go to Fixed assets > Setup > Assets intercompany transfer mapping.
2. Define the source and destination legal entities (for example, USMF → USSI).
3. Enable bidirectional mapping if needed, or create separate records for each direction.

### Mapping

Map the following before splitting and transferring fixed assets:
 - Asset groups - Map source asset groups to destination groups (for example, COPM→ Computers).
 - Asset books - Ensure posting layers match between source and destination books.
 - Asset book fields - Map fields like acquisition method and depreciation.  
      - Copy – replicate values from the source asset to the destination asset. When a field value is called from a table, create the values in the destination legal entity.
      - Constant – assign a fixed value. For example, set the **Acquisition method** field in the asset book to **Transferred**. The defined value is assigned to the destination asset.
      - Map values – translate values between entities. For example, map the **Acquisition method** field to **Purchased** in the source asset and is **Transferred** in the destination asset.
      - The copy and map values options enables **Assign field values to define** button defines the constant value or mapping values.

## Configure Fixed assets parameters

This step sets up the foundational numbering rules that govern intercompany transfers. It ensures transfers have number sequence.
- Under **Shared settings**, set up the intercompany transfer ID number sequence.

## Configure Fixed assets intercompany accounting

For each legal entity pair: 
 - Configure the fixed asset intercompany accounting by specifying the journal names
 - Select intercompany accounts for both the source and destination companies
 - Select an asset transfer clearing account
 - Define the intercompany accounts and clearing accounts for both the source and destination companies
 - Assign the appropriate journals for each company and applicable posting layer 

## Transfer wizard

The wizard guides you through the transfer process step by step. It simplifies asset selection, destination, review and journal generation—ensuring accuracy.

1. Go to **Fixed assets** > **Fixed assets intercompany transfer**.
2. Create a new transfer record and select the source legal entity.
3. Launch the wizard and follow these steps.
4. The **Asset transfer status** reflects the progress of the transfer process.
    - When a transfer is first created, the status is **Started**.
    - On the **Review journal details** step, it changes to **Assets generated**, indicating that destination assets have been created but no journal exists yet.
    - After completing the wizard and successfully generating the journal, the status is **Journal created.**
    - After the journal is posted, the status is **Journal posted**.
    - If all generated journals are deleted before posting, the status reverts back to **Assets generated.**

### Select assets

Choose which assets to transfer and how they should be distributed. This step supports selecting multiple assets or manually add fixed assets from the source company. Choose assets manually or use filters.

### Choose destination

Define the receiving company and how the asset values and service life should be handled. This ensures accurate financial treatment in the destination entity.

- Select how to distribute the fixed assets:
  - **Send all assets to same destination** - Transfer all selected assets as a group to a single destination company. For example, move 100 office furniture assets together to one company.
  - **Split assets value between multiple entities by percentage** - Allocate each asset’s value across multiple companies based on specified percentages. Portions of the asset value can be assigned to different
    companies, with any remaining value optionally retained by the source company. For example, 20% of an asset’s value goes to one company, 50% to another, and 30% remains with the source.
  - **Split assets between multiple entities by ID** - Distribute complete assets among multiple companies by assigning them individually in the worksheet. For example, Out of 100 office furniture assets, 70 are
     fully transferred to one company and 30 to another.

>[!Note]
> Confirm that mappings exist between legal entities to avoid errors.

The **Transfer details** section defines how the asset’s value and timing are treated during the transfer. Selecting the appropriate method ensures that the destination company reflects the correct financial 
value, while the source company accurately removes the asset from its books.

- **Transfer value method** - Select how the asset’s value is transferred. Either by using its original acquisition and depreciation values or by applying its current net book value. Regardless of the method
  selected, the transfer process resets the source asset’s netbook value to zero by removing both its acquisition cost and accumulated depreciation, ensuring accurate financial treatment in the destination
  company.
  - **Acquisition and depreciation value** - Records the destination asset acquisition using the source asset’s original acquisition and accumulated depreciation amounts separately.
  - **Net book value** - Records the destination asset acquisition as a single amount equal to the source asset’s net book value.
  - **Transfer date** is the posting date for the transaction, the acquisition date for the destination asset, and the date the source asset is removed from the source company’s books.

### Destination details  
Select a destination company. In the company, select a **Rate type**: 
  - **Acquisition date** - use the historical rate from the asset’s original acquisition date, maintaining consistency with the original financial context—ideal for retrospective or compliance-driven reporting.
  - **Transfer date rate** - use the exchange rate recorded in the ledger on the transfer date, reflecting the most current rate available and aligning with real-time financial reporting.
  - **Maximize destination asset value** - select the rate that results in the highest asset value in the destination company’s books. 

Select a service life to determine how the destination asset’s service life is handled during the transfer: 
  - **Use the default value from destination configuration** - Use the default service life defined in the destination company’s asset book.
  - **Copy service life from source asset** - Copy the full service life from the source asset.
  - **Use source assets remaining periods** - Continue the depreciation schedule based on the source asset’s remaining depreciation periods.

### Complete worksheet

The Complete worksheet step allows you to review and fine tune asset level details before reviewing the transfer journal. 
You can adjust key fields: 
 - **Source asset**
 - **Transfer value method** (acquisition and depreciation vs. net book value)
 -  **Service life configuration**
 -  **Financial dimensions**
 -  **Financial tags**
 -  **Split percentages**

The **Transfer value** and **Percentage** fields are interdependent. Updating one automatically recalculates the other to maintain consistency. For destination asset IDs, if the field is left blank, an ID is 
automatically generated and displays **Auto-generate**. The destination asset is generated when you move to the **Review journal details** step. Alternatively, you can manually assign a predefined ID. You can 
also preview asset book values, including acquisition cost, accumulated depreciation, and net book value for both source and destination assets. To streamline updates, bulk editing options are available for 
financial dimensions and tags. Additionally, the **Reapply book mapping** function resets and regenerates destination book values based on current mapping settings. This step ensures that all transfer data is 
validated and tailored before proceeding to journal review and posting.

### Review and post

Preview the journal entries before posting. This ensures transparency and allows you to verify that debits, credits, and clearing accounts are correct.

Preview journal entries:
  - Debits, credits, and clearing accounts for both companies
  - Complete the wizard to generate unposted fixed assets transfer journal. From the **Intercompany transfer** page, select **Linked journal** to open the linked journal.

>[!Tip]
> An unposted fixed asset journal is created that can be reviewed and posted manually.
