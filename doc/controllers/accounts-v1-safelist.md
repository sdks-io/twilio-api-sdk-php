# Accounts V1 Safelist

```php
$accountsV1SafelistApi = $client->getAccountsV1SafelistApi();
```

## Class Name

`AccountsV1SafelistApi`

## Methods

* [Create Safelist](../../doc/controllers/accounts-v1-safelist.md#create-safelist)
* [Fetch Safelist](../../doc/controllers/accounts-v1-safelist.md#fetch-safelist)
* [Delete Safelist](../../doc/controllers/accounts-v1-safelist.md#delete-safelist)


# Create Safelist

Add a new phone number or phone number 1k prefix to SafeList.

```php
function createSafelist(string $phoneNumber): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `string` | Form, Required | The phone number or phone number 1k prefix to be added in SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Safelist`](../../doc/models/safelist.md).

## Example Usage

```php
$phoneNumber = '+18001234567';

$accountsV1SafelistApi = $client->getAccountsV1SafelistApi();
$apiResponse = $accountsV1SafelistApi->createSafelist($phoneNumber);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Safelist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "GNaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "phone_number": "+18001234567"
}
```


# Fetch Safelist

Check if a phone number or phone number 1k prefix exists in SafeList.

```php
function fetchSafelist(?string $phoneNumber = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `?string` | Query, Optional | The phone number or phone number 1k prefix to be fetched from SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Safelist`](../../doc/models/safelist.md).

## Example Usage

```php
$phoneNumber = '+18001234567';

$accountsV1SafelistApi = $client->getAccountsV1SafelistApi();
$apiResponse = $accountsV1SafelistApi->fetchSafelist($phoneNumber);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Safelist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "GNaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "phone_number": "+18001234567"
}
```


# Delete Safelist

Remove a phone number or phone number 1k prefix from SafeList.

```php
function deleteSafelist(?string $phoneNumber = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `phoneNumber` | `?string` | Query, Optional | The phone number or phone number 1k prefix to be removed from SafeList. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$phoneNumber = '+18001234567';

$accountsV1SafelistApi = $client->getAccountsV1SafelistApi();
$apiResponse = $accountsV1SafelistApi->deleteSafelist($phoneNumber);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

