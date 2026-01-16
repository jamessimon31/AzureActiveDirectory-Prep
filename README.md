# Part 1 - Azure AD Lab: Prepuration and Infrastructure 
## Overview
In this part of the lab, you will set up a **Windows Server 2022 Domain Controller** and a **Windows 10 client** in Microsoft Azure. These virtual machines will be reused in future AD labs.

---

## Network Diagram 

<img width="733" height="595" alt="image" src="https://github.com/user-attachments/assets/a628b8b5-203b-4bd1-9a07-f7f2b14838fc" />


---

## Part 1: Set Up the Domain Controller (DC-1)

### Step 1: Create a Resource Group

![Create Resource Group](screenshots/create-resource-group.png)

1. Sign in to the **Azure Portal**
2. Create a new **Resource Group**
3. Choose a region and name it (e.g., `AD-Lab-RG`)

---

### Step 2: Create a Virtual Network and Subnet

![Create Virtual Network](screenshots/create-vnet.png)

1. Create a **Virtual Network (VNet)**
2. Create a **Subnet**
3. Ensure all VMs will use this same VNet

---

### Step 3: Create the Domain Controller VM (DC-1)

![Create DC-1 VM](screenshots/create-dc1-vm.png)

1. Create a new **Virtual Machine**
2. Use the following settings:
   - **VM Name:** DC-1
   - **OS:** Windows Server 2022
   - **Username:** labuser
   - **Password:** Cyberlab123!
3. Place the VM in the same **Resource Group**, **Region**, and **VNet**
4. Complete the deployment

---

### Step 4: Set DC-1 Private IP Address to Static

![Set Static Private IP](screenshots/set-static-ip-dc1.png)

1. Go to **DC-1 → Networking → Network Interface**
2. Open **IP configurations**
3. Change **Private IP** from Dynamic to **Static**
4. Save changes

---

### Step 5: Disable Windows Firewall (Testing Only)

![Disable Windows Firewall](screenshots/disable-firewall.png)

1. Log into **DC-1**
2. Open **Windows Defender Firewall**
3. Turn off firewall for:
   - Domain
   - Private
   - Public

> ⚠️ This is for lab testing only

---

## Part 2: Set Up Client-1

### Step 6: Create the Client VM (Client-1)

![Create Client-1 VM](screenshots/create-client1-vm.png)

1. Create a new **Virtual Machine**
2. Use the following settings:
   - **VM Name:** Client-1
   - **OS:** Windows 10
   - **Username:** labuser
   - **Password:** Cyberlab123!
3. Ensure it is in:
   - The **same region**
   - The **same Virtual Network** as DC-1

---

### Step 7: Configure Client-1 DNS Settings

![Client-1 DNS Settings](screenshots/client1-dns-settings.png)

1. Go to **Client-1 → Networking → Network Interface**
2. Open **DNS Servers**
3. Select **Custom**
4. Enter **DC-1’s Private IP Address**
5. Save changes

---

### Step 8: Restart Client-1

![Restart Client-1](screenshots/restart-client1.png)

1. Restart **Client-1** from the Azure Portal

---

### Step 9: Test Network Connectivity

![Ping DC-1](screenshots/ping-dc1.png)

1. Log into **Client-1**
2. Open **PowerShell**
3. Run:
   ```powershell
   ping <DC-1 Private IP>
   ```

   ---

### Step 10: Verify DNS Configuration

1. Open PowerShell on Client-1
   
2. Run: ``ipconfig /all``
   
3. Confirm DNS Server Matches DC-1s Private IP
   

---

### Continue to [**Part 2-Deploying Active Directory**](https://github.com/jamessimon31/AzureActiveDirectory-Deploying)
