# Graphs

## Overview

Organize triples into graphs

### Available Operations

* [list_all](#list_all) - List graphs
* [create](#create) - Create a graph
* [get](#get) - Get a graph
* [delete](#delete) - Delete a graph

## list_all

List all graphs with triple counts

### Example Usage

<!-- UsageSnippet language="python" operationID="listGraphs" method="get" path="/api/graphs" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.graphs.list_all(limit=50)

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

**[models.ListGraphsResponse](../../models/listgraphsresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## create

Create a new graph to organize triples

### Example Usage

<!-- UsageSnippet language="python" operationID="createGraph" method="post" path="/api/graphs" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.graphs.create(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `name`                                                                      | *str*                                                                       | :heavy_check_mark:                                                          | N/A                                                                         |
| `description`                                                               | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `index_id`                                                                  | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | N/A                                                                         |
| `metadata`                                                                  | [Optional[models.GraphCreateMetadata]](../../models/graphcreatemetadata.md) | :heavy_minus_sign:                                                          | N/A                                                                         |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.CreateGraphResponse](../../models/creategraphresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## get

Get a specific graph by ID with triple count

### Example Usage

<!-- UsageSnippet language="python" operationID="getGraph" method="get" path="/api/graphs/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.graphs.get(id="e80002d6-317d-4bf6-8a6f-0e1b5532a7d8")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.GetGraphResponse](../../models/getgraphresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## delete

Delete a graph and optionally its triples

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteGraph" method="delete" path="/api/graphs/{id}" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.graphs.delete(id="36c00bb2-7b2d-44d3-b87f-0e9a30a59845", delete_triples=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `delete_triples`                                                    | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Also delete all triples in this graph                               |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteGraphResponse](../../models/deletegraphresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 404                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |