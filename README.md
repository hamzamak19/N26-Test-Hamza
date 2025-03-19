# Monefy App - Exploratory Testing Report  

This document contains the testing scope, identified issues, and detailed bug reports for the Monefy app.  

---

## **Devices Used**  

### **Android Device**  
| Device Name         | OS Version  |  
|--------------------|------------|  
| Redmi Note 13 Pro | Android 15 |  

### **iOS Device**  
| Device Name | OS Version |  
|------------|------------|  
| iPhone X   | iOS 16     |  

---

# Exploratory Testing Report

## Contents

This document provides a detailed overview of the exploratory testing process, findings, and mitigation strategies. Below is the breakdown of key sections:

1. [**Exploratory Testing Charters**](#exploratory-testing-charters)
2. [**Bug Reports**](#findings-and-bugs)
3. [**Prioritization of Charters & Bugs**](#prioritization-of-charters)
4. [**Risks & Mitigation Strategies**](#risks-and-mitigations)

---

## **1. Exploratory Testing Charters**  

| **Charter No.** | **Testing Scope** | **Objective** |  
|---------------|------------------|---------------------------------------------------| 
| 1 | User registration & login | Verify if the user can successfully log in or register. |  
| 2 | Adding transactions | Ensure a user can add an expense/income correctly. | 
| 3 | Editing transactions | Verify if users can modify or remove transactions. | 
| 4 | Verify All Categories | Test if users can create categories and set budgets. | 
| 5 | Budget Tracking | Budget Mode, Carry Over, and Recurring Payments validation. |
| 6 | Currency Selection & Conversion | Verify if currency selection and conversions work correctly. | 
| 7 | Transfer Functionality | Ensure transfers between accounts reflect correctly. |
| 8 | Transaction Display | Transactions should be listed consistently. |
| 9 | Backup & Restore | Ensure backups can be restored properly. |
| 10 | App Navigation | Verify the back button functions correctly. |
| 11 | Export Files | Ensure that all data is properly exported in CSV format. |

---

## **2. Bug Reports**  

### **Bug Report 1: Unable to Perform Transfer (Android)**  

**Bug ID:** MONEFY-001  
**Feature:** Transfer Between Accounts  

### **Steps to Reproduce:**  
1. Open the Monefy app on an Android device.  
2. Tap the three dots in the top-right corner.  
3. Navigate to **Accounts**.  
4. Attempt to perform a transfer using the **two arrows (left/right)** option.  

### **Expected Result:**  
The transfer should be successfully performed from the **Accounts** screen, just like it works from the main screen and the top-left corner.  

### **Actual Result:**  
Transfer cannot be performed from the **Accounts** screen, but it works from the main screen and top-left corner.  

### **Priority:** Medium  
### **Severity:** Major  
  

![Bug Screenshot](images/monefy_bug_1.png)  

---

### **Bug Report 2: Inconsistent Transaction Lines (Android & iOS)**  

**Bug ID:** MONEFY-002  
**Feature:** Transaction Display  

### **Steps to Reproduce:**  
1. Open the Monefy app on an Android or iOS device.  
2. Perform multiple transactions around the **transaction wheel**.  
3. Observe the transaction history lines.  

### **Expected Result:**  
Transaction lines should be consistently displayed, maintaining a structured format.  

### **Actual Result:**  
Transaction order rearranges unexpectedly, and sometimes the transaction lines appear connected, while other times they disappear.  

### **Priority:** High  
### **Severity:** Low  
  

![Bug Screenshot](images/monefy_bug_2.png)  

---

### **Bug Report 3: Unable to Restore Backup (iOS)**  

**Bug ID:** MONEFY-003  
**Feature:** Backup & Restore  

### **Steps to Reproduce:**  
1. Open the Monefy app on an iOS device.  
2. Navigate to **Settings → Backup & Restore**.  
3. Attempt to restore a previous backup.  

### **Expected Result:**  
The backup should restore successfully without errors.  

### **Actual Result:**  
Restoring the backup shows an error like **"0 days ago"**, preventing successful restoration.  

### **Priority:** High  
### **Severity:** Critical  
  

![Bug Screenshot](images/monefy_bug_3.png)  

---

### **Bug Report 4: Back Button Not Working (iOS)**  

**Bug ID:** MONEFY-004  
**Feature:** Navigation  

### **Steps to Reproduce:**  
1. Open the Monefy app on an iOS device.  
2. Navigate through different sections of the app.  
3. Try to exit the app using the **Back button**.  

### **Expected Result:**  
Pressing the Back button should allow users to navigate back and exit the app if needed.  

### **Actual Result:**  
The Back button does not function, preventing users from exiting the app properly.  

### **Priority:** High  
### **Severity:** Major  
 

---

### **Bug Report 5: Transfer Not Reflected Properly (iOS)**  

**Bug ID:** MONEFY-005  
**Feature:** Transfer Functionality  

### **Steps to Reproduce:**  
1. Open the Monefy app on an iOS device.  
2. Tap the three dots in the top-right corner.  
3. Navigate to **Accounts** and perform a transfer.  

### **Expected Result:**  
The transfer should be correctly reflected in both the beneficiary and host accounts.  

### **Actual Result:**  
The transfer is not displayed properly in the beneficiary and host accounts, leading to incorrect balances.  

### **Priority:** High  
### **Severity:** Major  
  

![Bug Screenshot](images/monefy_bug_5.png)  

---

## **Potential Bugs to Investigate in Monefy**  

1. **Data Sync Issues** – Transactions added on one device may not sync properly across multiple devices.  
2. **Incorrect Balance Updates** – After performing transactions, the balance may not update immediately.  
3. **No ligin provided** – User not able to login from same account in two devices, future not available.  
4. **Dark Mode UI Glitches** – Some UI elements might not be properly visible in dark mode, need to buy premium to test that.  
5. **Category Deletion/Addition Bug** – Deleting/Adding a category might not remove associated transactions properly, need to buy premium to test that.

---

## **3. Prioritization of Charters & Bugs**  

| **Charter No.** | **Testing Scope** | **Objective** | **Priority** | **Android Issues** | **iOS Issues** |  
|---------------|------------------|---------------------------------------------------|------------|----------------|-------------|  
| 1 | User registration & login | Verify if the user can successfully log in or register. | Medium | ❌ | ❌ |  
| 2 | Adding transactions | Ensure a user can add an expense/income correctly. | High | ❌ | ❌ |  
| 3 | Editing transactions | Verify if users can modify or remove transactions. | Medium | ❌ | ❌ |  
| 4 | Verify All Categories | Test if users can create categories and set budgets. | Medium | ❌ | ❌ |  
| 5 | Budget Tracking | Budget Mode, Carry Over, and Recurring Payments validation. | High | ❌ | ❌ |  
| 6 | Currency Selection & Conversion | Verify if currency selection and conversions work correctly. | Medium | ❌ | ❌ |  
| 7 | Transfer Functionality | Ensure transfers between accounts reflect correctly. | High | [Bug 1](#bug-report-1) | [Bug 5](#bug-report-5) |  
| 8 | Transaction Display | Transactions should be listed consistently. | High | [Bug 2](#bug-report-2) | [Bug 2](#bug-report-2) |  
| 9 | Backup & Restore | Ensure backups can be restored properly. | Critical | ❌ | [Bug 3](#bug-report-3) |  
| 10 | App Navigation | Verify the back button functions correctly. | High | ❌ | [Bug 4](#bug-report-4) |  
| 11 | Export Files | Ensure that all data is properly exported in CSV format. | High | ❌ | ❌ |  

---
## **4. Risks & Mitigation Strategies**

| **Risk**                                                                 | **Impact**                                       | **Mitigation Strategy**                                               |  
|-------------------------------------------------------------------------|-------------------------------------------------|----------------------------------------------------------------------|  
| Registration of user is not present which may cause inconsistent data or data loss | Potential data inconsistency or loss, leading to user frustration | Implement user registration and ensure data synchronization and storage |  
| Lack of passcode or password, making the app vulnerable to hacking    | Risk of unauthorized access to sensitive financial data | Add passcode or password functionality to secure the app data |  
| Financial calculations may lose precision due to 2 decimal point limitations | Incorrect calculations leading to financial discrepancies | Implement unit testing for financial calculations to ensure accuracy |  
| UI glitches on different mobile sizes                                     | Poor user experience, causing app dissatisfaction | Conduct responsive design testing and fix UI issues across various devices |  
---
