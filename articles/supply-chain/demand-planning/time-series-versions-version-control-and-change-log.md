# Time series versions, version control, and change log

Demand planning lets you edit cell values directly, which means that you can modify the underlying data for any time series. Each time you do this, the change is noted in the change log, where all users can see when the change was made and who made it. At any time, you can save your edits so far (since the last version) as a new version, which you can give a name. You can view any version by selecting it in the version history, and you can restore any previous version to the current version.

Sometimes, when you're selecting a time series, you'll be able to choose which version to use. For example, when you use **Select data** to overlay one time series over the current one, you can choose which version to use. You can even overlay a previous version of the same time series to quickly see what changed between versions.

To view the change log and version history for a time series, open the time series and then select **Version history** from the Action Pane. The **Version history** panel opens, which shows a log entry for each relevant edit event, with log entries grouped under the version where they apply.

The following illustration highlights the features of the **Version history** panel.

![A screenshot of a computer Description automatically generated](media/image12.png)

Legend:

1. **Save changes as current version** – Select this button to save a new version that includes all of the changes made since the last saved version. You'll be asked to provide a version name.

2. **Time series version** – Each saved version shows its version name next to a blue dot on the timeline. Select a version to view it in the graph and data table. You can collapse or expand each version to hide or view the log of edits made to create that version. The top version is always the current version, which may include edits made since the last saved version.

3. **Change log entry** – Change log entries are nested below the version where they were made. Each entry shows the date and time the change was made and the user who made it.

4. **Initial version** – The initial version and its change log entry represent the time series creation event. It's always saved as a version so you can easily view or restore it as needed.

5. **Version edit button** – Select this button to open a menu where you can select any of the following actions:

    - **Rename** – Lets you enter a new name for the version.

    - **Restore** – Makes the selected version the current version.

    - **Deactivate** – Deactivates the selected version but doesn't affect the values of newer versions. Deactivated versions aren't shown in version selectors.

    - **Activate** – Reactivates an inactive version.

