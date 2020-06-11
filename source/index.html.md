---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - swift

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Zoho Catalyst! You can find all available Catalyst end points here.


# Authorization

## User Signup

```shell
curl -X POST \
  https://catalyst.zoho.com/baas/v1/project/3000000002001/project-user/signup \
  -H 'Content-Type: application/json' \
  -H 'PROJECT_ID: 1010309726' \
  -d '{
	"zaid":"1010309726",
	"user_details":{
		"first_name":"Amelia",
		"last_name":"Burrows",
		"email_id":"emma@zylker.com"  
	},
	"platform_type":"web",
	"redirect_url":"https://zylker.zohocatalyst.com/app/index.html"
}'
```

```swift
let user = User(firstName: "Amelia", lastName: "Burrows", email: "emma@zylker.com")
        AuthHandler.signUp(user: user) { (result) in
            switch result{
            case .success(let user):
                print("\(user) successfully created")
            case .error(let error):
                print("Error in creating user \(error)")
            }
        }
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": {
        "zaid": 1011481670,
        "user_details": {
            "user_id": 11000000000039,
            "zuid": 1011521034,
            "zaaid": 1011520995,
            "status": "ACTIVE",
            "is_confirmed": true,
            "email_id": "emma@zylker.com",
            "first_name": "Amelia",
            "last_name": "Burrows",
            "created_time": "May 13, 2019 09:16 PM",
            "modified_time": "May 13, 2019 09:16 PM",
            "invited_time": "May 13, 2019 09:16 PM",
            "role_details": {
                "role_id": 11000000000037,
                "role_name": "App Administrator"
            }
        },
        "redirect_url": "https://zylker.zohocatalyst.com/app/index.html",
        "platform_type": "web",
        "org_id": 1011520995
    }
}
```

This API is used to add a user to the Catalyst application for a specific platform.

### HTTP Request

`POST https://catalyst.zoho.com/baas/v1/project/{project_id}/project-user/signup`

### Authentication

`Not Required`

### Query Parameters

Attributes | Data Type | Mandatory | Max Size | Description
--------- | ------- | ----------- | --------| ------------|
zaid | String | true | 100 | Project Key
user_details | json | true |  | The JSON contains the details of the user.
platform_type | String | true | N/A | Accepted values are "web", "android", "ios"
redirect_url | String | false | 200 | Represents the redirect url after the user resets the password.


## Add User

```shell
curl -X POST \
  https://catalyst.zoho.com/baas/v1/project/3000000002001/project-user \
  -H 'Content-Type: application/json' \
  -d '{
	"user_details":{
		"last_name":"Burrows",
		"email_id":"emma@zylker.com",
		"zaaid":4567899
	},
	"platform_type":"web"
}'
```


> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": {
        "zaid": 1011481670,
        "user_details": {
            "user_id": 11000000000039,
            "zuid": 1011521034,
            "zaaid": 1011520995,
            "status": "ACTIVE",
            "is_confirmed": true,
            "email_id": "emma@zylker.com",
            "first_name": "Amelia",
            "last_name": "Burrows",
            "created_time": "May 13, 2019 09:16 PM",
            "modified_time": "May 13, 2019 09:16 PM",
            "invited_time": "May 13, 2019 09:16 PM",
            "role_id": 11000000000037
        },
        "redirect_url": "https://zylker.zohocatalyst.com/app/index.html",
        "platform_type": "web",
        "org_id": 1011520995
    }
}
```

This API is used to add a user to a particular org.

### HTTP Request

`POST https://catalyst.zoho.com/baas/v1/project/{project_id}/project-user`

***project_id*** - The unique ID of the project

### OAuth Scope

`scope=ZohoCatalyst.projects.users.CREATE`

### URL Parameters

Attributes | Data Type | Mandatory | Max Size | Description
--------- | ------- | ----------- | --------| ------------|
zaid | String | false | 100 | Project Key
user_details | json | true |  | The JSON contains the details of the user.
platform_type | String | true | N/A | Accepted values are "web", "android", "ios"
redirect_url | String | false | 200 | Represents the redirect url after the user resets the password.


## Reset Password

```shell
curl -X POST \
  'https://catalyst.zoho.com/baas/v1/project/56000000023001/project-user/forgotpassword' \
  -H 'Content-Type: application/json' \
  -H 'PROJECT_ID: 1001854921' \
  -d '{
	"user_details":{
		"email_id":"nishath.n+temp1@zohocorp.com"
	},
	"platform_type":"web"
}'
```

