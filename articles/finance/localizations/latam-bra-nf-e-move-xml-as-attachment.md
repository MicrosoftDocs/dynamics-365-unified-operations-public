# Move NF-e XML files as attachments #

In the Brazilian localization, use this feature when it is necessary to free up database space consumed by the XML files created during issuing of electronic fiscal documents
(NF-e), which are stored into Microsoft Dynamics 365 Finance and Supply Chain Management database.

For a given range of dates, and for a given Fiscal establishment, this feature moves the NF-e XML files from Microsoft Dynamics 365 Finance and Supply Chain Management database
to the BLOB storage from your Azure subscription, making them available only as attachments. When the XML files are successfully moved to the BLOB storage, the original files
are deleted from the Microsoft Dynamics 365 Finance and Supply Chain Management database, releasing database space.

To enable the feature:

1. Login in Microsoft Dynamics 365 Finance and Supply Chain Management.
3. Navigate to Feature management workspace.
4. Select All tab.
5. Search for feature **NF-e XML move as attachment**.
6. Select the feature in the grid.
7. Select **Enable now**

To move the NF-e XML files as attachment:

1. Navigate to **Accounts receivable > Fiscal documents > Electronic fiscal documents > Move NF-e XML as attachments**.
2. Select the **From date** and the **To date**.
3. Select the **Fiscal establishment ID**.
4. Select **OK**.

**Important**: The process is not reversible and once moved, the NF-e XML files can be viewed only through the icon Attachments available on the top of Fiscal document page.

