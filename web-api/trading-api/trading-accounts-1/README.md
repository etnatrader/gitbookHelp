# Account Transfer

The Account Transfer API provides functionalities for users to initiate and manage account transfer requests within the ETNA trade platform.&#x20;

The API offers methods to create, submit, cancel, and retrieve pending account transfer requests.

### Basic Workflow for Account Transfer:

1. Create Transfer Request
   * The user initiates the account transfer process by creating a transfer request using the **Create Account Transfer Request** endpoint.
2. Submit Transfer Request
   * After creating the transfer request, the user submits it using the **Submit Account Transfer Request** endpoint.
   * In this request, the user provides the necessary information for the transfer.
   * The submitted transfer request is then sent to the broker for processing.
3. Broker Processing
   * The broker receives the submitted transfer request and starts processing it.
4. Check Status of Pending Requests
   * While the broker is processing the transfer request, the user can use the **Get User's Pending Account Transfer Requests** endpoint to check the status of their pending requests.
5. Cancel Pending Requests (Optional)
   * If the user wishes to cancel a pending transfer request for any reason, they can use the **Cancel Account Transfer Request** endpoint.
   * This allows the user to manage their transfer requests and make necessary adjustments if needed.

The Account Transfer API provides users with a seamless and efficient process for initiating and managing account transfers. Users can create, submit, and monitor their transfer requests, while also having the option to cancel pending requests if necessary. This streamlines the transfer process and ensures a smooth experience for investors when transferring assets between brokerage firms.
