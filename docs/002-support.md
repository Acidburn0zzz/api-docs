# Group Support
Manage support tickets.

## Tickets [/tickets]
A collection of support tickets that the current user has access to.

### Retrieve all Tickets [GET]
Returns a list of all tickets that the current user can access.

+ Response 200

    + Headers

            Link: https://api.packethost.net/tickets?page=1&per_page=3; rel="previous", https://api.packethost.net/tickets?page=3&per_page=3; rel="next"

    + Body

            {
                "tickets": [
                    { "href": "https://api.packethost.net/tickets/A84F8FE0-9089-4651-8545-255D3F44CD42" },
                    { "href": "https://api.packethost.net/tickets/7BD284B9-4954-4CE6-9C6C-40A2515CD25C" },
                    { "href": "https://api.packethost.net/tickets/E0B12951-C60F-4FFE-A30C-CC0C0FFED88A" }
                ],
                "total": 300,
                "page": 2,
                "per_page": 3,
                "previous": "https://api.packethost.net/tickets?page=1&per_page=3",
                "next": "https://api.packethost.net/tickets?page=3&per_page=3"
            }

### Create a Ticket [POST]
Creates a new support ticket.

+ Request

    + Body

            {
                "title": "This is a new ticket",
                "body": "I have a question about using your API to build a super-duper new app that will change everything ...",
            }

+ Response 201

    + Headers

            Location: https://api.packethost.net/tickets/A84F8FE0-9089-4651-8545-255D3F44CD42

    + Body

            {
                "href": "https://api.packethost.net/tickets/A84F8FE0-9089-4651-8545-255D3F44CD42"
            }

## Ticket [/tickets/{id}]
A single support ticket object.

+ Parameters
    + id (string) ... The ticket ID (in the form of a UUID).

### Retrieve a Ticket [GET]

+ Response 200

    + Body

            {
                "href": "https://api.packethost.net/tickets/023725DA-A6FB-42EC-9882-BDFD6AB17638",
                "id": "023725DA-A6FB-42EC-9882-BDFD6AB17638",
                "title": "Error message when de-provisioning my device",
                "body": "Hello, Packetfolk. I tried to de-provision my device the other day when ...",
                "status": "open",
                "priority": 2,
                "organization": {
                    "href": "https://api.packethost.net/organizations/9CDE70BD-281C-49BA-BDBE-FB571EFCA473"
                },
                "comments": [
                    { "href": "https://api.packethost.net/comments/576147ED-A696-4301-8E18-37E8CBAF599A" },
                    { "href": "https://api.packethost.net/comments/509D25B2-A8C5-4DC8-8545-87714F3262ED" },
                    { "href": "https://api.packethost.net/comments/2D7781B6-CD05-4816-B54D-FB06A9E7043A" },
                    ...
                ],
                "created_by": {
                    "href": "https://api.packethost.net/users/C53711CE-A228-4E3C-86B3-20A4BA0AAC42"
                },
                "created_at": "2014-08-20T22:03:00Z",
                "updated_at": "2014-08-20T23:03:00Z"
            }

### Update a Ticket [PATCH]

+ Request

    + Body

            {
                "status": "closed"
            }

+ Response 204

    + Headers

            Location: https://api.packethost.net/tickets/9A0B312C-4001-4F1D-9505-F7D043713C6B

### Delete a Ticket [DELETE]
+ Response 204

## Ticket Comments [/ticket/{ticket_id}/comments]
A collection of comments for a given ticket.

+ Parameters
    + ticket_id (string) ... The ticket ID (in the form of a UUID).

### Retrieve all Ticket Comments [GET]
Returns a list of all comments for a given ticket.

+ Response 200

    + Body

            {
                "comments": [
                    { "href": "https://api.packethost.net/comments/576147ED-A696-4301-8E18-37E8CBAF599A" },
                    { "href": "https://api.packethost.net/comments/509D25B2-A8C5-4DC8-8545-87714F3262ED" },
                    { "href": "https://api.packethost.net/comments/2D7781B6-CD05-4816-B54D-FB06A9E7043A" },
                    ...
                ]
            }

### Create a Ticket Comment [POST]
Create a new comment for the given ticket.

+ Request

    + Body

            {
                "body": "Here's what I think about this ticket ...",
                "public": true
            }

+ Response 201

    + Headers

            Location: https://api.packethost.net/comments/576147ED-A696-4301-8E18-37E8CBAF599A

    + Body

            {
                "href": "https://api.packethost.net/comments/576147ED-A696-4301-8E18-37E8CBAF599A"
            }

## Ticket Comment [/comments/{id}]
A single ticket comment object.

+ Parameters
    + id (string) ... The ID of the ticket comment (as a UUID).

### Retrieve a Ticket Comment [GET]
Returns a single ticket comment object.

+ Response 200

### Update a Ticket Comment [PATCH]
Update a ticket comment.

+ Response 204

### Delete a Ticket Comment [DELETE]
Delete a ticket comment.

+ Response 204
