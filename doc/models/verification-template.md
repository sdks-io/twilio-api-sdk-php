
# Verification Template

*This model accepts additional fields of type array.*

## Structure

`VerificationTemplate`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies a Verification Template.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique SID identifier of the Account.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | A descriptive string that you create to describe a Template. It can be up to 32 characters long. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `channels` | `?(string[])` | Optional | A list of channels that support the Template. Can include: sms, voice. | getChannels(): ?array | setChannels(?array channels): void |
| `translations` | `?array` | Optional | An object that contains the different translations of the template. Every translation is identified by the language short name and contains its respective information as the approval status, text and created/modified date. | getTranslations(): ?array | setTranslations(?array translations): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name2",
  "channels": [
    "channels1",
    "channels0"
  ],
  "translations": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

