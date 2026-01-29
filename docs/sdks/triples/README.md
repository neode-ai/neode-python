# Triples

## Overview

Store and query knowledge as subject-predicate-object triples

### Available Operations

* [query](#query) - Query triples
* [create](#create) - Create triples
* [update](#update) - Update a triple
* [delete](#delete) - Delete triples

## query

Retrieve triples with various filtering options. Use this to query your knowledge graph.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryTriples" method="get" path="/api/triples" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.query(offset=0, limit=50)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `search`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Full-text search across subject, predicate, and object              |
| `subject`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by exact subject match                                       |
| `graph_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by graph ID                                                  |
| `index_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by index ID                                                  |
| `subject_entity_id`                                                 | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by subject entity ID                                         |
| `object_entity_id`                                                  | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by object entity ID                                          |
| `predicate`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by predicate (can be repeated for multiple predicates)       |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Number of results to skip for pagination                            |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Maximum number of results                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.QueryTriplesResponse](../../models/querytriplesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## create

Create one or more triples. Entities are automatically created/disambiguated based on subject and object names.

### Example Usage

<!-- UsageSnippet language="python" operationID="createTriples" method="post" path="/api/triples" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.create(triples=[
        {
            "subject": "Elon Musk",
            "predicate": "founded",
            "object": "SpaceX",
            "object_type": "entity",
            "confidence": 0.95,
            "source": "https://wikipedia.org/wiki/SpaceX",
        },
    ], index_id="550e8400-e29b-41d4-a716-446655440000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `triples`                                                           | List[[models.TripleCreate](../../models/triplecreate.md)]           | :heavy_check_mark:                                                  | N/A                                                                 |
| `index_id`                                                          | *str*                                                               | :heavy_check_mark:                                                  | Index for entity disambiguation (required)                          |
| `graph_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Default graph for all triples                                       |
| `source`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Default source for all triples                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.CreateTriplesResponse](../../models/createtriplesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## update

Update an existing triple by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTriple" method="put" path="/api/triples" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.update(id="09e374df-0d13-4f0b-af04-6e489ba8e428")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `subject`                                                           | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `predicate`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `object`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `confidence`                                                        | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | N/A                                                                 |
| `source`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `graph_id`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.UpdateTripleResponse](../../models/updatetripleresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |

## delete

Delete one or more triples by ID

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteTriples" method="delete" path="/api/triples" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.triples.delete()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Single triple ID to delete                                          |
| `ids`                                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Comma-separated list of triple IDs for batch delete                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DeleteTriplesResponse](../../models/deletetriplesresponse.md)**

### Errors

| Error Type               | Status Code              | Content Type             |
| ------------------------ | ------------------------ | ------------------------ |
| errors.Error             | 400                      | application/json         |
| errors.Error             | 500                      | application/json         |
| errors.NeodeDefaultError | 4XX, 5XX                 | \*/\*                    |