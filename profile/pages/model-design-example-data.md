[Back](https://github.com/springboot-oauth2-server-project/)

### Diagram
![image](https://github.com/springboot-oauth2-server-project/.github/assets/11941308/bb8ef2b4-1969-4096-a14a-9058948608d4)

### Resource
| Resource Name|Resource Id|
|--|--|
|App-1|xxx-xxx-app1|
|App-2|xxx-xxx-app2|
|App-3|xxx-xxx-app3|

 ### Client
|Client Name|Client Id|Client Secreet|Resource Ids|
|--|--|--|--|
|Client-1|xxx-xxx-client1|xxx-xxx-secreet1|xxx-xxx-app1|
|Client-2|xxx-xxx-client2|xxx-xxx-secreet2|xxx-xxx-app2|
|Client-3|xxx-xxx-client3|xxx-xxx-secreet3|xxx-xxx-app3|
|Client-4|xxx-xxx-client4|xxx-xxx-secreet4|xxx-xxx-app1 xxx-xxx-app2 xxx-xxx-app3|

 ### User
|Username|Password|Role|Resource Ids|
|--|--|--|--|
|admin|admin|ADMIN||
|rs-owner|owner|RESOURCE-OWNER||
|user1|user|RESOURCE-CLIENT|xxx-xxx-app1|
|user2|user|RESOURCE-CLIENT|xxx-xxx-app2|
|user3|user|RESOURCE-CLIENT|xxx-xxx-app3|
|user4|user|RESOURCE-CLIENT|xxx-xxx-app1 xxx-xxx-app2 xxx-xxx-app3|


