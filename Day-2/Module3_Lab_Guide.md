# 🧪 Module 3 — Lab Guide

## Building Intelligent Conversations: Employee Onboarding Assistant

### Agentic AI Foundation Programme | Day 1

---

> **Lab Duration:** ~45 Minutes  
> **Platform:** Microsoft Copilot Studio (copilotstudio.microsoft.com)  
> **Difficulty:** Foundation

---

## 🗺️ Lab Overview

In this lab, you will build a fully functional **Employee Onboarding Assistant** agent from scratch in Microsoft Copilot Studio. By the end, your agent will:

- Greet new employees by name and collect onboarding details
- Intelligently route each user to a department-specific onboarding path
- Deliver personalised, contextual responses using variables
- Handle unknown inputs gracefully with a custom fallback topic
- Answer policy questions using an uploaded knowledge document

This lab mirrors a real-world enterprise use case and covers every concept from Module 3: conversation flow design, entities, variables, conditional logic, and fallback handling.

---

## ⏱️ Time Plan

| Phase       | Task                                | Time        |
| ----------- | ----------------------------------- | ----------- |
| **Phase 1** | Agent Setup & Configuration         | 5 min       |
| **Phase 2** | Upload Knowledge Sources            | 5 min       |
| **Phase 3** | Topic 1 — Welcome & Data Collection | 10 min      |
| **Phase 4** | Topic 2 — Conditional Routing       | 10 min      |
| **Phase 5** | Personalised Responses & Variables  | 5 min       |
| **Phase 6** | Custom Fallback Topic               | 5 min       |
| **Phase 7** | Test & Validate                     | 5 min       |
| **Total**   |                                     | **~45 min** |

---

## 📋 Part 1 — Agent Setup & Configuration (5 min)

### Step 1.1 — Create a New Agent

