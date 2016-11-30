# Jobs

## The job object

An organization's jobs.

```json
{
  "id": 6404,
  "name": "Archaeologist",
  "requisition_id": "abc123",
  "notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
  "status": "closed",
  "created_at": "2013-12-10T14:42:58Z",
  "opened_at": "2013-12-11T14:42:58Z",
  "closed_at": "2013-12-12T14:42:58Z",
  "departments": [
    {
      "id": 562,
      "name": "Exploration"
    }
  ],
  "offices": [
    {
      "id": 175,
      "name": "San Francisco",
      "location": {
        "name": "San Francisco, CA"
      }
    }
  ],
  "custom_fields": {
    "employment_type": "Full-Time",
    "maximum_budget": "$81.5k",
    "salary_range": {
      "min_value": 70000,
      "max_value": 90000,
      "unit": "USD"
    }
  },
  "hiring_team": {
    "hiring_managers": [
      {
        "id": 84275,
        "name": "Kaylee Prime"
      },
      {
        "id": 169779,
        "name": "Hank Hollandaise"
      }
    ],
    "recruiters": [
      {
        "id": 81111,
        "name": "Samuel Skateboard",
        "responsible": false
      },
      {
        "id": 153448,
        "name": "Stegosaurus Heels",
        "responsible": true
      }
    ],
    "coordinators": [
      {
        "id": 122635,
        "name": "Teddy Pizzazz",
        "responsible": true
      },
      {
        "id": 177046,
        "name": "Mirandella Lager",
        "responsible": false
      }
    ],
    "sourcers": [
      {
        "id": 122635,
        "name": "Teddy Pizzazz"
      }
    ]
  },
  "openings": [
    {
      "opening_id": "3-1",
      "status": "open",
      "opened_at": "2015-11-20T23:14:14.736Z",
      "closed_at": null,
      "application_id": null
    },
    {
      "opening_id": "3-2",
      "status": "open",
      "opened_at": "2015-11-20T23:14:14.739Z",
      "closed_at": null,
      "application_id": null
    },
    {
      "opening_id": null,
      "status": "open",
      "opened_at": "2016-02-03T20:00:00.000Z",
      "closed_at": null,
      "application_id": null
    },
    {
      "opening_id": "2-4",
      "status": "closed",
      "opened_at": "2016-02-03T16:38:46.985Z",
      "closed_at": "2016-02-03T16:39:09.811Z",
      "application_id": 1232
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The job's unique identifier |
| requisition_id | An arbitrary ID provided by an external source; does not map to another entity within Greenhouse.
| status | One of `open`, `closed`, `draft`.
| departments | An array containing the [department](#departments) which this job belongs to.
| offices | An array containing the [offices](#offices) this job is associated with.
| hiring_team | Lists the names and User IDs of the hiring managers, recruiters, coordinators and sourcers associated with this job. For recruiters and coordinators, there is a `responsible` boolean flag which indicates that the user is the responsible recruiter or coordinator for this job.
| custom_fields | Contains any custom job fields which have been defined by your organization.
| openings | Lists the openings associated with this job.
| openings[].id | Custom identifier set by an organization. Can be `null`.
| openings[].status | One of: `["open", "closed"]`
| openings[].opened_at | Timestamp when the opening was created. |
| openings[].closed_at | Timestamp when the opening was closed. An opening is closed when it is filled or removed.
| openings[].application_id | If the opening is closed and a candidate was hired to fill the opening, this is the ID of the candidate's application. Otherwise, null.


## GET: List Jobs

```shell
curl 'https://harvest.greenhouse.io/v1/jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 144371,
    "name": "Good Cop",
    "requisition_id": "1",
    "notes": null,
    "status": "open",
    "created_at": "2015-11-19T19:53:32.662Z",
    "opened_at": "2015-11-19T19:53:32.662Z",
    "closed_at": null,
    "departments": [
      {
        "id": 13585,
        "name": "Rule Enforcement"
      }
    ],
    "offices": [
      {
        "id": 8787,
        "name": "New York City",
        "location": {
          "name": "New York, NY, United States"
        }
      }
    ],
    "hiring_team": {
      "hiring_managers": [
        {
          "id": 158108,
          "name": "Sam McsSamson"
        }
      ],
      "recruiters": [
        {
          "id": 158101,
          "name": "Major Tom",
          "responsible": true
        }
      ],
      "coordinators": [
        {
          "id": 158109,
          "name": "Roger Cord",
          "responsible": true
        }
      ],
      "sourcers": [
        {
          "id": 158102,
          "name": "Lara Sourcerer"
        }
      ]
    },
    "custom_fields": {
      "bonus": "1000",
      "employment_type": "Full-time",
      "options": "2000",
      "salary": "54111"
    },
    "openings": [
      {
        "opening_id": "1-1",
        "status": "closed",
        "opened_at": "2015-11-19T19:53:32.564Z",
        "closed_at": "2016-01-26T23:59:07.592Z",
        "application_id": 24709881
      },
      {
        "opening_id": "1-2",
        "status": "open",
        "opened_at": "2015-11-19T19:53:32.565Z",
        "closed_at": null,
        "application_id": null
      }
    ]
  }
]
```

List all of an organization's jobs.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only jobs that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only jobs that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only jobs that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only jobs that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.


<br>
[See noteworthy response attributes.](#the-job-object)


## GET: Retrieve Job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 144371,
  "name": "Good Cop",
  "requisition_id": "1",
  "notes": null,
  "status": "open",
  "created_at": "2015-11-19T19:53:32.662Z",
  "opened_at": "2015-11-19T19:53:32.662Z",
  "closed_at": null,
  "departments": [
    {
      "id": 13585,
      "name": "Rule Enforcement"
    }
  ],
  "offices": [
    {
      "id": 8787,
      "name": "New York City",
      "location": {
        "name": "New York, NY, United States"
      }
    }
  ],
  "hiring_team": {
    "hiring_managers": [
      {
        "id": 158108,
        "name": "Sam McsSamson"
      }
    ],
    "recruiters": [
      {
        "id": 158101,
        "name": "Major Tom",
        "responsible": true
      }
    ],
    "coordinators": [
      {
        "id": 158109,
        "name": "Roger Cord",
        "responsible": true
      }
    ],
    "sourcers": [
      {
        "id": 158102,
        "name": "Lara Sourcerer"
      }
    ]
  },
  "custom_fields": {
    "bonus": "1000",
    "employment_type": "Full-time",
    "options": "2000",
    "salary": "54111"
  },
  "openings": [
    {
      "opening_id": "1-1",
      "status": "closed",
      "opened_at": "2015-11-19T19:53:32.564Z",
      "closed_at": "2016-01-26T23:59:07.592Z",
      "application_id": 24709881
    },
    {
      "opening_id": "1-2",
      "status": "open",
      "opened_at": "2015-11-19T19:53:32.565Z",
      "closed_at": null,
      "application_id": null
    }
  ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve

<br>
[See noteworthy response attributes.](#the-job-object)

## PATCH: Update Job

```shell
curl --request PATCH 'https://harvest.greenhouse.io/v1/jobs/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
   "id": 144371,
   "name": "New job name",
   "requisition_id": "1",
   "notes": "Here are some notes",
   "team_and_responsibilities": "Info",
   "how_to_sell_this_job": "the snacks",
   "custom_fields": [
    {
        "id": 1234,
        "value": "Some new value"
    },
    {
        "name_key": "salary_range",
        "min_value": 100000,
        "max_value": 150000,
        "unit": "USD"
   },
   {
        "id": 5678,
        "delete_value": "true"
   }
  ]
}
```

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/jobs/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
name | No | string | The job's name
notes | No | string | Notes on the hiring plan
anywhere | No | boolean | Boolean value indicating where the job can be done anywhere
requisition_id | No | string | The id of the requisition corresponding to this job posting, if applicable
team_and_responsibilities | No | string | A description of the team the candidate would join and their responsibilities
how_to_sell_this_job | No | string | A description for the recruiter of the desirable aspects of the job
custom_fields | No | custom_field | Array of hashes containing new custom field values.  Passing an empty array does nothing.

### Custom Field Parameters

The custom field parameter structure is different in the PATCH method then in GET methods and responses.  Certain type of custom fields require different elements to be included, while deleting a field requires a specific argument.  What follows is the description of each item in a custom field element and what is required depending on the type.

Parameter | Required for | Description
---------- | -------------- | ----------------
id | all | The custom field id for this particular custom field.  One of this or name_key is required.
name_key | all | The field key for this custom field. This can be found in Greenhouse while editing custom options as "Immutable Field Key"  This or id is required for all custom field elements.
value | all | The value field contains the new custom field value.  In most cases this will be a string or a number.  In the case of single-select or multi-select custom fields, this will be a custom field option id or an array of custom field option ids, respectively.  Value is only not used for range type custom fields.
min_value | number_range, currency range | This contains the minimum value that is allowable for this custom field.  Must be less than max_value
max_value | number_range, currency_range | This contains the maximum value that is allowable for this custom field.  Must be greater than min_value
unit | currency, currency_range | This contains the currency unit for a currency custom field. It is only required when updating a currency custom field.  This should accept any 3-character currency code from the ISO-4217 standard.
delete_value  | n/a | When this element is included with a value of "true" (note, string true, not boolean true) the custom field value will be removed from Greenhouse.  Note that updating a custom field value to nil or a blank string will not work, as validations require these to be non-blank values.

> The above returns a JSON response, structured like this:

```
{
  "id": 112746,
  "name": "new name",
  "requisition_id": 2,
  "notes": "Looking for the best!",
  "status": "open",
  "created_at": "2015-09-10T19:01:46.078Z",
  "opened_at": "2015-09-10T19:01:46.078Z",
  "closed_at": null,
  "departments": [
    {
      "id": 74,
      "name": "Guideshops",
      "parent_id": null,
      "child_ids": []
    }
  ],
  "offices": [
    {
      "id": 1556,
      "name": "San Diego",
      "location": {
        "name": "San Diego, CA, United States"
      },
      "parent_id": null,
      "child_ids": []
    }
  ],
  "hiring_team": {
    "hiring_managers": [],
    "recruiters": [],
    "coordinators": [],
    "sourcers": []
  },
  "custom_fields": {
    "employment_type": null,
    "salary": null,
    "bonus": null,
    "options": null
  },
  "openings": [
    {
      "opening_id": null,
      "status": "closed",
      "opened_at": "2015-09-10T19:01:46.077Z",
      "closed_at": "2015-09-21T21:28:17.628Z",
      "application_id": 18682391
    },
    {
      "opening_id": null,
      "status": "closed",
      "opened_at": "2015-09-21T21:28:17.679Z",
      "closed_at": "2016-03-09T20:07:35.649Z",
      "application_id": 18492607
    },
    {
      "opening_id": null,
      "status": "open",
      "opened_at": "2016-03-09T20:07:35.675Z",
      "closed_at": null,
      "application_id": null
    }
  ]
}
```

<br>
[See noteworthy response attributes.](#the-job-object)