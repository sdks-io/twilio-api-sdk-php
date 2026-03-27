# Accounts V1 Bulk Contacts

```php
$accountsV1BulkContactsApi = $client->getAccountsV1BulkContactsApi();
```

## Class Name

`AccountsV1BulkContactsApi`


# Create Bulk Contacts

```php
function createBulkContacts(array $items): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `items` | `array[]` | Form, Required | A list of objects where each object represents a contact's details. Each object includes the following fields: `contact_id`, which must be a string representing phone number in [E.164 format](https://www.twilio.com/docs/glossary/what-e164); `correlation_id`, a unique 32-character UUID that maps the response to the original request; `country_iso_code`, a string representing the country using the ISO format (e.g., US for the United States); and `zip_code`, a string representing the postal code. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`BulkContacts`](../../doc/models/bulk-contacts.md).

## Example Usage

```php
$items = [
    ApiHelper::deserialize('"{\\"contact_id\\":\\"+19999999999\\",\\"correlation_id\\":\\"ad388b5a46b33b874b0d41f7226db2eh\\",\\"country_iso_code\\":\\"US\\",\\"zip_code\\":\\"12345\\"}"'),
    ApiHelper::deserialize('"{\\"contact_id\\":\\"+19\\",\\"correlation_id\\":\\"02520cfa6c432f0e3ec3a38c122d428a\\",\\"country_iso_code\\":\\"US\\",\\"zip_code\\":\\"12345\\"}"')
];

$accountsV1BulkContactsApi = $client->getAccountsV1BulkContactsApi();
$apiResponse = $accountsV1BulkContactsApi->createBulkContacts($items);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'BulkContacts:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

