## About
**Springboot OAuth2 Project**, is an example of OAuth2 Server Project, for do **authenticate & authorize** the user, and then user can login & access into the resources who already **register & implement the OAuth2 Flow** on their projects.

### Context 
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/9e73c681-364f-4d04-bbfb-25b73323cd82)

### Container
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/b2a25b2f-ffe4-4f49-a71d-ba11c354b5d0)

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

### OAuth2 Flow
[OAuth2 Flow](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/seq-oauth2-flow.md)

### API Spec
- [Verification Resource](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-resource.md) 
- [Verification User](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-user.md)  
- [Verify Token](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-verify-token.md)  
- [Register or Update user](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/api-registration-update-user.md)

### Resource 
- [ Resource Config ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/config-reasource.md)
- [ Resource Screenshoot ](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/sc-resource-web.md)

## Github Repository
All [Github Repositories](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/github-repository.md) about `OAuth2` & `Resource` `Client` project

## Insight
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/00dd708c-6f35-42f5-a536-15eb5463688a)

## Status
|Task|Assign|Start Date|End Date|Status|
|--|--|--|--|--|
|Create OAuth2 Backend|[denitiawan](https://github.com/denitiawan)|29/09/2023|16/10/2023|Done|
|Create OAuth2 Web|[denitiawan](https://github.com/denitiawan)|29/09/2023|16/10/2023|Done|
|Create Resource backend|[denitiawan](https://github.com/denitiawan)|17/10/2023|21/10/2023|Done|
|Create Resource client|[denitiawan](https://github.com/denitiawan)|17/10/2023|21/10/2023|Done|
|Create documentation|[denitiawan](https://github.com/denitiawan)|21/10/2023|21/10/2023|Done|
