# How to Convert and Export Posted Trade Agreement Lines

This article provides step-by-step instructions on how to convert posted trade agreement lines into unposted lines and export them. Microsoft Dynamics 365 standard data entities do not support the direct export of posted trade agreement lines. By following these steps, you can convert the posted lines to unposted ones, making them exportable.


## Convert and export posted trade agreement lines

Follow these steps to convert posted trade agreement lines into unposted lines and export them:
1. **Access active trade agreement lines:**

    Open your browser and navigate to the following URL, replacing <your-url> and <your_cmp_name> with your environment and company name values:

    https://<your-url>/?cmp=<your_cmp_name>&amp;mi=PriceDiscTable_PricePurchAction</your_cmp_name></your-url>

    This will open the page displaying all active sales or purchase prices.
2. **Select and edit the lines:**
    - Select all the lines or a subset of lines you want to export.
    - Click on the **Edit selected lines** button in the ribbon.
    ![image](https://github.com/user-attachments/assets/5845e27f-4654-4f43-8be5-9164ee168320)

3. **Assign to a journal:**
    - In the slider dialog that appears, select a journal name.
    - Click **OK**.

    This action converts the active price trade agreement lines into open trade agreement lines, which are now exportable.
![image](https://github.com/user-attachments/assets/aefa21fe-071f-47bc-81ce-6c3ac8d38078)

4. **Export the open trade agreement lines:**

    Once the lines have been converted to open trade agreements, you can proceed to export them.

![image](https://github.com/user-attachments/assets/c703927f-a80a-4331-b960-73cb5efa8958)


## Clean up resources

After exporting the data, ensure that any temporary journal entries used for the conversion process are deleted or archived to maintain data integrity and avoid clutter in your system.
