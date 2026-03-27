
# Safelist 1

*This model accepts additional fields of type array.*

## Structure

`Safelist1`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the SafeList resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^GN[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `phoneNumber` | `?string` | Optional | The phone number in SafeList. | getPhoneNumber(): ?string | setPhoneNumber(?string phoneNumber): void |
| `url` | `?string` | Optional | The absolute URL of the SafeList resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "phone_number": "phone_number8",
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

