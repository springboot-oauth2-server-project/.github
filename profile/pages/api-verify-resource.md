[Back](https://github.com/springboot-oauth2-server-project/)

## Verify Resource API
### CURL
  ```bash
  curl --location --request POST 'http://localhost:8991/v1/oauth/verify/resource/client' \
--header 'x-oauth-token: YDR2u5ouxw0ne0c2nz8Spl3VZ3adJGpCbHpz' \
--data-raw '{
    "clientId": "fstTysjNpkNtNGsLuSGVhvfmZEARogUaQEpG",
    "clientSecreet": "lYFwVWQNSeWv120BgafwKEQwGLWBDewCdeVC" ,
    "resourceId":"IdnKmJWVHZqhkWaeFzSvBezUHEdSzhGFwaDj",
    "username": "client"
}'
  ```
  ```bash
  {
    "status": "200 OK",
    "headers": "",
    "body": {
        "code": "200-100-1",
        "message": "Verify resource & client success",
        "data": {
            "key": "x-oauth-verified-resource-token",
            "value": "oFAcFmWl1Zrn9EBen3LQsBYHQpqbVxblGQi4"
        }        
    }
}
  ```
### Message & Validation
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-100-1 | Verify resource & client success |
| 403 FORBIDDEN | 403-100-1 | x-oauth-token cannot be null or empty |
| 403 FORBIDDEN | 403-100-2 | Field clientId cannot be null or empty, Field clientSecreet cannot be null or empty, Field resourceId cannot be null or empty, Field username cannot be null or empty |
| 403 FORBIDDEN | 403-100-3 | x-oauth-token is not valid! |
| 403 FORBIDDEN | 403-100-4 | ClientId is not found on OAUTH Server |
| 403 FORBIDDEN | 403-100-5 | ClientId {clientName} has been expired! |
| 403 FORBIDDEN | 403-100-6 | Client {clientName} has been non active! |
| 403 FORBIDDEN | 403-100-7 | ClientSecreet is wrong! |
| 403 FORBIDDEN | 403-100-8 | ResourceId is not found on OAUTH Server! |
| 403 FORBIDDEN | 403-100-9 | Client {clientName} is not allowed to access this resource : {resource name} |
| 403 FORBIDDEN | 403-100-10 | User {username} is not found on OAUTH server! |
| 403 FORBIDDEN | 403-100-11 | User {username} is not allowed to accessing this resource : {resourceName} |
| 403 FORBIDDEN | 403-100-12 | You have request access still not finished the OAUTH flow, please finish this OAUTH Flow (VERIFY_RESOURCE -> VERIFY_USER) |
| 403 FORBIDDEN | 403-100-13 | ClientId & verifiyResourceToken is already exist |