1. Navigate to [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
2. Click **Create** → **New agent**
3. Select your solution from the Drop Down list

### Step 1.2 — Agent Details

Fill in the following fields exactly as shown:

| Field            | Value                                                                                                                                                                   |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Agent Name**   | `Contoso Onboarding Assistant`                                                                                                                                          |
| **Description**  | `An intelligent onboarding assistant that welcomes new employees, collects their details, routes them to the right department resources, and answers policy questions.` |
| **Instructions** | _(See below — copy the full block)_                                                                                                                                     |
| **Icon**         | Choose any people/team icon from the gallery                                                                                                                            |

### Step 1.3 — Agent Instructions

Copy and paste the following into the **Instructions** field:

```
You are Contoso's friendly and professional Employee Onboarding Assistant. Your role is to welcome new employees joining the company and guide them through their first steps.

Always follow these rules:
1. Greet every user warmly and address them by their first name once collected.
2. Collect the user's Name, Department, and Start Date before providing any department-specific guidance.
3. After collecting details, confirm them back to the user before proceeding.
4. Route users to their correct department onboarding path based on their department.
5. If the user's department is not one of the recognised departments (IT, HR, Finance, Operations), offer them a General Onboarding path and escalate to a human if they need further help.
6. Use uploaded knowledge documents to answer policy questions accurately. Cite the document when answering.
7. Always maintain a warm, professional, and encouraging tone. This is someone's first experience with the company — make it memorable.
8. If you do not know an answer, say so honestly and offer to connect the user with a human colleague.
9. Never make up information about company policies, systems, or benefits.
10. Keep responses concise — maximum 3 short paragraphs per response.
```

### Step 1.4 — Language & Settings

- **Primary Language:** English (United States)
- **Classic mode:** Leave OFF (keep Generative AI mode enabled)
- Click **Create** to save the agent

---

## 📚 Part 2 — Upload Knowledge Sources (5 min)

Your agent will use two uploaded documents to answer employee policy questions.

These documents are provided as part of your lab kit:

- `Contoso_IT_Onboarding_Policy.md`
- `Contoso_HR_Onboarding_Policy.md`

### Step 2.1 — Add Knowledge Sources

1. In the agent editor, click the **Knowledge** tab (left sidebar)
2. Click **+ Add knowledge**
3. Select **Files**
4. Upload both documents:
   - `Contoso_IT_Onboarding_Policy.md`
   - `Contoso_HR_Onboarding_Policy.md`
5. Wait for indexing to complete (green checkmark = ready)

### Step 2.2 — Configure Knowledge Settings

1. After upload, click on each document and verify the **Description** field:
   - For the IT doc: `IT department onboarding policies, equipment setup, system access, and first-week checklist`
   - For the HR doc: `HR onboarding policies, leave entitlements, benefits, and people systems`
2. Ensure **"Allow the AI to search this source"** is toggled ON for both

> 💡 **Trainer Tip:** Copilot Studio uses these descriptions to decide _which_ document to query for a given question. Precise descriptions = better retrieval accuracy.

---

## 🗣️ Part 3 — Topic 1: Welcome & Data Collection (10 min)

This is the main conversation entry point. It greets the user and collects the three pieces of information needed to route them correctly.

### Step 3.1 — Create the Topic

1. Click **Topics** tab → **+ Add topic** → **From blank**
2. Set topic **Name:** `Employee Onboarding Welcome`
3. Set **Description:** `Greets new employees and collects their name, department, and start date`

### Step 3.2 — Configure Trigger Phrases

In the **Trigger** node, add the following phrases (one per line):

```
I'm a new employee
I just joined
New employee onboarding
Help me get started
I need onboarding help
Welcome
Hello I'm new here
Just joined the company
```

> 💡 Add at least 5–6 diverse phrases. More variety = better intent recognition.

### Step 3.3 — Add the Greeting Message Node

1. After the Trigger node, click **+** → **Send a message**
2. Enter:

```
Welcome to Contoso! 🎉 I'm your Onboarding Assistant and I'm here to make your first days smooth and stress-free.

Let's get you set up. I just need a few quick details.
```

### Step 3.4 — Collect User's Name

1. Click **+** → **Ask a question**
2. **Question text:**

```
First — what's your name? (First name is fine!)
```

3. **Identify:** Set to **"User's entire response"** (or create a simple text entity)
4. **Variable name:** Click the variable → rename to `UserName`
5. **Scope:** Topic (we will promote to Global in the next step)

> ⚠️ **Important:** After creating the variable, open the variable panel and change the scope from **Topic** to **Global**. Name it `Global.UserName`.

### Step 3.5 — Collect Department

1. Click **+** → **Ask a question**
2. **Question text:**

```
Thanks, {Global.UserName}! Which department are you joining?
```

3. **Identify:** Select **Create a new entity** → name it `DepartmentEntity`
4. Configure the entity:
   - Type: **Closed list**
   - Add the following values and synonyms:

| Value      | Synonyms                                                |
| ---------- | ------------------------------------------------------- |
| IT         | Information Technology, Tech, Technology, IT Department |
| HR         | Human Resources, People, People Team, HR Department     |
| Finance    | Finance Department, Accounts, Accounting                |
| Operations | Ops, Operations Team, Operations Department             |

5. **Variable name:** `selectedDepartment` (Topic scope is fine here)

### Step 3.6 — Collect Start Date

1. Click **+** → **Ask a question**
2. **Question text:**

```
Perfect! And when is your official start date?
```

3. **Identify:** Select **Date** (pre-built entity)
4. **Variable name:** `startDate` (Topic scope)

### Step 3.7 — Confirmation Message

1. Click **+** → **Send a message**
2. Enter:

```
Great — let me confirm your details:

👤 Name: {Global.UserName}
🏢 Department: {selectedDepartment}
📅 Start Date: {startDate}

Everything look correct? I'll now pull up your personalised onboarding guide!
```

> 💡 You're using **variable interpolation** here. Click the `{x}` button in the message editor to insert variables rather than typing them manually — this ensures correct variable binding.

---

## 🔀 Part 4 — Topic 2: Conditional Routing by Department (10 min)

Now we build the branching logic that delivers a unique experience for each department.

### Step 4.1 — Add a Condition Node

1. After the confirmation message node, click **+** → **Add a condition**
2. This creates a branching structure

### Step 4.2 — Configure Branch: IT Department

1. Click the **first condition branch**
2. Set the condition:
   - Variable: `selectedDepartment`
   - Operator: **is equal to**
   - Value: `IT`
3. In the IT branch, click **+** → **Send a message**
4. Enter:

```
🖥️ Welcome to the IT Team, {Global.UserName}!

Here's your IT onboarding checklist for Day 1:

✅ Step 1: Check your email for a welcome message from IT Support
✅ Step 2: Your laptop will be ready at the IT Help Desk — bring your employee ID
✅ Step 3: Request system access using the IT Self-Service Portal
✅ Step 4: Set up your VPN using the guide in your welcome email
✅ Step 5: Join the #it-team Slack/Teams channel

Your IT buddy for the first week is assigned from the IT Support team. They'll reach out by end of Day 1.

Do you have any questions about your IT setup, systems, or policies?
```

### Step 4.3 — Configure Branch: HR Department

1. Click **+ Add condition** to add a second branch
2. Set the condition:
   - Variable: `selectedDepartment`
   - Operator: **is equal to**
   - Value: `HR`
3. In the HR branch, add a message:

```
👥 Welcome to the HR Team, {Global.UserName}!

Here's your HR onboarding checklist for Day 1:

✅ Step 1: Complete your new hire paperwork in Workday (link in welcome email)
✅ Step 2: Attend the company-wide orientation at 10:00 AM on your start date
✅ Step 3: Review the Employee Handbook shared in your welcome pack
✅ Step 4: Set up your Benefits portal account — deadline is 30 days from start
✅ Step 5: Book a 1:1 with your HR Business Partner in the first week

Your HR onboarding buddy will contact you within 24 hours of your start date.

Would you like to know about leave entitlements, benefits, or HR systems?
```

### Step 4.4 — Configure Branch: Finance Department

1. Add a third condition branch:
   - Variable: `selectedDepartment`
   - Operator: **is equal to**
   - Value: `Finance`
2. Add a message:

```
💼 Welcome to the Finance Team, {Global.UserName}!

Here's your Finance onboarding checklist for Day 1:

✅ Step 1: Your Finance systems access request has been sent — allow 24 hours
✅ Step 2: Complete compliance and AML training modules in the Learning Portal
✅ Step 3: Your manager will walk you through the month-end reporting calendar
✅ Step 4: Review the Finance Policies and Procedures document in SharePoint
✅ Step 5: Set up your Oracle/SAP credentials with the Finance Systems team

Finance induction sessions run every other Monday — you'll receive a calendar invite.

Is there anything else you'd like to know about getting started in Finance?
```

### Step 4.5 — Configure the Default Branch (Catch-All)

The **All Other Conditions** branch handles any department not explicitly listed:

1. Click the **All Other Conditions** branch (auto-created)
2. Add a message:

```
🌟 Welcome aboard, {Global.UserName}! Great to have you joining us on {startDate}.

I don't have a specific onboarding guide for your department yet, but here's your general Day 1 checklist:

✅ Check your email for a welcome message from your manager
✅ Complete new hire paperwork in Workday
✅ Attend the company-wide orientation
✅ Introduce yourself to your team
✅ Review the general Employee Handbook

Would you like me to connect you with an HR colleague who can give you department-specific guidance?
```

3. After this message, add **+** → **Transfer to Agent**
4. Set the transfer message: `I'm connecting you with an HR colleague who can help with your specific department onboarding. Please hold for a moment.`

---

## ✨ Part 5 — Personalised Closing & Variable Usage (5 min)

### Step 5.1 — Add a Closing Message to Each Branch

At the end of **each department branch** (after the department-specific content), add a consistent personalised close:

```
That's everything to get you started, {Global.UserName}! 🚀

Remember: your official start date is {startDate}, so you have time to review everything before then.

You can come back to me any time to ask about company policies, benefits, systems, or anything else. Just type your question and I'll do my best to help.

Good luck — and welcome to the Contoso family! 🎉
```

### Step 5.2 — End Conversation Node

After the closing message, add **+** → **End conversation** to cleanly terminate the session.

> 💡 Always end with an **End conversation** node — leaving it open causes the agent to loop back to the trigger, which can confuse users.

---

## 🛡️ Part 6 — Custom Fallback Topic (5 min)

The fallback topic fires when the user says something that doesn't match any of your topics. Never leave this as the default.

### Step 6.1 — Navigate to System Topics

1. Click **Topics** tab
2. At the top, click **System** tab (next to Custom)
3. Find and click **Fallback**

### Step 6.2 — Customise the Fallback Message

1. Click on the existing **Message node** in the Fallback topic
2. Replace the default content with:

```
Hmm, I didn't quite catch that, {Global.UserName}. 🤔

I'm your Onboarding Assistant, so I'm best at helping with:
• 🖥️ Department onboarding checklists
• 📋 Company policies and procedures
• 🏥 Benefits and leave entitlements
• 💻 System access and IT setup

Try rephrasing your question, or choose one of these options:
• Type **"Onboarding"** to restart the onboarding process
• Type **"Policy"** to ask about company policies
• Type **"Help"** to see all available topics
• Type **"Agent"** to speak with a human colleague
```

> 💡 **Note:** If `Global.UserName` hasn't been set yet (the user hasn't gone through onboarding), the variable will be blank. That's okay for a foundation lab — advanced handling would check if the variable is populated first.

