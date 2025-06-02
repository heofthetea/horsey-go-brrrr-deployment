## horsey-go-brrrr

This is where a central docker compose file resides to run the horsey-go-brrrr project.<br>
The horsey-go-brrrr project is a connect-4 game developed in the scope of the lecture "Web-Engineering II" at dhbw. It comprises of:

- [https://github.com/heofthetea/horsey-go-brrrr-be](https://github.com/heofthetea/horsey-go-brrrr-be) - a quarkus REST api
- [https://github.com/heofthetea/horsey-go-brrrr-fe](https://github.com/heofthetea/horsey-go-brrrr-fe) - a Vue.js application serving as an indepentend client

## How to run

Currently, the only docker compose file in here is the one that works, and **should only be used** for local testing. This is because one container, more specifically the api, needs to run in `network_mode: host` in order to validate keycloak JWT tokens correctly (otherwise there would be an issuer mismatch - disgusting stuff). Assuming you have built the docker containers correctly, according to the respective repo's instructions, all you need to do is run the project.

```bash
docker compose up -d
```

The following should be provided:

- A keycloak accessible under `localhost:8081`
  - the keycloak will have a fully configured realm, with the following two testing users:
    - username: `test1`, password: `test`
    - username: `test2`, password: `test`
- The Vue.js app accessible under `localhost:15173`

> **Warning**: please test the game workflow only with two different users. Playing a game with oneself leads to... questionable behaviour, which is not yet fixed.
