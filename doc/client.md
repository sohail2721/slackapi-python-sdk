
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| http_client_instance | `Union[Session, HttpClientProvider]` | The Http Client passed from the sdk user for making requests |
| override_http_client_configuration | `bool` | The value which determines to override properties of the passed Http Client from the sdk user |
| http_call_back | `HttpCallBack` | The callback value that is invoked before and after an HTTP call is made to an endpoint |
| timeout | `float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `int` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| backoff_factor | `float` | A backoff factor to apply between attempts after the second try. <br> **Default: 2** |
| retry_statuses | `Array of int` | The http statuses on which retry is to be done. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array of string` | The http methods on which retry is to be done. <br> **Default: ["GET", "PUT"]** |
| proxy_settings | [`ProxySettings`](../doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](../doc/logging-configuration.md) | The SDK logging configuration for API calls |
| authorization_code_auth_credentials | [`AuthorizationCodeAuthCredentials`](auth/oauth-2-authorization-code-grant.md) | The credential object for OAuth 2 Authorization Code Grant |

The API client can be initialized as follows:

## Code-Based Client Initialization

```python
import logging

from slackwebapi.configuration import Environment
from slackwebapi.http.auth.oauth_2 import AuthorizationCodeAuthCredentials
from slackwebapi.logging.configuration.api_logging_configuration import LoggingConfiguration
from slackwebapi.logging.configuration.api_logging_configuration import RequestLoggingConfiguration
from slackwebapi.logging.configuration.api_logging_configuration import ResponseLoggingConfiguration
from slackwebapi.models.oauth_scope import OauthScope
from slackwebapi.slackwebapi_client import SlackwebapiClient

client = SlackwebapiClient(
    authorization_code_auth_credentials=AuthorizationCodeAuthCredentials(
        oauth_client_id='OAuthClientId',
        oauth_client_secret='OAuthClientSecret',
        oauth_redirect_uri='OAuthRedirectUri',
        oauth_scopes=[
            OauthScope.ADMIN,
            OauthScope.ADMIN_APPSREAD
        ]
    ),
    environment=Environment.PRODUCTION,
    logging_configuration=LoggingConfiguration(
        log_level=logging.INFO,
        request_logging_config=RequestLoggingConfiguration(
            log_body=True
        ),
        response_logging_config=ResponseLoggingConfiguration(
            log_headers=True
        )
    )
)
```

## Environment-Based Client Initialization

```python
from slackwebapi.slackwebapi_client import SlackwebapiClient

# Specify the path to your .env file if it’s located outside the project’s root directory.
client = SlackwebapiClient.from_environment(dotenv_path='/path/to/.env')
```

See the [Environment-Based Client Initialization](../doc/environment-based-client-initialization.md) section for details.

## Slack Web API Client

The gateway for the SDK. This class acts as a factory for the Controllers and also holds the configuration of the SDK.

## Controllers

| Name | Description |
|  --- | --- |
| admin_apps | Gets AdminAppsController |
| admin_apps_approved | Gets AdminAppsApprovedController |
| admin_apps_requests | Gets AdminAppsRequestsController |
| admin_apps_restricted | Gets AdminAppsRestrictedController |
| admin_conversations | Gets AdminConversationsController |
| admin_conversations_ekm | Gets AdminConversationsEkmController |
| admin_conversations_restrict_access | Gets AdminConversationsRestrictAccessController |
| admin_emoji | Gets AdminEmojiController |
| admin_invite_requests | Gets AdminInviteRequestsController |
| admin_invite_requests_approved | Gets AdminInviteRequestsApprovedController |
| admin_invite_requests_denied | Gets AdminInviteRequestsDeniedController |
| admin_teams_admins | Gets AdminTeamsAdminsController |
| admin_teams | Gets AdminTeamsController |
| admin_teams_owners | Gets AdminTeamsOwnersController |
| admin_teams_settings | Gets AdminTeamsSettingsController |
| admin_usergroups | Gets AdminUsergroupsController |
| admin_users | Gets AdminUsersController |
| admin_users_session | Gets AdminUsersSessionController |
| api | Gets ApiController |
| apps_event_authorizations | Gets AppsEventAuthorizationsController |
| apps_permissions | Gets AppsPermissionsController |
| apps_permissions_resources | Gets AppsPermissionsResourcesController |
| apps_permissions_scopes | Gets AppsPermissionsScopesController |
| apps_permissions_users | Gets AppsPermissionsUsersController |
| apps | Gets AppsController |
| auth | Gets AuthController |
| bots | Gets BotsController |
| calls | Gets CallsController |
| calls_participants | Gets CallsParticipantsController |
| chat | Gets ChatController |
| chat_scheduled_messages | Gets ChatScheduledMessagesController |
| conversations | Gets ConversationsController |
| dialog | Gets DialogController |
| dnd | Gets DndController |
| emoji | Gets EmojiController |
| files_comments | Gets FilesCommentsController |
| files | Gets FilesController |
| files_remote | Gets FilesRemoteController |
| migration | Gets MigrationController |
| oauth | Gets OauthController |
| oauth_v_2 | Gets OauthV2Controller |
| pins | Gets PinsController |
| reactions | Gets ReactionsController |
| reminders | Gets RemindersController |
| rtm | Gets RtmController |
| search | Gets SearchController |
| stars | Gets StarsController |
| team | Gets TeamController |
| team_profile | Gets TeamProfileController |
| usergroups | Gets UsergroupsController |
| usergroups_users | Gets UsergroupsUsersController |
| users | Gets UsersController |
| users_profile | Gets UsersProfileController |
| views | Gets ViewsController |
| workflows | Gets WorkflowsController |
| oauth_authorization | Gets OauthAuthorizationController |

