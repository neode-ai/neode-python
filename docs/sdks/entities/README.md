# Entities

## Overview

Manage entities (subjects and objects) with automatic disambiguation

### Available Operations

* [list](#list) - List entities
* [create](#create) - Create an entity
* [get](#get) - Get an entity
* [update](#update) - Update an entity
* [delete](#delete) - Delete an entity

## list

Search and list entities. Entities are automatically created when triples are stored.

### Example Usage

<!-- UsageSnippet language="python" operationID="listEntities" method="get" path="/api/entities" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.entities.list(exact=False, offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `search`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Search by name or description                                       |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by index ID                                                  |
| `exact`                                                             | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Use exact name matching instead of fuzzy search                     |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Number of results to skip for pagination                            |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Maximum number of results                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListEntitiesResponse](../../models/listentitiesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## create

Manually create an entity. Note: entities are also auto-created when storing triples.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntity" method="post" path="/api/entities" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.entities.create(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CreateEntityResponse](../../models/createentityresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## get

Get a specific entity by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="getEntity" method="get" path="/api/entities/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.entities.get(id="d919603f-4abe-4b60-83d8-56320a0a9875")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetEntityResponse](../../models/getentityresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## update

Update an existing entity

### Example Usage

<!-- UsageSnippet language="python" operationID="updateEntity" method="put" path="/api/entities/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.entities.update(id="d181c8e9-9612-4e8d-b176-bf3218d3e4c9")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `avatar_url`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.UpdateEntityResponse](../../models/updateentityresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400, 404                 | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## delete

Delete an entity by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteEntity" method="delete" path="/api/entities/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.entities.delete(id="603fb0b8-b005-4f8f-b4f0-6d3e338d4ab9")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SuccessMessage](../../models/successmessage.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |