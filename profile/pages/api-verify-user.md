[Back](https://github.com/springboot-oauth2-server-project/)

## Verify User API
### CURL
- Request
```bash
curl --location --request POST 'http://localhost:8991/v1/oauth/verify/user' \
--header 'x-oauth-verified-resource-token: vvv.vvv.vvv' \
--data-raw '{        
    "username": "client",
    "password": "admin"     
}'
```
- Response
```bash
{
    "status": "200 OK",
    "headers": "",
    "body": {
        "code": "200-150-1",
        "message": "Verify user success",
        "data": {
            "authorizationToken": {
                "key": "x-oauth-authorization-token",
                "value": "aaa.aaa.aaa"
            },
            "refreshToken": {
                "key": "x-oauth-refresh-token",
                "value": "rrr.rrr.rrr"
            },
            "username": "client"
        }        
    }
}
  ```
#### Message & Validation
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-150-1 | Verify user success |
| 403 FORBIDDEN | 403-150-1 | x-oauth-verified-resource-token cannot be null or empty |
| 403 FORBIDDEN | 403-150-2 | Field username cannot be null or empty, Field password cannot be null or empty |
| 403 FORBIDDEN | 403-150-3 | x_verify_resource_token is not found on OAUTH Server |
| 403 FORBIDDEN | 403-150-4 | You are not allowed to access this resource, cause your token status is {token status} |
| 403 FORBIDDEN | 403-150-5 | User {username} is not found on OAUTH server! |
| 403 FORBIDDEN | 403-150-6 | Login Failed! Cause wrong username & password! |
