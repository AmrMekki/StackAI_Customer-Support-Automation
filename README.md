# Helpful Resources: Building a Routed AI Customer Support Workflow with StackAI

This document is a **hands-on reference** for recreating or extending a routed customer support workflow using StackAI.
The focus is on **AI routing**, **specialized agents**, and **email-ready outputs** designed to assist human support teams.

---

## 1. StackAI Website

Start here:

* **StackAI**: [https://www.stack-ai.com/](https://www.stack-ai.com/)

Create an account and log in before building the workflow.

---

## 2. Creating the Project (UI Flow)

Inside StackAI:

1. Click **New Project**
2. Select **Workflow Builder**
3. Click **New Workflow / New Project**

You are now inside the visual workflow canvas.

---

## 3. Workflow Overview (Final Design)

### High-Level Flow

```
Text Input
   ↓
AI Router (no prompt)
   ↓
 ┌──────────────────────────────┐
 │ Billing Issues → Billing AI  │
 │ Technical Issues → Tech AI   │
 │ Complaint (optional)         │
 │ General Question (optional)  │
 └──────────────────────────────┘
   ↓
Unified Output
```

### Design Philosophy

> The router decides **where** the request goes.
> Each AI agent decides **how to respond — within its expertise only**.

---

## 4. Building the Workflow

### Step 1 — Text Input Node

#### Purpose

Represents a customer support message as plain text.

#### Example Input

```
Hello, I was charged twice for my subscription this month and would like some help.
```

This input feeds directly into the AI Router.

---

### Step 2 — AI Router (No Prompt)

#### Purpose

Automatically routes incoming messages to predefined paths based on configuration.

#### Router Paths

1. **Billing Issues**
2. **Technical Issues**
3. **Complaint** (optional)
4. **General Question** (optional)

> No prompt is required.
> Routing is handled using StackAI's built-in routing logic and labels.

---

### Step 3 — Specialized AI Agents (Email Responses)

Each route connects to a **dedicated AI agent**.
All agents must return responses in **professional email format**, branded as **CompanyX**.

#### 3.1 Billing Support AI Agent

**Scope**

* Charges
* Invoices
* Subscriptions
* Payments

**Prompt (Copy & Paste)**

```
You are a customer support agent at CompanyX specializing ONLY in billing issues.

Instructions:
- Respond in a professional email format
- Clearly address billing-related concerns
- Ask for any missing billing details if needed
- Do NOT handle technical or product issues

If the issue is outside billing:
- Politely state that the request will be transferred to the appropriate department

Sign the email as:
CompanyX Support Team
```

---

#### 3.2 Technical Support AI Agent

**Scope**

* Login issues
* Errors
* Bugs
* Product functionality

**Prompt (Copy & Paste)**

```
You are a customer support agent at CompanyX specializing ONLY in technical issues.

Instructions:
- Respond in a professional email format
- Provide clear technical guidance
- Ask for relevant technical details if needed
- Do NOT handle billing or payment issues

If the issue is outside technical support:
- Politely indicate that the request will be transferred to the correct department

Sign the email as:
CompanyX Technical Support Team
```

---

#### 3.3 Complaint Route (Optional)

Used for dissatisfaction or negative feedback.

Example response behavior:

* Acknowledge frustration
* Maintain a calm, professional tone
* Avoid promises of compensation

Example output style:

```
Hello,

Thank you for taking the time to share your feedback with CompanyX.
We understand your concerns, and your message has been forwarded to the appropriate team for review.

Best regards,
CompanyX Support Team
```

---

#### 3.4 General Question Route (Optional)

Handles non-urgent, informational inquiries.

* Product features
* Capabilities
* General usage questions

Responses should still follow **email format and CompanyX branding**.

---

### Step 4 — Unified Output Node

#### Purpose

All AI agent responses connect to **one output node**.

Benefits:

* Single interface for users
* Easier publishing
* Consistent response delivery

---

## 5. Interface Guide (User Experience)

### What the User Interacts With

* One **text input field**
* One **email-formatted response**

### Interaction Flow

1. User submits a message
2. AI Router selects the correct path
3. A specialized AI agent generates an email-style reply
4. The response is displayed in the output

### Key Insight

> The system behaves like one inbox,
> powered by multiple focused support agents behind the scenes.

---

## 6. Example Inputs for Testing

Use these messages to test different scenarios:

### Billing Issue

```
I was charged twice for my subscription this month.
```

### Technical Issue

```
I can't log into my account even after resetting my password.
```

### General Question

```
Does your product support exporting reports as PDF?
```

### Complaint

```
Your support team hasn't replied in days and this is very frustrating.
```

---

## 7. Expected Output (Example)

### Input

```
I was charged twice for my subscription this month.
```

### Expected AI Output

```
Hello,

Thank you for reaching out, and I'm sorry for the inconvenience you've experienced.

I understand your concern regarding being charged twice for your subscription. To help us look into this, could you please confirm the email address associated with your account and the date of the charges?

Once we have that information, we'll be happy to assist you further.

Best regards,
Customer Support Team
```

---

## 8. Publishing Guide

### How to Publish

1. Click **Publish** in the StackAI workflow editor
2. Select a deployment method:

   * Web interface
   * Embedded widget
   * API endpoint
3. Confirm and publish

---

## 9. Optional Extension — Email-Based Workflow

If time allows or for further learning, the same workflow can be extended:

* Replace text input with **email input**
* Extract:

  * Sender name
  * Subject
  * Body
* Feed the body into the **same AI prompt**

Key idea:

> The AI logic stays the same — only the input source changes.

---

## 10. Key Learning Takeaways

* Start with the simplest possible input
* Focus on AI behavior and guardrails
* Design AI to assist humans, not replace them
* Build workflows that are explainable and teachable

---

## 11. Contact

**Amr Mekki**
Applied AI Instructor

📧 Email: [amr.mekki21@gmail.com](mailto:amr.mekki21@gmail.com)
🌐 Website: [https://amrmekki.github.io/portfolio/](https://amrmekki.github.io/portfolio/)

Feel free to reach out for questions, collaboration, or training.
