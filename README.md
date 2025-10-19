# 🔹 ServiceNow Change Request Workflow

## 📘 Overview
This project demonstrates a **Change Request Management Workflow** built in **ServiceNow** using Flow Designer, Client Scripts, and Business Rules.  
It automates the change request lifecycle — from submission and approval to implementation and closure — providing a practical example of ITSM automation skills.

---

## 🎯 Goal
To design and implement an automated **Change Request Workflow** that includes:
- Dynamic request numbering (`CHG0001`, `CHG0002`, etc.)
- Multi-stage lifecycle management
- Manager-based approval process
- Automatic date updates and UI behavior control

---

## ⚙️ Features Implemented

### 1. **Auto Request Numbering**
Automatically generates sequential numbers like `CHG0001`, `CHG0002`, etc., when a new record is created.

### 2. **Workflow Stages**
`Draft → Review → Approval → Implementation → Closed`

### 3. **Approval Workflow**
- When the state = “Review”, the system sends the request for **Manager approval**.  
- The flow waits for the approval result before proceeding.
- If approved → State changes to **Implementation**  
- If rejected → State reverts to **Draft/Rejected**

### 4. **Client Script**
Disables the *Implementation Plan* field if the state is not “Approved”.

### 5. **Business Rule**
When the state changes to “Closed”, the system automatically updates the **Closed Date**.

### 6. **Custom Table**
Created a custom table:  
`u_mini_change_request_user`  
Used to store and manage custom change request records.

---

## 🧩 Flow Designer Details
**Trigger:** Record Created or Updated on `u_mini_change_request_user`

**Conditions:**
- If Category = “Network”, assign to “Network Support Group”
- When state transitions to “Review”, initiate approval from “Change Request Managers” group

**Actions:**
- Wait for approval
- Update record state accordingly

---

## 👥 Approval Configuration
- **Group:** Change Request Managers  
  (`sys_user_group` table)
- All users in this group receive approval requests.
- The record proceeds only after at least one approval (or all, depending on rule setup).

---

## 🧠 Learning Outcomes
- Hands-on experience with **Flow Designer**
- Configuring **Approvals & Conditions**
- Writing **Client Scripts** and **Business Rules**
- Managing **Custom Tables** and **Groups**
- Understanding **Change Management lifecycle**

---

## 🚀 How to Import the Update Set
1. Go to **System Update Sets → Retrieved Update Sets**
2. Click **Import Update Set from XML**
3. Upload the provided XML file
4. **Preview → Commit** the update set
5. Test the workflow by creating a new Change Request record

---

## 📂 Files Included
- `Change_Request_Workflow_Update_Set.xml`
- `README.md`

---

## 👤 Author
**Shahjad**  
B.Tech in Computer Science | ServiceNow Administrator  
Hands-on experience in:
- Flow Designer
- Catalog & Record Management
- ITSM Workflows  

---

## 🏷️ Tags
`#ServiceNow` `#ITSM` `#FlowDesigner` `#WorkflowAutomation` `#ChangeManagement` `#BeginnerToAdvanced`

---

