
# Verification Attempts

*This model accepts additional fields of type array.*

## Structure

`VerificationAttempts`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `totalAttempts` | `?int` | Optional | Total of attempts made according to the provided filters<br><br>**Default**: `0` | getTotalAttempts(): ?int | setTotalAttempts(?int totalAttempts): void |
| `totalConverted` | `?int` | Optional | Total of  attempts made that were confirmed by the end user, according to the provided filters.<br><br>**Default**: `0` | getTotalConverted(): ?int | setTotalConverted(?int totalConverted): void |
| `totalUnconverted` | `?int` | Optional | Total of attempts made that were not confirmed by the end user, according to the provided filters.<br><br>**Default**: `0` | getTotalUnconverted(): ?int | setTotalUnconverted(?int totalUnconverted): void |
| `conversionRatePercentage` | `?string` | Optional | Percentage of the confirmed messages over the total, defined by (total_converted/total_attempts)*100. | getConversionRatePercentage(): ?string | setConversionRatePercentage(?string conversionRatePercentage): void |
| `url` | `?string` | Optional | - | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "total_attempts": 0,
  "total_converted": 0,
  "total_unconverted": 0,
  "conversion_rate_percentage": "conversion_rate_percentage2",
  "url": "url6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

