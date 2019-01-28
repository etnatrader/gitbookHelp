# User-Creation-Triggered Actions

## User-Creation-Triggered Actions

In ETNA Trader, after a user is created, the service automatically triggers a multitude of actions to ensure that the newly created user is properly configured. These actions are defined in a special configuration file that is stored internally in ETNA Trader. Although you have no access to this file and therefore cannot modify any of these actions, you do have the opportunity to contact our support team and request that our developers implement different actions or have certain actions removed from the list.

The following table outlines of all these actions:

| Action | Description |
| :--- | :--- |
| AddNewUserToGroup | This action adds the user to the company's default group |
| EmitWebhookEventOnUserCreation | This action invokes a corresponding [webhook](../bo-companies/10.-webhooks.md) |
| CopyWatchListsFromUser | This action copies watchlists from the company's default user to the newly created user |
| SetDefaultNotificationSettingsToNewUser | This action adds the new user's notification settings to the service's database |
| AddUserHotKeysHandler | This action copies shortcuts from the company's default user to the newly created user |
| EnsureLayoutExistHandler | This action copies the web terminal layout from the company's default user to the newly created user |
| CreateAccountForNewUser | This action creates a clearing account for the new user in case they don't have one |
| DeleteForbiddenWidgetsFromDefaultLayout | This action removes the widgets that the user has no rights for |
| UnsubscribeFromForbiddenNotifications | This action unsubscribes the user from the notifications they're forbidden from receiving |

