# 🧠 Integration: Airtable → Gmail + Slack Automation

This Make.com automation streamlines the process of qualifying leads and sending follow-up communications using **Airtable**, **Gmail**, and **Slack**.

## 🔍 Overview

This automation performs the following:

1. **Monitors Airtable** for new qualified leads.
2. **Sends a personalized follow-up email** to the lead using Gmail.
3. **Updates Airtable** to log the contact time.
4. **Parses the lead message** using RegEx.
5. **Posts a formatted update** to a Slack channel.

## ⚙️ Key Components

| Service    | Action                             |
|------------|------------------------------------|
| Airtable   | Watch Records, Update Record       |
| Gmail      | Send Follow-up Email               |
| RegEx      | Parse `Message` field              |
| Slack      | Send Message to Public Channel     |

## 📁 Scenario Flow

1. **Trigger**: Airtable watches for new records in the **"Lead Contact"** table where  
   `Qualification = "Qualified"`  
   → Limit: 10 records at a time

2. **Router**:
   - **Path A – Email Follow-up**:
     - Sends email via Gmail to the lead's address.
     - Updates the `Contacted on` field in Airtable.

   - **Path B – Slack Notification**:
     - Extracts a value from the `Message` field using RegEx.
     - Sends a Slack message to a public channel using the parsed data.

## 📑 Airtable Fields Used

- `First Name`, `Last Name`
- `Email`, `Phone`, `Company`, `Budget`
- `Created on`, `Qualification`, `Message`, `Contacted on`, `Notes`

## 📨 Email Template

**Subject**:  
`{{First Name}} let's talk`

**Body**:  
`Hey {{First Name}}, we got your request for help with {{Company}}. Please feel free to book a call with me here:`

## 🧠 Use Case

- Fast follow-up with inbound leads
- Slack-based alerting system for new qualified records
- CRM sync via Airtable

## 📌 How to Import

1. Go to [make.com](https://www.make.com/)
2. Create a new scenario
3. Click the **Import Blueprint** icon
4. Upload this `.json` file
5. Update your Airtable, Gmail, and Slack connections
