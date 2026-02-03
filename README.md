# Helpful Resources: Building a Simple AI Agent with StackAI

This document is a **hands-on reference** for anyone who watched the demo and wants to recreate or extend the workflow on their own.

---

## 1. StackAI Website

Start here:

* **StackAI**: [https://www.stack-ai.com/](https://www.stack-ai.com/)

Create an account and log in before starting the workflow.

---

## 2. Creating the Project (UI Flow)

Follow this exact sequence inside StackAI:

1. Click **New Project**
2. Choose **Workflow Builder**
3. Click **New Workflow / New Project**

You are now inside the visual workflow canvas where you can connect inputs, prompts, and outputs.

---

## 3. Workflow Overview (Simple First)

For the demo and first implementation, keep the workflow intentionally simple:

**Flow:**

```
Text Input → AI Prompt → Output
```

This allows you to focus on AI logic and behavior rather than integrations.

---

## 4. Step 1 — Text Input Node

### Purpose

Simulates a customer support message.

### Example Input

```
Hi, I was charged twice for my subscription and no one has replied to my previous emails.
```

This represents the message body only (plain text).

---

## 5. Step 2 — AI Prompt: Issue Classification

### Purpose

Classify the customer message so the workflow can reason about *what type of issue this is* before responding.

### Prompt (Copy & Paste)

```
You are a customer support classification assistant.

Your task:
Classify the customer message into ONE of the following categories:
- Billing Issue
- Technical Issue
- General Question
- Complaint

Rules:
- Choose only one category
- Do not explain your choice
- Return only the category name exactly as written above
```

### Input Variable

```
{{input_text}}
```

### Expected Output (Example)

```
Billing Issue
```

---

## 6. Step 3 — AI Prompt: Customer Support Reply

### Prompt (Copy & Paste)

```
You are a professional customer support assistant helping a human support agent.

Your task:
Write a clear, polite, and helpful reply to the customer message provided.

Instructions:
- Address the customer by name if provided.
- Respond directly to the issue described.
- Use a professional and empathetic tone.
- Do NOT promise refunds or compensation.
- If information is missing, politely ask for it.

Return only the reply text.
```

### Input Variables

```
Customer message: {{input_text}}
Issue type: {{classification}}
```

---

## 6. Example Inputs for Testing

Use these messages to test different scenarios:

### Billing Issue

```
I was charged twice for my subscription this month.
```

### Technical Issue

```
I can’t log into my account even after resetting my password.
```

### General Question

```
Does your product support exporting reports as PDF?
```

### Complaint

```
Your support team hasn’t replied in days and this is very frustrating.
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

Thank you for reaching out, and I’m sorry for the inconvenience you’ve experienced.

I understand your concern regarding being charged twice for your subscription. To help us look into this, could you please confirm the email address associated with your account and the date of the charges?

Once we have that information, we’ll be happy to assist you further.

Best regards,
Customer Support Team
```

---

## 8. Optional Extension — Email-Based Workflow

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

## 9. Key Learning Takeaways

* Start with the simplest possible input
* Focus on AI behavior and guardrails
* Design AI to assist humans, not replace them
* Build workflows that are explainable and teachable

---

## 10. Contact

**Amr Mekki**
Applied AI Instructor

📧 Email: [amr.mekki21@gmail.com](mailto:amr.mekki21@gmail.com)
🌐 Website: [https://amrmekki.github.io/portfolio/](https://amrmekki.github.io/portfolio/)

Feel free to reach out for questions, collaboration, or training.
