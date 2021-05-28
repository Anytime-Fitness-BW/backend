# Backend
PVD link: https://docs.google.com/document/d/1E3Ag0oa06bZAriOL5TGW17oBy2SGV1-P3SEnl5zoFi0/edit?usp=sharing

## Deployed URL:
### https://anytime-fitness-bw.herokuapp.com/

# Scripts

- **start**: Runs the app.
- **server**: Runs the app with Nodemon.
- **migrate**: Migrates the local development database to the latest.
- **rollback**: Rolls back migrations in the local development database.
- **seed**: Truncates all tables in the local development database, feel free to add more seed files.
- **test**: Runs tests.
- **migratetest**: Test migrations
- **rollbacktest**: Test rollbacks

## User
      first_name:       not required
      last_name:        not required
      city:             not required
      zipcode:          not required
      username:         *Required*,
      email:             not required
      password:         *Required*


| Method | Endpoint                                  | Returns                                                         | Parameters                                                                                                     |
| ------ | ----------------------------------------- | --------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| GET    | `/api/auth/users`                 | `200` array of items that is posted by logged in user           | Must have authorization token in the header                                                                              |


## classes

         name:   String        *Required*
          type: String        *Required*
          startTime: Int        *Required*
          duration: INT        *Required*
          intensity:INT          *Required*
          location: String        *Required*
          numberOfRegisteredAttendees:INT *Required*
          maxClassSize:INT           *Required*

| Method | Endpoint         | Returns                                         | Parameters                                                                                                                                           |
| ------ | ---------------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| GET    | `/api/classes`     | `200` with array of items with user information | Authorization in the header
| POST   | `/api/classes`     | `201` with the created item object              | name, type, startTime, duration, intensity, location, numberOfRegisteredAttendees, maxClassSize
| PUT  | `/api/classes/:id` | `200` with the updated item object              | Authorization token in the header, same fields as POST request, all optional                                                                         |
| DELETE | `/api/classes/:id` | `204` with no content                           | Authorization token in the header                                                                                                                    |

## Authentication

| Method | Endpoint        | Returns                                  | Parameters                                                                                                                               |
| ------ | --------------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| POST   | `/api/auth/register` | `201` with the registered user object    | `username`, `password` , set `admin` = 1 for making an instructor
| POST   | `/api/auth/login`    | `200` with a welcome message and a token | `username` and`password` (required)
