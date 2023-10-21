[Back](https://github.com/springboot-oauth2-server-project/)

## Verify Token API
### CURL
- Request
```bash
curl --location 'http://localhost:8991/v1/oauth/verify/authorization' \
--header 'x-oauth-token: yyy.yyy.yyy' \
--data '{
    "authorization":"xxxx.xxxx.xxxx"
}'
```
- Response
```bash
{
    "status": "200 OK",
    "headers": "",
    "body": {
        "code": "200-150-1",
        "message": "Verify Authorization Token success",
        "data": {            
            "enabled": true,
            "username": "client",
            "authorities": [
                {
                    "authority": "ROLE_RESOURCE-CLIENT"
                }
            ],
            "accountNonExpired": true,
            "credentialsNonExpired": true,
            "accountNonLocked": true
        }        
    }
}
```
### Message & Validation
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-150-1 | verify Authorization Token success|
| 403 FORBIDDEN | 403-150-1 | x-oauth-token cannot be null or empty |
| 403 FORBIDDEN | 403-150-2 | Authorization Token cannot be null or empty |
| 403 FORBIDDEN | 403-150-3 | Authorization Token has been expired |
| 403 FORBIDDEN | 403-150-4 | Authorization Token has badformat |

