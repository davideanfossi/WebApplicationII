# WA2_Lab05_G32
## Authors:
- s301201, Anfossi Davide
- s292623, Mistruzzi Luca Guglielmo
- s303513, Serra Matteo
- s305985, Torredimare Andrea

## How to run 
### Prerequisites:
- Docker
- Docker Compose plugin
- jibDockerBuild (Gradle task)
- Postman (optional, to test APIs)

1. Build the image of the server by using jibDockerBuild (either from the terminal or selecting it in Gradle tasks menu from Intellij)
2. Open a terminal in the root of the project and type:
   ```sh
   docker-compose up
   ```
#### Note:
We finally solved the bug we had in Lab4, so now all the components can be deployed simply from the above command

### Suggested method for testing APIs:
1. Be sure to have all the required containers up and running
2. Prepare a Postman request like this: 
   - Method: GET
   - Url: http://localhost:8080/API/login
   - Body: raw Json containing an object like { "username" : <username_you_want>, "password":"password" }
   
    This will return the JWT token from Keycloak you need to provide to APIs in order to get the role recognized.

3. Try testing different APIs by following the rules from the Security Chain in the WebSecurityConfig file. Include the correct body if needed, remember to select "Bearer Token" for the Authorization Type and paste the token provided by the second point.

4. Try also giving tokens from unauthorized users for the API you are testing in order to verify its behaviour.

### Credentials for users with roles on Keycloak
- john.doe@mail.com : password --> app_client
- linus.torvalds@mail.com : password --> app_expert
- steve.jobs@mail.com : password -> app_manager

All the other user that can be found in the PostgreDB container are simply there from previous lab, the DO NOT have a corresponding entry on the KeyCloak container, so they can't be used as real profiles.
We will make sure to provide a sufficient number of usable profiles (for all roles) for the final and complete project.