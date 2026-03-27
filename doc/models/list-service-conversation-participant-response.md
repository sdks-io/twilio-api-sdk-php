
# List Service Conversation Participant Response

*This model accepts additional fields of type array.*

## Structure

`ListServiceConversationParticipantResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `participants` | [`?(ServiceConversationParticipant[])`](../../doc/models/service-conversation-participant.md) | Optional | - | getParticipants(): ?array | setParticipants(?array participants): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "participants": [
    {
      "account_sid": "account_sid0",
      "chat_service_sid": "chat_service_sid4",
      "conversation_sid": "conversation_sid0",
      "sid": "sid6",
      "identity": "identity8",
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

