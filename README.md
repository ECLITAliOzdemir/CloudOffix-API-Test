# CloudOffix CloudConnect API

CloudOffix is usually extended internally via modules, but many of its features and all of its data are also available for external analysis or integration with various tools. API is easily available over [XML-RPC](http://en.wikipedia.org/wiki/XML-RPC),  [JSON-RPC](https://en.wikipedia.org/wiki/JSON-RPC) or simple http requests.

Since CloudOffix is simpy a fully customizable and extendable platform, all base and custom methods can be executed through API.

Please **DO NOT FORGET** to replace "demo.cloudoffix.com" with your instance url.

## API PATHS
###  Authentication (HTTP)

This method is used to create a session and also capture uid (user-id) which is a required parameter for calling other API methods like create, write etc. If uid parameter of the response is false this means that the authentication failed. Below you can examine the response of a successful call.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /web/session/authenticate  

**Request Body:**  

    {
		"params":{
			"login":"{{Username}}",
			"password":"{{Password}}",
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
### Read (HTTP)
Used for reading object(s) from api

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  
**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Read(ids, field names))
    - ids: list of object ids that is going to be read from the api.
    - fields: list of field names that should be returned for objects.  

**Request Body:**  

    {
      "jsonrpc": "2.0",
      "method": "call",
      "params": {
      	"service" : "object",
      	"method" : "execute",
      	"args" : [
          "demo.cloudoffix.com",
          {{UserId}},
          "{{Password}}",
          "res.partner",
          "read",
          [1],
          []
      	]
      }
    }
    
 **Response Sample:**  
 
     {
        "jsonrpc": "2.0",
        "id": null,
        "result": [
            {
                "id": 1,
                "activity_ids": [],
                "activity_date_deadline": false,
                "display_name": "CloudOffix Inc.",
                "date": false,
                "title": false,
                "parent_id": false,
                "child_ids": [],
                "ref": false,
                "lang": "en_US",
                "tz": false,
                "user_id": false,
                "vat": false,
                "bank_ids": [],
                "website": "https://www.mydemo.com/",
                "comment": false,
                "category_id": [],
                "credit_limit": 0.0,
                "barcode": false,
                "active": true,
                "customer": false,
                "supplier": false,
                "employee": false,
                "function": false,
                "type": "contact",
                "street": "",
                "street2": false,
                "zip": "",
                "city": "",
                "state_id": false,
                "country_id": [
                    1,
                    "USA"
                ],
                "phone": "",
                "mobile": false,
                "is_company": true,
                "industry_id": false,
                "company_id": [
                    1,
                    "CloufOffix Inc."
                ],
                "color": 0,
                "user_ids": [],
                "partner_share": true,
                "commercial_partner_id": [
                    1,
                    "CloudOffix Inc."
                ],
                "commercial_partner_country_id": [
                    1,
                    "USA"
                ],
                "commercial_company_name": "CloudOffix Inc.",
                "company_name": false,
                "image": <base64>,
                "image_small":<base64>,
                "message_follower_ids": [],
                "message_ids": [],
                "message_last_post": false,
                "message_bounce": 0,
                "opt_out": false,
                "channel_ids": [],
                "website_message_ids": [],
                "debit_limit": 0.0,
                "ref_company_ids": [
                    1
                ],
                "last_time_entries_checked": false,
                "invoice_ids": [],
                "contract_ids": [],
                "invoice_warn": "no-message",
                "invoice_warn_msg": false,
                "signup_token": false,
                "signup_type": false,
                "signup_expiration": false,
                "calendar_last_notif_ack": "2019-06-11 12:21:51",
                "payment_token_ids": [],
                "sale_order_ids": [],
                "sale_warn": "no-message",
                "sale_warn_msg": false,
                "team_id": false,
                "website_meta_title": false,
                "website_meta_description": false,
                "website_meta_keywords": false,
                "website_published": true,
                "website_description": false,
                "website_short_description": false,
                "partner_latitude": 0.0,
                "partner_longitude": 0.0,
                "date_localization": false,
                "is_email_address_valid": "valid",
                "email_validation_result": "Catchall",
                "email": "info@cloudoffix.com",
                "firstname": false,
                "lastname": "CloudOffix Inc.",
                "name": "CloudOffix Inc.",
                "tax_office_id": false,
                "create_uid": false,
                "create_date": false,
                "write_uid": [
                    9,
                    "JOHN DOE USER"
                ],
                "write_date": "2020-09-15 10:59:17",
                "activity_state": false,
                "activity_user_id": false,
                "activity_type_id": false,
                "activity_summary": false,
                "parent_name": false,
                "tz_offset": "+0000",
                "email_formatted": "",
                "company_type": "company",
                "contact_address": "CloudOffix Inc.\n\n\n  \nUSA",
                "self": [
                    1,
                    "CloudOffix Inc."
                ],
                "message_is_follower": false,
                "message_partner_ids": [],
                "message_channel_ids": [],
                "message_unread": false,
                "message_unread_counter": 0,
                "message_needaction": false,
                "message_needaction_counter": 0,
                "im_status": "offline",
                "credit": 0.0,
                "debit": 0.0,
                "total_invoiced": 0.0,
                "currency_id": [
                    32,
                    "TRY"
                ],
                "contracts_count": 0,
                "journal_item_count": 0,
                "property_account_payable_id": [
                    123,
                    "320000 Receivable"
                ],
                "property_account_receivable_id": [
                    12,
                    "120000 Payable"
                ],
                "property_account_position_id": false,
                "property_payment_term_id": false,
                "property_supplier_payment_term_id": false,
                "has_unreconciled_entries": false,
                "bank_account_count": 0,
                "trust": "normal",
                "signup_valid": false,
                "signup_url": false,
                "payment_token_count": 0,
                "property_product_pricelist": [
                    1,
                    "Public Pricelist (USD)"
                ],
                "sale_order_count": 0,
                "website_url": "/partners/cloudoffix-inc",
                "__last_update": "2020-09-15 10:59:17"
            }
        ]
    }

### Search Read (HTTP)
Used for searching object(s) by a filter and reading fields from results through api.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  
**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Search Read(filter, fields, offset, limit, order))
    - **filter**: list of arrays that will be interpreted with [polish notation](https://en.wikipedia.org/wiki/Polish_notation)<br>
 **For example:**<br>
 ['&', ["name", "ilike", "john"], ["write_date", ">", "2021-01-01"]]<br>
 **Will be Interpreted as:**<br>
 name field contains john **AND** write date is after 2021-01-01<br>
 **Available search operators:**<br>
        - '='
        - '!='
        - 'in'
        - 'not in'
        - \'>='
        - \'<='
        - 'ilike'
        - 'like'
    - **fields (optional):** list of field names that should be returned for objects.<br>
 **For Example:**<br>
 A list like ["name", "email","country_id"] can be passed to get only these fields.<br>
 An empty list like [] can be passed to get all the fields available.<br>
    - **offset (optional):** Number of records to skip
    - **limit (optional):** Number of records to get
    - **order (optional):** Used to sort records asc / desc<br>
 **Example:**<br>
 "create_date DESC"
 
 **Request Body:**  

    {
        "jsonrpc": "2.0",
        "method": "call",
        "params": {
            "service" : "object",
            "method" : "execute",
            "args" : [
                "demo.cloudoffix.com",
                {{UserId}}, 
                "{{Password}}", 
                "res.partner",
                "search_read",
                [["name", "ilike", "john"]],
                ["name", "create_date"],
                0,
                0,
                "create_date DESC"
            ]
        }
	}
 **Response Sample:**
 
     {
        "jsonrpc": "2.0",
        "id": null,
        "result": [
            {
                "id": 40,
                "name": "John Doe",
                "create_date": "2020-09-11 06:59:03"
            },
            {
                "id": 16,
                "name": "John Farewell",
                "create_date": "2020-08-27 06:04:30"
            }
        ]
    }

### Search (HTTP)
Used for searching object(s) by a filter and **returns only IDs** of matching results through api.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  

**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Search Read(filter, offset, limit, order, count))
    - **filter**: list of arrays that will be interpreted with [polish notation](https://en.wikipedia.org/wiki/Polish_notation)<br>
 **For example:**<br>
 ['&', ["name", "ilike", "john"], ["write_date", ">", "2021-01-01"]]<br>
 **Will be Interpreted as:**<br>
 name field contains john **AND** write date is after 2021-01-01<br>
 **Available search operators:**<br>
        - '='
        - '!='
        - 'in'
        - 'not in'
        - \'>='
        - \'<='
        - 'ilike'
        - 'like'
    - **offset (optional):** Number of records to skip
    - **limit (optional):** Number of records to get
    - **order (optional):** Used to sort records asc / desc<br>
 **Example:**<br>
 "create_date DESC"<br>
    - **count (optional):** If sent true only count will be returned

 **Request Body (Example to get only the count):**  

    {
        "jsonrpc": "2.0",
        "method": "call",
        "params": {
            "service" : "object",
            "method" : "execute",
            "args" : [
                "demo.cloudoffix.com",
                {{UserId}}, 
                "{{Password}}", 
                "res.partner",
                "search_read",
                [["name", "ilike", "john"]],
                0,
                0,
                "create_date DESC",
                true
            ]
        }
	}
 **Response Sample:**
 
     {
        "jsonrpc": "2.0",
        "id": null,
        "result": 2
     }

### Create (HTTP)
Can be used to create object(s) in a Cloudoffix instance.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  
**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Create(vals))
    - **vals**: An array that contains fields and values

 **Request Body :**  

    {
        "jsonrpc": "2.0",
        "method": "call",
        "params": {
            "service" : "object",
            "method" : "execute",
            "args" : [
                "{{InstanceId}}",
                {{UserId}}, 
                "{{Password}}", 
                "res.partner",
                "create",
                {"name" : "John Doe"}
            ]
        }
    }
 **Response Sample:**
 
     {
        "jsonrpc": "2.0",
        "id": null,
        "result": 1307
     }

### Write (HTTP)
Can be used for editing object(s) in a Cloudoffix instance.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  
**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Write(ids, vals))
    - **ids:** An array that holds the ids of the records that will be updated. 
    - **vals** An array that contains fields and values.

 **Request Body :**  

    {
            "jsonrpc": "2.0",
            "method": "call",
            "params": {
                "service" : "object",
                "method" : "execute",
                "args" : [
                    "{{InstanceId}}",
                    {{UserId}}, 
                    "{{Password}}", 
                    "res.partner",
                    "write",
                    [1307],
                    {"email" : "john.doe@cloudoffix.com"}
                ]
            }
    }
 **Response Sample :**  

    {
        "jsonrpc": "2.0",
        "id": null,
        "result": true
    }

### Unlink (HTTP)
Can be used for deleting object(s) from a Cloudoffix instance.

**Base-URL:** http://demo.cloudoffix.com  
**Content-Type:** application/json  
**Path:** /jsonrpc  
**Params:** (args)
 - **First param:** Database instance
 - **Second param:** User id (uid that is returned from authentication)
 - **Third param:** Password
 - **Fourth param:** Model's name (hr.employee, res.partner, project.project, helpdesk ticket etc.)
 - **Fifth param:** Name of the method to be executed
 - **Sixth param:** Arguments to be sent to the called method (Unlink(ids))
    - **ids:**: An array that holds the ids of the records that will be deleted. 

 **Request Body :**  

    {
        "jsonrpc": "2.0",
        "method": "call",
        "params": {
            "service" : "object",
            "method" : "execute",
            "args" : [
                "{{InstanceId}}",
                {{UserId}}, 
                "{{Password}}", 
                "res.partner",
                "unlink",
                [1307]
            ]
        }
    }

 **Response Sample :**  

    {
        "jsonrpc": "2.0",
        "id": null,
        "result": true
    }
