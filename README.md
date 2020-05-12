# wh-documentation

This repository serve as documentation project related to the fictive company World Hoster.

[Link to specifications](./documents/specifications.md)

[Link to logs from 2020-05-08 to 2020-05-11](./documents/logs.md)

## Description
`Front-end` and `back-end` are `dockerized` and hosted on `Heroku` in three environments: `development`, `staging` and `production`. 

`Sonarcloud` is used to accomplish `static analyzing` of the `codebase`.

The `codebase` is hosted on `github`.

The `CI/CD` will be implemented by `github actions`.

The `security` will be assured by `Auth0`.

The `database` will be in `Postgresql` format.

The solution is composated as two projets.

### Project1: wh-web (Front-end)

[Tasks to complete](https://github.com/hollox/wh-documentation/projects/3)

[Repository](https://github.com/hollox/wh-web)

Environments:
- [production](https://www.worldhoster.live)
- [staging](http://staging.worldhoster.live)
- [development](http://dev.worldhoster.live) 
    
### Project 2: wh-tickets-api (Back-end)
  
[Tasks to complete](https://github.com/hollox/wh-documentation/projects/1)

[Repository](https://github.com/hollox/wh-support-api)

Environments:
- [production](https://tickets-api.worldhoster.live/v1/tickets) 
- [staging](https://tickets-api.worldhoster.live/v1/tickets) 
- [development](https://tickets-api.worldhoster.live/v1/tickets) 
