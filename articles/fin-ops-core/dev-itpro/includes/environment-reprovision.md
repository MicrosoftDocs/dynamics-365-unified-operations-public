> [!IMPORTANT]
> When a Commerce headquarters database (previously called AOS database) is migrated, the associated Commerce Scale Units (CSUs) are not moved. In several cases, depending on the features that are in use, a CSU redeployment may be required. Redeployment must then be followed by a full synchronization of data to the CSU. In extreme scenarios where data discrepancies still exist, the final action is to delete the CSU, deploy a fresh CSU to replace it, and then perform a full synchronization of data to the new CSU.
> 
> Some environment-specific records are not included in automated database movement operations and require additional steps. These include the following:
> - Commerce self-service installer references.
> - Commerce Scale Unit channel database configuration records.

If you copy a database between environments, Commerce capabilities in the destination environment won't be fully functional until you perform the following additional steps.

### Initialize Commerce Scale Units
If you're moving a database to a sandbox user acceptance testing (UAT) or production environment, you must [Initialize Commerce Scale Unit](../deployment/Initialize-Retail-Channels.md) after the database movement operation is complete. The Commerce Scale Unit's association from the source environment won't copy over to the destination environment. 

### Synchronize Commerce self-service installers
To be able to access Commerce self-service installers in headquarters, you must [Synchronize self-service installers](../../../commerce/dev-itpro/synchronize-installers.md) after the database movement operation is complete.

> [!IMPORTANT]
> The environment reprovisioning step has now been fully automated as part of database movement operations, and no longer needs to be run manually. The environment reprovisioning tool is still available in the asset library, but is only required for restoring a database to a development environment running Commerce version 10.0.37 or earlier. For development environments running Commerce version 10.0.38 and later, the environment reprovisioning tool doesn't apply because these environments use a sealed CSU.  

To run the environment reprovisioning tool on the destination environment, run the following steps:

1. In your project's **Asset Library**, in the **Software deployable packages** section, select **Import**.
2. From the list of shared assets, select the **Environment Reprovisioning Tool**.
3. On the **Environment details** page for your destination environment, select **Maintain** > **Apply updates**.
4. Select the **Environment Reprovisioning** tool that you uploaded earlier, and then select **Apply** to apply the package.
5. Monitor the progress of the package deployment.

For more information about how to apply a deployable package, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

### Reactivate POS devices

If you use point of sale (POS) devices, you must activate the POS devices again after you import a database. Previously activated devices in the destination environment will no longer function. For more information, see [Point of sale device activation](../../../commerce/dev-itpro/retail-device-activation.md).
