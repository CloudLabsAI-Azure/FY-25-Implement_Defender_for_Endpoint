# Lab 1 - Configure Sentinel Workbooks and Detection Rules

## Exercise 1: Configure Sentinel Workbooks

## Lab Overview
Microsoft Sentinel allows you to create custom workbooks across your data and comes with built-in workbook templates to allow you to quickly gain insights across your data as soon as you connect a data source.

## Lab scenario
You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. Once you have connected your data sources to Microsoft Sentinel, you can visualize and monitor the data using the Microsoft Sentinel adoption of Azure Monitor Workbooks, which provides versatility in creating custom dashboards. 

## Lab objectives 
 In this lab, you will Understand the following:
 - Task 1: Create Sentinel Workspace
 - Task 2: Connect the Windows security event connector
 - Task 3: Save and modify a workbook template
 - Task 4: Create a Workbook

### Task 1: Create Sentinel Workspace

In this task, you will create a Microsoft Sentinel workspace where you will be monitoring and analyzing security events in upcoming labs.

1.  On Azure Portal page, in **Search resources, services and docs (G+/)** box at the top of the portal, enter **Microsoft Sentinel**, and then select **Microsoft Sentinel** under services.

    ![Picture 1](media/image_7.png)

1. From the Microsoft Sentinel page, select **+ Create**.

1. From Add Microsoft Sentinel to a workspace, select **+ Create a new workspace**.

1. From the basics tab of the Create Log Analytics workspace, enter the following and click **Review + Create**.   

    | Setting | Action |
    | -- | -- |
    | Subscription | Retain the default Subscription.  |
    | Resource group | select ResourceGroup(sentinel-rg). |
    | Name | Set the name to 'sentinelworkspace'. |
    | Region | Retain the default region. |
    |||

    ![Picture 1](media/Log22.png)

1. Verify the information you entered then select **Create**.

1. If you don’t see the new workspace listed, select **Refresh**, then select the newly created workspace **sentinelworkspace** and click on **Add**.

   ![Picture 1](media/Log33.png)

