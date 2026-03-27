
# List Credential Response

*This model accepts additional fields of type array.*

## Structure

`ListCredentialResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `credentials` | [`?(Credential[])`](../../doc/models/credential.md) | Optional | - | getCredentials(): ?array | setCredentials(?array credentials): void |
| `meta` | [`?Meta`](../../doc/models/meta.md) | Optional | - | getMeta(): ?Meta | setMeta(?Meta meta): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "credentials": [
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "friendly_name": "friendly_name8",
      "type": "fcm",
      "sandbox": "sandbox6",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "friendly_name": "friendly_name8",
      "type": "fcm",
      "sandbox": "sandbox6",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "sid": "sid2",
      "account_sid": "account_sid2",
      "friendly_name": "friendly_name8",
      "type": "fcm",
      "sandbox": "sandbox6",
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

