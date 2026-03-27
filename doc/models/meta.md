
# Meta

*This model accepts additional fields of type array.*

## Structure

`Meta`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `firstPageUrl` | `?string` | Optional | - | getFirstPageUrl(): ?string | setFirstPageUrl(?string firstPageUrl): void |
| `key` | `?string` | Optional | - | getKey(): ?string | setKey(?string key): void |
| `nextPageUrl` | `?string` | Optional | - | getNextPageUrl(): ?string | setNextPageUrl(?string nextPageUrl): void |
| `page` | `?int` | Optional | - | getPage(): ?int | setPage(?int page): void |
| `pageSize` | `?int` | Optional | - | getPageSize(): ?int | setPageSize(?int pageSize): void |
| `previousPageUrl` | `?string` | Optional | - | getPreviousPageUrl(): ?string | setPreviousPageUrl(?string previousPageUrl): void |
| `url` | `?string` | Optional | - | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "first_page_url": "first_page_url6",
  "key": "key8",
  "next_page_url": "next_page_url0",
  "page": 178,
  "page_size": 118,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

