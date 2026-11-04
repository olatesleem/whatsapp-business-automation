# Setup Guide

## Current status

This guide is a preparation checklist, not a complete provider-specific installation procedure. The original n8n workflow export and WhatsApp provider configuration have not yet been verified in this repository.

## Before setup

You will need access to:
- An n8n instance
- The WhatsApp Business integration used by the original project
- The relevant account and API configuration for that integration

The exact provider, account requirements, and API permissions must be confirmed from the original implementation.

## Importing the workflow

Once a verified workflow export is added:

1. Open your n8n instance.
2. Use the workflow import option to import the JSON file from the `workflow/` directory.
3. Review every node and replace placeholder values with your own configuration.
4. Configure credentials through n8n's credential manager.
5. Confirm the incoming trigger and outbound message settings for your WhatsApp provider.
6. Test with a controlled account before enabling the workflow for real customer conversations.

Do not assume this project is ready for production until the actual export, credentials, event handling, and failure behaviour have been reviewed.

## Security checklist

- Keep credentials in n8n's credential manager.
- Do not put access tokens, API keys, or webhook secrets in workflow JSON committed to Git.
- Use placeholders for account IDs and phone-number identifiers in public examples.
- Remove or anonymise customer phone numbers and message content in screenshots and execution examples.
- Restrict access to the n8n instance and its execution data.

## Testing checklist

- Confirm that a valid incoming customer message triggers the workflow.
- Confirm that the intended welcome response is sent.
- Check how the workflow behaves when a message cannot be processed.
- Check whether repeated webhook events could cause duplicate responses.
- Verify that no secrets or personal customer data appear in logs or exported files.

Provider-specific instructions will be added after the original workflow configuration is recovered.
