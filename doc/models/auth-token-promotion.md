
# Auth Token Promotion

*This model accepts additional fields of type array.*

## Structure

`AuthTokenPromotion`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that the secondary Auth Token was created for.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `authToken` | `?string` | Optional | The promoted Auth Token that must be used to authenticate future API requests. | getAuthToken(): ?string | setAuthToken(?string authToken): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in UTC when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The URI for this resource, relative to `https://accounts.twilio.com` | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "auth_token": "auth_token4",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "url": "url2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

