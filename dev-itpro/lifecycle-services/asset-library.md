---
# required metadata

title: Asset library (LCS)
description: This topic provides information abou tthe Asset Library functionality in Lifecycle Services (LCS).
author: kfend
manager: AnnBe
ms.date: 06/22/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 266824
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset library (LCS)

[!include[banner](../includes/banner.md)]

The Asset library is a storage location for the different assets that are associated with a tenant in LCS. There are two kinds of Asset libraries available in LCS:
- **Shared asset library**
- **Project level asset library**

**Shared asset library:** This library is used by Microsoft and Partners to share assets across multiple tenants, projects, and environments in LCS. This library can be accessed by any user that signs into LCS. To get to the **Shared Asset library**, log in to LCS and then click the **Shared asset library** tile.
     
  [![sharedassetlibrary](./media/SharedAssetLibrary.jpg)](./media/SharedAssetLibrary.jpg)
  
**Project level asset library:** This library is a project level asset library that is used to share assets across environments within a project in LCS. This library can be accessed by all users within a project. To get to the **Project asset library**, log in to LCS, open a project, click the hamburger icon, and then click **Asset library**.
     
     
 [![projectassetlibrary](./media/ProjectAssetLibrary.jpg)](./media/ProjectAssetLibrary.jpg)

## Asset library support 
The Asset library supports multiple asset types. Some commonly used assets include:
- **Software deployable packages:** Represents all of the packages that are used for updating an environment with latest set of updates.
- **Data Packages:** Stores assets that are used for configuration and data management. 
- **GER Configuration:** Stores all localization and translation assets that are applied to the Client. 
- **Retail SDK:** Stores all of the latest scripts for the Retail SDK. 

### Asset scopes
Each of the assets that are supported by the Asset library has multiple scopes. These include:
- **Me:** When an asset is uploaded, it is set to the **Me** scope. This means that it is visible only to the person that uploaded the asset. 
- **Project:** When a project is imported from the **Global** scope to another project, the scope is set to **Project** scope. 
- **Organization:** When an asset needs to be shared with multiple users within a tenant, the tenant admin can promote the asset to **Organization** scope. 
- **Global:** Only Microsoft can upload assets to the **Global** scope. These are assets that Microsoft wants to be made publicly available to all LCS projects and users.  

### Asset status
Each asset has a status of either **Draft**, the asset can still be edited, or **Published**, the asset is published at an Organization or Global level and edits are complete. 

## Actions in the Asset library
You can perform different actions in the asset library as needed. 

### Upload an asset to the asset library
1. Select the tab where you want to upload the asset.
2. Click the **'+'**. 
3. Enter a name and description for the asset. 
4. Upload the file for the asset and then click **Confirm**. 
    
### Upload a new version for a specific asset
1. Select the asset in the Asset library.
2. Click the **Upload** icon on the Asset library toolbar. 
3. Follow the same steps as uploading a new asset. 
To view multiple versions for a single asset, on the toolbar, click **Versions**. 

### Move assets from the Global asset library to the Project asset library
There are two ways to move an asset from the Global to the Project scope, import or copy.

#### Import from Global scope
Import an asset from the Global scope to the Project scope so that it can be applied across environments. 
1. In the **Project asset library**, select the tab of the asset type that you want to import.
2. Click **Import**. This will open list of assets from the **Shared asset library**. 
3. Select the asset that you want to import, and then click **Pick**.
This will import the selected asset and put it in the **Project asset library** with a status of **Published**. This is for packages that you do not plan to edit. If you want to edit an imported package, create a copy using the following steps which will put the package in a **Draft** state. 
    
#### Copy from Global Scope
Create a copy of the assets so they can be edited. 
1. In the project asset library, select the tab of the asset type that you want to copy.
2. Select the asset that you want to copy, and on the toolbar, click **Copy**.
This will create a copy of the published asset and put it in a **Draft** state.
        
### Save to My Library
Move the edited asset back to the **Shared asset library** so that it can be promoted to the **Organization** scope and shared with multiple customers. 
1. In the **Project asset library**, select the tab of the asset type that you want to import.
2. Select the asset you want to save, and then click **Save to My Library**.
This will save the asset from the **Project asset library** back to the **Shared asset library** in the **Me** Scope. 
  




