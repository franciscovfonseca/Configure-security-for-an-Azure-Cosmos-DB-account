<br>

<p align="center">
<img width="500" src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/5795419a-3012-4a57-b4b0-155c2dd93fc7" alt="Microsoft Active Directory Logo"/>
<br>
<br>
<br>



<h1> Configure Security for an Azure Cosmos DB Account</h1>
<br>

In this exercise, you will configure security for an Azure Cosmos DB account.

1. First, you will create a Cosmos DB account, and then you will create a container.

2. Next, you will populate the container with items, and then you will configure secure access.

3. Finally, you will access the data by using the Core (SQL) API and role-based access control (RBAC) for security.

<br>


Azure Cosmos DB is a non-relational, NoSQL distributed database that is designed for the cloud.

It supports high volume and low latency for capturing big data.
<br>

<br>

<h2>1️⃣ Create a Cosmos DB Account</h2>
<br>

### ✔️ In this task, you will create and secure an Azure Cosmos DB account that contains data.
<br>

1. First, you will create an Azure Cosmos DB account.
2. Next, you will create a container in a new database, and then you will populate the container with items. 
3. Finally, you will access the data by using the Core (SQL) API.
<br>

<br>

◻️ On the Azure portal menu, select **Create a resource** to display the Azure Marketplace.

<br>

◻️ In Search services and marketplace, search for and select ***🆃 Azure Cosmos DB***, and then select **Create**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the Select API option page, in Core (SQL) - Recommended, select **Create**.

<br>

◻️ On the Create Azure Cosmos DB Account blade, complete the Basics page by using the values in the following table. For any property that is not specified, use the default value.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ Select **Next : Global Distribution**.

<br>

◻️ On the Global Distribution page, in Geo-Redundancy, select **Disable**, and then in Multi-region Writes, select **Disable**.

<br>

◻️ Select **Review + create**, review the configuration, select **Create**, and then wait for the deployment to complete.

- It will take approximately 3–5 minutes to deploy the Azure Cosmos DB account.
<br>

<br>

◻️ When you are presented with a **Your deployment is complete** message, select **Go to resource** to display the cdb42241754 Azure Cosmos DB account page.

<br>

<br>

◻️ On the cdb42241754 resource menu, select **Quick start**, and then select **Create 'Items' container**.

- 💡 You create a container in a database.
  
  - In the Azure portal, you can create a database at the same time as the first container.
    
  - In this case, a container named Items will be created in a new database named ToDoList for a sample application.
<br>

<br>

◻️ Select **Open Data Explorer**.

<br>

◻️ On the Data Explorer page, in SQL API, expand **ToDoList**, expand **Items**, select **Items**, and then on the command bar, select **New Item**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the Items page, replace the existing code with the following JavaScript object notation (JSON) code:

```commandline
{
    "firstName": "Chip",
    "lastName": "Oneal",
    "age": 26,
    "salary": 90000.00,
    "company": "Veraq",
    "isVested": false
}
```

- The Data Explorer intellisense feature may generate extra indentation and braces { }.
- Delete any extra braces to prevent errors.
- The extra indentation should not cause errors.
<br>

<br>

◻️ On the command bar, select **Save** to save the new item.

- You may need to select the ellipsis (…) to see the Save option.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the command bar, select **New Item**.

<br>

◻️ On the Items page, replace the existing code with the following JSON code:

```commandline
{
    "firstName": "Pat",
    "lastName": "Oneal",
    "company": "Veraq"
}
```
<br>

<br>

◻️ On the command bar, select **Save** to save the new item.

<br>

◻️ On the command bar, select **New SQL Query**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ You should see the following default query:

```commandline
    SELECT * FROM c
```
<br>

<br>

◻️ On the command bar, select **Execute Query**, and then review the results.

- You may need to select the (…) to see the Execute Query option.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

- The two items you created should be displayed.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>



<br>
<br>

<h2>2️⃣ Configure Security for the Cosmos DB Database</h2>
<br>

### ✔️ In this task, you will limit network access to the Cosmos DB account to a specific IP address
### ✔️ Then you will assign RBAC security permissions to a user.
<br>

<br>

◻️ On the cdb42241754 resource menu, in Settings, select **Firewall and virtual networks**.

- Note that, currently, the Cosmos DB account is accessible from all networks.
<br>

<br>

◻️ On the Firewall and virtual networks page, in Allow access from, select **Selected networks**.

<br>

◻️ In Firewall, select **Add my current IP**.

<br>

◻️ In Exceptions, select **Accept connections from within public Azure datacenters**, and then ensure that **Allow access from Azure Portal** is selected.

<br>

◻️ Select Save to update the Firewall and virtual networks settings.

- Wait for the update to complete. This will take approximately 1–2 minutes.
<br>

<br>

◻️ On the cdb42241754 resource menu, select **Access control (IAM)**

<br>

◻️ On the Access control (IAM) page, on the command bar, select **Add**, and then select **Add role assignment**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the Add role assignment blade, on the Role page, select ***🆃 Cosmos DB Account Reader Role***, and then select **Next**.

<br>

◻️ On the Members page, select **Select members**, search for and select ***🆃 dev-42241754***, and then select **Select**.

<br>

◻️ On the Add role assignment blade, select **Next**, and then select **Review + Assign** to assign the role to the user.
<br>


<br>
<br>


<h2>3️⃣ Test Access to the Cosmos DB Database</h2>
<br>

### ✔️ In this task, you will test network access to the Cosmos DB account.
<br>

<br>

◻️ Open an InPrivate or incognito browser window:

- Go to the Azure portal at ***🆃 http://portal.azure.com***, and then sign in as ***🆃 dev-42241754*** using ***🆃 cDeC3e!0D@*** as the password.

- You will use this browser session for the remaining steps in this task.
<br>

<br>

◻️ If prompted to stay signed in, select **No**.

<br>

◻️ On the Azure portal home page, select **All resources**, and then select the **cdb42241754** Azure Cosmos DB account.

<br>

◻️ On the cdb42241754 resource menu, select **Data Explorer**.

<br>

◻️ On the Data Explorer page, in SQL API, expand **ToDoList**, expand **Items**, select **Items**, and then on the command bar, select **New Item**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the Items page, replace the existing code with the following JSON code:

```commandline
{
    "firstName": "Harry",
    "lastName": "Oneal",
    "company": "Veraq"
}
```
<br>

<br>

◻️ On the command bar, select **Save** to attempt to save the new item.

- You may need to select the ellipsis (…) to see the Save option.

- ⚠️ The operation should fail.

  - You should see a ***The input authorization token can't serve the request message*** because the user has read-only access.
<br>

<br>

◻️ Review the failure message, and then select **Close**.

<br>

◻️ On the command bar, select **New SQL Query**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Create-and-manage-a-SAS-key/assets/172988970/a7da6891-3630-4da5-b8da-62ab6b63a1c3" height="40%" width="40%" alt="9"/><br />
<br>

<br>

◻️ On the command bar, select **Execute Query**, and then review the results.

- The two items you created should be displayed because the user has read-only access.

<br>

<br>
<br>
<br>

