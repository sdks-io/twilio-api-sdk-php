# Verify V2 Verification Check

```php
$verifyV2VerificationCheckApi = $client->getVerifyV2VerificationCheckApi();
```

## Class Name

`VerifyV2VerificationCheckApi`


# Create Verification Check

challenge a specific Verification Check.

```php
function createVerificationCheck(
    string $serviceSid,
    ?string $code = null,
    ?string $to = null,
    ?string $verificationSid = null,
    ?string $amount = null,
    ?string $payee = null,
    ?string $snaClientToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the verification [Service](https://www.twilio.com/docs/verify/api/service) to create the resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `code` | `?string` | Form, Optional | The 4-10 character string being verified. |
| `to` | `?string` | Form, Optional | The phone number or [email](https://www.twilio.com/docs/verify/email) to verify. Either this parameter or the `verification_sid` must be specified. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |
| `verificationSid` | `?string` | Form, Optional | A SID that uniquely identifies the Verification Check. Either this parameter or the `to` phone number/[email](https://www.twilio.com/docs/verify/email) must be specified.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VE[0-9a-fA-F]{32}$` |
| `amount` | `?string` | Form, Optional | The amount of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `payee` | `?string` | Form, Optional | The payee of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `snaClientToken` | `?string` | Form, Optional | A sna client token received in sna url invocation response needs to be passed in Verification Check request and should match to get successful response. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`VerificationCheck`](../../doc/models/verification-check.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$code = '1234';

$to = '+15017122661';

$verificationSid = 'VEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$amount = '€39.99';

$payee = 'Acme Inc.';

$verifyV2VerificationCheckApi = $client->getVerifyV2VerificationCheckApi();
$apiResponse = $verifyV2VerificationCheckApi->createVerificationCheck(
    $serviceSid,
    $code,
    $to,
    $verificationSid,
    $amount,
    $payee
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'VerificationCheck:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "VEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "service_sid": "VAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "to": "+15017122661",
  "channel": "sms",
  "status": "approved",
  "valid": true,
  "amount": null,
  "payee": null,
  "sna_attempts_error_codes": [],
  "date_created": "2015-07-30T20:00:00Z",
  "date_updated": "2015-07-30T20:00:00Z"
}
```

