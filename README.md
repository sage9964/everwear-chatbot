# CoreFlash Systems — AI Lead Qualification & Booking Agent

An AI-powered presales assistant for a fictional bulk/OEM SSD vendor, built to demonstrate how a business can triage inbound sales inquiries, qualify real buyers from tire-kickers, and book consultations straight onto a calendar — without a human reading every inquiry first.

**Live demo:** [sage9964.github.io/coreflash-chatbot](https://sage9964.github.io/coreflash-chatbot)
**Demo video:** [Watch on Loom](https://www.loom.com/share/8e1fb85321e945579208fcb4838d45fd)

---

## The problem

Bulk and OEM sales inquiries arrive at every volume, from every kind of buyer, in the same inbox:
- A 500-unit data center order and a one-off personal question get read in whatever order they happen to arrive
- By the time a real buyer hears back, they've often already gotten a quote from someone faster
- Inquiries that don't convert to a call today just disappear — no record to follow up on later

This project builds an assistant that qualifies every lead the moment it arrives, books the ones worth a consultant's time directly onto their calendar, and keeps a full record of everyone else.

## What it does

- **Gathers what it needs conversationally** — name, quantity, use case, and who the buyer represents — a couple of natural questions, not a rigid form
- **Qualifies leads against real business logic** — a hard-override gate checks business legitimacy first (no real organizational connection, e.g. a student or personal-use buyer, is never booked regardless of how large the stated quantity is), then weighs quantity and use case into a tiered priority
- **Books straight onto the consultant's calendar** — checks real availability, offers exactly 3 open slots, and confirms the booking with a scannable event title (`[HIGH] 67 units — Manager`) and full details in the description
- **Logs every single lead, booked or not** — a real business wants full pipeline visibility, not just a record of who fell through

## Why this matters for a business

The hardest part of automating presales isn't answering questions — it's knowing who's actually worth a consultant's time. This assistant asks for quantity instead of budget (a natural business question every buyer can answer, versus an invasive one that puts leads on the defensive), and treats business legitimacy as a hard gate that beats even an impressive-looking quantity claim. It never promises pricing or timelines on the business's behalf — that's what the human consultation call is for.

---

## How it works

```
Customer message
      ↓
AI Agent (reads the message, applies qualification logic)
      ↓
  ┌───┴────────────────┬─────────────────────┐
  ↓                     ↓                     ↓
Check availability   Book consultation     Log the lead
(existing events)    (calendar event)      (every outcome)
```

The assistant has access to three tools, and decides on its own which combination a conversation calls for:

| Tool | What it does |
|---|---|
| **Check Availability** | Reads the consultant's existing calendar events for the next 5 days and calculates real open gaps to offer |
| **Book Consultation** | Creates a calendar event for a qualifying lead, with priority, contact info, and details in the notes |
| **Log Lead** | Records every lead in a tracking sheet — booked or not — exactly once per conversation |

All of this runs with memory — the assistant remembers earlier parts of the same conversation, so a customer never has to repeat themselves, and never gets logged twice for restating their situation.

---

## Tech stack

- **[n8n](https://n8n.io)** — workflow automation platform connecting everything together
- **Claude (Anthropic)** — the AI reasoning behind qualification decisions and conversation
- **Google Calendar** — consultation availability and booking
- **Google Sheets** — full lead tracking log, every outcome
- **GitHub Pages** — hosting for this demo page

## Project files

- [`index.html`](./index.html) — the branded demo page with the embedded chat widget

*The exported n8n workflow JSON and detailed build notes will be added once the project is fully closed out.*

---

## A note on this demo

This is a portfolio project built around a fictional brand ("CoreFlash Systems") to demonstrate real qualification and booking patterns businesses actually use. The underlying workflow — hard-override qualification gates, tiered priority, calendar booking, and full-pipeline logging — is directly reusable for a real B2B business with its own calendar and lead-tracking setup.

*Interested in something similar for your business? [Add your contact info / site link here]*