> The above command returns JSON structured like this:

```json
{
    "status":"success",
    "data":"Reset link sent to your emma@zylker.com email address. Please check your email :)"
}
```

This API allows the user to reset the password of their Catalyst application. When this API is called, the reset password link will be sent to the user's email address.

### HTTP Request

`POST https://catalyst.zoho.com/baas/v1/project/{project_id}/project-user/forgotpassword`

***project_id*** - The unique ID of the project

### URL Parameters

Attributes | Data Type | Mandatory | Max Size | Description
--------- | ------- | ----------- | --------| ------------|
user_details | json | true |  | The JSON contains the details of the user.
platform_type | String | true | N/A | Accepted values are "web", "android", "ios"
redirect_url | String | false | 200 | Represents the redirect url after the user resets the password.


## Get Current Project User

```shell
curl -X GET \
  https://catalyst.zoho.com/baas/v1/project/3000000005007/project-user/current \
  -H "Authorization: Zoho-oauthtoken 1000.910***************************16.2f****************************57"
```


> The above command returns JSON structured like this:

```json
{
    "status":"success",
    "data":{
        "zuid":1019540152,
        "zaaid":1019540153,
        "status":"ACTIVE",
        "user_id":3000000006001,
        "is_confirmed":true,
        "email_id":"emma@zylker.com",
        "first_name":"Amelia",
        "last_name":"Burrows",
        "created_time":"Jul 09, 2019 04:11 PM",
        "modified_time":"Jul 09, 2019 04:11 PM",
        "invited_time":"Jul 09, 2019 04:11 PM",
        "role_details":{
            "role_id":3000000005015,
            "role_name":"App User"
        }
    }

}
```

This API fetches the details of the Catalyst application user logged in currently.

### HTTP Request

`GET https://catalyst.zoho.com/baas/v1/project/{project_id}/project-user/current`

***project_id*** - The unique ID of the project

### OAuth Scope

`scope=scope=ZohoCatalyst.projects.users.READ`




# Data Store

## Insert Row

```shell
curl "https://catalyst.zoho.com/baas/v1/project/4000000006007/table/testTab/row"  \
-X POST \
-d '[{"Department_ID":"IT678",Department_Name":"Marketing", Employee_Name":"Robert Page"}]' \
-H "Content-Type:application/json" \
-H "Authorization: Zoho-oauthtoken 1000.910***************************16.2f****************************57"
```

```swift
let database = Database()  // create instance for Database
let mexRecord = CLRecord(table: "Restaurant") // create row
mexRecord["name"] = "Mexican Grill"
mexRecord["location"] = "San Jose, CA"
mexRecord["price_for_two"] = 200
        
database.save(mexRecord) { (result) in
      switch result{
            case .success(let record):
                print("Record Saved \(record)")
            case .error(let error):
                print("Error in saving record \(error)")
        }
  }
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": [
        {
            "CREATORID": 56000000002003,
            "MODIFIEDTIME": "2019-03-13 18:20:49",
            "Department_ID": "IT678"
            "Department_Name": "Marketing"
            "Employee_Name": "Robert Page",
            "CREATEDTIME": "2019-03-13 18:20:49",
            "ROWID": 56000000359193,
        }
    ]
}
```

This API is used to insert a row of data or a record in a table in the Data Store referred through the table ID.

### HTTP Request

`POST https://catalyst.zoho.com/baas/v1/project/{project_id}/table/{tableIdentifier}/row`

***project_id*** - The unique ID of the project

***tableIdentifier*** - The unique ID of the table or table name

### OAuth Scope

`scope=ZohoCatalyst.tables.rows.CREATE`


### Request JSON

Attributes | Data Type | Mandatory |  Description
--------- | ------- | ----------- | ------------|
column_name | String | true |  Specifies the attribute name of the given table
column_value | String | true | Specifies the value of the attribute


## Select Row

```shell
curl "https://catalyst.zoho.com/baas/v1/project/4000000006007/table/testTab/row"  \
-X GET \
-H "Authorization: Zoho-oauthtoken 1000.910***************************16.2f****************************57"
```

