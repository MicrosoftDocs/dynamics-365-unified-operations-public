> [!IMPORTANT]
> Some environment-specific records are not included in automated database movement operations and require additional steps. These include the following:
> - Commerce self-service installer references
> - Commerce Scale Unit channel database configuration records

If you copy a database between environments, Commerce capabilities in the destination environment will not be fully functional until you perform the following additional steps.

### Initialize Commerce Scale Units
If you are moving a database to a sandbox UAT or production environment, you must [Initialize Commerce Scale Unit](../deployment/Initialize-Retail-Channels.md) after the database movement operation is complete. The Commerce Scale Unit's association from the source environment will not copy over to the destination environment. 

### Synchronize Commerce self-service installers
To be able to access Commerce self-service installers in HQ, you must [Synchronize self-service installers](../../../commerce/dev-itpro/synchronize-installers.md) after the database movement operation is complete.

> [!IMPORTANT]
> The Environment re-provisioning step has now been fully automated as part of database movement operations, and no longer needs to be run manually. The Environment re-provisioning tool is still available in the Asset Library and may be used in certain situations to mitigate error conditions. 

To run the Environment re-provisioning tool on the destination environment, run the following steps:

1. In your project's **Asset Library**, in the **Software deployable packages** section, select **Import**.
2. From the list of shared assets, select the **Environment Reprovisioning Tool**.
3. On the **Environment details** page for your destination environment, select **Maintain** > **Apply updates**.
4. Select the **Environment Reprovisioning** tool that you uploaded earlier, and then select **Apply** to apply the package.
5. Monitor the progress of the package deployment.

For more information about how to apply a deployable package, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

### Re-activate POS devices

If you use point of sale (POS) devices, after you import a database you must activate the POS devices again. Previously activated devices in the destination environment will no longer function. For more information, see [Point of sale device activation](../../../commerce/dev-itpro/retail-device-activation.md).