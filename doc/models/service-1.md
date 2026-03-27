
# Service 1

*This model accepts additional fields of type array.*

## Structure

`Service1`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `apnCredentialSid` | `?string` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getApnCredentialSid(): ?string | setApnCredentialSid(?string apnCredentialSid): void |
| `gcmCredentialSid` | `?string` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getGcmCredentialSid(): ?string | setGcmCredentialSid(?string gcmCredentialSid): void |
| `fcmCredentialSid` | `?string` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getFcmCredentialSid(): ?string | setFcmCredentialSid(?string fcmCredentialSid): void |
| `messagingServiceSid` | `?string` | Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. In order to send SMS notifications this parameter has to be set.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` | getMessagingServiceSid(): ?string | setMessagingServiceSid(?string messagingServiceSid): void |
| `facebookMessengerPageId` | `?string` | Optional | Deprecated. | getFacebookMessengerPageId(): ?string | setFacebookMessengerPageId(?string facebookMessengerPageId): void |
| `defaultApnNotificationProtocolVersion` | `?string` | Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. | getDefaultApnNotificationProtocolVersion(): ?string | setDefaultApnNotificationProtocolVersion(?string defaultApnNotificationProtocolVersion): void |
| `defaultGcmNotificationProtocolVersion` | `?string` | Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. | getDefaultGcmNotificationProtocolVersion(): ?string | setDefaultGcmNotificationProtocolVersion(?string defaultGcmNotificationProtocolVersion): void |
| `defaultFcmNotificationProtocolVersion` | `?string` | Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. | getDefaultFcmNotificationProtocolVersion(): ?string | setDefaultFcmNotificationProtocolVersion(?string defaultFcmNotificationProtocolVersion): void |
| `logEnabled` | `?bool` | Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. | getLogEnabled(): ?bool | setLogEnabled(?bool logEnabled): void |
| `url` | `?string` | Optional | The absolute URL of the Service resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of the Binding, Notification, Segment, and User resources related to the service. | getLinks(): ?array | setLinks(?array links): void |
| `alexaSkillId` | `?string` | Optional | Deprecated. | getAlexaSkillId(): ?string | setAlexaSkillId(?string alexaSkillId): void |
| `defaultAlexaNotificationProtocolVersion` | `?string` | Optional | Deprecated. | getDefaultAlexaNotificationProtocolVersion(): ?string | setDefaultAlexaNotificationProtocolVersion(?string defaultAlexaNotificationProtocolVersion): void |
| `deliveryCallbackUrl` | `?string` | Optional | URL to send delivery status callback. | getDeliveryCallbackUrl(): ?string | setDeliveryCallbackUrl(?string deliveryCallbackUrl): void |
| `deliveryCallbackEnabled` | `?bool` | Optional | Callback configuration that enables delivery callbacks, default false | getDeliveryCallbackEnabled(): ?bool | setDeliveryCallbackEnabled(?bool deliveryCallbackEnabled): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid6",
  "friendly_name": "friendly_name6",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

