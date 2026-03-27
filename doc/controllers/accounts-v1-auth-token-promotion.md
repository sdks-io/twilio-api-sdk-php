# Accounts V1 Auth Token Promotion

```php
$accountsV1AuthTokenPromotionApi = $client->getAccountsV1AuthTokenPromotionApi();
```

## Class Name

`AccountsV1AuthTokenPromotionApi`


# Update Auth Token Promotion

Promote the secondary Auth Token to primary. After promoting the new token, all requests to Twilio using your old primary Auth Token will result in an error.

```php
function updateAuthTokenPromotion(): ApiResponse
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AuthTokenPromotion`](../../doc/models/auth-token-promotion.md).

## Example Usage

```php
$accountsV1AuthTokenPromotionApi = $client->getAccountsV1AuthTokenPromotionApi();
$apiResponse = $accountsV1AuthTokenPromotionApi->updateAuthTokenPromotion();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AuthTokenPromotion:';
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
  "auth_token": "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "url": "https://accounts.twilio.com/v1/AuthTokens/Promote"
}
```

