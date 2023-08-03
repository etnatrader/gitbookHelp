---
description: >-
  The Paperless Settings API provides users with a comprehensive set of methods
  to manage electronic document notifications.
---

# Paperless Settings

In this section, we'll cover how to enable users to subscribe or unsubscribe to electronic document notifications seamlessly.&#x20;

Here's the suggested sequence of steps to get started:

1. **Authentication**: Begin by authenticating through an OAuth 2.0 server and acquire an authentication token. Include this token in the headers of subsequent API requests to ensure secure access.
2. **Checking Paperless Settings**: When checking the paperless settings, you can use the **Get Paperless Settings By Account Id** API endpoint to verify if any settings have been established for the specified account. If no settings are returned - create default settings. Once the default settings are in place, you can further customize them as needed.
3. **Create Default Paperless Settings**: Use the **Create Default Paperless Settings** endpoint to create default paperless settings for a specific account. Please note that when using this endpoint to create paperless settings, any existing settings for the specified account will be overridden.
4. **Update Settings**: If you need to modify any settings, utilize the **Update Paperless Settings By Account Id** endpoint. This allows you to update the paperless settings for the account.
