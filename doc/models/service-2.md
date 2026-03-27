
# Service 2

*This model accepts additional fields of type array.*

## Structure

`Service2`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | The name that appears in the body of your verification messages. It can be up to 30 characters long and can include letters, numbers, spaces, dashes, underscores. Phone numbers, special characters or links are NOT allowed. It cannot contain more than 4 (consecutive or non-consecutive) digits. **This value should not contain PII.** | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `codeLength` | `?int` | Optional | The length of the verification code to generate.<br><br>**Default**: `0` | getCodeLength(): ?int | setCodeLength(?int codeLength): void |
| `lookupEnabled` | `?bool` | Optional | Whether to perform a lookup with each verification started and return info about the phone number. | getLookupEnabled(): ?bool | setLookupEnabled(?bool lookupEnabled): void |
| `psd2Enabled` | `?bool` | Optional | Whether to pass PSD2 transaction parameters when starting a verification. | getPsd2Enabled(): ?bool | setPsd2Enabled(?bool psd2Enabled): void |
| `skipSmsToLandlines` | `?bool` | Optional | Whether to skip sending SMS verifications to landlines. Requires `lookup_enabled`. | getSkipSmsToLandlines(): ?bool | setSkipSmsToLandlines(?bool skipSmsToLandlines): void |
| `dtmfInputRequired` | `?bool` | Optional | Whether to ask the user to press a number before delivering the verify code in a phone call. | getDtmfInputRequired(): ?bool | setDtmfInputRequired(?bool dtmfInputRequired): void |
| `ttsName` | `?string` | Optional | The name of an alternative text-to-speech service to use in phone calls. Applies only to TTS languages. | getTtsName(): ?string | setTtsName(?string ttsName): void |
| `doNotShareWarningEnabled` | `?bool` | Optional | Whether to add a security warning at the end of an SMS verification body. Disabled by default and applies only to SMS. Example SMS body: `Your AppName verification code is: 1234. Don’t share this code with anyone; our employees will never ask for the code` | getDoNotShareWarningEnabled(): ?bool | setDoNotShareWarningEnabled(?bool doNotShareWarningEnabled): void |
| `customCodeEnabled` | `?bool` | Optional | Whether to allow sending verifications with a custom code instead of a randomly generated one. | getCustomCodeEnabled(): ?bool | setCustomCodeEnabled(?bool customCodeEnabled): void |
| `push` | `?array` | Optional | Configurations for the Push factors (channel) created under this Service. | getPush(): ?array | setPush(?array push): void |
| `totp` | `?array` | Optional | Configurations for the TOTP factors (channel) created under this Service. | getTotp(): ?array | setTotp(?array totp): void |
| `defaultTemplateSid` | `?string` | Optional | **Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` | getDefaultTemplateSid(): ?string | setDefaultTemplateSid(?string defaultTemplateSid): void |
| `whatsapp` | `?array` | Optional | - | getWhatsapp(): ?array | setWhatsapp(?array whatsapp): void |
| `passkeys` | `?array` | Optional | - | getPasskeys(): ?array | setPasskeys(?array passkeys): void |
| `verifyEventSubscriptionEnabled` | `?bool` | Optional | Whether to allow verifications from the service to reach the stream-events sinks if configured | getVerifyEventSubscriptionEnabled(): ?bool | setVerifyEventSubscriptionEnabled(?bool verifyEventSubscriptionEnabled): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | The absolute URL of the resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "code_length": 0,
  "sid": "sid6",
  "account_sid": "account_sid0",
  "friendly_name": "friendly_name0",
  "lookup_enabled": false,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

