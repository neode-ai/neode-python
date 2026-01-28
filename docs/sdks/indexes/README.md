# Indexes

## Overview

Organize entities into indexes

### Available Operations

* [list](#list) - List indexes
* [create](#create) - Create an index

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

    res = n_client.indexes.list(limit=50)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `search`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Search by name or description                                       |
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

**[models.CreateIndexResponse](../../models/createindexresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |