## Import of goods where there is GST

1. Click **Accounts payable > Purchase orders > All purchase orders**.

2. Create a purchase order for a foreign vendor account.

3. Save the record.

4. Click **Tax information**

   ![](media/Capture2019052101.PNG)

5. Click the **GST** tab

6. Click the **Customs** tab

   ![](media/Capture2019052104.PNG)

7. Click the **Vendor tax information** tab

   ![](media/Capture2019052103.PNG)

8. Click OK.

9. Click **Functions > Maintain charges**.

10. Select a **charges code**.

11. Select the **Assessable value** check box.

12. In the **Charges value** field, enter a value.

13. Save the record.

    ![](media/Capture2019052105.PNG)

14. Click Close

    ![](media/Capture2019052106.PNG)

Note: The assessable value is calculated as Net amount + Misc. charges + 1% of Landing charges that are defined in Accounts payable parameters

### Validate the tax details

15. On the Action Pane, on the **Purchase** tab, in the **Tax** group, click **Tax document**.
16. On the **Tax details** FastTab, review the tax calculation.

Example:

- BCD: 10 percent
- LOI: 100 percent
- IGST: 20 percent
- Import exchange rate: 1 USD = 52 INR

Note: IGST can be calculated on Assessable value + BCD tax amount, by extending the configuration.

17. Click Close.
18. Click **Confirm**.

### Update the invoice registration

19. On the Action Pane, on the **Customs** tab, in the **Maintain** group, click **Invoice registration**.
20. In the **Import invoice number** field, select a value.
21. Click **Update**.

### Post the bill of entry

22. On the Action Pane, on the **Customs** tab, in the **Generate** group, click **Bill of entry**.
23. In the **Import invoice number** field, select a value.
24. In the **Bill of entry number** field, select a value.
25. Click the **Lines** tab.
26. In the **Quantity** field, enter a value.
27. Close the message.
28. Click **Tax document**
29. Click Close.
30. Click OK

### Post the product receipt

31. On the Action Pane, on the **Receive** tab, in the Generate group, click Product receipt.
32. In the **Quantity** field, select **Bill of entry quantity**.
33. Enter the **Product receipt**.
34. Click OK.

Sample Journal Entry for Import Purchase Order with GST

![](media/Annotation 2019-05-20 165539.png)
