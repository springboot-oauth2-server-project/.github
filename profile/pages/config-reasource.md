[Back](https://github.com/springboot-oauth2-server-project/)

## OAuth Config on Resource
### Application.yml
```yml
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

### OAuthProperties.java
```java
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

### VerifyResourceAPICall.java
```java
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
