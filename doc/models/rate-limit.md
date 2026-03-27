
# Rate Limit

*This model accepts additional fields of type array.*

## Structure

`RateLimit`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this Rate Limit.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RK[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Rate Limit resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `uniqueName` | `?string` | Optional | Provides a unique and addressable name to be assigned to this Rate Limit, assigned by the developer, to be optionally used in addition to SID. **This value should not contain PII.** | getUniqueName(): ?string | setUniqueName(?string uniqueName): void |
| `description` | `?string` | Optional | Description of this Rate Limit | getDescription(): ?string | setDescription(?string description): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The URL of this resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "service_sid": "service_sid4",
  "account_sid": "account_sid2",
  "unique_name": "unique_name0",
  "description": "description6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

