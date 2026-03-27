
# List Conversation Message Receipt Response

*This model accepts additional fields of type array.*

## Structure

`ListConversationMessageReceiptResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `deliveryReceipts` | [`?(ConversationMessageReceipt[])`](../../doc/models/conversation-message-receipt.md) | Optional | - | getDeliveryReceipts(): ?array | setDeliveryReceipts(?array deliveryReceipts): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "delivery_receipts": [
    {
      "account_sid": "account_sid6",
      "conversation_sid": "conversation_sid4",
      "sid": "sid8",
      "message_sid": "message_sid8",
      "channel_message_sid": "channel_message_sid6",
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

