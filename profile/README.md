## About
**Springboot OAuth Project** is an example of OAuth Provider build using springboot 2.7*.

### Context 
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/9e73c681-364f-4d04-bbfb-25b73323cd82)

### Info
|Service Name|OAuth Protocol|Open ID Connect|Grant Type|
|--|--|--|--| 
|Springboot OAuth2 App| 2.0 |No|AUTHORIZATION_CODE| 

### Features
- **Management Admin** CRUD (User, Role, Menu, Permission)
  - [Admin Menu](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-admin.md) 
- **Management Resource** CRUD (Resource, Client, User, Log User)
  - [Resource Menu](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-oauth-cpanel-resourceowner.md)

### Roles
- `Admin` : full controll all menus
  -  [Admin Register new User (Resource Owner)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sequence-register-user-resource-owner.md)
  -  [Admin Register new User (Client)](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-admin-reg-new-user-client.md)  
- `Resource-owner` : can manage datas (resource, client, user, user log)
  -  [(Resource Owner) Register new Resource ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-reg-new-resource.md)
  -  [(Resource Owner) Register new Client ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-resource-owner-regitster-new-client.md)
- `Resource-client` : cannot login to `Springboot OAuth2 App`

### Data & Diagram
[Data & Diagram](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/model-design-example-data.md)

### Container
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/b2a25b2f-ffe4-4f49-a71d-ba11c354b5d0)

### OAuth2 Flow
[OAuth2 Flow](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)

### APIs
- [Verification Resource API](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-resource.md) 
- [Verification User API](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-user.md)  
- [Verify Token API](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-token.md)  
- [Register or Update user API](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-registration-update-user.md) 


## Github Repositories
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
