## About
This project is an example of OAuth project. for allowing single user data, can login to 1 or many resource (application).
also this project can manage, resource, client and user.

## Features Plan
[Oauth2 Server Features](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/features.md/)

# Context 
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/9e73c681-364f-4d04-bbfb-25b73323cd82)

# Data
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/bb8ef2b4-1969-4096-a14a-9058948608d4)

# Container
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/b2a25b2f-ffe4-4f49-a71d-ba11c354b5d0)

# Sequence of Authentication & Authorization
[Sequence of Authentication & Authorization](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)

# Sequence of CRUD on OAuth App
- [Admin Register new User (Resource Owner)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sequence-register-user-resource-owner.md)
- [Admin Register new User (Client)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-admin-reg-new-user-client.md)
- [(Resource Owner) Register new Resource ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-reg-new-resource.md)
- [(Resource Owner) Register new Client ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-regitster-new-client.md)

# Screenshoot of OAuth App
- [Role : Admin](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-admin.md)
- [Role : Resource Owner](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-resourceowner.md)

# API : Verify Resource
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

# API : Verify User 
### CURL
  ```bash
curl --location --request POST 'http://localhost:8991/v1/oauth/verify/user' \
--header 'x-oauth-verified-resource-token: FIor4BECZRteDPf2prgDA3CShnDJ0OMHBEk0' \
--data-raw '{        
    "username": "client",
    "password": "admin"     
}'
  ```
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
                "value": "authorization.eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGllbnQiLCJleHAiOjE2OTczNjM5MjF9.XkR6cg8e-61eRaD-PC1486SvR0roXcZ9iaOHMVsPLRX_uTpONeFp6KbtWoaOF33pXTCcq2tUiOXD2yoAXBOX5g"
            },
            "refreshToken": {
                "key": "x-oauth-refresh-token",
                "value": "refresh.eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJjbGllbnQiLCJleHAiOjE2OTczNjM5ODF9.3jlBMFvffKU-6MXPTktMl8XE3vYkjQvLxBwRWQVnIKp6bLqvFujq1ND7njmupa_Q2VAvOtJxrRH3rVrx68cfIQ"
            },
            "username": "client"
        }        
    }
}
  ```
### Message & Validation
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-150-1 | Verify user success |
| 403 FORBIDDEN | 403-150-1 | x-oauth-verified-resource-token cannot be null or empty |
| 403 FORBIDDEN | 403-150-2 | Field username cannot be null or empty, Field password cannot be null or empty |
| 403 FORBIDDEN | 403-150-3 | x_verify_resource_token is not found on OAUTH Server |
| 403 FORBIDDEN | 403-150-4 | You are not allowed to access this resource, cause your token status is {token status} |
| 403 FORBIDDEN | 403-150-5 | User {username} is not found on OAUTH server! |
| 403 FORBIDDEN | 403-150-6 | Login Failed! Cause wrong username & password! |



# Github Repositories
| Name | Desc | Url | Visibility |
|--|--|--|--|
| .github | Short Info & About Project | https://github.com/springboot-oauth2-server-project/.github | public |
| oauth2-doc | All documentatations likes (FSD, TSD, ERD, Postman, Sequence, all related technical docs about this projects) | https://github.com/springboot-oauth2-server-project/oauth2-doc | private |
| oauth2-deploy | All related deployment docs likes (compose for production, configuration, syntax) | https://github.com/springboot-oauth2-server-project/oauth2-deploy | private |
| oauth2-web | Oauth Frontend project | https://github.com/springboot-oauth2-server-project/oauth2-web | private |
| oauth2-backend | Oauth backend project| https://github.com/springboot-oauth2-server-project/oauth2-backend | private |
| oauth2-client-react | example react.js frontend project as an client | https://github.com/springboot-oauth2-server-project/oauth2-client-react| private |
| oauth2-resource-springboot | example springboot backend project as an resource | https://github.com/springboot-oauth2-server-project/oauth2-resource-springboot | private |
| oauth2-resource-go | example go backend project as an resource | https://github.com/springboot-oauth2-server-project/oauth2-resource-go | private |
