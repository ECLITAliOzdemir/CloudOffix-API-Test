# CloudOffix CloudConnect API

CloudOffix is usually extended internally via modules, but many of its features and all of its data are also available from the outside for external analysis or integration with various tools. API is easily available over [XML-RPC](http://en.wikipedia.org/wiki/XML-RPC),  [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) or simple http requests.

Since CloudOffix is simpy fully customizable and extendable platform all base and custom methods can be executed through API.

Please **DO NOT FORGET** to replace "demo.cloudoffix.com" with your instance url.

>  ###  Authentication (HTTP)

This method is used to create a session and also capture uid (user-id) which is a required parameter for calling other API methods like create, write etc. If uid parameter of the response is false this means that the authentication failed. Below you can examine the response of a successful call.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /web/session/authenticate   
  
**Request- Body**:  

	{
		"params" : {
		"login":"service.user@local",
		"password":"Qwerty123",
		"db":"demo.cloudoffix.com"
		}
	}
**Response Sample:**

	{
	    "jsonrpc": "2.0",
	    "id": null,
	    "result": {
	        "session_id": "a2af0ec0399e82cbca42ccf0900aa65e43ab3607",
	        "uid": 5079,
	        "is_system": true,
	        "is_superuser": false,
	        "user_context": {
	            "lang": "tr_TR",
	            "tz": "Turkey",
	            "uid": 5079
	        },
	        "db": "demo.cloudoffix.com",
	        "server_version": "11.0",
	        "server_version_info": [
	            11,
	            0,
	            0,
	            "final",
	            0,
	            ""
	        ],
	        "name": "service user",
	        "username": "service.user@local",
	        "company_id": 1,
	        "partner_id": 5206,
	        "user_companies": false,
	        "currencies": {
	            "1": {
	                "symbol": "€",
	                "position": "after",
	                "digits": [
	                    69,
	                    2
	                ]
	            },
	            "32": {
	                "symbol": "₺",
	                "position": "after",
	                "digits": [
	                    69,
	                    2
	                ]
	            },
	            "3": {
	                "symbol": "$",
	                "position": "before",
	                "digits": [
	                    69,
	                    2
	                ]
	            }
	        },
	        "web.base.url": "https://demo.cloudoffix.com",
	        "mfa_login_needed": null,
	        "is_saas_client": "yes",
	        "expiration_datetime": 35,
	        "trial": "False",
	        "background_css": false
	    }
	}
