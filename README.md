# wh-documentation

This repository serve as documentation project related to the fictive company World Hoster.

[Link to specifications](./documents/specifications.md)

[Link to logs from 2020-05-08 to 2020-05-12](./documents/logs.md)

`Front-end` and `back-end` are `dockerized` and hosted on `Heroku` in three environments: `development`, `staging` and `production`. 

`Sonarcloud` is used to accomplish `static analyzing` of the `codebase`.

The `codebase` is hosted on `github`.

The `CI/CD` will be implemented by `github actions`.

The solution consist in two projets.

# Project 1: wh-web (Front-end)

[Tasks to complete](https://github.com/hollox/wh-documentation/projects/3)

[Repository](https://github.com/hollox/wh-web)

Environments:
- [production](https://www.worldhoster.live)
- [staging](http://staging.worldhoster.live)
- [development](http://dev.worldhoster.live) 
    
# Project 2: wh-tickets-api (Back-end)

[Tasks to complete](https://github.com/hollox/wh-documentation/projects/1)

[Repository](https://github.com/hollox/wh-support-api)

Environments:
- [production](https://tickets-api.worldhoster.live/v1/tickets) 
- [staging](https://tickets-api.worldhoster.live/v1/tickets) 
- [development](https://tickets-api.worldhoster.live/v1/tickets) 

# Security

[Auth0](auth0.com) assure the security of the application by acting as a Single Sign On.

The front-end manage the implicit flow while the back-end validate the JWT token by calling Auth0. 

| User                | Roles
|---------------------|---------------------------------
| customer@hollox.net | Customer
| employee@hollox.net | Employee
| manager@hollox.net  | Employee, Manager

| Role       | Description
|------------|---------------------------------
| Customer   | Can create tickets
| Employee   | Can create customer accounts
| Manager    | Can create employee accounts

# Entities

### Tickets

A request opened by a customer.

### Ticket statuses

Those statuses manage the state of customer tickets.

| Type        | Description
|-------------|-------------------------
| open        | Ticket that are opened but not processed
| in progress | Ticket where an employee start to work on it
| close       | Ticket where a user was satisfy by employee work

### Messages

A message wrote by a customer, employee or manager to request more details about a ticket or communicating the progress of the ticket.

### Message types

Those types manage the state of messages so employees can hide certain messages.

| Type    | Description
|---------|-------------------------
| visible | Message that bring value to the discussion
| spam    | Ads to remove from the discussion
| harmful | Hateful message not tolerated in a discussion
| useless | Message without any value that make the discussion confusing

### Users

An identity to access the system.

### User types

A type to specify the user responsability.

| Type        | Description
|-------------|-------------------------
| customer    | A person that may represent an organization that require attention to an issue.
| employee    | A person that work for World Hoster or a partner that is trying to resolve the customer ticket.
| manager     | A person that manage the employee and validate the quality of the ticket process.


# Storage

Postgresl database manage the persistence of the application.

Here the database schema:

< TODO: convert table to a schema >

**tickets**

| Name             | Type
|------------------|--------
| ticket_id        | uuid
| title            | varchar(250)
| html_body        | text
| author_user_id   | uuid
| ticket_status_id | uuid
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp

**ticket_statuses**

| Name             | Type
|------------------|--------
| status_id        | uuid
| name             | varchar(25)
| description      | text
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp

**messages**

| Name             | Type
|------------------|--------
| message_id       | uuid
| html_body        | text
| ticket_id        | uuid
| author_user_id   | uuid
| type_id          | uuid
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp

**message_types**

| Name             | Type
|------------------|--------
| type_id          | uuid
| name             | varchar(25)
| description      | text
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp

**users**

| Name             | Type
|------------------|--------
| user_id          | uuid
| firstname        | varchar(25)
| lastname         | varchar(25)
| email            | varchar(250)
| user_type_id     | uuid
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp

**users_types**

| Name             | Type
|------------------|--------
| type_id          | uuid
| name             | varchar(25)
| description      | text
||
| creation_user_id | uuid
| creation_date    | time with timestamp
| update_user_id   | uuid
| update_date      | time with timestamp
