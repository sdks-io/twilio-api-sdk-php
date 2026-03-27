
# List Task Channel Response

*This model accepts additional fields of type array.*

## Structure

`ListTaskChannelResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `channels` | [`?(TaskChannel[])`](../../doc/models/task-channel.md) | Optional | - | getChannels(): ?array | setChannels(?array channels): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "channels": [
    {
      "account_sid": "account_sid6",
      "date_created": "2016-03-13T12:52:32.123Z",
      "date_updated": "2016-03-13T12:52:32.123Z",
      "friendly_name": "friendly_name6",
      "sid": "sid2",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "account_sid": "account_sid6",
      "date_created": "2016-03-13T12:52:32.123Z",
      "date_updated": "2016-03-13T12:52:32.123Z",
      "friendly_name": "friendly_name6",
      "sid": "sid2",
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