```swift
let database = Database()
database.fetch("Restaurant") { (result) in
switch result{
    case .success(let rows):
        for row in rows {
            print(row["name"].stringValue)
         }
        case .error(let error):
           print("Error in Fetching \(error)")
       }
 }
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": [
       {
            "CREATORID": 56000000002003,
            "MODIFIEDTIME": "2019-03-06 10:16:41",
            "Department_ID": "IT148",
            "Department_Name": "Admin",
            "Employee_Name": "Anne Hathkins",
            "CREATEDTIME": "2019-03-06 10:16:41",
            "ROWID": 56000000342025,
            "doubleDataType": null
        },
        {
            "CREATORID": 56000000002003,
            "MODIFIEDTIME": "2019-03-06 10:18:56",
            "Department_ID": "IT170",
            "Department_Name": "Sales",
            "Employee_Name": "Steven Hyde",
            "CREATEDTIME": "2019-03-06 10:18:56",
            "ROWID": 56000000342028,
            "doubleDataType": null
        }
    ]
}
```

This API enables you to read all the available records or rows from the referred table in the Data Store.

### HTTP Request

`GET https://catalyst.zoho.com/baas/v1/project/{project_id}/table/{tableIdentifier}/row`

***project_id*** - The unique ID of the project

***tableIdentifier*** - The unique ID of the table or table name

### OAuth Scope

`scope=ZohoCatalyst.tables.rows.READ`



## Update Row

```shell
curl "https://catalyst.zoho.com/baas/v1/project/4000000006007/table/testTab/row"  \
-X PUT \
-d '[{"Employee_Name":"Morgan Jones","ROWID":4000000042728}]' \
-H "Content-Type:application/json" \
-H "Authorization: Zoho-oauthtoken 1000.910***************************16.2f****************************57"
```

```swift
let database = Database()
mexRecord["cost_for_two"] = 30
database.save(mexRecord)  { (result) in
   switch result{
     case .success(let record):
          print("Record Saved \(record)")
      case .error(let error):
          print("Error in saving record \(error)")
     }
}
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": [
        {
            "CREATORID": 56000000002003,
            "MODIFIEDTIME": "2019-02-26 11:18:49",
            "Department_ID":"IT245",
            "Department_Name":"Human Resources",
            "Employee_Name": "Morgan Jones",
            "CREATEDTIME": "2019-02-26 11:18:49",
            "ROWID": 4000000042728
        }
    ]
}
```

This API allows you to update rows in a table in the Data Store by modifying the relevant column values. This is done by referring the ROWID of the record in the table.

### HTTP Request

`PUT https://catalyst.zoho.com/baas/v1/project/{project_id}/table/{tableIdentifier}/row`

***project_id*** - The unique ID of the project

***tableIdentifier*** - The unique ID of the table or table name

### OAuth Scope

`scope=ZohoCatalyst.tables.rows.UPDATE`


### Request JSON

Attributes | Data Type | Mandatory |  Description
--------- | ------- | ----------- | ------------|
column_name | String | true |  Specifies the attribute name of the given table
column_value | String | true | Specifies the value of the attribute
ROWID | Long | true | Refers the ROWID to update the record



## Delete Row

```shell
curl "https://catalyst.zoho.com/baas/v1/project/4000000006007/table/testTab/row/4000000042360"  \
-X DELETE \
-H "Authorization: Zoho-oauthtoken 1000.910***************************16.2f****************************57"
```

```swift
let database = Database()
database.delete(mexRecord) { (result) in
     switch result{
       case .success(let record):
           print("Record Deleted \(record)")
       case .error(let error):
          print("Error in Deleting record \(error)")
     }
}
```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "data": {
        "CREATORID": 56000000002003,
        "MODIFIEDTIME": "2019-02-26 11:18:49",
        "Department_ID": "IT809"
        "Department_Name": "Accounting",
        "Customer_Name": "Jason Pierre",
        "CREATEDTIME": "2019-02-26 11:18:49",
        "ROWID": 4000000042360,
        "doubleDataType": null
    }
}
```

This API deletes a particular record or a row of a table in the Data Store referring it by its ROWID.

### HTTP Request

`DELETE https://catalyst.zoho.com/baas/v1/project/{project_id}/table/{tableIdentifier}/row/{row_id}`

***project_id*** - The unique ID of the project

***tableIdentifier*** - The unique ID of the table or table name

***row_id*** - The unique ID of the row

### OAuth Scope

`scope=ZohoCatalyst.tables.rows.DELETE`

