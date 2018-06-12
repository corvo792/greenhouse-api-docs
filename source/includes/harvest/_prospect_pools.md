# Prospect Pools

## The prospect pools object

An organization's prospect pools.

```json
{
    "id": 25,
    "name": "Cold Outreach: Sourced",
    "active": true,
    "prospect_stages": [
        {
            "id": 85,
            "name": "Discussed"
        },
        {
            "id": 86,
            "name": "Had email listed on their blog"
        }
    ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The pool's unique identifier |
| active | true or false. False means the pool is hidden from view in Greenhouse.

## GET: List Prospect Pools

```shell
curl 'https://harvest.greenhouse.io/v1/prospect_pools'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```json
[
    {
        "id": 25,
        "name": "Cold Outreach: Sourced",
        "active": true,
        "prospect_stages": [
            {
                "id": 85,
                "name": "Discussed"
            },
            {
                "id": 86,
                "name": "Had email listed on their business card"
            },
            {
                "id": 87,
                "name": "Had email listed on their blog"
            },
            {
                "id": 88,
                "name": "Not Contacted"
            }
        ]
    },
    {
        "id": 26,
        "name": "Opted In: Referral",
        "active": false,
        "prospect_stages": [
            {
                "id": 90,
                "name": "1st. Follow Up Sent-90"
            },
            {
                "id": 91,
                "name": "2nd Follow Up Sent-91"
            },
            {
                "id": 92,
                "name": "In Discussion-92"
            },
            {
                "id": 93,
                "name": "Discussed-93"
            },
            {
                "id": 94,
                "name": "Had email listed on their github profile-94"
            }
        ]
    }
]
```

List all of an organization's prospect pools.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/prospect_pools`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.

<br>
[See noteworthy response attributes.](#the-prospect-pool-object)


## GET: Retrieve Prospect Pool

```shell
curl 'https://harvest.greenhouse.io/v1/prospect_pools/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```json
{
    "id": 25,
    "name": "Cold Outreach: Sourced",
    "active": true,
    "prospect_stages": [
        {
            "id": 85,
            "name": "Discussed"
        },
        {
            "id": 86,
            "name": "Had email listed on their blog"
        }
    ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/prospect_pools/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the prospect pool to retrieve

<br>
[See noteworthy response attributes.](#the-prospect-pool-object)