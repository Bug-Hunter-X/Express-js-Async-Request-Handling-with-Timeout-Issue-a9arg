# Express.js Async Request Handling Bug

This repository demonstrates a common issue in Express.js applications where asynchronous request handling combined with timeouts can lead to unhandled promise rejections.  The bug occurs when a client abruptly closes the connection before the server has a chance to send a response after an asynchronous operation completes.  The solution involves checking the response's status before sending data to ensure the connection remains active.

## Bug
The `bug.js` file contains the buggy code.  It uses `setTimeout` to simulate an asynchronous operation (e.g., database query, external API call). If the client closes the connection before the timeout expires, the response will never be sent and an error will result.