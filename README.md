[ServiceNow_Service_Catalog_Guide.md](https://github.com/user-attachments/files/21976134/ServiceNow_Service_Catalog_Guide.md)# ServiceNow-Service-Catalog **Service Catalog Item**
Scenario:

>You're a new ServiceNow admin at DXC Technology, and your team just received a request from IT leadership:<br>
>"We need to add the new iPhone 16 to the Service Catalog so employees can request it. Make sure it's properly categorized, priced, and includes storage and color options. And don't forget to follow access controls — only authorized editors should be able to manage catalog items." <br>

Your task is to: <br>

1. Create a Catalog Administrators group and assign the proper role.
2. Add team member to that group so he can manage catalog items.
3. Use Catalog Builder to create a new item for the iPhone 16.
4. Add dropdowns for Storage (256 GB / 512 GB) and Color (Space Black / Silver).
5. Add pricing logic (e.g., $100 extra for 512 GB).
6. Make the item active and test it from the Self-Service portal.
---
[# 📚 ServiceNow Service Catalog Guide
_A practical walkthrough for creating and configuring a catalog item in ServiceNow._

## 📌 Table of Contents
- [✅ What is the Service Catalog?](#what-is-the-service-catalog)
- [🔄 Request Lifecycle](#request-lifecycle)
- [📂 Navigation to Service Catalog](#navigation-to-service-catalog)
- [🏗 Activity: Add iPhone 16 to Service Catalog](#activity-add-iphone-16-to-service-catalog)
  - [🔐 Step 1: Create Catalog Administrators Group](#step-1-create-catalog-administrators-group)
  - [🛠 Step 2: Assign Editors for Service Catalog](#step-2-assign-editors-for-service-catalog)
  - [📦 Step 3: Create iPhone 16 Catalog Item with Catalog Builder](#step-3-create-iphone-16-catalog-item-with-catalog-builder)
    - [🗂 Configure Category](#configure-category)
    - [❓ Add Variables (Questions)](#add-variables-questions)
  - [⚙ Settings & Access](#settings--access)
  - [✅ Step 4: Configure Fulfillment Flow](#step-4-configure-fulfillment-flow)
  - [💲 Step 5: Add Pricing Logic](#step-5-add-pricing-logic)
  - [🔍 Step 6: Test in Self-Service Portal](#step-6-test-in-self-service-portal)

## ✅ What is the Service Catalog?
The **Service Catalog** in ServiceNow is a **user-friendly interface for employees to request goods or services internally**—such as laptops, mobile phones, or software licenses. These requests typically require approval and must be fulfilled by the appropriate teams (IT, Finance, etc.).

The catalog provides:
- **Centralized ordering** for employees
- **Approval workflows** to ensure compliance
- **Task-driven fulfillment** for accountability

**Example:**
> Brian requests an iPhone 16 with specific features and cost. The system records the request, notifies his manager for approval, and assigns tasks to IT for inventory and delivery.

## 🔄 Request Lifecycle
1. **User submits a catalog item request**
2. **Approval tasks** – e.g., manager review
3. **IT tasks** – inventory allocation and setup
4. **Fulfillment tasks** – delivery or handover

Each step is tracked as a **task** in ServiceNow for visibility and accountability.

## 📂 Navigation to Service Catalog
```
All > Self-Service > Service Catalog
```
From here, you can view categories and add new ones if needed.

![](https://github.com/CodeWithLuwam/July-30-ServiceNow-Service-Catalog/blob/main/Images/All%20%3E%20Self-Service%20%3E%20Service%20Catalog.png?raw=true)

## 🏗 Activity: Add iPhone 16 to Service Catalog
**Scenario:**
> You are a new ServiceNow Admin at DXC Technology. IT leadership asks:
> _"Add the new iPhone 16 to the Service Catalog so employees can request it. Include storage and color options, pricing logic, and ensure access controls."_

### **Your Tasks**
- [ ] Create a **Catalog Administrators** group and assign the `catalog_admin` role
- [ ] Add a team member (Bud Richmond) to that group
- [ ] Grant **editor access** to Bud for the Service Catalog
- [ ] Use **Catalog Builder** to create a new iPhone 16 item
- [ ] Add dropdowns for:
  - Storage: `256 GB` / `512 GB`
  - Color: `Space Black` / `Silver`
- [ ] Add pricing logic:
  - Base Price: `$999.99`
  - + `$100` for 512 GB
- [ ] Test the item from **Self-Service Portal**

## 🔐 Step 1: Create Catalog Administrators Group
1. Navigate to:
   ```
   All > Users and Groups > Groups
   ```
2. Click **New**, name it `Catalog Administrators`.
3. **Save** the record (right-click gray header → Save).
4. In the **Roles** tab:
   - Click **Edit**
   - Add role: `catalog_admin`
   - Save.
5. In the **Group Members** tab:
   - Click **Edit**
   - Add **Bud Richmond** to the group
   - Save.

## 🛠 Step 2: Assign Editors for Service Catalog
Even though Bud now has the role, you must **explicitly assign him as an editor for the Service Catalog**:
1. Navigate to:
   ```
   All > Service Catalog > Catalog Definitions > Maintain Catalogs
   ```
2. Open **Service Catalog** (the one we use for IT hardware/software).
3. Under:
   - **Manager** → Add `System Administrator`
   - **Editors** → Add `Bud Richmond`
4. **Save**.

## 📦 Step 3: Create iPhone 16 Catalog Item with Catalog Builder
1. **Impersonate Bud Richmond**.
2. Go to:
   ```
   All > Service Catalog > Catalog Builder
   ```
3. Click **Create a New Catalog Item**.
4. Select:
   - **Item Type:** `Standard Item in Service Catalog`
   - **Name:** `iPhone 16`
   - **Short Description & Description:** Fill details.

### 🗂 Configure Category
- Click **Edit Categories** (pencil icon).
- Assign to:
  - `Hardware`
  - `Mobiles`

### ❓ Add Variables (Questions)
Purpose: Gather user preferences for configuration.

**Add Storage Question**
- Click **Insert New Question**
- **Type:** `Choice`
- **Label:** `How much storage do you want?`
- Check **Mandatory**
- **Choices:**
  - `256 GB`
  - `512 GB`

**Add Color Question**
- **Label:** `What color do you want?`
- Choices: `Space Black`, `Silver`.

## ⚙ Settings & Access
- **Settings:** Leave defaults
- **Access:** Nothing to configure (Bud is editor)

## ✅ Step 4: Configure Fulfillment Flow
- Select **Service Catalog Item Request** as the flow
- Review & **Submit**

## 💲 Step 5: Add Pricing Logic
1. Navigate to:
   ```
   All > Service Catalog > Catalog Definitions > Maintain Items
   ```
2. Find `iPhone 16` (filter by Recently Updated).
3. Set **Price:** `$999.99`
4. Go to **Variables** tab → Select `Storage` question:
   - Under `Question Choices`, for **512 GB**, set **Price:** `$100.00`.
5. Save & Update.

## 🔍 Step 6: Test in Self-Service Portal
```
All > Self-Service > Service Catalog > Mobiles
```
- Select `iPhone 16`.
- Choose **512 GB** → Verify price updates to **$1,099.99**.

---
**Tip:** Ensure the file is saved as `README.md` in your repository root so GitHub renders the Markdown.
Uploading ServiceNow_Service_Catalog_Guide.md…]()



