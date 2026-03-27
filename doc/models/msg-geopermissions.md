
# Msg Geopermissions

*This model accepts additional fields of type array.*

## Structure

`MsgGeopermissions`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `permissions` | `?array` | Optional | A list of objects where each object represents the result of processing a messaging Geo Permission. Each object contains the following fields: `country_code`, the country code of the country for which the permission was updated; `type`, the type of the permission i.e. country; `enabled`, true if the permission is enabled else false; `error_code`, an integer where 0 indicates success and any non-zero value represents an error; and `error_messages`, an array of strings describing specific validation errors encountered. If the request is successful, the error_messages array will be empty. | getPermissions(): ?array | setPermissions(?array permissions): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "permissions": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

