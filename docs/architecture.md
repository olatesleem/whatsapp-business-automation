# BookBot Architecture

## Main message path

1. **WhatsApp Trigger** receives an incoming customer message.
2. **AI Agent** reads the message and applies the BookBot system instructions.
3. **OpenAI Chat Model** provides the language-model reasoning.
4. **Simple Memory** supplies a bounded conversational context window.
5. The agent can call connected Google Sheets tools for inventory, orders, customer data, cart data and sales records.
6. The **send_email** Gmail tool sends customer emails when requested by the agent.
7. **WhatsApp Business Cloud** sends the response back to the customer.

## Tool names exposed to the AI Agent

| Tool name | Intended responsibility |
|---|---|
| `search_inventory` | Search the book catalogue, prices and stock |
| `update_inventory` | Update a book's stock quantity |
| `create_order` | Append a new order |
| `search_orders` | Retrieve an order for tracking or eligibility checks |
| `order_update` | Update an existing order record |
| `send_email` | Send order-related customer emails |
| `cart_search`, `cart_add`, `cart_update` | Cart line operations; worksheet references need configuration |
| `customer_search`, `customer_create`, `customer_update` | Customer record operations |
| `sale_record` | Record a sale |

The primary tool names above are aligned with the tool names listed in the AI Agent's system instructions.

## Data domains

| Data domain | Google Sheets nodes | Intended role |
|---|---|---|
| Inventory | search_inventory, update_inventory | Book catalogue, price and stock |
| Orders | create_order, search_orders, order_update | Create, retrieve and update order records |
| Customers | customer_search, customer_create, customer_update | Customer profile records |
| Cart | cart_search, cart_add, cart_update, orderItem_create | Cart line management |
| Sales | sale_record | Sales record creation |

## Operational boundaries

The JSON contains tool connections and AI instructions, but this document describes intended architecture, not proof of successful execution. Spreadsheet IDs, tab references, credentials and WhatsApp settings must be supplied in the target environment. The legacy connected tools `Get all orders`, `Delete Order` and `cancle Order` remain in the export and should be reviewed; `Delete Order` is a destructive operation.
