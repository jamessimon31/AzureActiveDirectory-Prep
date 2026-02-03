# Part 1 - Azure AD Lab: Prepuration and Infrastructure 
## Overview
In this part of the lab, you will set up a **Windows Server 2022 Domain Controller** and a **Windows 10 client** in Microsoft Azure. These virtual machines will be reused in future AD labs.

---

## Network Diagram 

<img width="733" height="595" alt="image" src="https://github.com/user-attachments/assets/a628b8b5-203b-4bd1-9a07-f7f2b14838fc" />


---

## Part 1: Set Up the Domain Controller (DC-1)

### Step 1: Create a Resource Group

<img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/7199188b-45d2-47f9-be8d-5abe00bfe6f1" />


1. Sign in to the **Azure Portal**
2. Create a new **Resource Group**
3. Choose a region and name it (e.g., `ActiveDirectoryLab`)

---

### Step 2: Create a Virtual Network and Subnet

<img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/3f698fc1-a809-447b-a570-377c6b6f8901" />

1. Create a **Virtual Network (VNet)**
2. Create a **Subnet**
3. Ensure all VMs will use this same VNet

---

### Step 3: Create the Domain Controller VM (DC-1)

1. Create a new **Virtual Machine**
2. Use the following settings:
   - **VM Name:** DC-1
   - **OS:** Windows Server 2022
   - **Username:** labuser
   - **Password:** Cyberlab123!
3. Place the VM in the same **Resource Group**, **Region**, and **VNet**

   <img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/39cb001a-54c9-4e64-9b0b-5fa680707952" />

4. Complete the deployment

---

### Step 4: Set DC-1 Private IP Address to Static

<img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/809b2fb5-194e-4b77-b3b0-a87cfe51f8c2" />

1. Go to **DC-1 → Networking → Network Interface**
2. Open **IP configurations**
3. Change **Private IP** from Dynamic to **Static**
4. Save changes

<img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/82d57b79-1480-4d8f-b1eb-b2180582fb89" />

---

### Step 5: Disable Windows Firewall (Testing Only)

![Disable Windows Firewall](screenshots/disable-firewall.png)

1. Log into **DC-1**
2. Open **Windows Defender Firewall**

   <img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/f2b9421a-34f0-40e9-8adf-8aee76e7c90b" />

3. Turn off firewall for:
   - Domain
   - Private
   - Public

     
  
   <img width="50%" height="50%" alt="image" src="https://github.com/user-attachments/assets/a0dc82ca-319a-420c-97b6-aaaf41b262dd" />


> ⚠️ This is for lab testing only

---

## Part 2: Set Up Client-1

### Step 6: Create the Client VM (Client-1)

<img width="468" height="278" alt="image" src="https://github.com/user-attachments/assets/d5a0b12a-8c13-4bfb-80e4-148e352f1bc4" />


1. Create a new **Virtual Machine**
2. Use the following settings:
   - **VM Name:** Client-1
   - **OS:** Windows 10
   - **Username:** labuser
   - **Password:** Cyberlab123!
3. Ensure it is in:
   - The **same region**
   - The **same Virtual Network** as DC-1
     
<img width="468" height="231" alt="image" src="https://github.com/user-attachments/assets/6d4188c1-b3cd-4d58-9129-a6eacb568dc8" />

---

### Step 7: Configure Client-1 DNS Settings


<img width="440" height="221" alt="image" src="https://github.com/user-attachments/assets/13524e2b-1296-4cdd-87c9-ebc10f52e44d" />


1. Go to **Client-1 → Networking → Network Interface**
2. Open **DNS Servers**
3. Select **Custom**
   
<img width="451" height="215" alt="image" src="https://github.com/user-attachments/assets/5a20d500-385f-481a-90ad-246b04723326" />

<img width="468" height="262" alt="image" src="https://github.com/user-attachments/assets/cf037625-451c-4913-a0f9-46953a3da1c0" />

4. Enter **DC-1’s Private IP Address**
5. Save changes

---

### Step 8: Restart Client-1

<img width="468" height="183" alt="image" src="https://github.com/user-attachments/assets/afff4b33-23ef-4dd5-ad01-57eb8fe686b3" />

1. Restart **Client-1** from the Azure Portal

---

### Step 9: Test Network Connectivity

<img width="404" height="228" alt="image" src="https://github.com/user-attachments/assets/dacb00a3-3255-41e1-814c-6a4eb0363b30" />

1. Log into **Client-1**
2. Open **PowerShell**
3. Run:
   ```powershell
   ping <DC-1 Private IP>
   ```

   ---

### Step 10: Verify DNS Configuration

<img width="468" height="366" alt="image" src="https://github.com/user-attachments/assets/c163f24d-3e2e-4853-b0a4-62a0901422c8" />

1. Open PowerShell on Client-1
   
2. Run: ``ipconfig /all``
   
3. Confirm DNS Server Matches DC-1s Private IP
   

---

### Continue to [**Part 2-Deploying Active Directory**](https://github.com/jamessimon31/AzureActiveDirectory-Deploying)

