
# Webhook

*This model accepts additional fields of type array.*

## Structure

`Webhook`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the Webhook resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^YW[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `serviceSid` | `?string` | Optional | The unique SID identifier of the Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the webhook. **This value should not contain PII.** | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `eventTypes` | `?(string[])` | Optional | The array of events that this Webhook is subscribed to. Possible event types: `*, factor.deleted, factor.created, factor.verified, challenge.approved, challenge.denied` | getEventTypes(): ?array | setEventTypes(?array eventTypes): void |
| `status` | [`?string(WebhookEnumStatus)`](../../doc/models/webhook-enum-status.md) | Optional | The webhook status. Default value is `enabled`. One of: `enabled` or `disabled` | getStatus(): ?string | setStatus(?string status): void |
| `version` | [`?string(WebhookEnumVersion)`](../../doc/models/webhook-enum-version.md) | Optional | The webhook version. Default value is `v2` which includes all the latest fields. Version `v1` is legacy and may be removed in the future. | getVersion(): ?string | setVersion(?string version): void |
| `webhookUrl` | `?string` | Optional | The URL associated with this Webhook. | getWebhookUrl(): ?string | setWebhookUrl(?string webhookUrl): void |
| `webhookMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Optional | The method to be used when calling the webhook's URL. | getWebhookMethod(): ?string | setWebhookMethod(?string webhookMethod): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The absolute URL of the Webhook resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "service_sid": "service_sid6",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name8",
  "event_types": [
    "event_types4",
    "event_types5"
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

