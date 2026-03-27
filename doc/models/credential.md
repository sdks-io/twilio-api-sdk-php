
# Credential

*This model accepts additional fields of type array.*

## Structure

`Credential`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this credential.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | The human-readable name of this credential, limited to 64 characters. Optional. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `type` | [`?string(CredentialPushType)`](../../doc/models/credential-push-type.md) | Optional | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. | getType(): ?string | setType(?string type): void |
| `sandbox` | `?string` | Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. | getSandbox(): ?string | setSandbox(?string sandbox): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | An absolute API resource URL for this credential. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "account_sid": "account_sid6",
  "friendly_name": "friendly_name6",
  "type": "gcm",
  "sandbox": "sandbox8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

