
# Safelist

*This model accepts additional fields of type array.*

## Structure

`Safelist`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the SafeList resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^GN[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `phoneNumber` | `?string` | Optional | The phone number or phone number 1k prefix in SafeList. | getPhoneNumber(): ?string | setPhoneNumber(?string phoneNumber): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "phone_number": "phone_number6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

