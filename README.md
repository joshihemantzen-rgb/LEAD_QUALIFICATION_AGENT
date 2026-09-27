# AI Lead Qualification Agent

An AI-powered lead qualification and routing system built with **n8n**, **Gemini**, **Google Sheets**, and **Gmail**.

The system automatically receives lead information, validates it, evaluates the lead using AI, assigns a score and category, stores qualified leads, detects duplicates, and sends appropriate notifications.

## Features

* Lead intake through webhook
* Email and lead-data validation
* AI-powered lead qualification
* Automatic score from 0–100
* HOT / WARM / COLD classification
* Structured AI output validation
* Score and category consistency checking
* Google Sheets lead database
* Duplicate lead detection
* HOT lead email notification
* WARM lead email notification
* COLD lead handling without email
* Google Sheets error handling
* Invalid input protection

## Workflow

```text
Lead Submission
      ↓
Input Validation
      ↓
Prepare Lead Data
      ↓
AI Qualification
      ↓
Structured Output
      ↓
Score & Category Validation
      ↓
Duplicate Check
      ↓
Google Sheets Database
      ↓
HOT / WARM / COLD Routing
      ├── HOT  → Gmail Notification
      ├── WARM → Gmail Notification
      └── COLD → End
```

## AI Qualification

The AI evaluates each lead using three factors:

### Budget — 40 points

Higher budgets receive more points.

### Requirement Clarity — 30 points

Specific and well-defined requirements receive more points.

### Business Value — 30 points

Leads representing larger or more significant opportunities receive more points.

### Classification

|  Score | Category |
| -----: | -------- |
| 80–100 | HOT      |
|  50–79 | WARM     |
|   0–49 | COLD     |

The category is determined from the final score.

## Example

### Input

```json
{
  "name": "Amit Digital",
  "email": "amit@example.com",
  "company": "Amit Digital",
  "budget": "$3,000",
  "requirement": "We need a professional business website with a contact form and basic SEO."
}
```

### AI Output

```text
Score: 50
Category: WARM
Reason: Budget of $3,000 yields 20 points; requirement is clear but lacks details; business value is limited.
```

## Duplicate Detection

Before saving a new lead, the system checks whether the email already exists in the Google Sheets database.

If a matching lead is found, the system returns:

```text
Status: DUPLICATE_LEAD
Message: This email already exists in the lead database.
```

The duplicate is not processed as a new lead.

## Error Handling

The workflow includes validation and error-handling mechanisms for:

* Invalid email addresses
* Missing lead information
* Invalid AI scores
* Invalid AI categories
* Score/category mismatches
* Duplicate leads
* Google Sheets failures

## Technologies

* **n8n** — workflow automation
* **Gemini** — AI lead qualification
* **Google Sheets** — lead database
* **Gmail** — lead notifications
* **Postman** — API testing

## Testing

The workflow was tested with:

* HOT leads
* WARM leads
* COLD leads
* Invalid email addresses
* Invalid AI results
* Duplicate leads
* New/non-duplicate leads
* End-to-end workflow execution

## Project Purpose

This project demonstrates how AI can be integrated with workflow automation to reduce manual lead qualification and automatically route leads based on their potential value.

It can be adapted for agencies, software companies, service businesses, and other organizations that receive leads through forms or APIs.

## Future Improvements

Possible future improvements include:

* CRM integration
* Lead analytics dashboard
* Slack notifications
* Automatic follow-up sequences
* Lead enrichment
* More advanced scoring models
* Human sales-team handoff
* Multi-channel lead intake
