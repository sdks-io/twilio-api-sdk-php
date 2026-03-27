# Accounts V1 Secondary Auth Token

```php
$accountsV1SecondaryAuthTokenApi = $client->getAccountsV1SecondaryAuthTokenApi();
```

## Class Name

`AccountsV1SecondaryAuthTokenApi`

## Methods

* [Create Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#create-secondary-auth-token)
* [Delete Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#delete-secondary-auth-token)


# Create Secondary Auth Token

Create a new secondary Auth Token

```php
function createSecondaryAuthToken(): ApiResponse
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`SecondaryAuthToken`](../../doc/models/secondary-auth-token.md).

## Example Usage

```php
$accountsV1SecondaryAuthTokenApi = $client->getAccountsV1SecondaryAuthTokenApi();
$apiResponse = $accountsV1SecondaryAuthTokenApi->createSecondaryAuthToken();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'SecondaryAuthToken:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "secondary_auth_token": "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb",
  "url": "https://accounts.twilio.com/v1/AuthTokens/Secondary"
}
```


# Delete Secondary Auth Token

Delete the secondary Auth Token from your account

```php
function deleteSecondaryAuthToken(): ApiResponse
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$accountsV1SecondaryAuthTokenApi = $client->getAccountsV1SecondaryAuthTokenApi();
$apiResponse = $accountsV1SecondaryAuthTokenApi->deleteSecondaryAuthToken();

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

