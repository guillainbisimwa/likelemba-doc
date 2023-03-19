# Introduction

Welcome to the likelemba API! You can use our API to access likelemba API endpoints, which can get informations  in our database.

# Authentication

Our API is able to support user accounts with each user having the ability managing their own resources.
In order to get your API key (token), you need to Signup or login!

## Signup

> Signup a new user - get token from here

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://likelemba-backend.herokuapp.com/api/register",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
    email : "guy@test.me",
    //socialMediaToken : "",
    guest : true,
    phoneNumber : "+243789456123",
    //otp : 12345,
    lang : "fr",
    password : "12345678",
    fingerPrintHash : "#242SDSD7GADSDGASGJN74",
    pseudo : "guyL",
    name : "Guy",
    lastName : "BRODY",
    imgUrl : "www.test.me/img.png",
  },
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "token": "*******************************",
    "account": {
        "email": "test8@me.com",
        "role": "customer",
        "roleData": {
            "customer": "63dc00a716439caa3a169a08"
        },
        "_id": "63dc00a716439caa3a169a08",
        "pseudo": "GuyL",
        "name": "Guy",
        "lastName": "BRODY",
    }
}
```
> If you faild to signup, you'll get this :

```json
{    
   "success": false,
   "msg": "Account Already exist"
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

Likelemba API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint creates a new user.

### HTTP Request

`POST https://likelemba-backend.herokuapp.com/api/register`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| name                  | string | Name of the user                                    |
| lastName              | string | Last Name of the user                               |
| email                 | string | An adress mail. It's must be unique in our database |
| password              | string | A password                                          |
| guest                 | Bool   |                                                     |
| phoneNumber           | string |                                                     |
| lang                  | String |  Default 'fr'                                       |
| fingerPrintHash       | String |                                                     |
| pseudo                | String |                                                     |
| imgUrl                | String |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>
"msg": "Account Already exist"
</code></aside>

## login by Phone

> login an existing user - get token from here

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://likelemba-backend.herokuapp.com/api/login/",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
   phone: "+243789456123",
  },
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
   "token": "*****************************",
   "account": {
      "roleData": {
         "customer": "63dbf013d61a9eaaffb4e47f"
      },
      "_id": "63dc00a716439caa3a169a08",
      "pseudo": "GuyL",
      "name": "Guy",
      "lastName": "BRODY",
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

Likelemba API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint log in an existing user

### HTTP Request

`POST https://likelemba-backend.herokuapp.com/api/login/`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| phone     | string | A phone number. It's must be unique in our database |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>


## Verify OTP

> OTP code verification

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://likelemba-backend.herokuapp.com/api/verifyOtp/",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
   phone: "+243789456123",
   otp: "123456"
  },
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "msg": "Valid OTP"
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

Likelemba API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint verify OTP code for an existing user

### HTTP Request

`POST https://likelemba-backend.herokuapp.com/api/verifyOtp/`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| phone     | string | A phone number. It's must be unique in our database |
| otp       | Number |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna have a success message!
</aside>


# Group

Our API is able to manage Groups and it's memebers

## Add a group

> Add a new group of users

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://likelemba-backend.herokuapp.com/api/group/add",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
    imgProfileUrl: "www.test.me/img.png",
    groupName: "Humanitarian",
    visibility: true,
    currency: "usd",
    amountContribution: 10,
    affiliationFee: 1,
    deadline: "M",
    precisionDeadline: 1,
    description: "The Humanitarian to help farmers",
    author : "45323drg5465df4g6d",
  },
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "group": {
        
    }
}
```
> If you faild to signup, you'll get this :

```json
{    
   "success": false,
   "msg": "Error"
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

Likelemba API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint adds a new group.

### HTTP Request

`POST https://likelemba-backend.herokuapp.com/api/group/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| imgProfileUrl         | string | Name of the user                                    |
| groupName             | string | Name of the user                                    |
| visibility            | Bool   | `True` if is Private, `False` if Public             |
| currency              | string | Can be `usd` or `cdf`                               |
| amountContribution    | Number |                                                     |
| affiliationFee        | Number |                                                     |
| deadline              | String |  Can be on of `D`, `W`, `M` or `Y`                  |
| precisionDeadline     | Number |                                                     |
| description           | String |                                                     |
| author                | String | Id of an existing customer                          |

<aside class="success">
Remember — if you post successfully, then you gonna save your new group!
</aside>

## List All groups

> Get all groups


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://likelemba-backend.herokuapp.com/api/group/all",
  params: {},
  headers: {
    "content-type": "application/json",
  }
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "msg": "Groups fetched successfully",
    "groups": {
        ...
    }
}
```

This endpoint will fecth a ALL GROUPS.

### HTTP Request

`GET https://likelemba-backend.herokuapp.com/api/group/all`

<aside class="success">
Remember — if you get successfully, then you gonna receive a success message and a group ojbect of array
</aside>


## List All groups by Customer

> Get all groups by Customer


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://likelemba-backend.herokuapp.com/api/group/all/ad55854a67f35asfas67",
  params: {},
  headers: {
    "content-type": "application/json",
  }
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "msg": "Groups fetched successfully",
    "groups": {
        ...
    }
}
```

This endpoint will fecth a ALL GROUPS.

### HTTP Request

`GET https://likelemba-backend.herokuapp.com/api/group/all/:customer`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| customer              | string |  ID Passed as params                                |

<aside class="success">
Remember — if you get successfully, then you gonna receive a success message and a group ojbect of array
</aside>
