
# Verification Attempt

*This model accepts additional fields of type array.*

## Structure

`VerificationAttempt`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The SID that uniquely identifies the verification attempt resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VL[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Verification resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) used to generate the attempt.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `verificationSid` | `?string` | Optional | The SID of the [Verification](https://www.twilio.com/docs/verify/api/verification) that generated the attempt.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VE[0-9a-fA-F]{32}$` | getVerificationSid(): ?string | setVerificationSid(?string verificationSid): void |
| `dateCreated` | `?DateTime` | Optional | The date that this Attempt was created, given in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this Attempt was updated, given in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `conversionStatus` | [`?string(VerificationAttemptEnumConversionStatus)`](../../doc/models/verification-attempt-enum-conversion-status.md) | Optional | A string specifying the conversion status of the verification. A conversion happens when the user is able to provide the correct code. Possible values are `CONVERTED` and `UNCONVERTED`. | getConversionStatus(): ?string | setConversionStatus(?string conversionStatus): void |
| `channel` | [`?string(VerificationAttemptEnumChannels)`](../../doc/models/verification-attempt-enum-channels.md) | Optional | A string specifying the communication channel used for the verification attempt. | getChannel(): ?string | setChannel(?string channel): void |
| `price` | `?array` | Optional | An object containing the charge for this verification attempt related to the channel costs and the currency used. The costs related to the succeeded verifications are not included. May not be immediately available. More information on pricing is available [here](https://www.twilio.com/en-us/verify/pricing). | getPrice(): ?array | setPrice(?array price): void |
| `channelData` | `?array` | Optional | An object containing the channel specific information for an attempt. | getChannelData(): ?array | setChannelData(?array channelData): void |
| `url` | `?string` | Optional | - | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "account_sid": "account_sid8",
  "service_sid": "service_sid0",
  "verification_sid": "verification_sid2",
  "date_created": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

