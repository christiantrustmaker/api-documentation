---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
 
  - javascript


includes:
  - errors

search: true
---

# Introduction

This API is used to allow clients to pull and push data to ePreventions system, to help manage their clients data.

# Authentication

While using the ePreventions API, you will need to add API key to each request header. The API key can be generated and invalidated at anytime by an admin in the ePrevention application.

`x-epreventions-auth-token: YOUR_AUTH_KEY`

<aside class="notice">
You must replace <code>YOUR_AUTH_TOKEN</code> with your company API key.
</aside>

# Clients



## GET All Users

This endpoint returns a list of all users a company.

<aside class="notice">
You can use the clientid that is returned for the users to modify and retrive data in client endpoints.
</aside>

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://stage.epreventions.com/api.php/companies/1/users',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "users": [
        {
            "clientid": 128,
            "email": "test@gmail.com",
            "fullname": "Sam Smith",
            "location": "",
            "mobile": "",
            "drug": "",
            "sobriety": "0000-00-00",
            "contact": "949 555-1234",
            "profile": "568d60cbb47219274947c5921456177448432.png",
            "id": 3
        },
        {
            "clientid": 881,
            "email": "test2@gmail.com",
            "fullname": "Admin Smith",
            "location": "",
            "mobile": "",
            "drug": "Opioids",
            "sobriety": "2015-06-19",
            "contact": "",
            "profile": "56d4e9061d24080221a53cc41456793982857.png",
            "id": 5
        }
    ]
}
```

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/users`




## GET Client

This endpoint returns a specified client.


```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://stage.epreventions.com/api.php/companies/1/client/128',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "client": {
        "clientid": 128,
        "email": "test@gmail.com",
        "fullname": "Sam Smith",
        "location": "",
        "mobile": "",
        "drug": "",
        "sobriety": "0000-00-00",
        "contact": "949 555-1234",
        "profile": "568d60cbb47219274947c5921456177448432.png",
        "id": 3
    }
}
```

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client/:clientid`



## POST Create Client

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://stage.epreventions.com/api.php/companies/1/client',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  body: {
    fullname: 'Sam Smith', //required
    email: 's.smith@gmail.com', //required
    age: '25',
    location: "2255 East ave st Irvine CA, 92168",
    mobile: "9683348912",
    sex: "male",
    drug: "narcotics",
    sobriety: "2015-01-01" 

  },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "status": "success",
  "clientid": 112
}
```

This endpoint creates a new client for you company.
### Required Fields
`fullname`
`email`

### Optional Fields
`age`
`location`
`mobile`
`sex`
`drugs`
`sobriety`

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client`


## PUT Update Client

```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://stage.epreventions.com/api.php/companies/1/client/112',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  body: {
    fullname: 'Sam Smith', //required
    email: 's.smith@gmail.com', //required
    age: '25',
    location: "2255 East ave st Irvine CA, 92168",
    mobile: "5551231234",
    sex: "male",
    drug: "narcotics",
    sobriety: "2015-01-01" 
  },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

This endpoint updated a client.

### Fields to update
`fullname`
`email`
`age`
`location`
`mobile`
`sex`
`drugs`
`sobriety`

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client/:clientid`

# Profile
Profile endpoints use the field names of the profile questions configured to your company, through your ePrevention admin. If you are note sure what field names to use, contact your ePreventions admin, and they can provide them for you.



## GET Profile History 
This endpoint retrieves the history for a profile field of a given client.
  
```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://stage.epreventions.com/api.php/companies/1/client/112/profile-history/field/background_notes',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   }
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
    "status": "success",
    "history": [
        {
            "answer": "sunt in culpa qui officia deserunt mollit anim",
            "timestamp": "2017-09-10T06:49:40+00:00"
        },
        {
            "answer": "Lorem ipsum dolor sit amet, consectetur adipiscing",
            "timestamp": "2017-08-19T06:49:40+00:00"
        },
        {
            "answer": "Phasellus egestas tellus rutrum tellus pellentesque eu tincidunt tortor aliquam",
            "timestamp": "2017-07-10T06:49:54+00:00"
        },
        {
            "answer": "Pellentesque habitant morbi tristique senectus. Dignissim enim sit amet venenatis urna cursus eget nunc scelerisque.",
            "timestamp": "2015-05-19T08:02:43+00:00"
        }
    ]
}
```

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client/:clientid/profile-history/field/:fieldname`






 

## PUT Update Profile 
All data will update the current value of the client's profile, and will also be added to a profile history table in the order the request are received.
  
```javascript
var request = require("request");

var options = { method: 'PUT',
  url: 'https://stage.epreventions.com/api.php/companies/1/client/112/profile',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  body: {
    living_arrangement: "Ut enim ad minim veniam, quis nostrud exercitation ullamco",
    background_notes: "Lorem ipsum dolor sit amet, consectetur adipiscing elit"
  },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

### Body format
{`fieldname`: `value`}

You can update one or multiple fields ina single request for a client.

### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client/:clientid/profile`

## POST Add Profile History 
This endpoint will add all data for a field to the clients profile history table. It **will not** update the current value of the client's profile
  
```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://stage.epreventions.com/api.php/companies/1/client/112/profile-history/field/background_notes',
  headers: 
   { 
     'cache-control': 'no-cache',
     'content-type': 'application/json',
     'x-epreventions-auth-token': '+9pf/G0zI/gATopJzgl8PKXkuEQLKxz4AfPy4OsaZwph9I3hDHiIUJsFI6Raw/a1tw0ymXXDQLFeutgbp6bCHBQXslBtXhdaNMUSg2m94QI=' 
   },
  body: [
    {"value": "Lorem ipsum dolor sit amet, consectetur", "timestamp": "2016-04-10"},
    {"value": "sunt in culpa qui officia deserunt mollit anim", "timestamp": "2016-01-01"}
  ],
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

### Body format
[ {`value`: "data to update", `timestamp`: "0000-00-00"} ]

This endpoint accepts an array of updates for a given field. Each update needs 2 fields, **value** which contains the information to be added. and **timestamp** which is used to represent the time and order the updates occurred.
`If a timestamp is not provides, it will default to the current time the request was made.`


### HTTP Request

`https://stage.epreventions.com/api.php/companies/:companyid/client/:clientid/profile-history/field/:fieldname`