### Step 6.3 — Add Escalation Option

1. After the fallback message, add **+** → **Ask a question**
2. Question: `Would you like me to connect you with a human colleague?`
3. Set **Options:** Yes / No (multiple choice)
4. Add condition:
   - If `Yes` → Add **Transfer to Agent** node
   - If `No` → Add **Send a message**: `No problem! Feel free to ask me anything else. I'm here to help. 😊`

---

## ✅ Part 7 — Test & Validate (5 min)

### Step 7.1 — Open the Test Canvas

1. Click **Test** (top right of the canvas)
2. Enable **"Track between topics"** toggle (helps you see variable values)

### Step 7.2 — Run Test Scenario 1: IT Employee

Test the following conversation flow:

| Turn | You type                         | Expected behaviour                   |
| ---- | -------------------------------- | ------------------------------------ |
| 1    | `I'm a new employee`             | Welcome message, asks for name       |
| 2    | `Alex`                           | Confirms name, asks for department   |
| 3    | `IT`                             | Accepts, asks for start date         |
| 4    | `May 5th`                        | Shows confirmation with all 3 fields |
| 5    | _(auto-continues)_               | Routes to IT onboarding checklist    |
| 6    | `What is the VPN setup process?` | Answers from knowledge document      |

### Step 7.3 — Run Test Scenario 2: HR Employee

