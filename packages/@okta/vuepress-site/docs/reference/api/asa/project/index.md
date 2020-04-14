---
title: Introduction to Project Endpoints
category: asa
---

# Projects API

## Getting Started

This article provides an overview of the project API

Explore the Projects API: [![Run in Postman](https://run.pstmn.io/button.svg)](https://example.com).


## Projects Operations

The Projects API has the following operations:
* [Lists the projects for a team](#lists-the-projects-for-a-team)
* [Create a project](#create-a-project)
* [Fetches a single project](#fetches-a-single-project)
* [Deleting a single project](#deleting-a-single-project)
* [Updating a single project](#updating-a-single-project)


### Lists the projects for a team

<ApiOperation method="GET" url="/v1/teams/{team_name}/projects" />


#### Request Path Parameters

| Parameter | Type        | Description   |
| --------- | ----------- | ------------- |
| team_name   | string |  |


#### Request Query Parameters

%List any query parameters here in alpha order%

| Parameter | Description   | Required |
| --------- | ------------- | -------- |
| offset   |   | false | 
| count   |   | false | 
| descending   |   | false | 
| prev   |   | false | 
| self   |   | false | 


#### Request Body

This endpoint has no request body.

#### Response Body

On returning a 200: List of Projects

Returns a list of [Project](/docs/asa/models.html#project) objects.

#### Usage Example

##### Request

```bash
curl -v -X GET \
-H "Authorization: Bearer ${jwt}" \
https://app.scaleft.com/v1/teams/{team_name}/projects
```

##### Response
```json
{"list":[{"create_server_users":true,"deleted_at":"0001-01-01T00:00:00Z","force_shared_ssh_users":false,"id":"96d26d9c-291b-4cba-ac6b-a324cb200ad5","name":"the-sound-and-the-fury","next_unix_gid":63001,"next_unix_uid":60001,"require_preauth_for_creds":true,"shared_admin_user_name":null,"shared_standard_user_name":null,"team":"william-faulkner","user_on_demand_period":null},{"create_server_users":true,"deleted_at":"0001-01-01T00:00:00Z","force_shared_ssh_users":false,"id":"96d26d9c-291b-4cba-ac6b-a324cb200ad5","name":"the-sound-and-the-fury","next_unix_gid":63001,"next_unix_uid":60001,"require_preauth_for_creds":true,"shared_admin_user_name":null,"shared_standard_user_name":null,"team":"william-faulkner","user_on_demand_period":null}]}
```
### Create a project

<ApiOperation method="POST" url="/v1/teams/{team_name}/projects" />
Creates a project for a team

#### Request Path Parameters

| Parameter | Type        | Description   |
| --------- | ----------- | ------------- |
| team_name   | string |  |


#### Request Query Parameters

This endpoint has no query parameters.

#### Request Body

*Required:* Project to create
Uses a [Project](/docs/asa/models.html#project) object.

#### Response Body

On returning a 201: The project that was created

Returns a [Project](/docs/asa/models.html#project) object.

#### Usage Example

##### Request

```bash
curl -v -X POST \
-H "Authorization: Bearer ${jwt}" \
https://app.scaleft.com/v1/teams/{team_name}/projects
```

##### Response
```json
{"create_server_users":true,"deleted_at":"0001-01-01T00:00:00Z","force_shared_ssh_users":false,"id":"96d26d9c-291b-4cba-ac6b-a324cb200ad5","name":"the-sound-and-the-fury","next_unix_gid":63001,"next_unix_uid":60001,"require_preauth_for_creds":true,"shared_admin_user_name":null,"shared_standard_user_name":null,"team":"william-faulkner","user_on_demand_period":null}
```
### Fetches a single project

<ApiOperation method="GET" url="/v1/teams/{team_name}/projects/{project_name}" />


#### Request Path Parameters

| Parameter | Type        | Description   |
| --------- | ----------- | ------------- |
| team_name   | string |  |
| project_name   | string |  |


#### Request Query Parameters

This endpoint has no query parameters.

#### Request Body

This endpoint has no request body.

#### Response Body

On returning a 200: The project that was requested

Returns a [Project](/docs/asa/models.html#project) object.

#### Usage Example

##### Request

```bash
curl -v -X GET \
-H "Authorization: Bearer ${jwt}" \
https://app.scaleft.com/v1/teams/{team_name}/projects/{project_name}
```

##### Response
```json

```
### Deleting a single project

<ApiOperation method="DELETE" url="/v1/teams/{team_name}/projects/{project_name}" />


#### Request Path Parameters

| Parameter | Type        | Description   |
| --------- | ----------- | ------------- |
| team_name   | string |  |
| project_name   | string |  |


#### Request Query Parameters

This endpoint has no query parameters.

#### Request Body

This endpoint has no request body.

#### Response Body

On returning a 204: The project was deleted successfully.



#### Usage Example

##### Request

```bash
curl -v -X DELETE \
-H "Authorization: Bearer ${jwt}" \
https://app.scaleft.com/v1/teams/{team_name}/projects/{project_name}
```

##### Response
```json

```
### Updating a single project

<ApiOperation method="PUT" url="/v1/teams/{team_name}/projects/{project_name}" />


#### Request Path Parameters

| Parameter | Type        | Description   |
| --------- | ----------- | ------------- |
| team_name   | string |  |
| project_name   | string |  |


#### Request Query Parameters

This endpoint has no query parameters.

#### Request Body

*Required:* 
Uses a [ProjectUpdate](/docs/asa/models.html#projectupdate) object.

#### Response Body

On returning a 204: The project was updated successfully.



#### Usage Example

##### Request

```bash
curl -v -X PUT \
-H "Authorization: Bearer ${jwt}" \
https://app.scaleft.com/v1/teams/{team_name}/projects/{project_name}
```

##### Response
```json

```

