# SemanticSearchGetRequest


## Fields

| Field                                              | Type                                               | Required                                           | Description                                        |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| `q`                                                | *str*                                              | :heavy_check_mark:                                 | Natural language search query                      |
| `types`                                            | List[[models.SearchType](../models/searchtype.md)] | :heavy_minus_sign:                                 | Types to search                                    |
| `index_id`                                         | *Optional[str]*                                    | :heavy_minus_sign:                                 | Filter results to a specific index                 |
| `offset`                                           | *Optional[int]*                                    | :heavy_minus_sign:                                 | Number of results to skip for pagination           |
| `limit`                                            | *Optional[int]*                                    | :heavy_minus_sign:                                 | Maximum results per type (default 20, max 100)     |
| `threshold`                                        | *Optional[float]*                                  | :heavy_minus_sign:                                 | Minimum similarity score 0-1 (default 0.3)         |