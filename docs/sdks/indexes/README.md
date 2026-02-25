# Indexes

## Overview

Organize entities into indexes

### Available Operations

* [list](#list) - List indexes
* [create](#create) - Create an index
* [get](#get) - Get an index
* [update](#update) - Update an index
* [delete](#delete) - Delete an index

## list

List all indexes with entity counts

### Example Usage

<!-- UsageSnippet language="python" operationID="listIndexes" method="get" path="/api/indexes" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.indexes.list(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `search`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Search by name or description                                       |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Number of results to skip for pagination                            |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Maximum number of results                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListIndexesResponse](../../models/listindexesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## create

Create a new index to organize entities

### Example Usage

<!-- UsageSnippet language="python" operationID="createIndex" method="post" path="/api/indexes" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.indexes.create(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.IndexResponse](../../models/indexresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## get

Get a specific index by ID with entity count

### Example Usage

<!-- UsageSnippet language="python" operationID="getIndex" method="get" path="/api/indexes/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.indexes.get(id="d3c99902-a26e-4cc2-b667-92943e206a8d")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.IndexResponse](../../models/indexresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## update

Update an existing index

### Example Usage

<!-- UsageSnippet language="python" operationID="updateIndex" method="put" path="/api/indexes/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.indexes.update(id="d30d49d3-196c-4e7a-ae21-dbd9e8d3bae0")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `is_public`                                                         | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `preferred_predicates`                                              | List[*str*]                                                         | :heavy_minus_sign:                                                  | Preferred predicate types for this index                            |
| `rules`                                                             | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Custom rules or instructions for triple generation in this index    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.IndexResponse](../../models/indexresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400, 404                 | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## delete

Delete an index and optionally its entities

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteIndex" method="delete" path="/api/indexes/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.indexes.delete(id="fdeecde6-d243-4f7f-a14f-afd8d537c824", delete_entities=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `delete_entities`                                                   | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Also delete all entities in this index                              |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SuccessMessage](../../models/successmessage.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |