
# Configuration Address

*This model accepts additional fields of type array.*

## Structure

`ConfigurationAddress`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IG[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) the address belongs to<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `type` | `?string` | Optional | Type of Address, value can be `whatsapp` or `sms`. | getType(): ?string | setType(?string type): void |
| `address` | `?string` | Optional | The unique address to be configured. The address can be a whatsapp address or phone number | getAddress(): ?string | setAddress(?string address): void |
| `friendlyName` | `?string` | Optional | The human-readable name of this configuration, limited to 256 characters. Optional. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `autoCreation` | `?array` | Optional | Auto Creation configuration for the address. | getAutoCreation(): ?array | setAutoCreation(?array autoCreation): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | An absolute API resource URL for this address configuration. | getUrl(): ?string | setUrl(?string url): void |
| `addressCountry` | `?string` | Optional | An ISO 3166-1 alpha-2n country code which the address belongs to. This is currently only applicable to short code addresses. | getAddressCountry(): ?string | setAddressCountry(?string addressCountry): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "account_sid": "account_sid8",
  "type": "type8",
  "address": "address8",
  "friendly_name": "friendly_name8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

