# n8n Workflow Export

The sanitised n8n workflow JSON will be stored in this directory once the original workflow configuration has been recovered and reviewed.

## Why the export is not included yet

The public project description confirms the customer use case and welcome-response behaviour, but the exact provider, trigger, nodes, configuration, and payloads have not been verified from the original workflow. A fabricated export would be misleading and may not import or run.

## Before committing an export

- Export the workflow from the original n8n instance.
- Remove credentials and secret values.
- Replace private account identifiers and phone numbers with safe placeholders where appropriate.
- Check for customer information in node parameters, sample data, and pinned execution data.
- Validate the sanitised JSON and test the import in a safe n8n environment.
