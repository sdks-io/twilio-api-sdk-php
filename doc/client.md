
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](../doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](../doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| basicAuthCredentials | [`BasicAuthCredentials`](auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

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

## Twilio APIs Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| getAccountsV1AuthTokenPromotionApi() | Gets AccountsV1AuthTokenPromotionApi |
| getAccountsV1AwsApi() | Gets AccountsV1AwsApi |
| getAccountsV1BulkConsentsApi() | Gets AccountsV1BulkConsentsApi |
| getAccountsV1BulkContactsApi() | Gets AccountsV1BulkContactsApi |
| getAccountsV1MessagingGeopermissionsApi() | Gets AccountsV1MessagingGeopermissionsApi |
| getAccountsV1PublicKeyApi() | Gets AccountsV1PublicKeyApi |
| getAccountsV1SafelistApi() | Gets AccountsV1SafelistApi |
| getAccountsV1SecondaryAuthTokenApi() | Gets AccountsV1SecondaryAuthTokenApi |
| getChatV3ChannelApi() | Gets ChatV3ChannelApi |
| getConversationsV1AddressConfigurationApi() | Gets ConversationsV1AddressConfigurationApi |
| getConversationsV1BindingApi() | Gets ConversationsV1BindingApi |
| getConversationsV1ConfigurationApi() | Gets ConversationsV1ConfigurationApi |
| getConversationsV1ConversationApi() | Gets ConversationsV1ConversationApi |
| getConversationsV1ConversationWithParticipantsApi() | Gets ConversationsV1ConversationWithParticipantsApi |
| getConversationsV1CredentialApi() | Gets ConversationsV1CredentialApi |
| getConversationsV1DeliveryReceiptApi() | Gets ConversationsV1DeliveryReceiptApi |
| getConversationsV1MessageApi() | Gets ConversationsV1MessageApi |
| getConversationsV1NotificationApi() | Gets ConversationsV1NotificationApi |
| getConversationsV1ParticipantApi() | Gets ConversationsV1ParticipantApi |
| getConversationsV1ParticipantConversationApi() | Gets ConversationsV1ParticipantConversationApi |
| getConversationsV1RoleApi() | Gets ConversationsV1RoleApi |
| getConversationsV1ServiceApi() | Gets ConversationsV1ServiceApi |
| getConversationsV1UserApi() | Gets ConversationsV1UserApi |
| getConversationsV1UserConversationApi() | Gets ConversationsV1UserConversationApi |
| getConversationsV1WebhookApi() | Gets ConversationsV1WebhookApi |
| getNotifyV1BindingApi() | Gets NotifyV1BindingApi |
| getNotifyV1CredentialApi() | Gets NotifyV1CredentialApi |
| getNotifyV1NotificationApi() | Gets NotifyV1NotificationApi |
| getNotifyV1ServiceApi() | Gets NotifyV1ServiceApi |
| getTaskrouterV1ActivityApi() | Gets TaskrouterV1ActivityApi |
| getTaskrouterV1EventApi() | Gets TaskrouterV1EventApi |
| getTaskrouterV1TaskApi() | Gets TaskrouterV1TaskApi |
| getTaskrouterV1TaskChannelApi() | Gets TaskrouterV1TaskChannelApi |
| getTaskrouterV1TaskQueueApi() | Gets TaskrouterV1TaskQueueApi |
| getTaskrouterV1TaskQueueBulkRealTimeStatisticsApi() | Gets TaskrouterV1TaskQueueBulkRealTimeStatisticsApi |
| getTaskrouterV1TaskQueueCumulativeStatisticsApi() | Gets TaskrouterV1TaskQueueCumulativeStatisticsApi |
| getTaskrouterV1TaskQueueRealTimeStatisticsApi() | Gets TaskrouterV1TaskQueueRealTimeStatisticsApi |
| getTaskrouterV1TaskQueueStatisticsApi() | Gets TaskrouterV1TaskQueueStatisticsApi |
| getTaskrouterV1TaskQueuesStatisticsApi() | Gets TaskrouterV1TaskQueuesStatisticsApi |
| getTaskrouterV1TaskReservationApi() | Gets TaskrouterV1TaskReservationApi |
| getTaskrouterV1WorkerApi() | Gets TaskrouterV1WorkerApi |
| getTaskrouterV1WorkerChannelApi() | Gets TaskrouterV1WorkerChannelApi |
| getTaskrouterV1WorkerReservationApi() | Gets TaskrouterV1WorkerReservationApi |
| getTaskrouterV1WorkerStatisticsApi() | Gets TaskrouterV1WorkerStatisticsApi |
| getTaskrouterV1WorkersCumulativeStatisticsApi() | Gets TaskrouterV1WorkersCumulativeStatisticsApi |
| getTaskrouterV1WorkersRealTimeStatisticsApi() | Gets TaskrouterV1WorkersRealTimeStatisticsApi |
| getTaskrouterV1WorkersStatisticsApi() | Gets TaskrouterV1WorkersStatisticsApi |
| getTaskrouterV1WorkflowApi() | Gets TaskrouterV1WorkflowApi |
| getTaskrouterV1WorkflowCumulativeStatisticsApi() | Gets TaskrouterV1WorkflowCumulativeStatisticsApi |
| getTaskrouterV1WorkflowRealTimeStatisticsApi() | Gets TaskrouterV1WorkflowRealTimeStatisticsApi |
| getTaskrouterV1WorkflowStatisticsApi() | Gets TaskrouterV1WorkflowStatisticsApi |
| getTaskrouterV1WorkspaceApi() | Gets TaskrouterV1WorkspaceApi |
| getTaskrouterV1WorkspaceCumulativeStatisticsApi() | Gets TaskrouterV1WorkspaceCumulativeStatisticsApi |
| getTaskrouterV1WorkspaceRealTimeStatisticsApi() | Gets TaskrouterV1WorkspaceRealTimeStatisticsApi |
| getTaskrouterV1WorkspaceStatisticsApi() | Gets TaskrouterV1WorkspaceStatisticsApi |
| getVerifyV2ServiceApi() | Gets VerifyV2ServiceApi |
| getVerifyV2VerificationApi() | Gets VerifyV2VerificationApi |
| getVerifyV2VerificationCheckApi() | Gets VerifyV2VerificationCheckApi |

