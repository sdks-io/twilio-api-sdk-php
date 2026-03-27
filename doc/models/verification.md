
# Verification

*This model accepts additional fields of type array.*

## Structure

`Verification`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the Verification resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VE[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Verification resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `to` | `?string` | Optional | The phone number or [email](https://www.twilio.com/docs/verify/email) being verified. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). | getTo(): ?string | setTo(?string to): void |
| `channel` | [`?string(VerificationEnumChannel)`](../../doc/models/verification-enum-channel.md) | Optional | The verification method used. One of: [`email`](https://www.twilio.com/docs/verify/email), `sms`, `whatsapp`, `call`, `sna`, or `rcs`. | getChannel(): ?string | setChannel(?string channel): void |
| `status` | `?string` | Optional | The status of the verification. Can be: `pending`, `approved`, `canceled`, `max_attempts_reached`, `deleted`, `failed` or `expired`. | getStatus(): ?string | setStatus(?string status): void |
| `valid` | `?bool` | Optional | Use "status" instead. Legacy property indicating whether the verification was successful. | getValid(): ?bool | setValid(?bool valid): void |
| `lookup` | `?array` | Optional | Information about the phone number being verified. | getLookup(): ?array | setLookup(?array lookup): void |
| `amount` | `?string` | Optional | The amount of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. | getAmount(): ?string | setAmount(?string amount): void |
| `payee` | `?string` | Optional | The payee of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. | getPayee(): ?string | setPayee(?string payee): void |
| `sendCodeAttempts` | `?(array[])` | Optional | An array of verification attempt objects containing the channel attempted and the channel-specific transaction SID. | getSendCodeAttempts(): ?array | setSendCodeAttempts(?array sendCodeAttempts): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `sna` | `?array` | Optional | The set of fields used for a silent network auth (`sna`) verification. Contains a single field with the URL to be invoked to verify the phone number. | getSna(): ?array | setSna(?array sna): void |
| `url` | `?string` | Optional | The absolute URL of the Verification resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "service_sid": "service_sid2",
  "account_sid": "account_sid6",
  "to": "to6",
  "channel": "sna",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

