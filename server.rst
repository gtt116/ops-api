Server (VM)
==========

POST /v2/{tenant}/servers
************************
Create a instance.

Request body schema:
------------

- **server** (*required*): A dict of server attributes, including:

  - **name** (*required*): String, the name of server.
  - **imageRef** (*required*): String, the uuid of image to use.


Example
--------
**Request** ::

    {
        "server": {
            "name": "server-1",
            "imageRef": "cedef40a-ed67-4d10-800e-17455edce175",
            "flavorRef": "1"
        },
        "os:scheduler_hints": {
            "different_host": ["a0cf03a5-d921-4877-bb5c-86d26cf818e1", "8c19174f-4220-44f0-824a-cd1eeef10287"],
            "same_host": ["a0cf03a5-d921-4877-bb5c-86d26cf818e1",
            "8c19174f-4220-44f0-824a-cd1eeef10287"],
            "build_near_host_ip": "192.168.1.1",
            "cidr": "24"
        }
    }

**Response** ::

    HTTP 200

    {
        "server": {
            "OS-DCF:diskConfig": "MANUAL",
            "adminPass": "5cxQ2GtAsH8T",
            "id": "95bc133f-5564-42f2-b903-99a37ae9e686",
            "links": [
                {
                    "href": "http://nova.163.org:8774/v2/81f502a8e4204ac7802b0b2273727049/servers/95bc133f-5564-42f2-b903-99a37ae9e686",
                    "rel": "self"
                },
                {
                    "href": "http://nova.163.org:8774/81f502a8e4204ac7802b0b2273727049/servers/95bc133f-5564-42f2-b903-99a37ae9e686",
                    "rel": "bookmark"
                }
            ]
        }
    }




GET /v2/{tenant}/servers
************************
Show all servers belong to the tenant.

Request Parameters:
----------
* **changes-since** (*optional*): dateTime, A time/date stamp for when the server last changed
  status.
* **image** (*optional*): string, UUID of image which the server is using.
* **flavor** (*optional*): string, id of flavor which the server is using.


GET /v2/{tenant}/servers/detail
*******************************

GET /v2/{tenant}/servers/{id}
*****************************
