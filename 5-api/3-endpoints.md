# API (v1) Endpoints

**Base API URL: `{{DIRECTUS_ROOT}}/api/1/`**


Resource | Return
:---------|:----------------
**`GET  privileges/:groupId/`**  |  JSON object of the privileges for a given group
**`GET tables/:table/rows/`**  |  Collection of table entries viewable by authenticated user
**`GET tables/:table/rows/:id`**  |  JSON object of a given table entry
**`GET activity/`**  |  Collection of latest directus/db activity
**`GET tables/:table/columns/`**  |  Collection of the column details for a given table
**`GET tables/:table/columns/:column/`**  |  Details for a given column in a given table
**`GET groups/`**  |  Collection of directus user-groups
**`GET groups/:id`**  |  User-group information
**`GET preferences/:table`**  |  Preferences for a given table
**`GET bookmarks/`**  |  Bookmarks for currently authenticated user
**`GET bookmarks/:id`**  |  Bookmark details for a specified bookmark (must belong to authenticated user)
**`GET tables/`**  |  Collection of all tables registered with Directus
**`GET messages/rows`**  |  Collection of messages for the authenticated user
**`GET messages/rows/:id`**  |  Message details for a given message



# Global Parameters

Parameter  |  Example  |  Description
:-----------|:-----------|:-----------------------
**`currentPage`**  |  *`0`, `1`, `2`*  |  Current page for paginated results
**`perPage`**  |  *`100`, `200`, `300`*  |  Number of results per page
**`sort`**  |  *`id`, `title`, `date_uploaded`*  |  Column to sort results upon
**`sort_order`**  |  *`ASC`, `DESC`*  |  Order direction for sorting
**`active`**  |  *`1`, `1,2`, `2`*  |  Filter by a CSV of status values **for tables with a status column** such as `active`
**`columns_visible`**  |  *`title`, `date`*  |  Name of column shown in results. Can be chained such as: `columns_visible=title&columns_visibile=first_name`


# Examples

## GET  privileges/:groupId/
*Returns JSON object of the privileges for a given group*

#### Example Request
**GET** http://directus.dev/api/1/privileges/0

```json
[
  {
    "id": "23",
    "table_name": "countries",
    "permissions": "add,edit,bigedit,delete,bigdelete,alter,view,bigview",
    "group_id": "0",
    "read_field_blacklist": null,
    "write_field_blacklist": null,
    "unlisted": null
  },
  {
    "id": "1",
    "table_name": "directus_activity",
    "permissions": "add,edit,bigedit,delete,bigdelete,alter,view,bigview",
    "group_id": "0",
    "read_field_blacklist": null,
    "write_field_blacklist": null,
    "unlisted": null
  },
  {
    "id": "18",
    "table_name": "directus_bookmarks",
    "permissions": "add,edit,bigedit,delete,bigdelete,alter,view,bigview",
    "group_id": "0",
    "read_field_blacklist": null,
    "write_field_blacklist": null,
    "unlisted": null
  }
]
```

## GET  tables/:table/rows/
*Returns a collection of table entries the authenticated user has permission to view*

Parameter  |  Example  |  Description
:-----------|:-----------|:-----------------------
**`ids`**  |  `1,2,3,5,6,7,8`  |  Comma delimited list of ids to return

#### Example Request
**GET** http://directus.dev/api/1/tables/directus_users/rows

```json
{
  "active": 1,
  "inactive": 0,
  "trash": 0,
  "total": 1,
  "rows": [
    {
      "id": 3,
      "active": 1,
      "first_name": "John",
      "last_name": "Smith",
      "email": "john.smith@example.com",
      "password": "asfafspojd92en1oi2n31b412ubb1n",
      "salt": "5329e597d9afa",
      "position": "",
      "email_messages": 1,
      "last_login": null,
      "last_access": null,
      "last_page": "",
      "ip": "",
      "group": {
            "id": 0,
            "name": "Administrator",
            "description": null,
            "restrict_to_ip_whitelist": 0
      },
      "avatar": null,
      "location": "",
      "phone": "",
      "address": "",
      "city": "",
      "state": "",
      "zip": ""
    }
]
```