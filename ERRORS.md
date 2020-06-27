# BottPoker Error Codes for Version 1
Errors within BottPoker contain a `meta` and `data` objects that house primary data. A user will find what is of value to them inside the `data` object. The `meta` object provides information pertaining to the current request.

**Example of `meta`**
```javascript


"meta":
{
    "api_version":1,
    "status":200,
    "endpoint":"system\/endpoints",
    "authorization_needed":false,
    "millisecond":1593255009571,
    "time":1593255009,
    "process_time":"0.003424"
}


````

**Example of `data`**

```javascript

"data": 
{
    "path":"system\/endpoints",
    "parent":"System",
    "name":"Endpoints",
    "description":"All system endpoints which are available to use within Bott Poker.",
    "auth_required":false,
    "parameters":[]
},
    
```

Many `endpoints` require `parameters` to be sent. If you send data that is malformed you will be provided a response and guidance to correct that mistake by the API. The three objects to guide you to correct your mistkaes are `incorrect_value_lengths`, `missing_information` and  `incorrect_value_lengths`. An example of what these look like rendered is as follows:

```javascript

"missing_information": 
[
    {
        "error": "We do not support the game type requested, please review the game_types that we support.",
        "game_types": 
        [
            "RNG",
            "SNG",
            "TRN"
        ]
    }
],

"missing_parameters": 
[
    "game_id",
],
    

"incorrect_value_lengths": 
[
    "game_id minimum length 1"
],

```

#### 100 - IP banned due to ignoring ratelimit
- IP banned due to repeated requests and ignoring ratelimit warnings. The IP ban will stay ineffect until a time seen fit to release.

#### 1507 - Rate Limited By Authorization
- You are sending to many requests.

```javascript
    "data": {
        "code": 1507,
        "error": "Ratelimit. Next access allowable at 1591765010484. Limit set to 1 request per 1000ms"
    },
```   

#### 1508 - Rate Limited at Firewall Level
- You are sending to many requests and being blocked at a firewall level

```javascript

    "data": {
        "code": 180,
        "error": "Ratelimited. Please allow 0 second(s) before your next request."
    },

```   

#### 190 - Rate Limited and Temporary IP Ban at the Firewall Level 
- Due to repeated requests to slow down your rate of request you have been automcatically banned for a specified period. Repeated violations can result in a permanent account or IP ban and will be reviewed on a case by case basis.

```javascript
    "data": {
        "code": 190,
        "error": "Ratelimit Hit! You have a ban applied. Please allow 59 second(s) before your next request."
    },
```   

## 2xx Network Issues
All codes in the 200 to 299 range relate to network issues.

## 3xx User Input Issues
Codes within the range of 300-399 are reserved for malformed inputs, these can be issues with 
illegal characters, missing fields or authorization.

#### 400 - API Key invalid
- The provided API Key, parameter `key` was not valid. 

#### 401 - Missing API Key
- The API key parameter named `key` was not present. This must be sent as part of the header.

#### 450 - Nonce missing
- The incoming payload was devoid of the parameter `nonce`. 

#### 460 - Nonce too small
- The `nonce` was part of the header. The issue pertains to the value being lower than the previous sent. When sending a `nonce` the value must be higher than the previous sent. Treat this sequentially. 


#### 465 - Nonce format invalid
- The `nonce` was present in the header. The `nonce` was not the expected length. A minimum of 17 characters are required.

```javascript
"data": {
        "code": 465,
        "error": "Nonce incorrectly formatted. Minimum 17 characters in length."
    },
```

#### 500 - Missing Authorization String
- The `authorization` parameter was missing.

#### 550 - Missing information
Review at the following objects if present for more information

- `missing_parameters`
- `incorrect_value_lengths`
- `missing_information`

#### 600 - Unknown Endpoint
- Provide invalid endpoint that we do not support

## 7xx Service Issues
Any codes which fall in the 700-799 are issues directly related to BottPoker.

## Help
If you are having any issues that you cannot figure out please contact us directly on support@bottpoker.com or via an issue ticket.


    