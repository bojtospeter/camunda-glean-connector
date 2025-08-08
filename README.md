
# Camunda Glean Connector

Supercharge your Camunda workflows with Glean’s AI-powered enterprise search! The Camunda Glean Connector brings intelligent information discovery and automation to your business processes, enabling you to instantly surface relevant knowledge from across your organization and drive smarter, faster decisions at scale.

## Prerequisites:

1. Camunda Modeler, which is available in two variants:
    - [Desktop Modeler](https://camunda.com/download/modeler/) for a local installation.
    - [Web Modeler](https://modeler.camunda.io/) for an online experience with a Camunda SaaS account


### Configuring Camunda Modeler

1. Install the Camunda Modeler if not already done.
2. Add the `element-templates/template-connector.json` to your Modeler configuration as per
   the [Element Templates documentation](https://docs.camunda.io/docs/components/modeler/desktop-modeler/element-templates/configuring-templates/).

## Installing the Glean Connector

This connector is a template connector based on the Camunda REST connector, so no compilation is required. To install and use it in your Camunda project:

1. **Download or copy the element template**
   - Locate the file `element-templates/glean_search_connector.json` in this repository.
   - Copy it to your Camunda Modeler configuration folder as described in the [Element Templates documentation](https://docs.camunda.io/docs/components/modeler/desktop-modeler/element-templates/configuring-templates/).

2. **Configure the REST connector in Camunda Platform**
   - Ensure the REST connector is enabled in your Camunda Platform instance. For SaaS, it is available by default. For self-managed, follow the [REST connector installation guide](https://docs.camunda.io/docs/components/connectors/connectors/rest/).

3. **Use the Glean Connector in your BPMN model**
   - In Camunda Modeler, select the Glean connector from the palette or properties panel, configure it using the element template, and deploy your process.

No build or compilation steps are necessary—just add the template and start automating with Glean!


## Configuring your Glean Connector

The Glean connector needs the following parameters to successfully run:

- Bearer token
- HTTP endpoint of your Glean instance
- Your question you want Glean to responde to

Your answer will contain what Glean has to tell you in JSON.

## Output

Example output
```json
{
  "result": {
    "messages": [
      {
        "role": "user",
        "content": "How do I reset my company password?"
      },
      {
        "role": "assistant",
        "content": "To reset your company password, visit the internal portal and follow the password reset instructions. If you need further assistance, contact IT support."
      }
    ],
    "chatId": "abc123",
    "status": "success"
  }
}
```

### Error codes

| Code | Description |
|------|-------------|
| 200  | OK - Request was successful |
| 400  | Bad Request - The request was invalid or cannot be otherwise served |
| 401  | Unauthorized - Authentication credentials were missing or incorrect |
| 408  | Request Timeout - The server timed out waiting for the request |
| 429  | Too Many Requests - Rate limit exceeded |

