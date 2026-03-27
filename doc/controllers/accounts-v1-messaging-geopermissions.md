# Accounts V1 Messaging Geopermissions

```php
$accountsV1MessagingGeopermissionsApi = $client->getAccountsV1MessagingGeopermissionsApi();
```

## Class Name

`AccountsV1MessagingGeopermissionsApi`

## Methods

* [Update Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#update-messaging-geopermissions)
* [Fetch Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#fetch-messaging-geopermissions)


# Update Messaging Geopermissions

Manage Geo Permissions for each country.

```php
function updateMessagingGeopermissions(array $permissions): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `permissions` | `array[]` | Form, Required | A list of objects where each object represents the Geo Permission to be updated. Each object contains the following fields: `country_code`, unique code for each country of Geo Permission; `type`, permission type of the Geo Permission i.e. country; `enabled`, configure true for enabling the Geo Permission, false for disabling the Geo Permission. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`MsgGeopermissions`](../../doc/models/msg-geopermissions.md).

## Example Usage

```php
$permissions = [
    ApiHelper::deserialize('"{\\"country_code\\": \\"IN\\",\\"type\\": \\"country\\", \\"enabled\\": false}"'),
    ApiHelper::deserialize('"{\\"country_code\\": \\"PK\\",\\"type\\": \\"country\\", \\"enabled\\": true}"')
];

$accountsV1MessagingGeopermissionsApi = $client->getAccountsV1MessagingGeopermissionsApi();
$apiResponse = $accountsV1MessagingGeopermissionsApi->updateMessagingGeopermissions($permissions);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'MsgGeopermissions:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Fetch Messaging Geopermissions

Manage Geo Permissions for each country.

```php
function fetchMessagingGeopermissions(?string $countryCode = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `countryCode` | `?string` | Query, Optional | The country code to filter the geo permissions. If provided, only the geo permission for the specified country will be returned. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`MsgGeopermissions`](../../doc/models/msg-geopermissions.md).

## Example Usage

```php
$countryCode = 'IN,PK,US';

$accountsV1MessagingGeopermissionsApi = $client->getAccountsV1MessagingGeopermissionsApi();
$apiResponse = $accountsV1MessagingGeopermissionsApi->fetchMessagingGeopermissions($countryCode);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'MsgGeopermissions:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

