
# V2 Services Verifications 429 Error Exception

*This model accepts additional fields of type array.*

## Structure

`V2ServicesVerifications429ErrorException`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `code` | `?int` | Optional | Twilio-specific error code | getCode(): ?int | setCode(?int code): void |
| `message` | `?string` | Optional | Error message | getMessage(): ?string | setMessage(?string message): void |
| `moreInfo` | `?string` | Optional | Link to Error Code References | getMoreInfo(): ?string | setMoreInfo(?string moreInfo): void |
| `status` | `?int` | Optional | HTTP response status code | getStatus(): ?int | setStatus(?int status): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "code": 0,
  "message": "message0",
  "more_info": "more_info2",
  "status": 178,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

