# Http Response Codes

The OptaCut API uses the following error codes:

| Response Code | Meaning                                                                                   |
|---------------|-------------------------------------------------------------------------------------------|
| 200           | The request was successful.                                                               |
| 201           | A new resource has been successfully created.                                             |
| 204           | The request was successful, but there is no content to return.                            |
| 400           | Bad Request -- Your request is invalid.                                                   |
| 401           | Unauthorized -- Your API/Token key is invalid.                                            |
| 403           | Forbidden -- The data requested is not available for your privilege.                      |
| 404           | Not Found -- The specified data could not be found.                                       |
| 405           | Method Not Allowed -- You tried to access a api with an invalid method.                   |
| 409           | Conflict -- There is constraint violation                                                 |
| 429           | Too Many Requests -- You're requesting too many kittens! Slow down!                       |
| 500           | Internal Server Error -- We had a problem with our server. Try again later.               |
| 503           | Service Unavailable -- We're temporarily offline for maintenance. Please try again later. |
