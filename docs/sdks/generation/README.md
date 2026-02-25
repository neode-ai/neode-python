# Generation

## Overview

AI-powered triple generation from natural language

### Available Operations

* [generate_triples](#generate_triples) - Generate triples

## generate_triples

Use OpenAI to extract knowledge triples from natural language. Supports web search for real-time information. Streams responses by default, use format=json for non-streaming.

### Example Usage

<!-- UsageSnippet language="python" operationID="generateTriples" method="post" path="/api/triples/generate" -->
```python
from neode import Neode
import os


with Neode(
    bearer_auth=os.getenv("NEODE_BEARER_AUTH", ""),
) as n_client:

    res = n_client.generation.generate_triples(query="Extract facts about Tesla's Q4 2025 earnings", index_id="550e8400-e29b-41d4-a716-446655440000", format_="json", web_search=True, triple_count=10, news_search=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                            | Type                                                                                                                                                 | Required                                                                                                                                             | Description                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `query`                                                                                                                                              | *str*                                                                                                                                                | :heavy_check_mark:                                                                                                                                   | Natural language description of what to extract triples about                                                                                        |
| `index_id`                                                                                                                                           | *str*                                                                                                                                                | :heavy_check_mark:                                                                                                                                   | Index for entity disambiguation (required)                                                                                                           |
| `format_`                                                                                                                                            | [Optional[models.Format]](../../models/format_.md)                                                                                                   | :heavy_minus_sign:                                                                                                                                   | Response format. 'json' returns a standard JSON response (default, recommended for SDKs). 'stream' returns a Vercel AI SDK data stream for chat UIs. |
| `graph_id`                                                                                                                                           | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Graph to store generated triples in                                                                                                                  |
| `web_search`                                                                                                                                         | *Optional[bool]*                                                                                                                                     | :heavy_minus_sign:                                                                                                                                   | Enable web search for real-time information                                                                                                          |
| `triple_count`                                                                                                                                       | *Optional[int]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Target number of triples to generate (approximate)                                                                                                   |
| `predicates`                                                                                                                                         | List[*str*]                                                                                                                                          | :heavy_minus_sign:                                                                                                                                   | Restrict to specific predicate types                                                                                                                 |
| `subject_entity`                                                                                                                                     | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Constrain all generated triples to use this exact subject                                                                                            |
| `rules`                                                                                                                                              | *Optional[str]*                                                                                                                                      | :heavy_minus_sign:                                                                                                                                   | Custom rules or instructions for the AI generation                                                                                                   |
| `news_search`                                                                                                                                        | *Optional[bool]*                                                                                                                                     | :heavy_minus_sign:                                                                                                                                   | Enable news-specific search for recent events                                                                                                        |
| `retries`                                                                                                                                            | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                     | :heavy_minus_sign:                                                                                                                                   | Configuration to override the default retry behavior of the client.                                                                                  |

### Response

**[models.GenerateTriplesResponse](../../models/generatetriplesresponse.md)**

### Errors

| Error Type                      | Status Code                     | Content Type                    |
| ------------------------------- | ------------------------------- | ------------------------------- |
| errors.Error                    | 400                             | application/json                |
| errors.InsufficientCreditsError | 402                             | application/json                |
| errors.Error                    | 500                             | application/json                |
| errors.NeodeDefaultError        | 4XX, 5XX                        | \*/\*                           |