1. Once the new workspace is added, the Microsoft Sentinel | News & guides page will display, including that the Microsoft Sentinel free trial is activated. Select **OK**. Note the 
   three steps listed on the Get Started page.

   ![Picture 1](media/image_8.png)
   
   ![Picture 1](media/ex-1-2.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:.
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
   
<validation step="334fdf37-4cce-4af9-ac55-73608002b9e6" />

### Task 2: Connect the Windows security event connector

1. Open a browser and go to the **Microsoft Defender portal**: https://security.microsoft.com. **Sign in** using your lab credentials.

1. In the **Microsoft Defender** portal, select **Microsoft Sentinel (1)** from the left navigation menu. Expand **Content management (2)** and click **Content hub (3)**.

    ![Picture 1](media/gs-ed-p_3.png)

      > **Note:** If you are not able to see the **Content hub** load, it may take up to 10-15 minutes to complete.

      > **Note:** If you are already able to see the **Content hub** load, it means the workspace is ready.

1. On the **Content hub** page, type **Windows Security Events (1)** in the search bar and press **Enter**, then select **Windows Security Events (2)** from the results.  

    ![Picture 1](media/gs-ed-p_4.png)

1. On the **Windows Security Events** details page, review the description and available connectors, then click **Install** to add the solution.  

    ![Picture 1](media/gs-ed-p_5.png)

1. On the **Content hub** page, type **Azure Activity (1)** in the search bar and press **Enter**, then select **Azure Activity (2)** from the results and click **Install (3)** on the details pane. 

    ![Picture 1](media/gs-ed-p_6.png)

1. After receiving the notification of a successful installation, return to the **Data Connector** page and click on the **Refresh** button to ensure that the changes take effect.

    ![Picture 1](media/gs-ed-p_7.png)

1. You should observe three options: **Security Events Via Legacy Agent**, **Windows Security Event Via AMA** and **Azure Activity**

1. Choose **Security Events Via Legacy Agent**, and then click on **Open connector page**.

    ![Picture 1](media/gs-ed-p_8.png) 
   
1. In the configuration section, opt for **Install Agent on Azure Windows Virtual Machine (1)**, and then choose **Download & Install Agent for Azure Windows Virtual Machines (2)**.

    ![Picture 1](media/t3_g_e2_7.png) 

1. Select the **svm-<inject key="DeploymentID" enableCopy="false" />** virtual machine and click on **Connect**.

    ![Picture 1](media/t3_g_e2_8.png) 

1. On the virtual machine page, click **Connect** to link the VM to Log Analytics.

    ![Picture 1](media/t3_g_e2_9.png)

1. Select the **Virtual Machine** link from the top.

    ![Picture 1](media/t3_g_e2_10.png)

1. On the virtual machine page, select the **s2vm-<inject key="DeploymentID" enableCopy="false" />** virtual machine and click on **Connect**. Wait until get connected.

    ![Picture 1](media/t3_g_e2_11.png)

1. On the second virtual machine page, click **Connect** to link the VM to Log Analytics.

    ![Picture 1](media/t3_g_e2_12.png)

1. Select the **Virtual Machine** link from the top.

    ![Picture 1](media/t3_g_e2_13.png)

1. Verify that both virtual machines **s2vm-<inject key="DeploymentID" enableCopy="false" />** and **svm-<inject key="DeploymentID" enableCopy="false" />** display **This workspace (1)** under the **Log Analytics Connection** column, then click **Security Events via Legacy Agent (2)** in the breadcrumb to return to the connector page.

    ![Picture 1](media/t3_g_e2_14.png)

1. In the **Instructions** section, under **Select which events to stream**, choose **All Events (1)** and click **Apply changes (2)**.

    ![Picture 1](media/t3_g_e2_15.png)

1. On the **Data connectors** page, locate **Security Events via Legacy Agent** from the list and click **Refresh** if needed to update the status.  

    ![Picture 1](media/gs-ed-p_9.png)      

1. On the **Data connectors** page, verify that the status of **Security Events via Legacy Agent** is now shown as **Connected**.  

    ![Picture 1](media/gs-ed-p_10.png)

### Task 3: Save and modify a workbook template

In this task, you will save the Microsoft Sentinel workbook templates.

1. In the **Microsoft Defender portal**, under **Threat management (1)**, select **Workbooks (2)** and then click on **Azure Activity (3)** from the available templates.  

    ![Picture 1](media/gs-ed-p_11.png)

5. Scroll down again and select the **Save** button for the *Azure Activity* workbook. 

    ![Picture 1](media/gs-ed-p_12.png)

6. Leave **East US** as the default value for *Region* and select **Yes**.

    ![Picture 1](media/gs-ed-p_13.png)

7. Select the **View saved workbook** button.

    ![Picture 1](media/log-1090.png)

8. On the top select **Open in Azure**.

    ![Picture 1](media/log-10090.png)

9. Select **Edit** in the command bar to enable changes in the workbook.

    ![Picture 1](media/gs-ed-p_14.png)    

10. Scroll down to the **Caller activities** area, and look at the color of the *Activities* column since we are going to format those columns. Select the **Edit** button below the grid and select the **ellipsis (...) > +Add > Add query**.

     ![Picture 1](media/editcaller.png)

     ![Picture 1](media/ex-1-11.png)

11.  Type **SecurityEvent (1)** into the query box and click on **Run Query (2)** then select the **Column Settings (3)** button, which appears after clicking the **Run Query** button. 
    
        >**Hint:**  This button only appears  if there  is data from the KQL query.

        ![Picture 1](media/updateu.png)
   
12. On the **Settings (1)** tab, scroll through the list of columns and select **Activity (Automatic) (2)** to include it in the workbook view.

    ![Picture 1](media/gs-ed-p_15.png)

13. On the **Edit column settings** page, change the **Column renderer (1)** to **Heatmap**, set the **Color palette (2)** to **32-color categorical**, and then click **Save and Close (3)** to apply the changes. 

    ![Picture 1](media/gs-ed-p_16.png)

15. Select **Done Editing** at the bottom of the query (not the top menu).

    ![Picture 1](media/gs-ed-p_17.png)

16. Now select **Done Editing** at the top menu and select the **Save** icon.

    ![Picture 1](media/gs-ed-p_18.png)

    ![Picture 1](media/gs-ed-p_19.png)

17. Close the workbook by selecting the **X** in the top-right corner.

### Task 4: Create a Workbook

In this task, you will create a new workbook with advanced visualizations.

1. Navigate back to the **Microsoft Defender** portal, from the left navigation menu select **Workbooks (1)** and select **+ Add Workbook (2)** to create a new workbook from scratch.
 
    ![Picture 1](media/log090-0.png)

    >**Note:** Although it is a new workbook, a startup template is used.

2. To edit the workbook, select **Edit**.

    ![Picture 1](media/lab16-image2.png)

3. Select the **Edit** button below the new workbook overview of the workbook.

    ![Picture 1](media/lab16-image3.png)

4. Type *# My workbook* in a new line on top of *## New workbook* and select **Done Editing** on the bottom of this section, *Editing text item: text - 2*. Notice that 
   your header increased in size and name changed.

    ![Picture 1](media/lab16-image4.png)

5. Select **Edit** below the only visible bar chart graph.

    ![Picture 1](media/lab16-image5.png)

6. Review the KQL statement that provides a *union* statement of counts across all tables.

7. Scroll down and select the **Done Editing** on the bottom menu, for the *Editing query item: query - 2*.

8. Select the ellipsis **...** next to the *Edit* button of the bar chart graph, then select **+ Add**, then select **Add query**.

    ![Picture 1](media/lab16-image6.png)

9. Type **SecurityEvent** into the query box.

    ![Picture 1](media/lab16-image7.png)
  
10. Change the *Time Range* to **Last hour(1)** and  *Visualization* to **Time chart(2)** and select the **Style(3)** tab from the query's command bar.

     ![Picture 1](media/lab16-image8.png)

11. Select the **Make this item a custom width** box and set the *Percent width* to **25** and *Maximum width* to **25**.

     ![Picture 1](media/lab16-image9.png)

12. Now select **Advanced Settings(1)** tab from the query's command bar and select **Show refresh icon when not editing(2)** box, scroll down and select **Done Editing(3)** on the bottom menu, 

     ![Picture 1](media/lab16-image10.png)

13. Scroll down and at the bottom of the workbook select **+ Add**, then **Add query**.

     ![Picture 1](media/addquery.png)

14. Type **SecurityEvent** into the query box.

15. Change the *Time Range* to **Last hour (1)**.

16. Change the *Visualization* to **Grid (2)**.

     ![Picture 1](media/grid.png)

17. Select **Style** from the query's command bar.

18. Select **Make this item a custom width** box.

19. Set the *Percent width* to **75** and *Maximum width* to **75**.

     ![Picture 1](media/75.png)

20. Scroll down and select **Done Editing** on the bottom menu, for the new *Editing query item: query - 3*.

21. Select **Done Editing** in Workbook's top command bar.

22. Select the **Save** icon, change the *Title* to **My Workbook** and Select **sentinel-rg** resource group, click on **Apply** to commit the changes. 
 
     ![Picture 1](media/lab16-image11.png)

23. Close the workbook by selecting the **X** at the top-right or select **Workbooks** in the Microsoft Sentinel portal.

24. Back in the *Workbooks* page, select the **My workbooks** tab.

25. Select the workbook you just created, **My workbook**.

26. On the right pane, select **View saved workbook** to review your workbook.

     ![Picture 1](media/ex-1-15.png) 

### Conclusion
 Connecting data to Microsoft Sentinel enables you to monitor and visualize it using custom dashboards in Azure Monitor Workbooks, improving threat detection and response.

### Review
 In this lab, you will Understand following:
 - Saved and modify a workbook template
 - Created a Workbook

## You have successfully completed the exercise. Click on Next to Continue

![](media/gs-ed-p_0.png)