# Everwear — AI Customer Support Agent

An AI-powered support assistant for a fictional e-commerce brand, built to demonstrate how a business can automate order support, issue tracking, and urgent escalations — without needing a full support team on standby 24/7.

**Live demo:** *(add your GitHub Pages link here once hosted)*
**Demo video:** [Watch the walkthrough](https://www.loom.com/share/b478a3b47a594a0ea0f81beb940970ef)

---

## The problem

Small e-commerce businesses lose time and customers to slow support response:
- Customers wait hours (or days) for basic order status updates
- Simple issues (wrong item, damaged item) sit in an inbox instead of getting logged and tracked
- Urgent, high-stakes situations — an angry customer threatening a chargeback — get buried in the same queue as routine questions, when they need a human's attention *immediately*

This project builds an assistant that handles the routine cases on its own, and knows exactly when to stop and bring in a human.

## What it does

- **Answers order questions instantly** — status, tracking, item details — by looking up real order data, not guessing
- **Logs issues that need follow-up** — damaged items, wrong items, returns — as tracked tickets, so nothing gets lost in a chat log
- **Escalates urgent situations to a real person** — automatically detects high-value refund requests, frustrated customers, or chargeback/legal threats, and alerts the team immediately via Slack, with a full written summary

## Why this matters for a business

The hardest part of automating support isn't answering questions — it's knowing the difference between *"I can handle this"* and *"a human needs to see this right now."* This assistant is built around that distinction, with clear rules for when it acts on its own versus when it hands off — so it never overpromises a refund or a timeline on a business's behalf.

---

## How it works

```
Customer message
      ↓
AI Agent (reads the message, decides what to do)
      ↓
  ┌───┴────────────┬──────────────────┬─────────────────┐
  ↓                ↓                  ↓                  ↓
Look up order   Log a support     Alert the team      Log the
status          ticket            on Slack             escalation
```

The assistant has access to four tools, and decides on its own which one (if any) a situation calls for:

| Tool | What it does |
|---|---|
| **Order Lookup** | Finds a customer's order by number or email and returns status, item, and tracking info |
| **Ticket Logging** | Creates a tracked record when a human needs to take action — a replacement, a return, etc. |
| **Team Alert (Slack)** | Sends an immediate alert to the support team when a situation is urgent, high-value, or emotionally charged |
| **Escalation Log** | Keeps a permanent record of every escalation, separate from the alert itself, so nothing relies on a message not getting missed in Slack |

All of this runs with memory — the assistant remembers earlier parts of the same conversation, so a customer never has to repeat themselves.

---

## Tech stack

- **[n8n](https://n8n.io)** — workflow automation platform connecting everything together
- **Claude (Anthropic)** — the AI reasoning behind the assistant's responses and decisions
- **Google Sheets** — order data, ticket log, and escalation log
- **Slack** — real-time alerts to the support team
- **GitHub Pages** — hosting for this demo page

## Project files

- [`index.html`](./index.html) — the branded demo page with the embedded chat widget
- [`workflow.json`](./workflow.json) — the exported n8n workflow *(add once exported)*
- [`docs/build-notes.md`](./docs/build-notes.md) — detailed build log, including architecture decisions and debugging notes *(optional, for anyone who wants to go deeper)*

---

## A note on this demo

This is a portfolio project built around a fictional brand ("Everwear") to demonstrate real automation patterns businesses actually use. The underlying workflow — order lookups, ticket tracking, and smart escalation — is directly reusable for a real e-commerce business with its own order data and support channels.

*Interested in something similar for your business? [Add your contact info / site link here]*
