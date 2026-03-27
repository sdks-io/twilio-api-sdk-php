
# List Service Conversation Message Response

*This model accepts additional fields of type array.*

## Structure

`ListServiceConversationMessageResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `messages` | [`?(ServiceConversationMessage[])`](../../doc/models/service-conversation-message.md) | Optional | - | getMessages(): ?array | setMessages(?array messages): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "messages": [
    {
      "account_sid": "account_sid4",
      "chat_service_sid": "chat_service_sid8",
      "conversation_sid": "conversation_sid4",
      "sid": "sid0",
      "index": 144,
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "account_sid": "account_sid4",
      "chat_service_sid": "chat_service_sid8",
      "conversation_sid": "conversation_sid4",
      "sid": "sid0",
      "index": 144,
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "account_sid": "account_sid4",
      "chat_service_sid": "chat_service_sid8",
      "conversation_sid": "conversation_sid4",
      "sid": "sid0",
      "index": 144,
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

