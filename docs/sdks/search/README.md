# Search

## Overview

Semantic search across your knowledge graph

### Available Operations

* [semantic_get](#semantic_get) - Semantic search (GET)
* [semantic](#semantic) - Semantic search (POST)

## semantic_get

Search across entities, triples, and graphs using natural language. Uses vector embeddings for semantic similarity matching.

### Example Usage

<!-- UsageSnippet language="python" operationID="semanticSearchGet" method="get" path="/api/search" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.search.semantic_get(q="<value>", types=[

    ], offset=0, limit=20, threshold=0.3)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `q`                                                                 | *str*                                                               | :heavy_check_mark:                                                  | Natural language search query                                       |
| `types`                                                             | List[[models.SearchType](../../models/searchtype.md)]               | :heavy_minus_sign:                                                  | Types to search                                                     |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter results to a specific index                                  |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Number of results to skip for pagination                            |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Maximum results per type (default 20, max 100)                      |
| `threshold`                                                         | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | Minimum similarity score 0-1 (default 0.3)                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SemanticSearchGetResponse](../../models/semanticsearchgetresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## semantic

Search across entities, triples, and graphs using natural language. Uses vector embeddings for semantic similarity matching.

### Example Usage: basic

<!-- UsageSnippet language="python" operationID="semanticSearch" method="post" path="/api/search" example="basic" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.search.semantic(query="electric vehicle companies", types=[
        "entities",
        "triples",
    ], limit=20, threshold=0.3)

    # Handle response
    print(res)

```
### Example Usage: filtered

<!-- UsageSnippet language="python" operationID="semanticSearch" method="post" path="/api/search" example="filtered" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.search.semantic(query="who founded SpaceX", types=[
        "triples",
    ], index_id="550e8400-e29b-41d4-a716-446655440000", limit=10, threshold=0.5)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `query`                                                             | *str*                                                               | :heavy_check_mark:                                                  | Natural language search query                                       |
| `types`                                                             | List[[models.SearchType](../../models/searchtype.md)]               | :heavy_minus_sign:                                                  | Types of objects to search                                          |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter results to a specific index                                  |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Maximum results per type                                            |
| `threshold`                                                         | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | Minimum similarity score (0-1)                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.SemanticSearchResponse](../../models/semanticsearchresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |