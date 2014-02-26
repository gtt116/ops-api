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
