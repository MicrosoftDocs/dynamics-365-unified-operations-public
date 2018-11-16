If you copy a database between environments, the copied database won't be fully functional until you run the Environment reprovisioning tool to make sure that all Retail components are up to date.

> [!IMPORTANT]
> We recommend that you complete this procedure even if you don't use Retail components, because Retail functionality is included in all environments. 

Before you continue, you must make sure that the following prerequisites are met:

1. The appropriate updates are applied to the target environment:

    - If the target environment runs the 7.3 release (December 2017), apply this update:

        - KB 4091254

    - If the target environment runs the July 2017 release (7.2), apply these updates:

        - KB 4035399
        - KB 4045801
        - KB 4091255

    - If the target environment runs version 1611 (November 2016, the 7.1 release), apply these updates:

        - KB 4025631
        - KB 4035355
        - KB 4035492
        - KB 4010947

2. Both the default channel database and the default channel data group must be named **Default**. If you've renamed them, you must change the names back.

Follow these steps to run the Environment reprovisioning tool.

1. In the Shared asset library, select **Software deployable package**.
2. Download the Environment reprovisioning tool.
3. In the asset library for your project, select **Software deployable package**.
4. Select **New** to create a new package.
5. Enter a name and description for the package. You can use **Environment reprovisioning tool** as the package name.
6. Upload the package that you downloaded earlier.
7. On the **Environment details** page for your target environment, select **Maintain** \> **Apply updates**.
8. Select the Environment reprovisioning tool that you uploaded earlier, and then select **Apply** to apply the package.
9. Monitor the progress of the package deployment. 

For more information about how to apply a deployable package, see [Apply a deployable package](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install a deployable package](../deployment/install-deployable-package.md).
