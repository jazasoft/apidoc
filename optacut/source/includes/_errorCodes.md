# Errors

The OptaCut API uses the following error codes:

| Error Code | Meaning                                                                                   |
|------------|-------------------------------------------------------------------------------------------|
| 400        | Bad Request -- Your request is invalid.                                                   |
| 401        | Unauthorized -- Your API/Token key is invalid.                                            |
| 403        | Forbidden -- The data requested is not available for your privilege.                      |
| 404        | Not Found -- The specified data could not be found.                                       |
| 405        | Method Not Allowed -- You tried to access a api with an invalid method.                   |
| 409        | Conflict -- There is constraint violation                                                 |
| 429        | Too Many Requests -- You're requesting too many kittens! Slow down!                       |
| 500        | Internal Server Error -- We had a problem with our server. Try again later.               |
| 503        | Service Unavailable -- We're temporarily offline for maintenance. Please try again later. |
