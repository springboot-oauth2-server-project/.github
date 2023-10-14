## About
OAUTH is an open authorization for allowing user can login & access into many applications with single user data. 

## Examples
- I have **google account**, and iam using that account for login & access into **fb, ig, twitter** applications. 
- how **google** can handle it?
- because **fb, ig, twitter** already registered & implements the **OAUTH Googles** on theirs project (backend & frontends)
- so (fb, ig, twitter) can let google for authenticate and authorize every user wants to login into **fb, ig, twitter**.

So iam create this project iam called **Springboot OAUTH2 Server Project** for try to implements simple **OAUTH** on my applications.

This project have **simple OAUTH flow & Features** likes:
- **OAUTH2 WEb CPANEL**, for managements datas **(Admin & Resource)**
- **OAUTH APIs** for **Verification Resource** & **Verification User**

## OAUTH CPANEL : Features
[Oauth2 Server Features](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/features.md/)
  
## OAUTH CPANEL : Screenshoot
- [Role : Admin](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-admin.md)
- [Role : Resource Owner](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-resourceowner.md)

## OAUTH FLow : Sequence of Authenticate & Authorization
- [Frontend request login to backend](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)
- [Backend request verify resource to oauth server](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)
- [Backend request verify user to oauth server](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)
- [Frontend request view dashboard to backend](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)

## OAUTH CPANEL : Sequence of CRUD
- [Admin Register new User (Resource Owner)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sequence-register-user-resource-owner.md)
- [Admin Register new User (Client)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-admin-reg-new-user-client.md)
- [(Resource Owner) Register new Resource ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-reg-new-resource.md)
- [(Resource Owner) Register new Client ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-regitster-new-client.md)

## OAUTH CPANEL : Model & Design
- [ERD](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/erd.md)
- [Example Data](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/model-design-example-data.md)

## Technologies
- [Oauth2 (Frontend-Backend)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/tech-oauth2.md/)
- [Pos (Frontend-Backend)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/tech-pos.md/)
- [Promo (Frontend-Backend)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/tech-promo.md/)
- [Point (Frontend-Backend)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/tech-point.md/)

## OAUTH API : Verify Resource API
### CURL
  ```bash
  curl --location --request POST 'http://localhost:8991/v1/oauth/verify/resource/client' \
--header 'x-oauth-token: YDR2u5ouxw0ne0c2nz8Spl3VZ3adJGpCbHpz' \
--data-raw '{
    "clientId": "fstTysjNpkNtNGsLuSGVhvfmZEARogUaQEpG",
    "clientSecreet": "lYFwVWQNSeWv120BgafwKEQwGLWBDewCdeVC" ,
    "resourceId":"IdnKmJWVHZqhkWaeFzSvBezUHEdSzhGFwaDj"
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
        },
        "server": null
    }
}
  ```
### Http Message
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-100-1 | Verify resource & client success |
| 403 FORBIDDEN | 403-100-1 | x-oauth-token cannot be null or empty |
| 403 FORBIDDEN | 403-100-2 | x-oauth-token is not valid! |
| 403 FORBIDDEN | 403-100-3 | ClientId is not found on OAUTH Server! |
| 403 FORBIDDEN | 403-100-4 | ClientSecreet is wrong! |
| 403 FORBIDDEN | 403-100-5 | ClientId has been non active! |
| 403 FORBIDDEN | 403-100-6 | ClientId has been expired! |
| 403 FORBIDDEN | 403-100-7 | ResourceId is not found on OAUTH Server! |
| 403 FORBIDDEN | 403-100-8 | ClientId is not allow to accessing this Resource : {resource name} |






# ... Under Development ...
