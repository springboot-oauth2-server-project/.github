## About
**Springboot OAuth Project** is an example of OAuth Provider build using springboot 2.7*.

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

### Resource : OAuth2 Configuration 
This is example of OAuth configuration on Resource Backend (Build using springboot)
- Application.yml
```bash
  custom:  
    app:

      # OAuth2 Config
      oauth:
        host: http://localhost:8991

        verify-resource:
          api-url: /v1/oauth/verify/resource/client
          x-oauth-token: YDR2u5ouxw0ne0c2nz8Spl3VZ3adJGpCbHpz
          client-id: UjlMBHgUdSpEnqFlUwflHPybQliFfZgPxpGL
          client-secreet: eg4R2e4ND95SpeqjS24KjJfPkcd7SIWt0CQQ
          resource-id: ziatrXUclubDFmiraYkuhAtBKoiyQWPVfWgV

        verify-user:
          api-url: /v1/oauth/verify/user

        verify-authorization:
          api-url: /v1/oauth/verify/authorization

        register-user:
          api-url: /v1/oauth/user/save
          username-requester: admin
```

- OAuthProperties.java
```bash
package com.deni.app.oauth;

import org.springframework.beans.factory.annotation.Value;

public class OAuthProperties {
    @Value("${custom.app.oauth.host}")
    public String hostOAuth;

    // VERIFY RESOURCE API
    @Value("${custom.app.oauth.verify-resource.api-url}")
    public String urlVerifyResource;

    @Value("${custom.app.oauth.verify-resource.x-oauth-token}")
    public String xOAuthToken;

    @Value("${custom.app.oauth.verify-resource.client-id}")
    public String clientId;

    @Value("${custom.app.oauth.verify-resource.client-secreet}")
    public String clientSecreet;

    @Value("${custom.app.oauth.verify-resource.resource-id}")
    public String resourceId;

    // VERIFY USER API
    @Value("${custom.app.oauth.verify-user.api-url}")
    public String urlVerifyUser;

    // VERIFY TOKEB API
    @Value("${custom.app.oauth.verify-authorization.api-url}")
    public String urlVerifyAuthorization;

    // REGISTER  & UPDATE USER OAUTH
    @Value("${custom.app.oauth.register-user.api-url}")
    public String urlRegisterUser;

    public String getUrlRegisterUser(String param) {
        return urlRegisterUser + "/" + param;
    }

    @Value("${custom.app.oauth.register-user.username-requester}")
    public String oauthUsernameRequesterForRegisterUser;

}    
```

- VerifyResourceAPICall.java
```bash
package com.deni.app.oauth.apicall;

import com.deni.app.oauth.OAuthProperties;
import com.deni.app.oauth.constants.OAuthHeaderConstants;
import com.deni.app.oauth.request.VerifyResourceBody;
import com.deni.app.oauth.response.APIResponse;
import com.google.gson.Gson;
import org.springframework.http.*;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;

@Service
public class VerifyResourceAPICall extends OAuthProperties {


    public APIResponse doRequest(String username) {

        VerifyResourceBody body = VerifyResourceBody.builder()
                .clientId(clientId)
                .clientSecreet(clientSecreet)
                .resourceId(resourceId)
                .username(username)
                .build();

        System.out.println("--------------------------------------");
        System.out.println("--- VERIFY RESOURCE TO OAUTH SERVER --");
        System.out.println("--------------------------------------");
        System.out.println(new Gson().toJson(body));

        HttpHeaders headers = new HttpHeaders();
        headers.set("Content-Type", MediaType.APPLICATION_JSON.toString());
        headers.set(OAuthHeaderConstants.X_OAUTH_TOKEN, xOAuthToken);
        HttpEntity<VerifyResourceBody> request = new HttpEntity<>(body, headers);

        String uri = hostOAuth + urlVerifyResource;
        RestTemplate restTemplate = new RestTemplate();
        ResponseEntity<APIResponse> responseEntity = null;
        try {
            responseEntity = restTemplate.exchange(uri, HttpMethod.POST, request, APIResponse.class);
            return (APIResponse) responseEntity.getBody();
        } catch (Exception e) {
            System.out.println(new Gson().toJson(e));
            String response = e.getMessage();
            if (response.contains("403")) {
                response = response.replace("403 : \"", "");
                response = response.replace("}}\"", "}}");
            }

            APIResponse apiResponse = new Gson().fromJson(response, APIResponse.class);
            return apiResponse;
        }
    }
}
```


## Github Repository
All [Github Repositories](https://github.com/springboot-oauth2-server-project/.github/blob/main/profile/pages/github-repository.md) about `OAuth2` & `Resource` `Client` project

## Status
|Task|Assign|Start Date|End Date|Status|
|--|--|--|--|--|
|Create OAuth2 Backend|[denitiawan](https://github.com/denitiawan)|29/09/2023|16/10/2023|Done|
|Create OAuth2 Web|[denitiawan](https://github.com/denitiawan)|29/09/2023|16/10/2023|Done|
|Create Resource backend|[denitiawan](https://github.com/denitiawan)|17/10/2023|21/10/2023|Done|
|Create Resource client|[denitiawan](https://github.com/denitiawan)|17/10/2023|21/10/2023|Done|
|Create documentation|[denitiawan](https://github.com/denitiawan)|21/10/2023|21/10/2023|Inprogress|
