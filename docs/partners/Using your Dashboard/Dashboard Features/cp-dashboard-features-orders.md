# Orders


The Orders tab allows you to see order activity as it comes in, as well as commission statuses and performance.

![](images/cp-order-list.png)

The callouts are as follows:

1.  **Orders**
    

This header summarises the aggregate performance across your integrations.

**2\. Select Date Range**

This feature allows you to break down the analysis into custom time periods. Using the tool, you can see the performance for custom time periods.

**3\. Export Orders**

This feature allows you to download order data in CSV format. The CSV itself contains User data and event data information useful for reconciliation or analysis at the broad level. Clicking the button will send a CSV to your downloads, and can be opened using most spreadsheet analysis tools such as Excel or Google Sheets.

**4\. Order Line Item**

Each order or sign-up which is placed for a product will get its own line item as soon as it is created by the user. A few notes:

*   **Status** \- refers to the success/failure of the delivery of the order.
    
    *   Each journey type has a specific goal in terms of delivering the user data, so as long as this is met, the order status will be marked as SUCCESSFUL.
        
    *   If the status is marked PENDING , the system is awaiting confirmation from an external system that the order has been created and received: this is particularly common with affiliate URL driven products.
        
    *   Finally, if it is marked as FAILED , it means there is an issue with the mmob system with regard to data capture and delivery
        
*   **Comm Status** - refers to the status of the commission due for a User order/ signup. This is dependent on the **Status** initially:
    
    *   If an order’s **status** is anything other than SUCCESSFUL, then its corresponding **comm status** will be N/A
        
    *   If **status** is SUCCESSFUL, then **comm status** can be PENDING, meaning we are waiting on the service provider to confirm when the commission is/will be paid. The amount under PENDING will be logged in the Orders header above under **Commission Pending**
        
    *   Once the service provider has confirmed the commission, the order’s **comm status** will be updated to SUCCESSFUL, and the amount which was previously under **Commission Pending** will move to **Commission Paid**
        
    *   **Comm status** is updated by the service provider, which occurs either through API or manually. For this reason, the wait time to confirm commission for a given order can vary
        
