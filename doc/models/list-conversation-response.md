
# List Conversation Response

*This model accepts additional fields of type array.*

## Structure

`ListConversationResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `conversations` | [`?(Conversation[])`](../../doc/models/conversation.md) | Optional | - | getConversations(): ?array | setConversations(?array conversations): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "conversations": [
    {
      "account_sid": "account_sid6",
      "chat_service_sid": "chat_service_sid0",
      "messaging_service_sid": "messaging_service_sid0",
      "sid": "sid2",
      "friendly_name": "friendly_name6",
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

