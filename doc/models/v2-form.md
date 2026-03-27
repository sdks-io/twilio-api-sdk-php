
# V2 Form

*This model accepts additional fields of type array.*

## Structure

`V2Form`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `formType` | [`?string(FormEnumFormTypes)`](../../doc/models/form-enum-form-types.md) | Optional | The Type of this Form. Currently only `form-push` is supported. | getFormType(): ?string | setFormType(?string formType): void |
| `forms` | `?array` | Optional | Object that contains the available forms for this type. This available forms are given in the standard [JSON Schema](https://json-schema.org/) format | getForms(): ?array | setForms(?array forms): void |
| `formMeta` | `?array` | Optional | Additional information for the available forms for this type. E.g. The separator string used for `binding` in a Factor push. | getFormMeta(): ?array | setFormMeta(?array formMeta): void |
| `url` | `?string` | Optional | The URL to access the forms for this type. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "form_type": "form-push",
  "forms": {
    "key1": "val1",
    "key2": "val2"
  },
  "form_meta": {
    "key1": "val1",
    "key2": "val2"
  },
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

