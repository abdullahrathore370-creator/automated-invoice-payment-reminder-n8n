# Automated Invoice & Payment Reminder System

An automated invoice payment reminder workflow built with n8n, Google Sheets, Gmail, and Google Gemini AI.

## Overview

This workflow automates the process of monitoring unpaid invoices and sending payment reminders to customers.

The workflow runs automatically every day, retrieves invoice records from Google Sheets, checks their payment status and due dates, and determines whether a reminder should be sent.

## Workflow

Schedule Trigger
→ Get Invoices
→ Paid Status
→ Edit Fields
→ AI Agent
→ Action Switch
→ Type Switch
→ Gmail
→ Update Google Sheets

## Features

- Automated daily invoice checking
- Google Sheets invoice management
- Paid invoice filtering
- Overdue invoice detection
- Due-today invoice detection
- AI Agent decision handling
- Automatic Gmail reminders
- Reminder tracking
- Last reminder date tracking
- Reminder count tracking
- Duplicate reminder prevention

## Technologies

- n8n
- Google Sheets
- Gmail
- Google Gemini
- AI Agents
- Workflow Automation

## Decision Logic

### Overdue
If an unpaid invoice has a due date before the current date:

`SEND_REMINDER → OVERDUE → Overdue Email`

### Due Today
If an unpaid invoice is due today:

`SEND_REMINDER → DUE_TODAY → Due Today Email`

### No Action
If the invoice is paid, already reminded, or has a future due date:

`NO_ACTION → No Email`

## Google Sheets Fields

- Invoice ID
- Customer Name
- Email
- Amount
- Invoice Date
- Due Date
- Status
- Reminder Sent
- Last Reminder Date
- Reminder Count

## Architecture

```text
Schedule Trigger
       ↓
Get Invoices
       ↓
Paid Status
       ↓
Edit Fields
       ↓
AI Agent
       ↓
Action Switch
       ↓
Type Switch
    ↙       ↘
Overdue   Due Today
   ↓          ↓
 Gmail      Gmail
    \        /
     ↓      ↓
   Update Google Sheet
