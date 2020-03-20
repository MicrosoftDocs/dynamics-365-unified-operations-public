When copying a database between environments, you will need to run the environment re-provisioning tool before the copied database is fully functional, to ensure that all Commerce components are up-to-date.

> [!IMPORTANT]
> We recommend that you run this procedure whether you are using Commerce components or not, because Commerce functionality is included in all environments. 

Before you continue, you must make sure that the following prerequisites are met:
1. If you are upgrading to the July 2017 release (also known as 7.2) 7.2.11792.56024, apply the following application X++ hotfixes in the destination environment before running the data upgrade in that environment. These will prevent various errors occurring during the data upgrade:

    - KB 4036156 - Retail minor version upgrade - 'Variant number sequence is not set.' This fix package also includes KB 4035399 and KB 4035751. Note that you must have a minimum of Platform Update 9 to use this package. If you are unsure, install the latest binaries.
    
2. If you are upgrading from Microsoft Dynamics AX 2012, install the following application X++ fixes in the destination environment before you run the data upgrade:
    - KB 4033183 - Dynamics AX 2012 R2 or Dynamics AX 2012 R3 Pre-CU8 non-retail upgrade fails with Object not found for dbo.RETAILTILLLAYOUTZONE.
    - KB 4040692 - Dynamics AX 2012 R3 to Microsoft Dynamics 365 for Operations 7.2 upgrade fails on RetailSalesLine duplicate index on SalesLineIdx.
    - KB 4035490 - Performance issue with GeneralJournalAccountEntry MainAccount field upgrade script.


Follow these steps to run the Environment reprovisioning tool.

1. In the Shared asset library, select **Software deployable package**.
2. Download the Environment reprovisioning tool.
3. In the asset library for your project, select **Software deployable package**.
4. Select **New** to create a new package.
5. Enter a name and description for the package. You can use **Environment reprovisioning tool** as the package name.
6. Upload the package that you downloaded earlier.
7. On the **Environment details** page for your target environment, select **Maintain** > **Apply updates**.
8. Select the Environment reprovisioning tool that you uploaded earlier, and then select **Apply** to apply the package.
9. Monitor the progress of the package deployment. 

For more information about how to apply a deployable package, see [Apply a deployable package](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install a deployable package](../deployment/install-deployable-package.md).
