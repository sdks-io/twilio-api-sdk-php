
# Getting Started with Twilio APIs

## Introduction

This is the public Twilio REST API.

## Install the Package

Run the following command to install the package and automatically add the dependency to your composer.json file:

```bash
composer require "twilio-apimatic/twilio-api-sdk:1.0.1"
```

Or add it to the composer.json file manually as given below:

```json
"require": {
    "twilio-apimatic/twilio-api-sdk": "1.0.1"
}
```

You can also view the package at:
https://packagist.org/packages/twilio-apimatic/twilio-api-sdk#1.0.1

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| basicAuthCredentials | [`BasicAuthCredentials`](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

```php
use TwilioApIsLib\Logging\LoggingConfigurationBuilder;
use TwilioApIsLib\Logging\RequestLoggingConfigurationBuilder;
use TwilioApIsLib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use TwilioApIsLib\Environment;
use TwilioApIsLib\Authentication\BasicAuthCredentialsBuilder;
use TwilioApIsLib\TwilioApIsClientBuilder;

$client = TwilioApIsClientBuilder::init()
    ->basicAuthCredentials(
        BasicAuthCredentialsBuilder::init(
            'BasicAuthUserName',
            'BasicAuthPassword'
        )
    )
    ->environment(Environment::PRODUCTION)
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** |

## Authorization

This API uses the following authentication schemes.

* [`accountSid_authToken (Basic Authentication)`](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/auth/basic-authentication.md)

## List of APIs

* [Accounts V1 Auth Token Promotion](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-auth-token-promotion.md)
* [Accounts V1 Aws](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-aws.md)
* [Accounts V1 Bulk Consents](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-bulk-consents.md)
* [Accounts V1 Bulk Contacts](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-bulk-contacts.md)
* [Accounts V1 Messaging Geopermissions](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-messaging-geopermissions.md)
* [Accounts V1 Public Key](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-public-key.md)
* [Accounts V1 Safelist](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-safelist.md)
* [Accounts V1 Secondary Auth Token](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/accounts-v1-secondary-auth-token.md)
* [Chat V3 Channel](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/chat-v3-channel.md)
* [Conversations V1 Address Configuration](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-address-configuration.md)
* [Conversations V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-binding.md)
* [Conversations V1 Configuration](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-configuration.md)
* [Conversations V1 Conversation](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-conversation.md)
* [Conversations V1 Conversation with Participants](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-conversation-with-participants.md)
* [Conversations V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-credential.md)
* [Conversations V1 Delivery Receipt](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-delivery-receipt.md)
* [Conversations V1 Message](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-message.md)
* [Conversations V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-notification.md)
* [Conversations V1 Participant](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-participant.md)
* [Conversations V1 Participant Conversation](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-participant-conversation.md)
* [Conversations V1 Role](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-role.md)
* [Conversations V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-service.md)
* [Conversations V1 User](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-user.md)
* [Conversations V1 User Conversation](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-user-conversation.md)
* [Conversations V1 Webhook](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/conversations-v1-webhook.md)
* [Notify V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/notify-v1-binding.md)
* [Notify V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/notify-v1-credential.md)
* [Notify V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/notify-v1-notification.md)
* [Notify V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/notify-v1-service.md)
* [Taskrouter V1 Activity](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-activity.md)
* [Taskrouter V1 Event](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-event.md)
* [Taskrouter V1 Task](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task.md)
* [Taskrouter V1 Task Channel](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-channel.md)
* [Taskrouter V1 Task Queue](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queue.md)
* [Taskrouter V1 Task Queue Bulk Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queue-bulk-real-time-statistics.md)
* [Taskrouter V1 Task Queue Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queue-cumulative-statistics.md)
* [Taskrouter V1 Task Queue Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queue-real-time-statistics.md)
* [Taskrouter V1 Task Queue Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queue-statistics.md)
* [Taskrouter V1 Task Queues Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-queues-statistics.md)
* [Taskrouter V1 Task Reservation](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-task-reservation.md)
* [Taskrouter V1 Worker](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-worker.md)
* [Taskrouter V1 Worker Channel](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-worker-channel.md)
* [Taskrouter V1 Worker Reservation](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-worker-reservation.md)
* [Taskrouter V1 Worker Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-worker-statistics.md)
* [Taskrouter V1 Workers Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workers-cumulative-statistics.md)
* [Taskrouter V1 Workers Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workers-real-time-statistics.md)
* [Taskrouter V1 Workers Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workers-statistics.md)
* [Taskrouter V1 Workflow](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workflow.md)
* [Taskrouter V1 Workflow Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workflow-cumulative-statistics.md)
* [Taskrouter V1 Workflow Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workflow-real-time-statistics.md)
* [Taskrouter V1 Workflow Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workflow-statistics.md)
* [Taskrouter V1 Workspace](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workspace.md)
* [Taskrouter V1 Workspace Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workspace-cumulative-statistics.md)
* [Taskrouter V1 Workspace Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workspace-real-time-statistics.md)
* [Taskrouter V1 Workspace Statistics](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/taskrouter-v1-workspace-statistics.md)
* [Verify V2 Service](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/verify-v2-service.md)
* [Verify V2 Verification](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/verify-v2-verification.md)
* [Verify V2 Verification Check](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/verify-v2-verification-check.md)
* [SMS](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/controllers/sms.md)

## SDK Infrastructure

### Configuration

* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/proxy-configuration-builder.md)
* [LoggingConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/logging-configuration-builder.md)
* [RequestLoggingConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/request-logging-configuration-builder.md)
* [ResponseLoggingConfigurationBuilder](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/response-logging-configuration-builder.md)

### HTTP

* [HttpRequest](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/http-request.md)

### Utilities

* [ApiResponse](https://www.github.com/sdks-io/twilio-api-sdk-php/tree/1.0.1/doc/api-response.md)

