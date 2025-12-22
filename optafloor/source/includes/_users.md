# Users

## Get All Users

```shell
curl "~/v1/api/external/users" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the users. Refer `Pagination and Sort` and `Schema` Section for exact response
> structure

This endpoint retrieves all users. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/v1/api/external/users`

## User Batch Create

```shell
curl "~/v1/api/external/users/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a user.

### HTTP Request

`POST ~/v1/api/external/users/batch`

### JSON Payload

<pre class="center-column">
[
  {
    "externalId": "E-1001",
    "employeeId": "123545",
    "fullName": "Test User1",
    "username": "test1",
    "email": "test1@gmail.com",
    "mobile": "1234567890",
    "roles": "admin",
    "doj": "2025-01-20",
    "gradeId": 1,
    "designationId": 1,
    "departmentId": 1,
    "lineIds": [
      1,
      2
    ],
    "stdHourlySalary": null,
    "otHourlySalary": null,
    "enabled": true
  }
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "createdAt": 1578194175519,
    "modifiedAt": 1578194175519,
    "createdBy": "admin_spms",
    "lastModifiedBy": "admin_spms",
    "fullName": "Test User1",
    "username": "test1",
    "email": "test1@gmail.com",
    "mobile": "1234567890",
    "roles": "admin",
    "employeeId": "123545"
  }
]
```


## Create User

```shell
curl "~/v1/api/external/users" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a user.

### HTTP Request

`POST ~/v1/api/external/users`

### JSON Payload

<pre class="center-column">
{
  "externalId": "E-1001",
  "employeeId": "123545",
  "fullName": "Test User1",
  "username": "test1",
  "email": "test1@gmail.com",
  "mobile": "1234567890",
  "roles": "admin",
  "doj": "2025-01-20",
  "gradeId": 1,
  "designationId": 1,
  "departmentId": 1,
  "lineIds": [
    1,
    2
  ],
  "stdHourlySalary": null,
  "otHourlySalary": null,
  "enabled": true
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "createdAt": 1578194175519,
  "modifiedAt": 1578194175519,
  "createdBy": "admin_spms",
  "lastModifiedBy": "admin_spms",
  "fullName": "Test User1",
  "username": "test1",
  "email": "test1@gmail.com",
  "mobile": "1234567890",
  "roles": "admin",
  "employeeId": "123545"
}
```

## Update a Specific User

```shell
curl "~/v1/api/external/users?externalId=E-1001" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing user.

### HTTP Request

`PUT ~/v1/api/external/users?externalId=<ExternalId>`

| Parameter  | Description                           |
|------------|---------------------------------------|
| externalId | The External Id of the user to update |

### JSON Payload

<pre class="center-column">
{
  "externalId": "E-1001",
  "employeeId": "123545",
  "fullName": "Test User1",
  "username": "test1",
  "email": "test1@gmail.com",
  "mobile": "1234567890",
  "roles": "admin",
  "doj": "2025-01-20",
  "gradeId": 1,
  "designationId": 1,
  "departmentId": 1,
  "lineIds": [
    1,
    2
  ],
  "stdHourlySalary": null,
  "otHourlySalary": null,
  "enabled": true
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "createdAt": 1578194175519,
  "modifiedAt": 1578194175519,
  "createdBy": "admin_spms",
  "lastModifiedBy": "admin_spms",
  "fullName": "Test User2",
  "username": "test2",
  "email": "test2@gmail.com",
  "mobile": "1234567890",
  "roles": "admin",
  "employeeId": "123545",
  "grade": "A"
}
```

## Delete a Specific User

```shell
curl "~/v1/api/external/users?externalId=<ExternalId>"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific user.

### HTTP Request

`DELETE ~/v1/api/external/users?externalId=<ExternalId>`

### URL Parameters

| Parameter  | Description                           |
|------------|---------------------------------------|
| externalId | The External Id of the user to delete |

## Schema

```json
{
  "id": "long",
  "externalId": "string",
  "employeeId": "string",
  "fullName": "string",
  "username": "string",
  "email": "string",
  "mobile": "string",
  "roles": "string",
  "doj": "yyyy-MM-dd",
  "gradeId": "long",
  "designationId": "long",
  "departmentId": "long",
  "lineIds": "long[]",
  "stdHourlySalary": "double",
  "otHourlySalary": "double"
}
```

Schema of product entity

| Field           | Type     | Constraints | Description                                                |
|-----------------|----------|-------------|------------------------------------------------------------|
| id              | Number   | Primary Key | Internal ID                                                |
| externalId      | String   | Unique      | External ID from external App                              |
| fullName        | String   | Required    | Full Name of Employee                                      |
| employeeId      | String   | Required    | User employee Id                                           |
| username        | String   | Required    | Username for login                                         |
| mobile          | String   | Required    | Mobile of Employee                                         |
| email           | String   |             | Email of Employee                                          |
| roles           | String   | Required    | Role of user. Must one of the roles available in OptaFloor |
| doj             | String   |             | Date of Joining in format: `yyyy-MM-dd`                    |
| gradeId         | Number   |             | Grade Id from Grade Master                                 |
| designationId   | Number   |             | Designation Id from Designation Master                     |
| departmentId    | Number   |             | Department Id from Department Master                       |
| lineIds         | Number[] |             | List of Line Ids from Line Master                          |
| stdHourlySalary | Number   |             | Standard Hourly Salary of Employee                         |
| otHourlySalary  | Number   |             | OT Hourly Salary of Employee                               |




