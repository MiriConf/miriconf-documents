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

  - Systems

    - /api/v1/systems - **POST** - create a system

      Example:
      ```bash
      curl -X POST -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"systemname": "George Laptop", "users": ["63607991d5cac44c012f7439"]}' localhost:8081/api/v1/systems
      ```
      Will return something like this on success, this is a client token:
      ```json
      "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InRlc3R1c2VyIiwiZXhwIjoxNjY2ODQ5NjM3fQ.3VV8USpoHo9ODaEK6jvkyJzjNaztHSNJdUfHEiaHWLs"
      ```

    - /api/v1/systems/list - **GET** - get all systems

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/systems/list
      ```
      Will return something like this:
      ```json
      [
        {
          "_id": "63577c20354451fa1baaf0a4",
          "createdat": "10-25-2022 06:03:12",
          "users": ["63607991d5cac44c012f7439"],
          "systemname": "george laptop",
          "lastseen": "-1"
        },
        {
          "_id": "63577c20jfdsfj989f0ssf",
          "createdat": "10-25-2022 06:03:12",
          "users": ["63607991d5cac44c012f7439"],
          "systemname": "john laptop",
          "lastseen": "166895385"
        }
      ]
      ```
      Note: a lastseen value of -1 means that the client has never succesfully sent a request to `/api/v1/systems/ping`

    - /api/v1/systems/ping - **GET** - end user client pinging up to miriconf server

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {client token from system creation}" localhost:8081/api/v1/systems/ping
      ```
      Will return something like this:
      ```json
      "success"
      ```
      Note: this endpoint is only used by the end user client to update it's lastseen value.

    - /api/v1/systems/get/{SYSTEM ID} - **GET** - get a system

      Example:
      ```bash
      curl -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/systems/get/{SYSTEM ID}
      ```
      Will return something like this:
      ```json
      [
        {
          "_id": "63577c20354451fa1baaf0a4",
          "createdat": "10-25-2022 06:03:12",
          "users": ["63607991d5cac44c012f7439"],
          "systemname": "george laptop",
          "lastseen": "-1"
        }
      ]
      ```

    - /api/v1/systems/{SYSTEM ID} - **PUT** - modify a system

      Example:
      ```bash
      curl -X PUT -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" -d '{"systemname": "new laptop", "users": ["63577c20354451fa1baaf0a4", "63577c20354451fa1baaf0a4"]}' localhost:8081/api/v1/systems/{SYSTEM ID}
      ```
      Will return something like this:
      ```json
      {
        "success": "new laptop successfully updated at ObjectID(\"63607991d5cac44c012f7439\")"
      }
      ```

    - /api/v1/systems/{SYSTEM ID} - **DELETE** - delete a system

      Example:
      ```bash
      curl -X DELETE -H 'Content-Type: application/json' -H "Authorization: Bearer {JWT Token recieved from login here}" localhost:8081/api/v1/systems/{SYSTEM ID}
      ```
      Will return something like this:
      ```json
      {
        "success": "system deleted"
      }
      ```
