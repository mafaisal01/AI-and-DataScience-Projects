
# 🔧 Blueprint CF – Customer Feedback Automation Agent

## 📘 Index

1. [🎯 Purpose & Scope](#-purpose--scope)
2. [⚡ Trigger](#-trigger)
3. [🤖 Actions](#-actions)
4. [🗺️ Workflow Mapping](#️-workflow-mapping)
5. [🧰 Tool Selection](#-tool-selection)

---

## 🎯 Purpose & Scope

### Objective

The core objective of this AI agent framework is to **reduce manual work** for the person responsible for handling customer feedback — including segregation, classification, and redirection to specific departments.

### Success Criteria

The agent will be considered successful if it can **reduce manual work by at least 30%** in feedback management.

---

## ⚡ Trigger

### When and How Does It Start?

The agent is triggered **whenever a customer fills out the feedback form**.
This form submission acts as the **starting point** for the automation workflow.

---

## 🤖 Actions

### Automated Tasks

The agent performs the following actions automatically:

1. **Analyze** the submitted feedback.
2. **Classify** it into categories:

   * Complaint
   * Compliment
   * Feature Request
3. **Send** the categorized feedback to the appropriate Slack group or department.
4. **Notify** the customer via email — especially if the feedback is a complaint or negative experience.

### Workflow Count

Only **one workflow** is required to handle all types of feedback.

---

## 🗺️ Workflow Mapping

### Step-by-Step Flow

1. Customer fills the feedback form.
2. The form data is sent to the AI agent.
3. The agent **analyzes** the feedback using an LLM (Large Language Model).
4. Based on analysis, the agent **categorizes** the feedback into:

   * **Complaint** → Forwarded to the complaint department + email notification sent to the customer.
   * **Feature Request** → Forwarded to the concerned department.
   * **Compliment** → Sent to the owner’s or appreciation department.
5. The respective Slack groups receive automated messages for each case.

### Branching Logic

* The **LLM** decides the category based on sentiment and content.
* Complaint → Complaint Department + Customer Email
* Feature Request → Concerned Department
* Compliment → Owner’s Department

---

## 🧰 Tool Selection

### Required Applications & Services

| Tool / Service                | Purpose                                                |
| ----------------------------- | ------------------------------------------------------ |
| **Slack**                     | Notify respective departments and handle communication |
| **Airtable**                  | Store and manage structured feedback data              |
| **Gmail**                     | Send automated email responses to customers            |
| **Calculator Node**           | Handle basic calculations or scoring logic if needed   |
| **LLM (Advanced Agent Node)** | Analyze and categorize customer feedback               |
| **Switch Node**               | Control branching logic in the workflow                |

---

### ✅ Summary

This Customer Feedback Automation Agent integrates Slack, Airtable, Gmail, and LLM-based analysis to streamline the entire feedback process — reducing manual effort and ensuring quick, intelligent response handling.

---
### ✅ BluePrint CF
<img width="817" height="294" alt="bluePrint CF" src="https://github.com/user-attachments/assets/485f56fa-2150-4a2c-b053-a96860b09922" />
---
### ✅ 
<img width="1253" height="641" alt="Building CF" src="https://github.com/user-attachments/assets/5549a04a-4f32-4664-9d89-5f358a8b1d20" />

---
### ✅ ChatBot Agent
<img width="1366" height="768" alt="chatBot" src="https://github.com/user-attachments/assets/bcd995a7-e567-4813-9c4c-aa02b15de8da" />

---
### ✅ FormSubmit
<img width="1366" height="732" alt="FormSubmit" src="https://github.com/user-attachments/assets/98c34301-b1a1-43e3-ab29-19a94d386e7a" />

---
### ✅ DataUpload
<img width="1366" height="720" alt="DataUpload" src="https://github.com/user-attachments/assets/98486f5d-ccbe-42e1-8dcf-6e82d585fe7f" />

