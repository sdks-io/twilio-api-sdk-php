
# Service User

*This model accepts additional fields of type array.*

## Structure

`ServiceUser`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | The unique string that we created to identify the User resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^US[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the User resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the User resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `roleSid` | `?string` | Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) assigned to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` | getRoleSid(): ?string | setRoleSid(?string roleSid): void |
| `identity` | `?string` | Optional | The application-defined string that uniquely identifies the resource's User within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). This value is often a username or an email address, and is case-sensitive. | getIdentity(): ?string | setIdentity(?string identity): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `attributes` | `?string` | Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `isOnline` | `?bool` | Optional | Whether the User is actively connected to this Conversations Service and online. This value is only returned by Fetch actions that return a single resource and `null` is always returned by a Read action. This value is `null` if the Service's `reachability_enabled` is `false`, if the User has never been online for this Conversations Service, even if the Service's `reachability_enabled` is `true`. | getIsOnline(): ?bool | setIsOnline(?bool isOnline): void |
| `isNotifiable` | `?bool` | Optional | Whether the User has a potentially valid Push Notification registration (APN or GCM) for this Conversations Service. If at least one registration exists, `true`; otherwise `false`. This value is only returned by Fetch actions that return a single resource and `null` is always returned by a Read action. This value is `null` if the Service's `reachability_enabled` is `false`, and if the User has never had a notification registration, even if the Service's `reachability_enabled` is `true`. | getIsNotifiable(): ?bool | setIsNotifiable(?bool isNotifiable): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | An absolute API resource URL for this user. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | - | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid6",
  "chat_service_sid": "chat_service_sid0",
  "role_sid": "role_sid6",
  "identity": "identity4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

