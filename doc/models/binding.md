
# Binding

*This model accepts additional fields of type array.*

## Structure

`Binding`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the Binding resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Binding resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `serviceSid` | `?string` | Optional | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getServiceSid(): ?string | setServiceSid(?string serviceSid): void |
| `credentialSid` | `?string` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) resource to be used to send notifications to this Binding. If present, this overrides the Credential specified in the Service resource. Applicable only to `apn`, `fcm`, and `gcm` type Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getCredentialSid(): ?string | setCredentialSid(?string credentialSid): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `notificationProtocolVersion` | `?string` | Optional | The protocol version to use to send the notification. This defaults to the value of `default_xxxx_notification_protocol_version` in the [Service](https://www.twilio.com/docs/notify/api/service-resource) for the protocol. The current version is `"3"` for `apn`, `fcm`, and `gcm` type Bindings. The parameter is not applicable to `sms` and `facebook-messenger` type Bindings as the data format is fixed. | getNotificationProtocolVersion(): ?string | setNotificationProtocolVersion(?string notificationProtocolVersion): void |
| `endpoint` | `?string` | Optional | Deprecated. | getEndpoint(): ?string | setEndpoint(?string endpoint): void |
| `identity` | `?string` | Optional | The `identity` value that uniquely identifies the resource's [User](https://www.twilio.com/docs/chat/rest/user-resource) within the [Service](https://www.twilio.com/docs/notify/api/service-resource). Up to 20 Bindings can be created for the same Identity in a given Service. | getIdentity(): ?string | setIdentity(?string identity): void |
| `bindingType` | `?string` | Optional | The transport technology to use for the Binding. Can be: `apn`, `fcm`, `gcm`, `sms`, or `facebook-messenger`. | getBindingType(): ?string | setBindingType(?string bindingType): void |
| `address` | `?string` | Optional | The channel-specific address. For APNS, the device token. For FCM and GCM, the registration token. For SMS, a phone number in E.164 format. For Facebook Messenger, the Messenger ID of the user or a phone number in E.164 format. | getAddress(): ?string | setAddress(?string address): void |
| `tags` | `?(string[])` | Optional | The list of tags associated with this Binding. Tags can be used to select the Bindings to use when sending a notification. Maximum 20 tags are allowed. | getTags(): ?array | setTags(?array tags): void |
| `url` | `?string` | Optional | The absolute URL of the Binding resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid0",
  "account_sid": "account_sid4",
  "service_sid": "service_sid4",
  "credential_sid": "credential_sid8",
  "date_created": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

