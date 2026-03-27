
# Bucket

*This model accepts additional fields of type array.*

## Structure

`Bucket`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this Bucket.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BL[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `rateLimitSid` | `?string` | Optional | The Twilio-provided string that uniquely identifies the Rate Limit resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RK[0-9a-fA-F]{32}$` | getRateLimitSid(): ?string | setRateLimitSid(?string rateLimitSid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Rate Limit resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `max` | `?int` | Optional | Maximum number of requests permitted in during the interval.<br><br>**Default**: `0` | getMax(): ?int | setMax(?int max): void |
| `interval` | `?int` | Optional | Number of seconds that the rate limit will be enforced over.<br><br>**Default**: `0` | getInterval(): ?int | setInterval(?int interval): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The URL of this resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "max": 0,
  "interval": 0,
  "sid": "sid6",
  "rate_limit_sid": "rate_limit_sid0",
  "service_sid": "service_sid0",
  "account_sid": "account_sid8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

