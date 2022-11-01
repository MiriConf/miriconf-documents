# API Endpoints

## Endpoints

All Endpoints Require a valid JWT token in the header, use the login endpoint to get a JWT token

Implemented:
  - Login
    - /api/v1/login - **POST** - Login (generate and recieve a JWT token)
      
      Example: 
      ```bash
      curl -X POST -H 'Content-Type: application/json' -d '{"username": "testuser", "password": "testing"}' localhost:8081/api/v1/login
      ```
      Will return something like this:
      ```
      eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InRlc3R1c2VyIiwiZXhwIjoxNjY2ODQ5NjM3fQ.3VV8USpoHo9ODaEK6jvkyJzjNaztHSNJdUfHEiaHWLs
      ```

  - Teams
    - /api/v1/teams/list - **GET** - get all teams

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/teams/list
      ```
      Will return something like this:
      ```json
      [
        {
          "_id": "63577c20354451fa1baaf0a4",
          "createdat": "10-25-2022 06:03:12",
          "department": "software engineering",
          "name": "devops team"
        },
        {
          "_id": "63577c2e354451fa1baaf0a6",
          "createdat": "10-25-2022 06:03:26",
          "department": "software engineering",
          "name": "frontend team"
        },
        {
          "_id": "63577c37354451fa1baaf0a8",
          "createdat": "10-25-2022 06:03:35",
          "department": "software engineering",
          "name": "backend team"
        },
        {
          "_id": "63577c50354451fa1baaf0aa",
          "createdat": "10-25-2022 06:04:00",
          "department": "IT",
          "name": "cybersecurity team"
        }
      ]
      ```

    - /api/v1/teams/get/{TEAM ID} - **GET** - get specific teams

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/teams/get/{_id value of a team here}
      ```
      Will return something like this:
      ```json
      {
        "_id": "63577c2e354451fa1baaf0a6",
        "createdat": "10-25-2022 06:03:26",
        "department": "software engineering",
        "name": "frontend team"
      }
      ```

    - /api/v1/teams - **POST** - create a team

      Example:
      ```bash
      curl -X POST -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"name": "exampleteam", "department": "test"}' localhost:8081/api/v1/teams
      ```
      Will return something like this on success:
      ```json
      {
        "success": "exampleteam successfully added at ObjectID(\"63607991d5cac44c012f7439\")"
      }
      ```

    - /api/v1/teams/{TEAM ID} - **PUT** - modify a team
      
      Example:
      ```bash
      curl -X PUT -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"name": "exampleteam", "department": "test"}' localhost:8081/api/v1/teams/63577c20354451fa1baaf0a4
      ```
      Will return something like this on success:
      ```json
      {
        "success": "exampleteam successfully updated at ObjectID(\"63607991d5cac44c012f7439\")"
      }
      ```

    - /api/v1/teams/{TEAM ID} - **DELETE** - delete a team

      Example:
      ```bash
      curl -X DELETE -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/teams/63577c20354451fa1baaf0a4
      ```
      Will return something like this on success:
      ```json
      {
        "success": "team deleted"
      }
      ```

  - Users
    - /api/v1/users/list - **GET** - get all users

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/users/list
      ```
      Will return something like this:
      ```json
      [
        {
          "username": "gbolmida",
          "fullname": "George Bolmida",
          "email": "gbolmida@georgebolmida.com",
          "createdat": "10-25-2022 06:03:12"
        },
        {
          "username": "testuser",
          "fullname": "Test User",
          "email": "test@georgebolmida.com",
          "createdat": "10-26-2022 02:34:02"
        },
        {
          "username": "testuser2",
          "fullname": "Test User2",
          "email": "test2@georgebolmida.com",
          "createdat": "10-26-2022 02:34:59"
        }
      ]
      ```

    - /api/v1/users/get/{TEAM ID} - **GET** - get specific users

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/users/get/{_id value of a team here}
      ```
      Will return something like this:
      ```json
      {
        "username": "gbolmida",
        "fullname": "George Bolmida",
        "email": "gbolmida@georgebolmida.com",
        "createdat": "10-25-2022 06:03:12"
      }
      ```

    - /api/v1/users - **POST** - create a user

      Example:
      ```bash
      curl -X POST -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"username": "blah", "email": "test@testing2.com", "fullname": "test user", "password": "test"}' localhost:8081/api/v1/users
      ```
      Will return something like this:
      ```json
      {
        "success": "blah successfully added at ObjectID(\"63607fc0d5cac44c012f7441\")"
      }
      ```
    
    - /api/v1/users/{USER ID} - **PUT** - modify a user

      Example:
      ```bash
      curl -X PUT -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"username": "blah", "email": "test@testing2.com", "fullname": "test user", "password": "test"}' localhost:8081/api/v1/users/63607fc0d5cac44c012f7441
      ```
      Will return something like this:
      ```json
      {
        "success": "exampleteam successfully updated at ObjectID(\"63607991d5cac44c012f7439\")"
      }
      ```

    - /api/v1/users/{USER ID} - **DELETE** - delete a user

      Example:
      ```bash
      curl -X DELETE -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/users/63607fc0d5cac44c012f7441
      ```
      Will return something like this:
      ```json
      {
        "success": "user deleted"
      }
      ```

Planned:
  - Templates
    - /api/v1/templates/list - get all templates
    - /api/v1/templates/get - get specific templates
    - /api/v1/templates/create - create a template
    - /api/v1/templates/edit - modify a template
    - /api/v1/templates/delete - delete a template
  - Applications
    - /api/v1/applications/list - get all applications
    - /api/v1/applications/get - get specific applications
    - /api/v1/applications/create - create a application
    - /api/v1/applications/edit - modify a application
    - /api/v1/applications/delete - delete a application
  - Configurations
    - /api/v1/configurations/list - get all configurations
    - /api/v1/configurations/get - get specific configurations
    - /api/v1/configurations/create - create a configuration
    - /api/v1/configurations/edit - modify a configuration
    - /api/v1/configurations/delete - delete a configuration
  - Groups
    - /api/v1/groups/list - get all groups
    - /api/v1/groups/get - get specific groups
    - /api/v1/groups/create - create a group
    - /api/v1/groups/edit - modify a group
    - /api/v1/groups/delete - delete a group
  - Roles
    - /api/v1/roles/list - get all roles
    - /api/v1/roles/get - get specific roles
    - /api/v1/roles/create - create a role
    - /api/v1/roles/edit - modify a role
    - /api/v1/roles/delete - delete a role

