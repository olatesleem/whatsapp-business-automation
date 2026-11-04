# Workflow Explanation

## Business use case

The project was developed around a household-utensils business that receives customer enquiries through WhatsApp.

## Confirmed customer journey

1. A customer sends a message to the business WhatsApp account.
2. The incoming message starts the automated response flow.
3. The business sends a welcome message introducing the business and its products.
4. The welcome message invites the customer to ask about products, prices, availability, and delivery.

## Intended value

- Provides a consistent first response.
- Helps customers understand what information they can request.
- Reduces repetitive manual introductory messages.
- Gives a small business a more structured starting point for customer conversations.

## Scope boundaries

The confirmed project description covers an automated welcome response. It does not establish that the system uses an AI agent, CRM, payment processing, inventory lookup, or fully automated order fulfilment. Those capabilities must not be presented as implemented features without evidence from the workflow.

## Technical notes

The project uses n8n automation concepts and WhatsApp integration, with APIs, webhooks, and JSON relevant to the integration approach. Exact node names, conditions, payloads, and provider details will be documented after inspecting the original workflow.
