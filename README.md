# WhatsApp Business Automated Response Workflow

A practical business automation project designed to improve how a household-utensils business responds to incoming WhatsApp customer enquiries.

The project uses **n8n workflow automation** and WhatsApp integration concepts to reduce repetitive first-response work and help customers understand what they can ask about.

> **Project status:** Portfolio documentation is being organised. This repository currently documents the confirmed use case and intended workflow. A verified, sanitised n8n export and implementation-specific setup details will be added after the original workflow configuration is recovered and checked.

## The problem

Small businesses often receive repeated enquiries through WhatsApp. Responding manually to every new conversation can take time and make it harder to provide a consistent first response.

## The solution

The workflow is designed to respond when a customer sends an incoming WhatsApp message. It sends a welcome message that introduces the business and its products, then invites the customer to ask about:
- Products
- Prices
- Product availability
- Delivery

This gives customers a clear starting point for the conversation while reducing the need to manually send the same introductory response.

## Workflow at a glance

1. A customer sends a message to the business on WhatsApp.
2. The incoming message initiates the automation.
3. The workflow processes the incoming event.
4. The customer receives an automated welcome message with guidance on the enquiries they can make.

The exact WhatsApp provider, n8n node configuration, message conditions, and response-handling behaviour are not documented here until they can be verified against the original workflow.

## Technology and concepts

- **n8n** — workflow automation and orchestration
- **WhatsApp Business integration** — customer messaging channel
- **Webhooks and APIs** — integration concepts used in the project
- **JSON** — workflow configuration and structured data

Specific provider names and node-level implementation details will be listed once verified.

## Repository structure

```text
whatsapp-business-automation/
├── README.md
├── workflow/
│   └── README.md
├── docs/
│   ├── architecture.md
│   ├── workflow-explanation.md
│   └── setup-guide.md
├── screenshots/
│   └── .gitkeep
└── .gitignore
```

## Security

- Never commit WhatsApp access tokens, API keys, passwords, webhook secrets, or private customer data.
- Replace credentials and account-specific identifiers with placeholders before sharing workflow exports.
- Review execution logs and screenshots to ensure customer phone numbers and message contents are not exposed.

## Current limitations

This repository does not yet contain a verified n8n workflow export. The technical implementation should not be inferred from the high-level project description. Provider-specific setup instructions and claims about testing will be added only after the original configuration is checked.

## About the developer

**Ola Tesleem**  
AI Automation Specialist | n8n Workflow Developer | AI Agents & Business Process Automation

Interested in building practical automation systems that connect business tools, reduce repetitive work, and improve customer operations.

- GitHub: [@Yesy121](https://github.com/Yesy121)
