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
    otp : 12345,
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
        "otp": "BRODY",
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

likelemba API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint creates a new user.

### HTTP Request

`POST https://likelemba-backend.herokuapp.com/api/register`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| name                  | string | Name of the user                                    |
| lastName              | string | Name of the user                                    |
| email                 | string | An adress mail. It's must be unique in our database |
| password              | string | A password                                          |
| guest                 | Bool   |                                                     |
| phoneNumber           | string |                                                     |
| otp                   | Number |                                                     |
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
