Server (VM)
==========

POST /v2/{tenant}/servers
************************
Create a instance.

Request body schema:
------------

- **server** (*required*): A dict of server attributes, including:

  - **tenant_id** (*optional*): string, 多tenant云环境下的tenant或账号Id
  - **name** (*required*): String, the name of server.
  - **imageRef** (*required*): String, The image reference. Specify as an ID or full URL.
  - **metadata** (*optional*): A dict of key and value pair:

    - **key** (*required*): String, key of metadata
    - **value** (*required*): String, value of metadata

- **os:scheduler_hints** (*optional*): Dict, scheduler hints

  - **query** (*optional*): String, An valid json string.  e.g. "[\\"in\\", \\"$service.availability_zone\\", \\"nova11\\", \\"nova12\\"]" 
  - **same_host** (*optional*): List, A instance uuid list which new instance will located in.



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
            "cidr": "24",
            "query": "[\"in\", \"$service.availability_zone\", \"nova11\", \"nova12\"]",
            "query": "[\"in\", \"$service.host\", \"10-120-120-11\", \"10-120-120-13\"]"
        }
    }

**Response** ::

    HTTP/1.1 200 OK

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

- **changes-since** (*optional*): dateTime, A time/date stamp for when the server last changed
  status.
- **image** (*optional*): string, UUID of image which the server is using.
- **flavor** (*optional*): string, id of flavor which the server is using.
- **name** (*optional*): string, name of instance.
- **marker** (*optional*): string, UUID of instance which is the start the response item.
- **limit** (*optional*): string, the count of response item.
- **status** (*optional*): string, the instance status, like 'ACITVE'
- **all_tenants** (*optional*): true/false, when you are `admin` you can query all instance in system.

Example
--------
**Request** ::

  GET /servers?image=imageRef&flavor=flavorRef&name=serverName&status=serverStatus&marker=markerID&limit=int&changes-since=dateTime


**Response** ::

 HTTP/1.1 200 OK

 {
    "servers": [
        {
            "id": "dc05163d-6a95-4590-bb0b-45334501cd39",
            "links": [
                {
                    "href": "http://10.120.120.11:8774/v2/3179fc9d69d747b4a06f27a6d2334050/servers/dc05163d-6a95-4590-bb0b-45334501cd39",
                    "rel": "self"
                },
                {
                    "href": "http://10.120.120.11:8774/3179fc9d69d747b4a06f27a6d2334050/servers/dc05163d-6a95-4590-bb0b-45334501cd39",
                    "rel": "bookmark"
                }
            ],
            "name": "jenkins"
        }
    ]
 }


GET /v2/{tenant}/servers/detail
*******************************

GET /v2/{tenant}/servers/{id}
*****************************
