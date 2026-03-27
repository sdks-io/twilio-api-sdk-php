
# Workflow

*This model accepts additional fields of type array.*

## Structure

`Workflow`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workflow resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `assignmentCallbackUrl` | `?string` | Optional | The URL that we call when a task managed by the Workflow is assigned to a Worker. See Assignment Callback URL for more information. | getAssignmentCallbackUrl(): ?string | setAssignmentCallbackUrl(?string assignmentCallbackUrl): void |
| `configuration` | `?string` | Optional | A JSON string that contains the Workflow's configuration. See [Configuring Workflows](https://www.twilio.com/docs/taskrouter/workflow-configuration) for more information. | getConfiguration(): ?string | setConfiguration(?string configuration): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `documentContentType` | `?string` | Optional | The MIME type of the document. | getDocumentContentType(): ?string | setDocumentContentType(?string documentContentType): void |
| `fallbackAssignmentCallbackUrl` | `?string` | Optional | The URL that we call when a call to the `assignment_callback_url` fails. | getFallbackAssignmentCallbackUrl(): ?string | setFallbackAssignmentCallbackUrl(?string fallbackAssignmentCallbackUrl): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the Workflow resource. For example, `Customer Support` or `2014 Election Campaign`. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Workflow resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `taskReservationTimeout` | `?int` | Optional | How long TaskRouter will wait for a confirmation response from your application after it assigns a Task to a Worker. Can be up to `86,400` (24 hours) and the default is `120`.<br><br>**Default**: `0` | getTaskReservationTimeout(): ?int | setTaskReservationTimeout(?int taskReservationTimeout): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Workflow.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Workflow resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "task_reservation_timeout": 0,
  "account_sid": "account_sid8",
  "assignment_callback_url": "assignment_callback_url0",
  "configuration": "configuration4",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

