To import a database prepared from a developer environment to a standard user acceptance test (UAT), or a database previously exported from a UAT environment please follow the process outlined below:

1. Visit your target sandbox **Environment Details** page , and click the **Maintain** > **Move database** menu option.
2. Select the **Import database** option and choose your source database backup (.bacpac format) file from the Asset Library.
3. Note the warnings and review the list of data elements that are cleaned up from the backup file.
4. The import operation will begin immediately.
5. After the import operation is completed, you must **Sign off** on the operation before you can perform another servicing operation, such as package deployment, database movement, or upgrade.