
# Access Token

*This model accepts additional fields of type array.*

## Structure

`AccessToken`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this Access Token.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^YK[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique SID identifier of the Account.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `serviceSid` | `?string` | Optional | The unique SID identifier of the Verify Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `entityIdentity` | `?string` | Optional | The unique external identifier for the Entity of the Service. | getEntityIdentity(): ?string | setEntityIdentity(?string entityIdentity): void |
| `factorType` | [`?string(AccessTokenEnumFactorTypes)`](../../doc/models/access-token-enum-factor-types.md) | Optional | The Type of the Factor. Currently only `push` is supported. | getFactorType(): ?string | setFactorType(?string factorType): void |
| `factorFriendlyName` | `?string` | Optional | A human readable description of this factor, up to 64 characters. For a push factor, this can be the device's name. | getFactorFriendlyName(): ?string | setFactorFriendlyName(?string factorFriendlyName): void |
| `token` | `?string` | Optional | The access token generated for enrollment, this is an encrypted json web token. | getToken(): ?string | setToken(?string token): void |
| `url` | `?string` | Optional | The URL of this resource. | getUrl(): ?string | setUrl(?string url): void |
| `ttl` | `?int` | Optional | How long, in seconds, the access token is valid. Max: 5 minutes<br><br>**Default**: `0` | getTtl(): ?int | setTtl(?int ttl): void |
| `dateCreated` | `?DateTime` | Optional | The date that this access token was created, given in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "ttl": 0,
  "sid": "sid8",
  "account_sid": "account_sid6",
  "service_sid": "service_sid2",
  "entity_identity": "entity_identity0",
  "factor_type": "push",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

