## About
This is an prototype of Oauth2 Server build using Springboot 2*, the target about this project for :
- Do Auhtentication & Authorization the Resource Server
- This Oauth Server will support with multi tech resource server likes (Springboot, Go, Js, Laravel, etc).
- Easy to use and integration for Management Oauth Server and Resource client want to Authentication & Authorization.

## Oauth Server Features
- **Web CPanel Admin** for OAuth Server
- **Management Role** for OAuth Server
- **Management User** for OAuth Server
- **Management Resource** (`CRUD`, `Limmit by email`)
- **Management Resource Client** (`CRUD`, `Limmit by Resource`)
- **Management User for Resource Client** (`CRUD`, `Limmit by Resource Client`,`Multiple Login`)
- **Resource-client authorization** : `resource-id` `client-id` `client-secreet` `code_challanger` `signature-key` `grand-type` 
- **Resource-client authentication** : `username` `password`
- **Email Verification** for register new user
- **Management Log User Activity**  on Resource Client
- **Provide Authentication & Authorization API** for user want to login into Resource client
- **Provide Register new user or existing user API**
- **Provide Loging API** for Resource client

## Oauth Server Rules for Resource client Integration
- Register Resource 
- Register Resource Client
- Register User for mapping into Resource Client
- 3 Step for Authentication & Authorization
	- Verify Resource Client
	- Verify User
	- Get Athorization Token
- Resource client loging to Oauth Server	

## Oauth Server Tech Stack
### Frontend
- *Language* : `JS`
- *Librarry* : `React.js` `CRA`
- *Style* : `MUI` `theming`
- *Translation* : `I18n`
- *State* : `Redux`
- *Containerization* : `Docker`
- *CI/CD* : `Github` `Github Action` `Github Pipeline`
- *Server* : `VPS`

### Backend
- *Language* : `Java` `17`
- *Librarry* : `Spring` `Spring Security`
- *Framework* : `Springboot`
- *Database* : `Postgres`
- *Cache* : `Redis`
- *Containerization* : `Docker`
- *CI/CD* : `Github` `Github Action` `Github Pipeline`
- *Server* : `VPS`


## Features Plan (Min Map)
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/1b7023ab-a38c-48ab-8fe3-a702393646cf)


## Flow (Sequence)
### Register new user (Resource Owner)
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/4d68d8fe-6ce6-4b36-a3aa-894ea549934e)

### Register new Resource
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/86e29a19-64eb-45ea-87f7-48b047cf5936)

### Register new Resource Client
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/51ae2b70-e22e-45e9-84be-1faf8c25c5dd)

### Register new user (Resource Client)
![register new user for resource client](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/eb4795c6-38ee-485c-bdea-b68a25fda4ac)

## ERD
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/463dbac2-8875-481e-a07b-69379dd33158)



# ... Under Development ...


