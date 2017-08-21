When copying a database between environments, you will need to run the environment re-provisioning tool before the copied database is fully functional, to ensure that all Retail components are up-to-date.

> [!IMPORTANT]
> We recommend that you run this procedure whether you are using Retail components or not, because Retail functionality is included in all environments. 

Before you continue, you must make sure that the following prerequisites are met:

1. If your target enviornment is running the July 2017 release or later, apply KB 4035399. 
2. If your target environment is running the November release (version 1611), apply the following hotfixes:
  -   KB 4025631
  -   KB 4035355
  -   KB 4035492
  -   KB 4010947
3. The default channel database and the default channel data group must be named **Default**. If you've renamed them, you must change the names back.

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
