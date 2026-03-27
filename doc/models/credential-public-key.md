
# Credential Public Key

*This model accepts additional fields of type array.*

## Structure

`CredentialPublicKey`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that that we created to identify the PublicKey resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Credential that the PublicKey resource belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The URI for this resource, relative to `https://accounts.twilio.com` | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name2",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

