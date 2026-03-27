
# Verification Check

*This model accepts additional fields of type array.*

## Structure

`VerificationCheck`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the VerificationCheck resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VE[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the VerificationCheck resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `to` | `?string` | Optional | The phone number or [email](https://www.twilio.com/docs/verify/email) being verified. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). | getTo(): ?string | setTo(?string to): void |
| `channel` | [`?string(VerificationCheckEnumChannel)`](../../doc/models/verification-check-enum-channel.md) | Optional | The verification method to use. One of: [`email`](https://www.twilio.com/docs/verify/email), `sms`, `whatsapp`, `call`, or `sna`. | getChannel(): ?string | setChannel(?string channel): void |
| `status` | `?string` | Optional | The status of the verification. Can be: `pending`, `approved`, `canceled`, `max_attempts_reached`, `deleted`, `failed` or `expired`. | getStatus(): ?string | setStatus(?string status): void |
| `valid` | `?bool` | Optional | Use "status" instead. Legacy property indicating whether the verification was successful. | getValid(): ?bool | setValid(?bool valid): void |
| `amount` | `?string` | Optional | The amount of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. | getAmount(): ?string | setAmount(?string amount): void |
| `payee` | `?string` | Optional | The payee of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. | getPayee(): ?string | setPayee(?string payee): void |
| `dateCreated` | `?DateTime` | Optional | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date and time in GMT when the Verification Check resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date and time in GMT when the Verification Check resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `snaAttemptsErrorCodes` | `?(array[])` | Optional | List of error codes as a result of attempting a verification using the `sna` channel. The error codes are chronologically ordered, from the first attempt to the latest attempt. This will be an empty list if no errors occured or `null` if the last channel used wasn't `sna`. | getSnaAttemptsErrorCodes(): ?array | setSnaAttemptsErrorCodes(?array snaAttemptsErrorCodes): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
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

