# Verify V2 Verification

```php
$verifyV2VerificationApi = $client->getVerifyV2VerificationApi();
```

## Class Name

`VerifyV2VerificationApi`


# Create Verification

Create a new Verification using a Service

```php
function createVerification(
    string $serviceSid,
    string $to,
    string $channel,
    ?string $customFriendlyName = null,
    ?string $customMessage = null,
    ?string $sendDigits = null,
    ?string $locale = null,
    ?string $customCode = null,
    ?string $amount = null,
    ?string $payee = null,
    ?array $rateLimits = null,
    ?array $channelConfiguration = null,
    ?string $appHash = null,
    ?string $templateSid = null,
    ?string $templateCustomSubstitutions = null,
    ?string $deviceIp = null,
    ?bool $enableSnaClientToken = null,
    ?string $riskCheck = null,
    ?string $tags = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the verification [Service](https://www.twilio.com/docs/verify/api/service) to create the resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `to` | `string` | Form, Required | The phone number or [email](https://www.twilio.com/docs/verify/email) to verify. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |
| `channel` | `string` | Form, Required | The verification method to use. One of: [`email`](https://www.twilio.com/docs/verify/email), `sms`, `whatsapp`, `call`, `sna` or `auto`. |
| `customFriendlyName` | `?string` | Form, Optional | A custom user defined friendly name that overwrites the existing one in the verification message |
| `customMessage` | `?string` | Form, Optional | The text of a custom message to use for the verification. |
| `sendDigits` | `?string` | Form, Optional | The digits to send after a phone call is answered, for example, to dial an extension. For more information, see the Programmable Voice documentation of [sendDigits](https://www.twilio.com/docs/voice/twiml/number#attributes-sendDigits). |
| `locale` | `?string` | Form, Optional | Locale will automatically resolve based on phone number country code for SMS, WhatsApp, and call channel verifications. It will fallback to English or the template’s default translation if the selected translation is not available. This parameter will override the automatic locale resolution. [See supported languages and more information here](https://www.twilio.com/docs/verify/supported-languages). |
| `customCode` | `?string` | Form, Optional | A pre-generated code to use for verification. The code can be between 4 and 10 characters, inclusive. |
| `amount` | `?string` | Form, Optional | The amount of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `payee` | `?string` | Form, Optional | The payee of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `rateLimits` | `?array` | Form, Optional | The custom key-value pairs of Programmable Rate Limits. Keys correspond to `unique_name` fields defined when [creating your Rate Limit](https://www.twilio.com/docs/verify/api/service-rate-limits). Associated value pairs represent values in the request that you are rate limiting on. You may include multiple Rate Limit values in each request. |
| `channelConfiguration` | `?array` | Form, Optional | [`email`](https://www.twilio.com/docs/verify/email) channel configuration in json format. The fields 'from' and 'from_name' are optional but if included the 'from' field must have a valid email address. |
| `appHash` | `?string` | Form, Optional | Your [App Hash](https://developers.google.com/identity/sms-retriever/verify#computing_your_apps_hash_string) to be appended at the end of your verification SMS body. Applies only to SMS. Example SMS body: `<#> Your AppName verification code is: 1234 He42w354ol9`. |
| `templateSid` | `?string` | Form, Optional | The message [template](https://www.twilio.com/docs/verify/api/templates). If provided, will override the default template for the Service. SMS and Voice channels only.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` |
| `templateCustomSubstitutions` | `?string` | Form, Optional | A stringified JSON object in which the keys are the template's special variables and the values are the variables substitutions. |
| `deviceIp` | `?string` | Form, Optional | Strongly encouraged if using the auto channel. The IP address of the client's device. If provided, it has to be a valid IPv4 or IPv6 address. |
| `enableSnaClientToken` | `?bool` | Form, Optional | An optional Boolean value to indicate the requirement of sna client token in the SNA URL invocation response for added security. This token must match in the Verification Check request to confirm phone number verification. |
| `riskCheck` | [`?string(VerificationEnumRiskCheck)`](../../doc/models/verification-enum-risk-check.md) | Form, Optional | Risk_check overrides Fraud Prevention measures like Fraud Guard, Geo Permissions etc per verification attempt basis, allowing Verify to block traffic considered fraudulent if enabled or bypass active protections if disabled. Can be: `enable`(default) or `disable`. For SMS channel only. |
| `tags` | `?string` | Form, Optional | A string containing a JSON map of key value pairs of tags to be recorded as metadata for the message. The object may contain up to 10 tags. Keys and values can each be up to 128 characters in length. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Verification`](../../doc/models/verification.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$to = '+15017122661';

$channel = 'sms';

$customFriendlyName = 'custom_friendly_name';

$customMessage = 'custom_message';

$sendDigits = 'ww1';

$locale = 'en';

$customCode = 'custom_code';

$amount = '€39.99';

$payee = 'Acme Inc.';

$rateLimits = ApiHelper::deserialize('{"my_rate_limit_key":"abc"}');

$channelConfiguration = ApiHelper::deserialize('{"from":"foo@bar.com","from_name":"Bar Inc.","substitutions":{"username":"ms. baz"},"template_id":"Dxxxxxxxxxx"}');

$appHash = 'AAAAAAAAAAA';

$templateSid = 'HJaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$templateCustomSubstitutions = '{"AppName": "MyApp", "Contact":"12345689"}';

$deviceIp = '0.000.00.000';

$riskCheck = VerificationEnumRiskCheck::ENABLE;

$tags = '{"tenant_id": "12345"}';

$verifyV2VerificationApi = $client->getVerifyV2VerificationApi();
$apiResponse = $verifyV2VerificationApi->createVerification(
    $serviceSid,
    $to,
    $channel,
    $customFriendlyName,
    $customMessage,
    $sendDigits,
    $locale,
    $customCode,
    $amount,
    $payee,
    $rateLimits,
    $channelConfiguration,
    $appHash,
    $templateSid,
    $templateCustomSubstitutions,
    $deviceIp,
    null,
    $riskCheck,
    $tags
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Verification:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 429 | Too Many Requests | [`V2ServicesVerifications429ErrorException`](../../doc/models/v2-services-verifications-429-error-exception.md) |

