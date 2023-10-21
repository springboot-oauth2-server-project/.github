[Back](https://github.com/springboot-oauth2-server-project/)

## Verify Register, Update User API
### CURL
- Request
```bash
curl --location 'http://localhost:8991/v1/oauth/user/save/{requestUsername}' \
--header 'x-oauth-token: ttt.ttt.ttt' \
--data '{    
    "code":"auto",
    "firstName":"denitiawan",
    "lastName":"github",
    "username":"denitiawan",
    "password":"password",    
    "blocked": 0,
    "active": 1,    
    "resourceId": "rrr.rrr.rrr"
}'
```
- Response
```bash
{
    "status": "200 OK",
    "headers": "",
    "body": {
        "code": "2XX-5",
        "message": "Save Success",
        "data": {
            "id": 21,
            "code": "USR-0973178762574732",
            "firstName": "denitiawan",
            "lastName": "github",
            "username": "denitiawan",            
            "blocked": 0,
            "active": 1,
            "createdBy": "admin",
            "createdDate": "2023-10-21T18:23:28.866+00:00",
            "updatedBy": "admin",
            "updatedDate": "2023-10-21T18:23:28.866+00:00",
            "roleCodes": "RESOURCE-CLIENT",
            "resourceCodes": "pointofsales",
            "roleCodesList": [
                "RESOURCE-CLIENT"
            ],
            "resourceCodesList": [
                "pointofsales"
            ]
        },
        "server": null
    }
}
```
### Message & Validation
| Http Status | Status Code | Message |
|--|--|--|
| 200 OK | 200-200-1 | Save Success |
| 403 FORBIDDEN | 403-200-1 | Request username cannot be null or empty |
| 403 FORBIDDEN | 403-200-2 | Request username is not found |
| 403 FORBIDDEN | 403-200-3 | x-oauth-token is not valid |
| 403 FORBIDDEN | 403-200-4 | Request body cannot be null or empty |
| 403 FORBIDDEN | 403-200-5 | Username cannot be null or empty |
| 403 FORBIDDEN | 403-200-6 | ResourceId cannot be null or empty |
| 403 FORBIDDEN | 403-200-7 | Resource is not found |

