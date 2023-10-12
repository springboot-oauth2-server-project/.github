[Back](https://github.com/springboot-oauth2-server-project/)

## Features Plan (Min Map)
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/1b7023ab-a38c-48ab-8fe3-a702393646cf)

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
