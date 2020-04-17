If you copy a database between environments, the copied database won't be fully functional until you run the Environment reprovisioning tool to make sure that all Commerce components are up to date.

Follow these steps to run the Environment reprovisioning tool.

1. In your project's **Asset Library**, in the **Software deployable packages** section, click **Import**.
2. From the list of shared assets, select the **Environment Reprovisioning Tool**.
3. On the **Environment details** page for your target environment, select **Maintain** > **Apply updates**.
4. Select the **Environment Reprovisioning** tool that you uploaded earlier, and then select **Apply** to apply the package.
5. Monitor the progress of the package deployment.

For more information about how to apply a deployable package, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

> [!IMPORTANT]
> Some environment specific records cannot be moved along with the database from the source to the target environment. The following records are not moved to the target environment:
> - Commerce Self-Service installers
> - Commerce Scale Unit channel database configuration record

### Database refresh and Commerce Scale Units

As part of database refresh, scale unit channel database records (in the Channel Database form) cannot be moved across environments since they represent environment specific configuration.

For **Commerce Scale Units**, you can regenerate the channel database record by issuing a re-deployment of your scale units in LCS. For more information, see [Refresh database](../database/database-refresh.md) and [Initialize Retail Cloud Scale Unit](../deployment/Initialize-Retail-Channels.md).

### Database refresh and Commerce Self-Service installers

Self-service installers are stored in environment specific storages that cannot be moved along with the database.

Installers are uploaded to the environment as part of a deployable package. The application and binary packages provided by Microsoft will contain the Microsoft provided installers. The deployable package produced by extensions through the Retail SDK will contain the extended installers. To make installer section available after database refresh, please apply the desired deployable package to the environment after database refresh.
