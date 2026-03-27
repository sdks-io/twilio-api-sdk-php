
# List Service Conversation Scoped Webhook Response

*This model accepts additional fields of type array.*

## Structure

`ListServiceConversationScopedWebhookResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `webhooks` | [`?(ServiceConversationScopedWebhook[])`](../../doc/models/service-conversation-scoped-webhook.md) | Optional | - | getWebhooks(): ?array | setWebhooks(?array webhooks): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "webhooks": [
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "chat_service_sid": "chat_service_sid6",
      "conversation_sid": "conversation_sid8",
      "target": "target6",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "chat_service_sid": "chat_service_sid6",
      "conversation_sid": "conversation_sid8",
      "target": "target6",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "meta": {
    "first_page_url": "first_page_url0",
    "key": "key2",
    "next_page_url": "next_page_url4",
    "page": 240,
    "page_size": 56,
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

