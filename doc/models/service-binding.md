
# Service Binding

*This model accepts additional fields of type array.*

## Structure

`ServiceBinding`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this binding.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `credentialSid` | `?string` | Optional | The SID of the [Credential](https://www.twilio.com/docs/conversations/api/credential-resource) for the binding. See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` | getCredentialSid(): ?string | setCredentialSid(?string credentialSid): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `endpoint` | `?string` | Optional | The unique endpoint identifier for the Binding. The format of this value depends on the `binding_type`. | getEndpoint(): ?string | setEndpoint(?string endpoint): void |
| `identity` | `?string` | Optional | The application-defined string that uniquely identifies the [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource) within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). See [access tokens](https://www.twilio.com/docs/conversations/create-tokens) for more info. | getIdentity(): ?string | setIdentity(?string identity): void |
| `bindingType` | [`?string(ServiceBindingBindingType)`](../../doc/models/service-binding-binding-type.md) | Optional | The push technology to use for the Binding. Can be: `apn`, `gcm`, `fcm`, or `twilsock`.  See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info. | getBindingType(): ?string | setBindingType(?string bindingType): void |
| `messageTypes` | `?(string[])` | Optional | The [Conversation message types](https://www.twilio.com/docs/chat/push-notification-configuration#push-types) the binding is subscribed to. | getMessageTypes(): ?array | setMessageTypes(?array messageTypes): void |
| `url` | `?string` | Optional | An absolute API resource URL for this binding. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "account_sid": "account_sid8",
  "chat_service_sid": "chat_service_sid2",
  "credential_sid": "credential_sid2",
  "date_created": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

