# BookBot — WhatsApp Bookstore Sales Assistant

An AI-powered WhatsApp bookstore assistant built with **n8n**, **OpenAI**, **WhatsApp Business Cloud**, **Google Sheets**, and **Gmail**.

BookBot is designed to help customers discover books, check availability and pricing, place orders, track existing orders, update eligible orders, cancel orders, and request replacement orders.

> **Portfolio status:** This repository contains a sanitised workflow export and implementation documentation. The workflow has been structurally checked, but it has **not** been imported into a clean n8n instance or execution-tested. Credentials and account-specific spreadsheet references must be reconnected before use.

## What BookBot is designed to do

- Search bookstore inventory by title, author, genre, ISBN, format and availability.
- Return book information using connected inventory data rather than inventing prices or stock levels.
- Collect customer and delivery details, show an order summary and request confirmation before creating an order.
- Create orders and update inventory quantities.
- Retrieve orders for tracking and eligibility checks.
- Restrict customer-requested order edits and cancellations to eligible order statuses, as described in the AI Agent instructions.
- Send order-related emails through Gmail after the relevant operation succeeds.
- Support replacement orders rather than silently reactivating cancelled orders.

## Architecture

```text
Customer on WhatsApp
        |
        v
WhatsApp Trigger
        |
        v
     AI Agent <---- OpenAI Chat Model
        |    <---- Simple Memory
        |
        +---- Inventory search / inventory update
        +---- Order create / order search / order update
        +---- Customer search / create / update
        +---- Cart search / add / update
        +---- Sales record
        +---- Gmail email tool
        |
        v
WhatsApp Business Cloud reply
```

Google Sheets is the operational data layer for inventory, orders, customer records, cart lines and sales. Gmail is used for customer email communication.

## Repository structure

```text
whatsapp-business-automation/
├── README.md
├── workflow/
│   └── bookbot-whatsapp-store-assistant.json
└── docs/
    ├── architecture.md
    └── workflow-review.md
```

## Workflow export

The sanitised n8n export is available at [workflow/bookbot-whatsapp-store-assistant.json](workflow/bookbot-whatsapp-store-assistant.json).

The export has been cleaned for portfolio sharing:
- Removed all **14 disabled nodes**.
- Removed credential bindings and webhook IDs.
- Replaced private Google Sheets document IDs and the WhatsApp phone-number ID with placeholders.
- Removed instance-specific export metadata.
- Added visible node notes to explain each node's role and highlight incomplete configuration.
- Kept the workflow inactive (`active: false`).

## Setup before importing or activating

1. Import the JSON into your n8n instance.
2. Reconnect your own OpenAI, WhatsApp Business Cloud, Google Sheets and Gmail credentials.
3. Replace the two Google Sheets document ID placeholders with the correct spreadsheet IDs.
4. Configure the blank worksheet references on `cart_search`, `cart_add` and `cart_update`. The `orderItem_create` node is also disconnected and has a blank worksheet reference.
5. Review the legacy connected tools `Get all orders`, `Delete Order` and `cancle Order`. In particular, `Delete Order` is destructive and should not be exposed to the AI agent unless there is a clear, protected business requirement.
6. Verify spreadsheet column names and matching fields for every Google Sheets operation.
7. Configure and verify the WhatsApp webhook and recipient mapping.
8. Test in a disposable environment with test data before connecting real customers or activating the workflow.

## Known implementation gaps

- Three connected cart tools have blank worksheet references.
- `orderItem_create` is not connected to the AI Agent and has a blank worksheet reference.
- Three additional legacy order tools remain connected to the AI Agent; their overlap with the primary order tools should be reviewed.
- The AI Agent instructions describe business rules, but those rules have not been validated through end-to-end execution.

These gaps are documented rather than silently repaired because the correct spreadsheet tabs, data schema and business rules cannot be inferred safely from the JSON alone.

## Validation

| Check | Result |
|---|---|
| JSON parsing | Passed |
| Disabled-node removal | 14 removed |
| Structural workflow check | Passed |
| Runtime/import test | Not performed |
| Live WhatsApp, Google Sheets and Gmail operations | Not tested |

A structural check does not prove that node versions, expressions, spreadsheet schemas, credentials or business logic will work in a live n8n instance.

## Technology stack

- **n8n** — workflow orchestration and tool routing
- **OpenAI** — AI agent language model
- **WhatsApp Business Cloud** — customer messaging interface
- **Google Sheets** — inventory, orders, customer, cart and sales data
- **Gmail** — customer email notifications
- **JSON, APIs and webhooks** — integration and workflow configuration

## About

**Ola Tesleem**  
AI Automation Specialist | n8n Workflow Developer | AI Agents & Business Process Automation

GitHub: [@olatesleem](https://github.com/olatesleem)