| Turn | You type                           | Expected behaviour                |
| ---- | ---------------------------------- | --------------------------------- |
| 1    | `Hello I'm new here`               | Welcome message                   |
| 2    | `Jamie`                            | Asks for department               |
| 3    | `Human Resources`                  | Recognised as HR (synonym match)  |
| 4    | `Next Monday`                      | Parsed as a date                  |
| 5    | _(auto)_                           | Routes to HR onboarding checklist |
| 6    | `How many days of leave do I get?` | Answers from HR policy document   |

### Step 7.4 — Run Test Scenario 3: Fallback

| Turn | You type                        | Expected behaviour             |
| ---- | ------------------------------- | ------------------------------ |
| 1    | `What's the stock price today?` | Triggers custom fallback topic |
| 2    | `Yes`                           | Offers transfer to human agent |

### Step 7.5 — Check Variable Values

While testing, click the **Variables** icon in the test pane to verify:

- ✅ `Global.UserName` is populated after name collection
- ✅ `selectedDepartment` matches what the user said
- ✅ `startDate` is parsed as a date object (not raw text)

---

## 🏁 Success Criteria Checklist

Before calling your lab complete, verify all of the following:

- [ ] Agent created with correct name, description, and instructions
- [ ] Both knowledge documents uploaded and indexed
- [ ] Welcome topic triggers correctly on at least 3 different trigger phrases
- [ ] Agent collects Name, Department, and Start Date in sequence
- [ ] Confirmation message shows all 3 collected values correctly
- [ ] IT, HR, and Finance branches each show department-specific content
- [ ] Catch-all branch handles unrecognised departments gracefully
- [ ] Closing message uses `Global.UserName` and `startDate` variables
- [ ] Custom fallback topic replaces the default message
- [ ] Fallback escalation path offers Transfer to Agent
- [ ] Knowledge source answers a policy question correctly in the test canvas

---

## 🚀 Bonus Challenges (If You Finish Early)

Try these extensions to deepen your learning:

### Bonus 1 — Add an Operations Department Branch

Build a fourth explicit branch for the Operations department with its own onboarding checklist (minimum 5 steps).

### Bonus 2 — Add a "Menu" Topic

Create a new topic triggered by the word `menu` or `help` that lists available capabilities and links to other topics using the **Go to topic** action.

### Bonus 3 — Add Input Validation

After collecting the department, add a check: _if the entity was not recognised_, send a message like `I didn't recognise that department. Please choose from: IT, HR, Finance, or Operations.` and re-ask the question (manual reprompt pattern).

### Bonus 4 — Test Knowledge Source Accuracy

Ask the agent 5 different policy questions based on the uploaded documents. Note which ones it answers accurately and which ones it misses. How would you improve the knowledge document to fix the gaps?

---

## 🔧 Common Issues & Fixes

| Issue                              | Likely Cause                   | Fix                                                             |
| ---------------------------------- | ------------------------------ | --------------------------------------------------------------- |
| Variable shows as blank in message | Variable not in scope          | Check Global vs Topic scope                                     |
| Department entity not matching     | Synonyms not added             | Add more synonyms to DepartmentEntity                           |
| Knowledge source not answering     | Description too vague          | Edit knowledge source description to be more specific           |
| Fallback triggers too often        | Trigger phrases too generic    | Add more specific trigger phrases to your main topic            |
| Date not parsed correctly          | User typed a non-standard date | Add a reprompt message asking for DD/MM/YYYY format             |
| Condition branch not routing       | Condition value case mismatch  | Entity values are case-sensitive — check the closed list values |

---

## 📎 Lab Kit Files

The following supporting documents are included in your lab kit folder:

| File                              | Purpose                                                         |
| --------------------------------- | --------------------------------------------------------------- |
| `Contoso_IT_Onboarding_Policy.md` | Knowledge source — IT policies, setup guides, access procedures |
| `Contoso_HR_Onboarding_Policy.md` | Knowledge source — HR policies, leave, benefits, systems        |
| `Module3_Lab_Guide.md`            | This document                                                   |

---

_Module 3 Lab Guide | Nived Varma | Agentic AI Foundation Programme_  
_Version 2.0 | Day 1_
